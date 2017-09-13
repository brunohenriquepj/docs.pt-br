---
title: Provedores ETW no CLR
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ETW, CLR providers
- CLR ETW providers
ms.assetid: 0beafad4-b2c8-47f4-b342-83411d57a51f
caps.latest.revision: 7
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 18353939108d58eb2aaffee97e059e4430b25e3a
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="clr-etw-providers"></a><span data-ttu-id="364c3-102">Provedores ETW no CLR</span><span class="sxs-lookup"><span data-stu-id="364c3-102">CLR ETW Providers</span></span>
<span data-ttu-id="364c3-103">O CLR (Common Language Runtime) tem dois provedores: o provedor de tempo de execução e o provedor de encerramento.</span><span class="sxs-lookup"><span data-stu-id="364c3-103">The common language runtime (CLR) has two providers: the runtime provider and the rundown provider.</span></span>  
  
 <span data-ttu-id="364c3-104">O provedor de tempo de execução aciona eventos, dependendo de quais palavras-chave (categorias de eventos) são habilitadas.</span><span class="sxs-lookup"><span data-stu-id="364c3-104">The runtime provider raises events, depending on which keywords (categories of events) are enabled.</span></span> <span data-ttu-id="364c3-105">Por exemplo, é possível coletar eventos de carregador habilitando a palavra-chave `LoaderKeyword`.</span><span class="sxs-lookup"><span data-stu-id="364c3-105">For example, you can collect loader events by enabling the `LoaderKeyword` keyword.</span></span>  
  
 <span data-ttu-id="364c3-106">Os eventos ETW (rastreamento de eventos para Windows) é registrado em um arquivo que tem uma extensão .etl, que posteriormente pode ser pós-processado em arquivos de valores separados por vírgula (.csv), conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="364c3-106">Event tracking for Windows (ETW) events are logged into a file that has an .etl extension, which can later be post-processed in comma-separated value (.csv) files as needed.</span></span> <span data-ttu-id="364c3-107">Para obter informações sobre como converter o arquivo .etl em um arquivo .csv, consulte [Controlando o log do .NET Framework](../../../docs/framework/performance/controlling-logging.md).</span><span class="sxs-lookup"><span data-stu-id="364c3-107">For information about how to convert the .etl file to a .csv file, see [Controlling .NET Framework Logging](../../../docs/framework/performance/controlling-logging.md).</span></span>  
  
## <a name="the-runtime-provider"></a><span data-ttu-id="364c3-108">O provedor de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="364c3-108">The Runtime Provider</span></span>  
 <span data-ttu-id="364c3-109">O provedor de tempo de execução é o principal provedor CLR ETW.</span><span class="sxs-lookup"><span data-stu-id="364c3-109">The runtime provider is the main CLR ETW provider.</span></span>  
  
 <span data-ttu-id="364c3-110">O GUID do provedor de tempo de execução CLR é e13c0d23-ccbc-4e12-931b-d9cc2eee27e4.</span><span class="sxs-lookup"><span data-stu-id="364c3-110">The CLR runtime provider GUID is e13c0d23-ccbc-4e12-931b-d9cc2eee27e4.</span></span>  
  
 <span data-ttu-id="364c3-111">Para obter exemplos de como registrar e exibir eventos CLR ETW usando as ferramentas geralmente disponíveis, consulte [Controlando o log do .NET Framework](../../../docs/framework/performance/controlling-logging.md).</span><span class="sxs-lookup"><span data-stu-id="364c3-111">For examples of how to log and view CLR ETW events by using commonly available tools, see [Controlling .NET Framework Logging](../../../docs/framework/performance/controlling-logging.md).</span></span>  
  
 <span data-ttu-id="364c3-112">Além de usar palavras-chave como `LoaderKeyword`, talvez você precise habilitar palavras-chave para registrar eventos que podem ser acionados com muita frequência.</span><span class="sxs-lookup"><span data-stu-id="364c3-112">In addition to using keywords such as `LoaderKeyword`, you may have to enable keywords for logging events that may be raised too frequently.</span></span> <span data-ttu-id="364c3-113">As palavras-chave `StartEnumerationKeyword` e `EndEnumerationKeyword` habilitam esses eventos e são resumidas em [Palavras-chave e níveis CLR ETW](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).</span><span class="sxs-lookup"><span data-stu-id="364c3-113">The `StartEnumerationKeyword` and the `EndEnumerationKeyword` keywords enable these events and are summarized in [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).</span></span>  
  
## <a name="the-rundown-provider"></a><span data-ttu-id="364c3-114">O provedor de encerramento</span><span class="sxs-lookup"><span data-stu-id="364c3-114">The Rundown Provider</span></span>  
 <span data-ttu-id="364c3-115">O provedor de encerramento deve ser ativado para determinados usos de finalidade especial.</span><span class="sxs-lookup"><span data-stu-id="364c3-115">The rundown provider must be turned on for certain special-purpose uses.</span></span> <span data-ttu-id="364c3-116">No entanto, para a maioria dos usuários, o provedor de tempo de execução deve ser suficiente.</span><span class="sxs-lookup"><span data-stu-id="364c3-116">However, for a majority of users, the runtime provider should suffice.</span></span>  
  
 <span data-ttu-id="364c3-117">O GUID do provedor de encerramento CLR é A669021C-C450-4609-A035-5AF59AF4DF18.</span><span class="sxs-lookup"><span data-stu-id="364c3-117">The CLR rundown provider GUID is A669021C-C450-4609-A035-5AF59AF4DF18.</span></span>  
  
 <span data-ttu-id="364c3-118">Normalmente, o log ETW é habilitado antes do início de um processo e é desativado depois que o processo é fechado.</span><span class="sxs-lookup"><span data-stu-id="364c3-118">Normally, ETW logging is enabled before a process launches, and the logging is turned off after the process exits.</span></span> <span data-ttu-id="364c3-119">No entanto, se o log ETW for ativado durante a execução do processo, serão necessárias informações adicionais sobre o processo.</span><span class="sxs-lookup"><span data-stu-id="364c3-119">However, if ETW logging is turned on while the process is executing, additional information is needed about the process.</span></span> <span data-ttu-id="364c3-120">Por exemplo, para a resolução de símbolo, você precisa registrar eventos de método para métodos que já foram carregados antes da ativação do log.</span><span class="sxs-lookup"><span data-stu-id="364c3-120">For example, for symbol resolution you have to log method events for methods that were already loaded before logging was turned on.</span></span>  
  
 <span data-ttu-id="364c3-121">Os eventos `DCStart` e `DCEnd` capturam o estado do processo quando a coleta de dados foi iniciada e interrompida.</span><span class="sxs-lookup"><span data-stu-id="364c3-121">The `DCStart` and `DCEnd` events capture the state of the process when data collection was started and stopped.</span></span> <span data-ttu-id="364c3-122">(Estado refere-se às informações em um alto nível, incluindo os métodos que já foram compilados pelo JIT [Just-In-Time] e os assemblies que foram carregados.) Esses dois eventos podem fornecer informações sobre o que já ocorreu no processo; por exemplo, quais métodos foram compilados pelo JIT e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="364c3-122">(State refers to information at a high level, including the methods that were already just-in-time (JIT) compiled and assemblies that were loaded.) These two events can provide information about what has already happened in the process; for example, which methods were JIT- compiled, and so on.</span></span>  
  
 <span data-ttu-id="364c3-123">Somente os eventos com `DC`, `DCStart`, `DCEnd` ou `DCInit` em seus nomes são acionados no provedor de encerramento.</span><span class="sxs-lookup"><span data-stu-id="364c3-123">Only the events with `DC`, `DCStart`, `DCEnd`, or `DCInit` in their names are raised under the rundown provider.</span></span> <span data-ttu-id="364c3-124">Além disso, esses eventos são acionados apenas no provedor de encerramento.</span><span class="sxs-lookup"><span data-stu-id="364c3-124">Additionally, these events are raised only under the rundown provider.</span></span>  
  
 <span data-ttu-id="364c3-125">Além dos filtros de palavra-chave do evento, o provedor de encerramento também dá suporte às palavras-chave `StartRundownKeyword` e `EndRundownKeyword` para fornecer filtragem direcionada.</span><span class="sxs-lookup"><span data-stu-id="364c3-125">In addition to the event keyword filters, the rundown provider also supports the `StartRundownKeyword` and `EndRundownKeyword` keywords to provide targeted filtering.</span></span>  
  
### <a name="start-rundown"></a><span data-ttu-id="364c3-126">Encerramento inicial</span><span class="sxs-lookup"><span data-stu-id="364c3-126">Start Rundown</span></span>  
 <span data-ttu-id="364c3-127">Um encerramento inicial é disparado quando o log no provedor de encerramento é habilitado com a palavra-chave `StartRundownKeyword`.</span><span class="sxs-lookup"><span data-stu-id="364c3-127">A start rundown is triggered when logging under the rundown provider is enabled with the `StartRundownKeyword` keyword.</span></span> <span data-ttu-id="364c3-128">Isso faz com que o evento `DCStart` seja acionado e captura o estado do sistema.</span><span class="sxs-lookup"><span data-stu-id="364c3-128">This causes the `DCStart` event to be raised, and captures the state of the system.</span></span> <span data-ttu-id="364c3-129">Antes do início da enumeração, o evento `DCStartInit` é acionado.</span><span class="sxs-lookup"><span data-stu-id="364c3-129">Before the start of the enumeration, the `DCStartInit` event is raised.</span></span> <span data-ttu-id="364c3-130">Ao final da enumeração, o evento `DCStartComplete` é acionado para notificar o controlador de que a coleta de dados terminou normalmente.</span><span class="sxs-lookup"><span data-stu-id="364c3-130">At the end of the enumeration, the `DCStartComplete` event is raised to notify the controller that data collection terminated normally.</span></span>  
  
### <a name="end-rundown"></a><span data-ttu-id="364c3-131">Encerramento final</span><span class="sxs-lookup"><span data-stu-id="364c3-131">End Rundown</span></span>  
 <span data-ttu-id="364c3-132">Um encerramento final é disparado quando o log no provedor de encerramento é habilitado com a palavra-chave `EndRundownKeyword`.</span><span class="sxs-lookup"><span data-stu-id="364c3-132">An end rundown is triggered when logging under the rundown provider is enabled with the `EndRundownKeyword` keyword.</span></span> <span data-ttu-id="364c3-133">O encerramento final interrompe a criação de perfil em um processo que continua sendo executado.</span><span class="sxs-lookup"><span data-stu-id="364c3-133">End rundown stops profiling on a process that continues to execute.</span></span> <span data-ttu-id="364c3-134">Os eventos `DCEnd` capturam o estado do sistema quando a criação de perfil é interrompida.</span><span class="sxs-lookup"><span data-stu-id="364c3-134">The `DCEnd` events capture the state of the system when profiling is stopped.</span></span>  
  
 <span data-ttu-id="364c3-135">Antes do início da enumeração, o evento `DCEndInit` é acionado.</span><span class="sxs-lookup"><span data-stu-id="364c3-135">Before the start of the enumeration, the `DCEndInit` event is raised.</span></span> <span data-ttu-id="364c3-136">Ao final da enumeração, o evento `DCEndComplete` é acionado para notificar o consumidor de que a coleta de dados terminou normalmente.</span><span class="sxs-lookup"><span data-stu-id="364c3-136">At the end of the enumeration, the `DCEndComplete` event is raised to notify the consumer that data collection terminated normally.</span></span> <span data-ttu-id="364c3-137">O encerramento inicial e final são usados principalmente para a resolução de símbolo gerenciado.</span><span class="sxs-lookup"><span data-stu-id="364c3-137">Start rundown and end rundown are primarily used for managed symbol resolution.</span></span> <span data-ttu-id="364c3-138">O encerramento inicial pode fornecer informações de intervalo de endereços para métodos que já foram compilados pelo JIT antes do início da sessão de criação de perfil.</span><span class="sxs-lookup"><span data-stu-id="364c3-138">Start rundown can provide address range information for methods that were already JIT-compiled before the profiling session was started.</span></span> <span data-ttu-id="364c3-139">O encerramento final pode fornecer informações de intervalo de endereços para todos os métodos que foram compilados pelo JIT quando a criação de perfil está prestes a ser desativada.</span><span class="sxs-lookup"><span data-stu-id="364c3-139">End rundown can provide address range information for all methods that have been JIT-compiled when profiling is about to be turned off.</span></span>  
  
 <span data-ttu-id="364c3-140">O encerramento final não ocorre automaticamente quando uma sessão de criação de perfil é interrompida.</span><span class="sxs-lookup"><span data-stu-id="364c3-140">End rundown does not happen automatically when a profiling session is stopped.</span></span> <span data-ttu-id="364c3-141">Em vez disso, uma ferramenta que está tentando executar a resolução de símbolo gerenciado deve invocar explicitamente uma sessão do provedor de encerramento CLR com a palavra-chave `EndRundownKeyword` habilitada, logo antes que a criação de perfil seja interrompida.</span><span class="sxs-lookup"><span data-stu-id="364c3-141">Instead, a tool that is seeking to perform managed symbol resolution has to explicitly invoke a CLR rundown provider session with the `EndRundownKeyword` keyword enabled, just before profiling is stopped.</span></span>  
  
 <span data-ttu-id="364c3-142">Embora o encerramento inicial ou final possa fornecer informações de intervalo de endereços do método para a resolução de símbolo gerenciado, recomendamos o uso da palavra-chave `EndRundownKeyword` (que fornece eventos `DCEnd`), em vez da palavra-chave `StartRundownKeyword` (que fornece eventos `DCStart`).</span><span class="sxs-lookup"><span data-stu-id="364c3-142">Although either start rundown or end rundown can provide method address range information for managed symbol resolution, we recommend that you use the `EndRundownKeyword` keyword (which supplies `DCEnd` events) instead of the `StartRundownKeyword` keyword (which supplies `DCStart` events).</span></span> <span data-ttu-id="364c3-143">O uso de `StartRundownKeyword` faz com que o encerramento ocorra durante a sessão de criação de perfil, o que pode interferir no cenário com perfil criado.</span><span class="sxs-lookup"><span data-stu-id="364c3-143">Using `StartRundownKeyword` causes the rundown to happen during the profiling session, which may disturb the profiled scenario.</span></span>  
  
## <a name="etw-data-collection-using-runtime-and-rundown-providers"></a><span data-ttu-id="364c3-144">Coleta de dados ETW usando o tempo de execução e provedores de encerramento</span><span class="sxs-lookup"><span data-stu-id="364c3-144">ETW Data Collection Using Runtime and Rundown Providers</span></span>  
 <span data-ttu-id="364c3-145">O exemplo a seguir demonstra como usar o provedor de encerramento CLR de uma maneira que permite a resolução de símbolo de processos gerenciados com impacto mínimo, independentemente do início ou término dos processos dentro ou fora da janela com perfil criado.</span><span class="sxs-lookup"><span data-stu-id="364c3-145">The following example demonstrates how to use the CLR rundown provider in a way that allows symbol resolution of managed processes with minimal impact, regardless of whether the processes start or end inside or outside the profiled window.</span></span>  
  
1.  <span data-ttu-id="364c3-146">Ative o log ETW usando o provedor de tempo de execução do CLR:</span><span class="sxs-lookup"><span data-stu-id="364c3-146">Turn on ETW logging by using the CLR runtime provider:</span></span>  
  
    ```  
    xperf -start clr -on e13c0d23-ccbc-4e12-931b-d9cc2eee27e4:0x1CCBD:0x5 -f clr1.etl      
    ```  
  
     <span data-ttu-id="364c3-147">O log será salvo no arquivo clr1.etl.</span><span class="sxs-lookup"><span data-stu-id="364c3-147">The log will be saved to the clr1.etl file.</span></span>  
  
2.  <span data-ttu-id="364c3-148">Para interromper a criação de perfil durante a execução do processo, inicie o provedor de encerramento para capturar os eventos `DCEnd`:</span><span class="sxs-lookup"><span data-stu-id="364c3-148">To stop profiling while the process continues to execute, start the rundown provider to capture the `DCEnd` events:</span></span>  
  
    ```  
    xperf -start clrRundown -on A669021C-C450-4609-A035-5AF59AF4DF18:0xB8:0x5 -f clr2.etl      
    ```  
  
     <span data-ttu-id="364c3-149">Isso permite que a coleção de eventos `DCEnd` inicie uma sessão de encerramento.</span><span class="sxs-lookup"><span data-stu-id="364c3-149">This enables the collection of `DCEnd` events to start a rundown session.</span></span> <span data-ttu-id="364c3-150">Talvez seja necessário aguardar de 30 a 60 segundos para que todos os eventos sejam coletados.</span><span class="sxs-lookup"><span data-stu-id="364c3-150">You may need to wait 30 to 60 seconds for all events to be collected.</span></span> <span data-ttu-id="364c3-151">O log será salvo no arquivo clr1.et2.</span><span class="sxs-lookup"><span data-stu-id="364c3-151">The log will be saved to the clr1.et2 file.</span></span>  
  
3.  <span data-ttu-id="364c3-152">Desligue toda a criação de perfil ETW:</span><span class="sxs-lookup"><span data-stu-id="364c3-152">Turn off all ETW profiling:</span></span>  
  
    ```  
    xperf -stop clrRundown   
    xperf -stop clr  
    ```  
  
4.  <span data-ttu-id="364c3-153">Mescle os perfis para criar um arquivo de log:</span><span class="sxs-lookup"><span data-stu-id="364c3-153">Merge the profiles to create one log file:</span></span>  
  
    ```  
    xperf -merge -d clr1.etl clr2.etl merged.etl  
    ```  
  
     <span data-ttu-id="364c3-154">O arquivo merged.etl conterá os eventos do tempo de execução e as sessões do provedor de encerramento.</span><span class="sxs-lookup"><span data-stu-id="364c3-154">The merged.etl file will contain the events from the runtime and the rundown provider sessions.</span></span>  
  
 <span data-ttu-id="364c3-155">Uma ferramenta pode executar as etapas 2 e 3 (iniciar uma sessão de encerramento e, em seguida, terminar a criação de perfil), em vez de desativar a criação de perfil imediatamente quando um usuário solicitar que a criação de perfil seja interrompida.</span><span class="sxs-lookup"><span data-stu-id="364c3-155">A tool can execute steps 2 and 3 (starting a rundown session and then terminating profiling) instead of immediately turning off profiling when a user requests profiling to be stopped.</span></span> <span data-ttu-id="364c3-156">Uma ferramenta também pode executar a etapa 4.</span><span class="sxs-lookup"><span data-stu-id="364c3-156">A tool can also execute step 4.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="364c3-157">Consulte também</span><span class="sxs-lookup"><span data-stu-id="364c3-157">See Also</span></span>  
 [<span data-ttu-id="364c3-158">Eventos ETW no Common Language Runtime</span><span class="sxs-lookup"><span data-stu-id="364c3-158">ETW Events in the Common Language Runtime</span></span>](../../../docs/framework/performance/etw-events-in-the-common-language-runtime.md)
