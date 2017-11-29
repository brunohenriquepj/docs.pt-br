---
title: "Função CorBindToRuntime"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorBindToRuntime
api_location:
- mscoree.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: CorBindToRuntime
helpviewer_keywords: CorBindToRuntime function [.NET Framework hosting]
ms.assetid: 799740aa-46ec-4532-95da-6444565b4971
topic_type: apiref
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a833be39f93082e8d2c0cb28f435f754143721f2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="corbindtoruntime-function"></a><span data-ttu-id="798dc-102">Função CorBindToRuntime</span><span class="sxs-lookup"><span data-stu-id="798dc-102">CorBindToRuntime Function</span></span>
<span data-ttu-id="798dc-103">Habilita a hosts não gerenciados para carregar o common language runtime (CLR) em um processo.</span><span class="sxs-lookup"><span data-stu-id="798dc-103">Enables unmanaged hosts to load the common language runtime (CLR) into a process.</span></span>  
  
 <span data-ttu-id="798dc-104">Essa função foi preterida no [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="798dc-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="798dc-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="798dc-105">Syntax</span></span>  
  
```  
HRESULT CorBindToRuntime (  
    [in]  LPCWSTR     pwszVersion,   
    [in]  LPCWSTR     pwszBuildFlavor,   
    [in]  REFCLSID    rclsid,   
    [in]  REFIID      riid,   
    [out] LPVOID FAR  *ppv  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="798dc-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="798dc-106">Parameters</span></span>  
 `pwszVersion`  
 <span data-ttu-id="798dc-107">[in] Uma cadeia de caracteres que descreve a versão do CLR que você deseja carregar.</span><span class="sxs-lookup"><span data-stu-id="798dc-107">[in] A string describing the version of the CLR you want to load.</span></span>  
  
 <span data-ttu-id="798dc-108">Um número de versão do .NET Framework consiste em quatro partes separadas por pontos: *Revision*.</span><span class="sxs-lookup"><span data-stu-id="798dc-108">A version number in the .NET Framework consists of four parts separated by periods: *major.minor.build.revision*.</span></span> <span data-ttu-id="798dc-109">A cadeia de caracteres passada como `pwszVersion` deve começar com o caractere "v" seguido as primeiras três partes do número de versão (por exemplo, "v1.0.1529").</span><span class="sxs-lookup"><span data-stu-id="798dc-109">The string passed as `pwszVersion` must start with the character "v" followed by the first three parts of the version number (for example, "v1.0.1529").</span></span>  
  
 <span data-ttu-id="798dc-110">Algumas versões do CLR são instalados com uma declaração de política que especifica a compatibilidade com versões anteriores do CLR.</span><span class="sxs-lookup"><span data-stu-id="798dc-110">Some versions of the CLR are installed with a policy statement that specifies compatibility with previous versions of the CLR.</span></span> <span data-ttu-id="798dc-111">Por padrão, a correção de inicialização avalia `pwszVersion` em declarações de política e carrega a versão mais recente do tempo de execução que é compatível com a versão que está sendo solicitada.</span><span class="sxs-lookup"><span data-stu-id="798dc-111">By default, the startup shim evaluates `pwszVersion` against policy statements and loads the latest version of the runtime that is compatible with the version being requested.</span></span> <span data-ttu-id="798dc-112">Um host pode forçar a correção para ignorar a avaliação de política e carregar a versão exata especificada no `pwszVersion` passando um valor de `STARTUP_LOADER_SAFEMODE` para o `flags` parâmetro, conforme descrito abaixo.</span><span class="sxs-lookup"><span data-stu-id="798dc-112">A host can force the shim to skip policy evaluation and load the exact version specified in `pwszVersion` by passing a value of  `STARTUP_LOADER_SAFEMODE` for the `flags` parameter, as described below.</span></span>  
  
 <span data-ttu-id="798dc-113">Se o chamador especificar null para `pwszVersion`, a versão mais recente do tempo de execução é carregada.</span><span class="sxs-lookup"><span data-stu-id="798dc-113">If the caller specifies null for `pwszVersion`, the latest version of the runtime is loaded.</span></span> <span data-ttu-id="798dc-114">Passando null não fornece o host nenhum controle sobre qual versão do tempo de execução é carregado.</span><span class="sxs-lookup"><span data-stu-id="798dc-114">Passing null gives the host no control over which version of the runtime is loaded.</span></span> <span data-ttu-id="798dc-115">Embora essa abordagem pode ser apropriada em alguns cenários, é altamente recomendável que o host de fornece uma versão específica para carregar.</span><span class="sxs-lookup"><span data-stu-id="798dc-115">Although this approach may be appropriate in some scenarios, it is strongly recommended that the host supply a specific version to load.</span></span>  
  
 `pwszBuildFlavor`  
 <span data-ttu-id="798dc-116">[in] Uma cadeia de caracteres que especifica se a carga do servidor ou a compilação de estação de trabalho do CLR.</span><span class="sxs-lookup"><span data-stu-id="798dc-116">[in] A string that specifies whether to load the server or the workstation build of the CLR.</span></span> <span data-ttu-id="798dc-117">Os valores válidos são `svr` e `wks`.</span><span class="sxs-lookup"><span data-stu-id="798dc-117">Valid values are `svr` and `wks`.</span></span> <span data-ttu-id="798dc-118">A compilação do servidor é otimizada para tirar proveito de vários processadores para coletas de lixo e a compilação de estação de trabalho é otimizada para aplicativos de cliente em execução em um computador com processador único.</span><span class="sxs-lookup"><span data-stu-id="798dc-118">The server build is optimized to take advantage of multiple processors for garbage collections, and the workstation build is optimized for client applications running on a single-processor machine.</span></span>  
  
 <span data-ttu-id="798dc-119">Se `pwszBuildFlavor` for definido como null, a compilação de estação de trabalho está carregada.</span><span class="sxs-lookup"><span data-stu-id="798dc-119">If `pwszBuildFlavor` is set to null, the workstation build is loaded.</span></span> <span data-ttu-id="798dc-120">Quando em execução em um computador com processador único, a compilação de estação de trabalho é sempre carregada, mesmo se `pwszBuildFlavor` é definido como `svr`.</span><span class="sxs-lookup"><span data-stu-id="798dc-120">When running on a single-processor machine, the workstation build is always loaded, even if `pwszBuildFlavor` is set to `svr`.</span></span> <span data-ttu-id="798dc-121">No entanto, se `pwszBuildFlavor` é definido como `svr` e coleta de lixo simultânea for especificada (consulte a descrição do `flags` parâmetro), a compilação do servidor é carregada.</span><span class="sxs-lookup"><span data-stu-id="798dc-121">However, if `pwszBuildFlavor` is set to `svr` and concurrent garbage collection is specified (see the description of the `flags` parameter), the server build is loaded.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="798dc-122">[in] O `CLSID` da coclass que implemente tanto o [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) ou o [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="798dc-122">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="798dc-123">Valores com suporte são CLSID_CorRuntimeHost ou CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="798dc-123">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="798dc-124">[in] O `IID` da interface solicitada de `rclsid`.</span><span class="sxs-lookup"><span data-stu-id="798dc-124">[in] The `IID` of the requested interface from `rclsid`.</span></span> <span data-ttu-id="798dc-125">Valores com suporte são IID_ICorRuntimeHost ou IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="798dc-125">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="798dc-126">[out] O ponteiro de interface retornado para `riid`.</span><span class="sxs-lookup"><span data-stu-id="798dc-126">[out] The returned interface pointer to `riid`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="798dc-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="798dc-127">Remarks</span></span>  
 <span data-ttu-id="798dc-128">Se `pwszVersion` Especifica uma versão de tempo de execução que não existe, `CorBindToRuntimeEx` retorna um valor HRESULT de CLR_E_SHIM_RUNTIMELOAD.</span><span class="sxs-lookup"><span data-stu-id="798dc-128">If `pwszVersion` specifies a runtime version that does not exist, `CorBindToRuntimeEx` returns an HRESULT value of CLR_E_SHIM_RUNTIMELOAD.</span></span>  
  
## <a name="execution-context-and-flow-of-windows-identity"></a><span data-ttu-id="798dc-129">Contexto de execução e o fluxo de identidade do Windows</span><span class="sxs-lookup"><span data-stu-id="798dc-129">Execution Context and Flow of Windows Identity</span></span>  
 <span data-ttu-id="798dc-130">Na versão 1 do CLR, o <xref:System.Security.Principal.WindowsIdentity> não fluxo do objeto pelos pontos assíncronos como novos threads, pools de threads ou retornos de chamada timer.</span><span class="sxs-lookup"><span data-stu-id="798dc-130">In version 1 of the CLR, the <xref:System.Security.Principal.WindowsIdentity> object does not flow across asynchronous points such as new threads, thread pools, or timer callbacks.</span></span> <span data-ttu-id="798dc-131">Na versão 2.0 do CLR, um <xref:System.Threading.ExecutionContext> objeto envolve algumas informações sobre o thread em execução no momento e fluxos de em qualquer ponto assíncrono, mas não nos limites do domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="798dc-131">In version 2.0 of the CLR, an <xref:System.Threading.ExecutionContext> object wraps some information about the currently executing thread and flows it across any asynchronous point, but not across application domain boundaries.</span></span> <span data-ttu-id="798dc-132">Da mesma forma, o <xref:System.Security.Principal.WindowsIdentity> objeto também passa em qualquer ponto assíncrono.</span><span class="sxs-lookup"><span data-stu-id="798dc-132">Similarly, the <xref:System.Security.Principal.WindowsIdentity> object also flows across any asynchronous point.</span></span> <span data-ttu-id="798dc-133">Portanto, a representação atual no thread, se houver, fluxos muito.</span><span class="sxs-lookup"><span data-stu-id="798dc-133">Therefore, the current impersonation on the thread, if any, flows too.</span></span>  
  
 <span data-ttu-id="798dc-134">Você pode alterar o fluxo de duas maneiras:</span><span class="sxs-lookup"><span data-stu-id="798dc-134">You can alter the flow in two ways:</span></span>  
  
1.  <span data-ttu-id="798dc-135">Modificando o <xref:System.Threading.ExecutionContext> configurações para suprimir o fluxo em uma base por thread (consulte o <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>, e <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> métodos).</span><span class="sxs-lookup"><span data-stu-id="798dc-135">By modifying the <xref:System.Threading.ExecutionContext> settings to suppress the flow on a per-thread basis (see the <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>, and <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> methods).</span></span>  
  
2.  <span data-ttu-id="798dc-136">Alterando o modo de processo padrão para o modo de compatibilidade de versão 1, onde o <xref:System.Security.Principal.WindowsIdentity> não fluxo do objeto em qualquer ponto assíncrono, independentemente do <xref:System.Threading.ExecutionContext> configurações no thread atual.</span><span class="sxs-lookup"><span data-stu-id="798dc-136">By changing the process default mode to the version 1 compatibility mode, where the <xref:System.Security.Principal.WindowsIdentity> object does not flow across any asynchronous point, regardless of the <xref:System.Threading.ExecutionContext> settings on the current thread.</span></span> <span data-ttu-id="798dc-137">Como alterar o modo padrão depende se você usar uma interface de hospedagem não gerenciada ou um executável gerenciado para carregar o CLR:</span><span class="sxs-lookup"><span data-stu-id="798dc-137">How you change the default mode depends on whether you use a managed executable or an unmanaged hosting interface to load the CLR:</span></span>  
  
    1.  <span data-ttu-id="798dc-138">Executáveis gerenciados, você deve definir o `enabled` atributo do [ \<legacyImpersonationPolicy >](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) elemento `true`.</span><span class="sxs-lookup"><span data-stu-id="798dc-138">For managed executables, you must set the `enabled` attribute of the [\<legacyImpersonationPolicy>](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) element to `true`.</span></span>  
  
    2.  <span data-ttu-id="798dc-139">Para não gerenciado interfaces de hospedagem, defina o `STARTUP_LEGACY_IMPERSONATION` sinalizador no `flags` parâmetro ao chamar o `CorBindToRuntimeEx` função.</span><span class="sxs-lookup"><span data-stu-id="798dc-139">For unmanaged hosting interfaces, set the `STARTUP_LEGACY_IMPERSONATION` flag in the `flags` parameter when calling the `CorBindToRuntimeEx` function.</span></span>  
  
     <span data-ttu-id="798dc-140">O modo de compatibilidade de versão 1 se aplica a todo o processo e todos os domínios de aplicativo no processo.</span><span class="sxs-lookup"><span data-stu-id="798dc-140">The version 1 compatibility mode applies to the entire process and to all the application domains in the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="798dc-141">Comentários</span><span class="sxs-lookup"><span data-stu-id="798dc-141">Remarks</span></span>  
 <span data-ttu-id="798dc-142">[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) e `CorBindToRuntime` executar a mesma operação, mas o `CorBindToRuntimeEx` função permite que você defina os sinalizadores para especificar o comportamento do CLR.</span><span class="sxs-lookup"><span data-stu-id="798dc-142">[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) and `CorBindToRuntime` perform the same operation, but the `CorBindToRuntimeEx` function allows you to set flags to specify the behavior of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="798dc-143">Requisitos</span><span class="sxs-lookup"><span data-stu-id="798dc-143">Requirements</span></span>  
 <span data-ttu-id="798dc-144">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="798dc-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="798dc-145">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="798dc-145">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="798dc-146">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="798dc-146">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="798dc-147">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="798dc-147">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="798dc-148">Consulte também</span><span class="sxs-lookup"><span data-stu-id="798dc-148">See Also</span></span>  
 [<span data-ttu-id="798dc-149">Função CorBindToCurrentRuntime</span><span class="sxs-lookup"><span data-stu-id="798dc-149">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)  
 [<span data-ttu-id="798dc-150">Função CorBindToRuntimeByCfg</span><span class="sxs-lookup"><span data-stu-id="798dc-150">CorBindToRuntimeByCfg Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)  
 [<span data-ttu-id="798dc-151">Função CorBindToRuntimeEx</span><span class="sxs-lookup"><span data-stu-id="798dc-151">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 [<span data-ttu-id="798dc-152">Função CorBindToRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="798dc-152">CorBindToRuntimeHost Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)  
 [<span data-ttu-id="798dc-153">Interface ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="798dc-153">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)  
 [<span data-ttu-id="798dc-154">Funções de hospedagem CLR reprovadas</span><span class="sxs-lookup"><span data-stu-id="798dc-154">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)