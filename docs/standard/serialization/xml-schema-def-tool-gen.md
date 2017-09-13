---
title: "Como usar a ferramenta de definição de esquema XML para gerar classes e documentos de esquema XML"
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
- generating XML classes using XML Schema Definition tool
- generating XML Schema Document using XML Schema Definition tool
- XML Schema Definition tool, using to generate classes that conform to specific schema
- XML Schema Definition tool, using to generate XML Schema Document
ms.assetid: 51f0edc3-993d-4051-b7f2-77753694d3d1
caps.latest.revision: 5
author: Erikre
ms.author: erikre
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 717bcb6f9f72a728d77e2847096ea558a9c50902
ms.openlocfilehash: 3d0d7a6fa5f8b6108567de02cfaec6f1fea71796
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="how-to-use-the-xml-schema-definition-tool-to-generate-classes-and-xml-schema-documents"></a><span data-ttu-id="d2644-102">Como usar a ferramenta de definição de esquema XML para gerar classes e documentos de esquema XML</span><span class="sxs-lookup"><span data-stu-id="d2644-102">How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents</span></span>
<span data-ttu-id="d2644-103">A ferramenta de Definição de Esquema XML (Xsd.exe) permite gerar um esquema XML que descreve uma classe ou gerar a classe definida por um esquema XML.</span><span class="sxs-lookup"><span data-stu-id="d2644-103">The XML Schema Definition tool (Xsd.exe) allows you to generate an XML schema that describes a class or to generate the class defined by an XML schema.</span></span> <span data-ttu-id="d2644-104">Os seguintes procedimentos mostram como executar essas operações.</span><span class="sxs-lookup"><span data-stu-id="d2644-104">The following procedures show how to perform these operations.</span></span>  
  
### <a name="to-generate-classes-that-conform-to-a-specific-schema"></a><span data-ttu-id="d2644-105">Para gerar classes que estão em conformidade com um esquema específico</span><span class="sxs-lookup"><span data-stu-id="d2644-105">To generate classes that conform to a specific schema</span></span>  
  
1.  <span data-ttu-id="d2644-106">Abra um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="d2644-106">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="d2644-107">Passe o esquema XML como um argumento para a ferramenta de definição de esquema XML, que cria um conjunto de classes que correspondem precisamente ao Esquema XML, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="d2644-107">Pass the XML Schema as an argument to the XML Schema Definition tool, which creates a set of classes that are precisely matched to the XML Schema, for example:</span></span>  
  
    ```  
    xsd mySchema.xsd  
    ```  
  
     <span data-ttu-id="d2644-108">A ferramenta somente pode processar esquemas que fazem referência à especificação de XML World Wide Web Consortium de 16 de março de 2001.</span><span class="sxs-lookup"><span data-stu-id="d2644-108">The tool can only process schemas that reference the World Wide Web Consortium XML specification of March 16, 2001.</span></span> <span data-ttu-id="d2644-109">Em outras palavras, o namespace do Esquema XML deve ser "http://www.w3.org/2001/XMLSchema", conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="d2644-109">In other words, the XML Schema namespace must be "http://www.w3.org/2001/XMLSchema" as shown in the following example.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <xs:schema attributeFormDefault="qualified" elementFormDefault="qualified" targetNamespace="" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    ```  
  
3.  <span data-ttu-id="d2644-110">Modifique as classes com métodos, propriedades ou campos, conforme o necessário.</span><span class="sxs-lookup"><span data-stu-id="d2644-110">Modify the classes with methods, properties, or fields, as necessary.</span></span> <span data-ttu-id="d2644-111">Para obter mais informações sobre como modificar uma classe com atributos, consulte [Controlando a serialização XML usando atributos](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md) e [Atributos que controlam a serialização SOAP codificada](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="d2644-111">For more information about modifying a class with attributes, see [Controlling XML Serialization Using Attributes](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md) and [Attributes That Control Encoded SOAP Serialization](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md).</span></span>  
  
 <span data-ttu-id="d2644-112">É geralmente útil examinar o esquema do fluxo de XML que é gerado quando instâncias de uma classe (ou classes) são serializadas.</span><span class="sxs-lookup"><span data-stu-id="d2644-112">It is often useful to examine the schema of the XML stream that is generated when instances of a class (or classes) are serialized.</span></span> <span data-ttu-id="d2644-113">Por exemplo, você pode publicar seu esquema para outros usarem ou pode compará-lo com um esquema com o qual está tentando obter conformidade.</span><span class="sxs-lookup"><span data-stu-id="d2644-113">For example, you might publish your schema for others to use, or you might compare it to a schema with which you are trying to achieve conformity.</span></span>  
  
#### <a name="to-generate-an-xml-schema-document-from-a-set-of-classes"></a><span data-ttu-id="d2644-114">Para gerar um documento de esquema XML de um conjunto de classes</span><span class="sxs-lookup"><span data-stu-id="d2644-114">To generate an XML Schema document from a set of classes</span></span>  
  
1.  <span data-ttu-id="d2644-115">Compile uma classe ou classes em uma DLL.</span><span class="sxs-lookup"><span data-stu-id="d2644-115">Compile the class or classes into a DLL.</span></span>  
  
2.  <span data-ttu-id="d2644-116">Abra um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="d2644-116">Open a command prompt.</span></span>  
  
3.  <span data-ttu-id="d2644-117">Passe a DLL como argumento para Xsd.exe, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="d2644-117">Pass the DLL as an argument to Xsd.exe, for example:</span></span>  
  
    ```  
    xsd MyFile.dll  
    ```  
  
     <span data-ttu-id="d2644-118">O esquema (ou esquemas) serão escritos, começando com o nome "schema0.xsd".</span><span class="sxs-lookup"><span data-stu-id="d2644-118">The schema (or schemas) will be written, beginning with the name "schema0.xsd".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2644-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d2644-119">See Also</span></span>  
 <span data-ttu-id="d2644-120"><xref:System.Data.DataSet></span><span class="sxs-lookup"><span data-stu-id="d2644-120"><xref:System.Data.DataSet></span></span>   
 <span data-ttu-id="d2644-121">[A ferramenta de definição de esquema XML e a serialização XML](../../../docs/standard/serialization/the-xml-schema-definition-tool-and-xml-serialization.md) </span><span class="sxs-lookup"><span data-stu-id="d2644-121">[The XML Schema Definition Tool and XML Serialization](../../../docs/standard/serialization/the-xml-schema-definition-tool-and-xml-serialization.md) </span></span>  
 <span data-ttu-id="d2644-122">[Apresentando a serialização XML](../../../docs/standard/serialization/introducing-xml-serialization.md) </span><span class="sxs-lookup"><span data-stu-id="d2644-122">[Introducing XML Serialization](../../../docs/standard/serialization/introducing-xml-serialization.md) </span></span>  
 <span data-ttu-id="d2644-123">[Ferramenta de Definição de Esquema XML (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md) </span><span class="sxs-lookup"><span data-stu-id="d2644-123">[XML Schema Definition Tool (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md) </span></span>  
 <span data-ttu-id="d2644-124"><xref:System.Xml.Serialization.XmlSerializer></span><span class="sxs-lookup"><span data-stu-id="d2644-124"><xref:System.Xml.Serialization.XmlSerializer></span></span>   
 <span data-ttu-id="d2644-125">[Como serializar um objeto](../../../docs/standard/serialization/how-to-serialize-an-object.md) </span><span class="sxs-lookup"><span data-stu-id="d2644-125">[How to: Serialize an Object](../../../docs/standard/serialization/how-to-serialize-an-object.md) </span></span>  
 [<span data-ttu-id="d2644-126">Como desserializar um objeto</span><span class="sxs-lookup"><span data-stu-id="d2644-126">How to: Deserialize an Object</span></span>](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
