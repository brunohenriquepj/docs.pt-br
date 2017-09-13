---
title: Elemento &lt;dateTimeSerialization&gt;
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- dateTimeSerialization element
- XML serialization, configuration
- <dateTimeSerialization> element
ms.assetid: 90fda55c-7730-41e9-bc4b-6423a4b920af
caps.latest.revision: 5
author: Erikre
ms.author: erikre
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 717bcb6f9f72a728d77e2847096ea558a9c50902
ms.openlocfilehash: 9ced207c17355cc9c1bd85bdada4208dea2ceb2f
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="ltdatetimeserializationgt-element"></a><span data-ttu-id="d2cf2-102">Elemento &lt;dateTimeSerialization&gt;</span><span class="sxs-lookup"><span data-stu-id="d2cf2-102">&lt;dateTimeSerialization&gt; Element</span></span>
<span data-ttu-id="d2cf2-103">Determina o modo de serialização de objetos <xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="d2cf2-103">Determines the serialization mode of <xref:System.DateTime> objects.</span></span>  
  
 <span data-ttu-id="d2cf2-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="d2cf2-104">\<configuration></span></span>  
<span data-ttu-id="d2cf2-105">\<dateTimeSerialization></span><span class="sxs-lookup"><span data-stu-id="d2cf2-105">\<dateTimeSerialization></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2cf2-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d2cf2-106">Syntax</span></span>  
  
```xml  
<dateTimeSerialization  
    mode = "Roundtrip" | "Local"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d2cf2-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d2cf2-107">Attributes and Elements</span></span>  
 <span data-ttu-id="d2cf2-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="d2cf2-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d2cf2-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="d2cf2-109">Attributes</span></span>  
  
|<span data-ttu-id="d2cf2-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="d2cf2-110">Attributes</span></span>|<span data-ttu-id="d2cf2-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="d2cf2-111">Description</span></span>|  
|----------------|-----------------|  
|`mode`|<span data-ttu-id="d2cf2-112">Opcional.</span><span class="sxs-lookup"><span data-stu-id="d2cf2-112">Optional.</span></span> <span data-ttu-id="d2cf2-113">Especifica o modo de serialização.</span><span class="sxs-lookup"><span data-stu-id="d2cf2-113">Specifies the serialization mode.</span></span> <span data-ttu-id="d2cf2-114">Define como um dos valores de <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>.</span><span class="sxs-lookup"><span data-stu-id="d2cf2-114">Set to one of the <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode> values.</span></span> <span data-ttu-id="d2cf2-115">O padrão é **RoundTrip**.</span><span class="sxs-lookup"><span data-stu-id="d2cf2-115">The default is **RoundTrip**.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d2cf2-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="d2cf2-116">Child Elements</span></span>  
 <span data-ttu-id="d2cf2-117">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="d2cf2-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d2cf2-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="d2cf2-118">Parent Elements</span></span>  
  
|<span data-ttu-id="d2cf2-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="d2cf2-119">Element</span></span>|<span data-ttu-id="d2cf2-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="d2cf2-120">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d2cf2-121">system.xml.serialization</span><span class="sxs-lookup"><span data-stu-id="d2cf2-121">system.xml.serialization</span></span>|<span data-ttu-id="d2cf2-122">O elemento de nível superior para controlar a serialização XML.</span><span class="sxs-lookup"><span data-stu-id="d2cf2-122">The top-level element for controlling XML serialization.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d2cf2-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="d2cf2-123">Remarks</span></span>  
 <span data-ttu-id="d2cf2-124">Em versões 1.0, 1.1, 2.0 e posteriores do .NET Framework, quando essa propriedade for definida como **Local**, os objetos <xref:System.DateTime> serão sempre formatados com a hora local.</span><span class="sxs-lookup"><span data-stu-id="d2cf2-124">In versions 1.0, 1.1, 2.0 and later versions of the .NET Framework, when this property is set to **Local**, <xref:System.DateTime> objects are always formatted as the local time.</span></span> <span data-ttu-id="d2cf2-125">Ou seja, as informações de fuso horário local são sempre incluídas com os dados serializados.</span><span class="sxs-lookup"><span data-stu-id="d2cf2-125">That is, local time zone information is always included with the serialized data.</span></span> <span data-ttu-id="d2cf2-126">Defina essa propriedade como **Local** para garantir a compatibilidade com versões mais antigas do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d2cf2-126">Set this property to **Local** to ensure compatibility with older versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="d2cf2-127">Na versão 2.0 e posterior do .NET Framework que têm essa propriedade definida como **Roundtrip**, os objetos <xref:System.DateTime> são sempre examinados para determinar se estão em um fuso horário local, UTC ou não especificado.</span><span class="sxs-lookup"><span data-stu-id="d2cf2-127">In version 2.0 and later versions of the .NET Framework that have this property set to **Roundtrip**, <xref:System.DateTime> objects are examined to determine whether they are in the local, UTC, or an unspecified time zone.</span></span> <span data-ttu-id="d2cf2-128">Os objetos <xref:System.DateTime> são então serializados de modo que essas informações sejam preservadas.</span><span class="sxs-lookup"><span data-stu-id="d2cf2-128">The <xref:System.DateTime> objects are then serialized in such a way that this information is preserved.</span></span> <span data-ttu-id="d2cf2-129">Esse é o comportamento padrão recomendado para todos os novos aplicativos que não se comunicam com versões antigas do framework.</span><span class="sxs-lookup"><span data-stu-id="d2cf2-129">This is the default behavior and is the recommended behavior for all new applications that do not communicate with older versions of the framework.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2cf2-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d2cf2-130">See Also</span></span>  
 <span data-ttu-id="d2cf2-131"><xref:System.DateTime></span><span class="sxs-lookup"><span data-stu-id="d2cf2-131"><xref:System.DateTime></span></span>   
 <span data-ttu-id="d2cf2-132"><xref:System.Xml.Serialization.XmlSchemaImporter></span><span class="sxs-lookup"><span data-stu-id="d2cf2-132"><xref:System.Xml.Serialization.XmlSchemaImporter></span></span>   
 <span data-ttu-id="d2cf2-133"><xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode></span><span class="sxs-lookup"><span data-stu-id="d2cf2-133"><xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode></span></span>   
 <span data-ttu-id="d2cf2-134">[Esquema de arquivo de configuração](../../../docs/framework/configure-apps/file-schema/index.md) </span><span class="sxs-lookup"><span data-stu-id="d2cf2-134">[Configuration File Schema](../../../docs/framework/configure-apps/file-schema/index.md) </span></span>  
 <span data-ttu-id="d2cf2-135">Elemento [\<schemaImporterExtensions>](../../../docs/standard/serialization/schemaimporterextensions-element.md) </span><span class="sxs-lookup"><span data-stu-id="d2cf2-135">[\<schemaImporterExtensions> Element](../../../docs/standard/serialization/schemaimporterextensions-element.md) </span></span>  
 <span data-ttu-id="d2cf2-136">[Elemento \<add> para \<xmlSchemaImporterExtensions>](../../../docs/standard/serialization/add-element-for-xmlschemaimporterextensions.md) </span><span class="sxs-lookup"><span data-stu-id="d2cf2-136">[\<add> Element for \<xmlSchemaImporterExtensions>](../../../docs/standard/serialization/add-element-for-xmlschemaimporterextensions.md) </span></span>  
 [<span data-ttu-id="d2cf2-137">\<Elemento system.xml.serialization></span><span class="sxs-lookup"><span data-stu-id="d2cf2-137">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)
