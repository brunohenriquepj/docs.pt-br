---
title: Exemplo de Streaming Feeds
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1f1228c0-daaa-45f0-b93e-c4a158113744
caps.latest.revision: "16"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: becc388a03d065b5763669929806c2f85e171ffc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="streaming-feeds-sample"></a><span data-ttu-id="9d117-102">Exemplo de Streaming Feeds</span><span class="sxs-lookup"><span data-stu-id="9d117-102">Streaming Feeds Sample</span></span>
<span data-ttu-id="9d117-103">Este exemplo demonstra como gerenciar feeds de agregação que contêm um grande número de itens.</span><span class="sxs-lookup"><span data-stu-id="9d117-103">This sample demonstrates how to manage syndication feeds that contain large numbers of items.</span></span> <span data-ttu-id="9d117-104">No servidor, o exemplo demonstra como atrasar a criação de um indivíduo <xref:System.ServiceModel.Syndication.SyndicationItem> objetos dentro do feed até imediatamente antes do item é gravado para o fluxo de rede.</span><span class="sxs-lookup"><span data-stu-id="9d117-104">On the server, the sample demonstrates how to delay the creation of individual <xref:System.ServiceModel.Syndication.SyndicationItem> objects within the feed until immediately before the item is written to the network stream.</span></span>  
  
 <span data-ttu-id="9d117-105">No cliente, o exemplo mostra como um formatador do feed de agregação personalizado pode ser usado para ler itens individuais do fluxo de rede para que o feed que está sendo lido totalmente nunca é armazenada em buffer na memória.</span><span class="sxs-lookup"><span data-stu-id="9d117-105">On the client, the sample shows how a custom syndication feed formatter can be used to read individual items from the network stream so that the feed being read is never fully buffered into memory.</span></span>  
  
 <span data-ttu-id="9d117-106">Para melhor demonstrar o recurso de streaming da API de distribuição, este exemplo usa um cenário improvável em que o servidor expõe um feed que contém um número infinito de itens.</span><span class="sxs-lookup"><span data-stu-id="9d117-106">To best demonstrate the streaming capability of the syndication API, this sample uses a somewhat unlikely scenario in which the server exposes a feed that contains an infinite number of items.</span></span> <span data-ttu-id="9d117-107">Nesse caso, o servidor continua a gerar novos itens no feed, até que ele determina que o cliente tem lê um número especificado de itens do feed (por padrão, 10).</span><span class="sxs-lookup"><span data-stu-id="9d117-107">In this case, the server continues generating new items into the feed until it determines that the client has read a specified number of items from the feed (by default, 10).</span></span> <span data-ttu-id="9d117-108">Para simplificar, o cliente e o servidor são implementadas no mesmo processo e usar compartilhado `ItemCounter` produziu um objeto para controlar quantos itens de cliente.</span><span class="sxs-lookup"><span data-stu-id="9d117-108">For simplicity, both the client and the server are implemented in the same process and use a shared `ItemCounter` object to keep track of how many items the client has produced.</span></span> <span data-ttu-id="9d117-109">O `ItemCounter` tipo existe somente para fins de permitir que o cenário de exemplo encerrar corretamente e não é um elemento de núcleo do padrão demonstrado.</span><span class="sxs-lookup"><span data-stu-id="9d117-109">The `ItemCounter` type exists only for the purpose of allowing the sample scenario to terminate cleanly, and is not a core element of the pattern being demonstrated.</span></span>  
  
 <span data-ttu-id="9d117-110">A demonstração usa [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] iteradores (usando o `yield``return` construção de palavra-chave).</span><span class="sxs-lookup"><span data-stu-id="9d117-110">The demonstration makes use of [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] iterators (using the `yield``return` keyword construct).</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="9d117-111">iteradores, consulte o tópico "Usando iteradores" no MSDN.</span><span class="sxs-lookup"><span data-stu-id="9d117-111"> iterators, see the "Using Iterators" topic on MSDN.</span></span>  
  
## <a name="service"></a><span data-ttu-id="9d117-112">Serviço</span><span class="sxs-lookup"><span data-stu-id="9d117-112">Service</span></span>  
 <span data-ttu-id="9d117-113">O serviço implementa básico <xref:System.ServiceModel.Web.WebGetAttribute> contrato que consiste em uma única operação, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="9d117-113">The service implements a basic <xref:System.ServiceModel.Web.WebGetAttribute> contract that consists of one operation, as shown in the following code.</span></span>  
  
```  
[ServiceContract]  
interface IStreamingFeedService  
{  
    [WebGet]  
    [OperationContract]  
    Atom10FeedFormatter StreamedFeed();  
}  
```  
  
 <span data-ttu-id="9d117-114">O serviço implementa esse contrato usando um `ItemGenerator` classe para criar um fluxo potencialmente infinito de <xref:System.ServiceModel.Syndication.SyndicationItem> instâncias usando um iterador, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="9d117-114">The service implements this contract by using an `ItemGenerator` class to create a potentially infinite stream of <xref:System.ServiceModel.Syndication.SyndicationItem> instances using an iterator, as shown in the following code.</span></span>  
  
```  
class ItemGenerator  
{  
    public IEnumerable<SyndicationItem> GenerateItems()  
    {  
        while (counter.GetCount() < maxItemsRead)  
        {  
            itemsReturned++;  
            yield return CreateNextItem();  
        }  
  
    }  
    ...  
}  
```  
  
 <span data-ttu-id="9d117-115">Quando a implementação do serviço cria o feed, a saída de `ItemGenerator.GenerateItems()` é usado em vez de uma coleção em buffer de itens.</span><span class="sxs-lookup"><span data-stu-id="9d117-115">When the service implementation creates the feed, the output of `ItemGenerator.GenerateItems()` is used instead of a buffered collection of items.</span></span>  
  
```  
public Atom10FeedFormatter StreamedFeed()  
{  
    SyndicationFeed feed = new SyndicationFeed("Streamed feed", "Feed to test streaming", null);  
    //Generate an infinite stream of items. Both the client and the service share  
    //a reference to the ItemCounter, which allows the sample to terminate  
    //execution after the client has read 10 items from the stream  
    ItemGenerator itemGenerator = new ItemGenerator(this.counter, 10);  
  
    feed.Items = itemGenerator.GenerateItems();  
    return feed.GetAtom10Formatter();  
}  
```  
  
 <span data-ttu-id="9d117-116">Como resultado, o fluxo de item nunca totalmente em buffer na memória.</span><span class="sxs-lookup"><span data-stu-id="9d117-116">As a result, the item stream is never fully buffered into memory.</span></span> <span data-ttu-id="9d117-117">Você pode observar esse comportamento definindo um ponto de interrupção no `yield``return` instrução dentro do `ItemGenerator.GenerateItems()` método e observar que esse ponto de interrupção é encontrado pela primeira vez depois que o serviço retornou o resultado da `StreamedFeed()` método.</span><span class="sxs-lookup"><span data-stu-id="9d117-117">You can observe this behavior by setting a breakpoint on the `yield``return` statement inside of the `ItemGenerator.GenerateItems()` method and noting that this breakpoint is encountered for the first time after the service has returned the result of the `StreamedFeed()` method.</span></span>  
  
## <a name="client"></a><span data-ttu-id="9d117-118">Cliente</span><span class="sxs-lookup"><span data-stu-id="9d117-118">Client</span></span>  
 <span data-ttu-id="9d117-119">O cliente neste exemplo usa um personalizado <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> implementação que atrasa a materialização de itens individuais no feed, em vez de armazenamento em buffer na memória.</span><span class="sxs-lookup"><span data-stu-id="9d117-119">The client in this sample uses a custom <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> implementation that delays the materialization of individual items in the feed instead of buffering them into memory.</span></span> <span data-ttu-id="9d117-120">Personalizado `StreamedAtom10FeedFormatter` instância é usada da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="9d117-120">The custom `StreamedAtom10FeedFormatter` instance is used as follows.</span></span>  
  
```  
XmlReader reader = XmlReader.Create("http://localhost:8000/Service/Feeds/StreamedFeed");  
StreamedAtom10FeedFormatter formatter = new StreamedAtom10FeedFormatter(counter);  
  
SyndicationFeed feed = formatter.ReadFrom(reader);  
```  
  
 <span data-ttu-id="9d117-121">Normalmente, uma chamada para <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter.ReadFrom%28System.Xml.XmlReader%29> não retorna até que todo o conteúdo do feed são lido da rede e armazenados em buffer na memória.</span><span class="sxs-lookup"><span data-stu-id="9d117-121">Normally, a call to <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter.ReadFrom%28System.Xml.XmlReader%29> does not return until the entire contents of the feed have been read from the network and buffered into memory.</span></span> <span data-ttu-id="9d117-122">No entanto, o `StreamedAtom10FeedFormatter` objeto substituições <xref:System.ServiceModel.Syndication.Atom10FeedFormatter.ReadItems%28System.Xml.XmlReader%2CSystem.ServiceModel.Syndication.SyndicationFeed%2CSystem.Boolean%40%29> para retornar um iterador em vez de uma coleção em buffer, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="9d117-122">However, the `StreamedAtom10FeedFormatter` object overrides <xref:System.ServiceModel.Syndication.Atom10FeedFormatter.ReadItems%28System.Xml.XmlReader%2CSystem.ServiceModel.Syndication.SyndicationFeed%2CSystem.Boolean%40%29> to return an iterator instead of a buffered collection, as shown in the following code.</span></span>  
  
```  
protected override IEnumerable<SyndicationItem> ReadItems(XmlReader reader, SyndicationFeed feed, out bool areAllItemsRead)  
{  
    areAllItemsRead = false;  
    return DelayReadItems(reader, feed);  
}  
  
private IEnumerable<SyndicationItem> DelayReadItems(XmlReader reader, SyndicationFeed feed)  
{  
    while (reader.IsStartElement("entry", "http://www.w3.org/2005/Atom"))  
    {  
        yield return this.ReadItem(reader, feed);  
    }  
  
    reader.ReadEndElement();  
}  
```  
  
 <span data-ttu-id="9d117-123">Como resultado, cada item não é lido da rede até que o aplicativo cliente passa os resultados de `ReadItems()` está pronto para usá-lo.</span><span class="sxs-lookup"><span data-stu-id="9d117-123">As a result, each item is not read from the network until the client application traversing the results of `ReadItems()` is ready to use it.</span></span> <span data-ttu-id="9d117-124">Você pode observar esse comportamento definindo um ponto de interrupção no `yield``return` instrução dentro do `StreamedAtom10FeedFormatter.DelayReadItems()` e observe que este ponto de interrupção é encontrado pela primeira vez após a chamada a `ReadFrom()` for concluída.</span><span class="sxs-lookup"><span data-stu-id="9d117-124">You can observe this behavior by setting a breakpoint on the `yield``return` statement inside of `StreamedAtom10FeedFormatter.DelayReadItems()` and noticing that this breakpoint is encountered for the first time after the call to `ReadFrom()` completes.</span></span>  
  
 <span data-ttu-id="9d117-125">As instruções a seguir mostram como criar e executar o exemplo.</span><span class="sxs-lookup"><span data-stu-id="9d117-125">The following instructions show how to build and run the sample.</span></span> <span data-ttu-id="9d117-126">Observe que, embora o servidor para gerar itens depois que o cliente tenha lido 10 itens, a saída mostra que o cliente lê significativamente mais de 10 itens.</span><span class="sxs-lookup"><span data-stu-id="9d117-126">Note that although the server stops generating items after the client has read 10 items, the output shows that the client reads significantly more than 10 items.</span></span> <span data-ttu-id="9d117-127">Isso ocorre porque a associação de rede usada pelo exemplo transmite dados em quatro quilobytes (KB) segmentos.</span><span class="sxs-lookup"><span data-stu-id="9d117-127">This is because the networking binding used by the sample transmits data in four-kilobyte (KB) segments.</span></span> <span data-ttu-id="9d117-128">Como tal, o cliente recebe a 4KB de dados do item antes que ele tenha a oportunidade de ler um item.</span><span class="sxs-lookup"><span data-stu-id="9d117-128">As such, the client receives 4KB of item data before it has the opportunity to read even one item.</span></span> <span data-ttu-id="9d117-129">Esse comportamento é normal (enviando dados transmitidos do HTTP aumenta o desempenho razoavelmente dimensionado segmentos).</span><span class="sxs-lookup"><span data-stu-id="9d117-129">This is normal behavior (sending streamed HTTP data in reasonably-sized segments increases performance).</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="9d117-130">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="9d117-130">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="9d117-131">Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9d117-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="9d117-132">Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9d117-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="9d117-133">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9d117-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9d117-134">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="9d117-134">The samples may already be installed on your computer.</span></span> <span data-ttu-id="9d117-135">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="9d117-135">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="9d117-136">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="9d117-136">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9d117-137">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="9d117-137">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\StreamingFeeds`  
  
## <a name="see-also"></a><span data-ttu-id="9d117-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9d117-138">See Also</span></span>  
 [<span data-ttu-id="9d117-139">Feed de diagnóstico independente</span><span class="sxs-lookup"><span data-stu-id="9d117-139">Stand-Alone Diagnostics Feed</span></span>](../../../../docs/framework/wcf/samples/stand-alone-diagnostics-feed-sample.md)