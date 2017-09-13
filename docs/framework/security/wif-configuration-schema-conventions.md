---
title: "Convenções do esquema de configuração do WIF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f7864356-f72f-4cae-995c-18e0431f8a58
caps.latest.revision: 3
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 092f6f4544e308dae45636f447f75100512a916a
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="wif-configuration-schema-conventions"></a><span data-ttu-id="ba599-102">Convenções do esquema de configuração do WIF</span><span class="sxs-lookup"><span data-stu-id="ba599-102">WIF Configuration Schema Conventions</span></span>
<span data-ttu-id="ba599-103">Este tópico aborda as convenções usadas nos tópicos de configuração do WIF (Windows Identity Foundation) e descreve alguns recursos e atributos comuns usados nas seções [\<system.identityModel>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) e [\<system.identityModel.services>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md).</span><span class="sxs-lookup"><span data-stu-id="ba599-103">This topic discusses conventions used throughout the Windows Identity Foundation (WIF) configuration topics and describes some common features and attributes used in the [\<system.identityModel>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) and the [\<system.identityModel.services>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) sections.</span></span>  
  
<a name="BKMK_Modes"></a>   
## <a name="modes"></a><span data-ttu-id="ba599-104">Modos</span><span class="sxs-lookup"><span data-stu-id="ba599-104">Modes</span></span>  
 <span data-ttu-id="ba599-105">Muitos dos elementos de configuração do WIF têm um atributo `mode`.</span><span class="sxs-lookup"><span data-stu-id="ba599-105">Many of the WIF configuration elements have a `mode` attribute.</span></span> <span data-ttu-id="ba599-106">Normalmente, esse atributo controla qual classe é usada para fazer determinada parte do processamento e quais elementos de configuração são permitidos como elementos filho do elemento atual.</span><span class="sxs-lookup"><span data-stu-id="ba599-106">This attribute typically controls which class is used to do a particular part of the processing and which configuration elements are allowed as child elements of the current element.</span></span> <span data-ttu-id="ba599-107">Um erro de configuração será acionado se elementos que estão incluídos no arquivo de configuração forem ignorados devido às configurações do modo.</span><span class="sxs-lookup"><span data-stu-id="ba599-107">A configuration error will be raised if elements that are included in the configuration file are ignored because of the mode settings.</span></span>  
  
<a name="BKMK_TimespanValues"></a>   
## <a name="timespan-values"></a><span data-ttu-id="ba599-108">Valores do intervalo de tempo</span><span class="sxs-lookup"><span data-stu-id="ba599-108">Timespan Values</span></span>  
 <span data-ttu-id="ba599-109">Quando <xref:System.TimeSpan> é usado como o tipo de um atributo, consulte o método <xref:System.TimeSpan.Parse%28System.String%29> para ver o formato permitido.</span><span class="sxs-lookup"><span data-stu-id="ba599-109">Where <xref:System.TimeSpan> is used as the type of an attribute, see the <xref:System.TimeSpan.Parse%28System.String%29> method to see the allowed format.</span></span> <span data-ttu-id="ba599-110">Esse formato está em conformidade com a especificação a seguir.</span><span class="sxs-lookup"><span data-stu-id="ba599-110">This format conforms to the following specification.</span></span>  
  
```  
[ws][-]{ d | [d.]hh:mm[:ss[.ff]] }[ws]  
```  
  
 <span data-ttu-id="ba599-111">Por exemplo, “30”, “30.00:00” e “30.00:00:00” significam 30 dias, enquanto “00:05”, “00:05:00” e “0.00:05:00.00” significam 5 minutos.</span><span class="sxs-lookup"><span data-stu-id="ba599-111">For example, "30", "30.00:00", "30.00:00:00" all mean 30 days; and "00:05", "00:05:00", "0.00:05:00.00" all mean 5 minutes.</span></span>  
  
<a name="BKMK_CertificateReferences"></a>   
## <a name="certificate-references"></a><span data-ttu-id="ba599-112">Referências de certificado</span><span class="sxs-lookup"><span data-stu-id="ba599-112">Certificate References</span></span>  
 <span data-ttu-id="ba599-113">Vários elementos levam referências a certificados usando o elemento `<certificateReference>`.</span><span class="sxs-lookup"><span data-stu-id="ba599-113">Several elements take references to certificates using the `<certificateReference>` element.</span></span> <span data-ttu-id="ba599-114">Ao referenciar um certificado, os atributos a seguir estão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="ba599-114">When referencing a certificate, the following attributes are available.</span></span>  
  
|||  
|-|-|  
|`storeLocation`|<span data-ttu-id="ba599-115">Um valor da enumeração <xref:System.Security.Cryptography.X509Certificates.StoreLocation>: `CurrentUser` ou `CurrentMachine`.</span><span class="sxs-lookup"><span data-stu-id="ba599-115">A value of the <xref:System.Security.Cryptography.X509Certificates.StoreLocation> enumeration: `CurrentUser` or `CurrentMachine`.</span></span>|  
|`storeName`|<span data-ttu-id="ba599-116">Um valor da enumeração <xref:System.Security.Cryptography.X509Certificates.StoreName>; os mais úteis para este contexto são `My` e `TrustedPeople`.</span><span class="sxs-lookup"><span data-stu-id="ba599-116">A value of the <xref:System.Security.Cryptography.X509Certificates.StoreName> enumeration; the most useful for this context are `My` and `TrustedPeople`.</span></span>|  
|`x509FindType`|<span data-ttu-id="ba599-117">Um valor da enumeração <xref:System.Security.Cryptography.X509Certificates.X509FindType>; os mais úteis para este contexto são `FindBySubjectName` e `FindByThumbprint`.</span><span class="sxs-lookup"><span data-stu-id="ba599-117">A value of the <xref:System.Security.Cryptography.X509Certificates.X509FindType> enumeration; the most useful for this context are `FindBySubjectName` and `FindByThumbprint`.</span></span> <span data-ttu-id="ba599-118">Para eliminar a possibilidade de erros, é recomendável que o tipo `FindByThumbprint` seja usado em ambientes de produção.</span><span class="sxs-lookup"><span data-stu-id="ba599-118">To eliminate the chance of error, it is recommended that the `FindByThumbprint` type be used in production environments.</span></span>|  
|`findValue`|<span data-ttu-id="ba599-119">O valor usado para encontrar o certificado, com base no atributo `x509FindType`.</span><span class="sxs-lookup"><span data-stu-id="ba599-119">The value used to find the certificate, based on the `x509FindType` attribute.</span></span> <span data-ttu-id="ba599-120">Para eliminar a possibilidade de erros, é recomendável que o tipo `FindByThumbprint` seja usado em ambientes de produção.</span><span class="sxs-lookup"><span data-stu-id="ba599-120">To eliminate the chance of error, it is recommended that the `FindByThumbprint` type be used in production environments.</span></span> <span data-ttu-id="ba599-121">Quando `FindByThumbPrint` é especificado, esse atributo usa um valor que é o formato de cadeia de caracteres hexadecimal da impressão digital do certificado; por exemplo, “97249e1a5fa6bee5e515b82111ef524a4c91583f”.</span><span class="sxs-lookup"><span data-stu-id="ba599-121">When `FindByThumbPrint` is specified, this attribute takes a value that is the hexadecimal-string form of the certificate thumbprint; for example, "97249e1a5fa6bee5e515b82111ef524a4c91583f".</span></span>|  
  
<a name="BKMK_CustomTypeReferences"></a>   
## <a name="custom-type-references"></a><span data-ttu-id="ba599-122">Referências de tipo personalizado</span><span class="sxs-lookup"><span data-stu-id="ba599-122">Custom Type References</span></span>  
 <span data-ttu-id="ba599-123">Vários elementos referenciam tipos personalizados usando o atributo `type`.</span><span class="sxs-lookup"><span data-stu-id="ba599-123">Several elements reference custom types using the `type` attribute.</span></span> <span data-ttu-id="ba599-124">Esse atributo deve especificar o nome do tipo personalizado.</span><span class="sxs-lookup"><span data-stu-id="ba599-124">This attribute should specify the name of the custom type.</span></span> <span data-ttu-id="ba599-125">Para referenciar um tipo do GAC (Cache de Assembly Global), um nome forte deve ser usado.</span><span class="sxs-lookup"><span data-stu-id="ba599-125">To reference a type from the Global Assembly Cache (GAC), a strong name should be used.</span></span> <span data-ttu-id="ba599-126">Para referenciar um tipo de um assembly no diretório Bin/, uma referência simples qualificada pelo assembly pode ser usada.</span><span class="sxs-lookup"><span data-stu-id="ba599-126">To reference a type from an assembly in the Bin/ directory, a simple assembly-qualified reference may be used.</span></span> <span data-ttu-id="ba599-127">Os tipos definidos no diretório App_Code/ também podem ser referenciados apenas especificando o nome do tipo sem nenhum assembly qualificado.</span><span class="sxs-lookup"><span data-stu-id="ba599-127">Types defined in the App_Code/ directory may also be referenced by simply specifying the type name with no qualifying assembly.</span></span>  
  
 <span data-ttu-id="ba599-128">Os tipos personalizados devem ser derivados do tipo especificado e devem fornecer um construtor `public` padrão (0 argumento).</span><span class="sxs-lookup"><span data-stu-id="ba599-128">Custom types must be derived from the type specified and they must provide a `public` default (0 argument) constructor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba599-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ba599-129">See Also</span></span>  
 <span data-ttu-id="ba599-130">[\<system.identityModel>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) </span><span class="sxs-lookup"><span data-stu-id="ba599-130">[\<system.identityModel>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) </span></span>  
 [<span data-ttu-id="ba599-131">\<system.identityModel.services></span><span class="sxs-lookup"><span data-stu-id="ba599-131">\<system.identityModel.services></span></span>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md)
