---
title: Como partir dados serializados
ms.date: 03/30/2017
ms.prod: .net
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- chunking serialized data
- data chunking
- binary serialization, chunking data
- large data set chunking
- serialization, chunking data
- serialization, examples
- binary serialization, examples
ms.assetid: 22f1b818-7e0d-428a-8680-f17d6ebdd185
caps.latest.revision: 3
author: Erikre
ms.author: erikre
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 717bcb6f9f72a728d77e2847096ea558a9c50902
ms.openlocfilehash: 5d8c56be905d6dbfa966546c109a322e013baaac
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="how-to-chunk-serialized-data"></a><span data-ttu-id="871a1-102">Como partir dados serializados</span><span class="sxs-lookup"><span data-stu-id="871a1-102">How to: chunk serialized data</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

<span data-ttu-id="871a1-103">Dois problemas que ocorrem ao enviar grandes conjuntos de dados em mensagens de serviço Web são:</span><span class="sxs-lookup"><span data-stu-id="871a1-103">Two issues that occur when sending large data sets in Web service messages are:</span></span>  
  
1.  <span data-ttu-id="871a1-104">Um grande conjunto de trabalho (memória) devido ao armazenamento em buffer pelo mecanismo de serialização.</span><span class="sxs-lookup"><span data-stu-id="871a1-104">A large working set (memory) due to buffering by the serialization engine.</span></span>  
  
2.  <span data-ttu-id="871a1-105">Consumo de largura de banda desordenado devido à inflação de 33 por cento após a codificação Base64.</span><span class="sxs-lookup"><span data-stu-id="871a1-105">Inordinate bandwidth consumption due to 33 percent inflation after Base64 encoding.</span></span>  
  
 <span data-ttu-id="871a1-106">Para resolver esses problemas, implemente a interface <xref:System.Xml.Serialization.IXmlSerializable> para controlar a serialização e a desserialização.</span><span class="sxs-lookup"><span data-stu-id="871a1-106">To solve these problems, implement the <xref:System.Xml.Serialization.IXmlSerializable> interface to control the serialization and deserialization.</span></span> <span data-ttu-id="871a1-107">Especificamente, implemente os métodos <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> e <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> para partir os dados.</span><span class="sxs-lookup"><span data-stu-id="871a1-107">Specifically, implement the <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> and <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> methods to chunk the data.</span></span>  
  
### <a name="to-implement-server-side-chunking"></a><span data-ttu-id="871a1-108">Para implementar o agrupamento do lado do servidor</span><span class="sxs-lookup"><span data-stu-id="871a1-108">To implement server-side chunking</span></span>  
  
1.  <span data-ttu-id="871a1-109">Na música do servidor, o método da Web deve desativar o buffer do ASP.NET e retornar um tipo que implementa <xref:System.Xml.Serialization.IXmlSerializable>.</span><span class="sxs-lookup"><span data-stu-id="871a1-109">On the server machine, the Web method must turn off ASP.NET buffering and return a type that implements <xref:System.Xml.Serialization.IXmlSerializable>.</span></span>  
  
2.  <span data-ttu-id="871a1-110">O tipo que implementa <xref:System.Xml.Serialization.IXmlSerializable> partir os dados no método <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A>.</span><span class="sxs-lookup"><span data-stu-id="871a1-110">The type that implements <xref:System.Xml.Serialization.IXmlSerializable> chunks the data in the <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> method.</span></span>  
  
### <a name="to-implement-client-side-processing"></a><span data-ttu-id="871a1-111">Para implementar o processamento do lado do cliente</span><span class="sxs-lookup"><span data-stu-id="871a1-111">To implement client-side processing</span></span>  
  
1.  <span data-ttu-id="871a1-112">Altere o método da Web no proxy do cliente para retornar o tipo que implementa <xref:System.Xml.Serialization.IXmlSerializable>.</span><span class="sxs-lookup"><span data-stu-id="871a1-112">Alter the Web method on the client proxy to return the type that implements <xref:System.Xml.Serialization.IXmlSerializable>.</span></span> <span data-ttu-id="871a1-113">Você pode usar uma <xref:System.Xml.Serialization.Advanced.SchemaImporterExtension> para fazer isso automaticamente, mas isso não é mostrado aqui.</span><span class="sxs-lookup"><span data-stu-id="871a1-113">You can use a <xref:System.Xml.Serialization.Advanced.SchemaImporterExtension> to do this automatically, but this isn't shown here.</span></span>  
  
2.  <span data-ttu-id="871a1-114">Implemente o método <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> para ler o fluxo de dados em partes e gravar os bytes no disco.</span><span class="sxs-lookup"><span data-stu-id="871a1-114">Implement the <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> method to read the chunked data stream and write the bytes to disk.</span></span> <span data-ttu-id="871a1-115">Essa implementação também gera eventos de progresso que podem ser usados por um controle de gráfico, como uma barra de progresso.</span><span class="sxs-lookup"><span data-stu-id="871a1-115">This implementation also raises progress events that can be used by a graphic control, such as a progress bar.</span></span>  
  
## <a name="example"></a><span data-ttu-id="871a1-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="871a1-116">Example</span></span>  
<span data-ttu-id="871a1-117">O exemplo de código a seguir mostra o método da Web no cliente que desativa o buffering do ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="871a1-117">The following code example shows the Web method on the client that turns off ASP.NET buffering.</span></span> <span data-ttu-id="871a1-118">Ele também mostra a implementação do lado do cliente da interface <xref:System.Xml.Serialization.IXmlSerializable> que parte os dados no método <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A>.</span><span class="sxs-lookup"><span data-stu-id="871a1-118">It also shows the client-side implementation of the <xref:System.Xml.Serialization.IXmlSerializable> interface that chunks the data in the <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> method.</span></span>  
  
<span data-ttu-id="871a1-119">[!code-csharp[HowToChunkSerializedData#1](../../../samples/snippets/csharp/VS_Snippets_Remoting/HowToChunkSerializedData/CS/SerializationChunk.cs#1)] [!code-vb[HowToChunkSerializedData#1](../../../samples/snippets/visualbasic/VS_Snippets_Remoting/HowToChunkSerializedData/VB/SerializationChunk.vb#1)]</span><span class="sxs-lookup"><span data-stu-id="871a1-119">[!code-csharp[HowToChunkSerializedData#1](../../../samples/snippets/csharp/VS_Snippets_Remoting/HowToChunkSerializedData/CS/SerializationChunk.cs#1)] [!code-vb[HowToChunkSerializedData#1](../../../samples/snippets/visualbasic/VS_Snippets_Remoting/HowToChunkSerializedData/VB/SerializationChunk.vb#1)]</span></span>  
<span data-ttu-id="871a1-120">[!code-csharp[HowToChunkSerializedData#2](../../../samples/snippets/csharp/VS_Snippets_Remoting/HowToChunkSerializedData/CS/SerializationChunk.cs#2)] [!code-vb[HowToChunkSerializedData#2](../../../samples/snippets/visualbasic/VS_Snippets_Remoting/HowToChunkSerializedData/VB/SerializationChunk.vb#2)]</span><span class="sxs-lookup"><span data-stu-id="871a1-120">[!code-csharp[HowToChunkSerializedData#2](../../../samples/snippets/csharp/VS_Snippets_Remoting/HowToChunkSerializedData/CS/SerializationChunk.cs#2)] [!code-vb[HowToChunkSerializedData#2](../../../samples/snippets/visualbasic/VS_Snippets_Remoting/HowToChunkSerializedData/VB/SerializationChunk.vb#2)]</span></span>  
<span data-ttu-id="871a1-121">[!code-csharp[HowToChunkSerializedData#3](../../../samples/snippets/csharp/VS_Snippets_Remoting/HowToChunkSerializedData/CS/SerializationChunk.cs#3)] [!code-vb[HowToChunkSerializedData#3](../../../samples/snippets/visualbasic/VS_Snippets_Remoting/HowToChunkSerializedData/VB/SerializationChunk.vb#3)]</span><span class="sxs-lookup"><span data-stu-id="871a1-121">[!code-csharp[HowToChunkSerializedData#3](../../../samples/snippets/csharp/VS_Snippets_Remoting/HowToChunkSerializedData/CS/SerializationChunk.cs#3)] [!code-vb[HowToChunkSerializedData#3](../../../samples/snippets/visualbasic/VS_Snippets_Remoting/HowToChunkSerializedData/VB/SerializationChunk.vb#3)]</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="871a1-122">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="871a1-122">Compiling the code</span></span>  
  
-   <span data-ttu-id="871a1-123">O código usa os seguintes namespaces: <xref:System>, <xref:System.Runtime.Serialization>, <xref:System.Web.Services>, <xref:System.Web.Services.Protocols>, <xref:System.Xml>, <xref:System.Xml.Serialization> e <xref:System.Xml.Schema>.</span><span class="sxs-lookup"><span data-stu-id="871a1-123">The code uses the following namespaces: <xref:System>, <xref:System.Runtime.Serialization>, <xref:System.Web.Services>, <xref:System.Web.Services.Protocols>, <xref:System.Xml>, <xref:System.Xml.Serialization>, and <xref:System.Xml.Schema>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="871a1-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="871a1-124">See also</span></span>  
 [<span data-ttu-id="871a1-125">Serialização personalizada</span><span class="sxs-lookup"><span data-stu-id="871a1-125">Custom Serialization</span></span>](custom-serialization.md)
