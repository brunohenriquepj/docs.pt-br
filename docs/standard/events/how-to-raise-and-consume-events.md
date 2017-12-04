---
title: Como acionar e consumir eventos
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- events [.NET Framework], raising
- raising events
- events [.NET Framework], samples
ms.assetid: 42afade7-3a02-4f2e-868b-95845f302f8f
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d052c865a554977ce5c8b0a347337d9d9b92fc57
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-raise-and-consume-events"></a><span data-ttu-id="d4f03-102">Como acionar e consumir eventos</span><span class="sxs-lookup"><span data-stu-id="d4f03-102">How to: Raise and Consume Events</span></span>
<span data-ttu-id="d4f03-103">Os exemplos neste tópico mostram como trabalhar com eventos.</span><span class="sxs-lookup"><span data-stu-id="d4f03-103">The examples in this topic show how to work with events.</span></span> <span data-ttu-id="d4f03-104">Elas incluem exemplos do <xref:System.EventHandler> delegado, o <xref:System.EventHandler%601> delegado e um representante personalizado, para ilustrar eventos com e sem dados.</span><span class="sxs-lookup"><span data-stu-id="d4f03-104">They include examples of the <xref:System.EventHandler> delegate, the <xref:System.EventHandler%601> delegate, and a custom delegate, to illustrate events with and without data.</span></span>  
  
 <span data-ttu-id="d4f03-105">Os exemplos usam conceitos descritos no [eventos](../../../docs/standard/events/index.md) artigo.</span><span class="sxs-lookup"><span data-stu-id="d4f03-105">The examples use concepts described in the [Events](../../../docs/standard/events/index.md) article.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d4f03-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d4f03-106">Example</span></span>  
 <span data-ttu-id="d4f03-107">O primeiro exemplo mostra como gerar e consumir um evento que não têm dados.</span><span class="sxs-lookup"><span data-stu-id="d4f03-107">The first example shows how to raise and consume an event that doesn't have data.</span></span> <span data-ttu-id="d4f03-108">Ele contém uma classe denominada `Counter` que tem um evento chamado `ThresholdReached`.</span><span class="sxs-lookup"><span data-stu-id="d4f03-108">It contains a class named `Counter` that has an event named `ThresholdReached`.</span></span> <span data-ttu-id="d4f03-109">Esse evento é gerado quando um valor de contador é igual a ou excede um valor de limite.</span><span class="sxs-lookup"><span data-stu-id="d4f03-109">This event is raised when a counter value equals or exceeds a threshold value.</span></span> <span data-ttu-id="d4f03-110">O <xref:System.EventHandler> delegado é associado ao evento, porque nenhum dado de evento é fornecido.</span><span class="sxs-lookup"><span data-stu-id="d4f03-110">The <xref:System.EventHandler> delegate is associated with the event, because no event data is provided.</span></span>  
  
 [!code-csharp[EventsOverview#5](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programnodata.cs#5)]
 [!code-vb[EventsOverview#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1nodata.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="d4f03-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d4f03-111">Example</span></span>  
 <span data-ttu-id="d4f03-112">O exemplo a seguir mostra como gerar e consumir um evento que fornece dados.</span><span class="sxs-lookup"><span data-stu-id="d4f03-112">The next example shows how to raise and consume an event that provides data.</span></span> <span data-ttu-id="d4f03-113">O <xref:System.EventHandler%601> delegado é associado ao evento e uma instância de um objeto de dados de evento personalizado é fornecida.</span><span class="sxs-lookup"><span data-stu-id="d4f03-113">The <xref:System.EventHandler%601> delegate is associated with the event, and an instance of a custom event data object is provided.</span></span>  
  
 [!code-cpp[EventsOverview#6](../../../samples/snippets/cpp/VS_Snippets_CLR/eventsoverview/cpp/programwithdata.cpp#6)]
 [!code-csharp[EventsOverview#6](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programwithdata.cs#6)]
 [!code-vb[EventsOverview#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1withdata.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="d4f03-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d4f03-114">Example</span></span>  
 <span data-ttu-id="d4f03-115">O exemplo a seguir mostra como declarar um delegado para um evento.</span><span class="sxs-lookup"><span data-stu-id="d4f03-115">The next example shows how to declare a delegate for an event.</span></span> <span data-ttu-id="d4f03-116">O representante chamado `ThresholdReachedEventHandler`.</span><span class="sxs-lookup"><span data-stu-id="d4f03-116">The delegate is named `ThresholdReachedEventHandler`.</span></span> <span data-ttu-id="d4f03-117">Isso é apenas uma ilustração.</span><span class="sxs-lookup"><span data-stu-id="d4f03-117">This is just an illustration.</span></span> <span data-ttu-id="d4f03-118">Normalmente, você não precisa declarar um delegado para um evento, porque você pode usar o <xref:System.EventHandler> ou <xref:System.EventHandler%601> delegate.</span><span class="sxs-lookup"><span data-stu-id="d4f03-118">Typically, you do not have to declare a delegate for an event, because you can use either the <xref:System.EventHandler> or the <xref:System.EventHandler%601> delegate.</span></span> <span data-ttu-id="d4f03-119">Você deve declarar um delegado somente em cenários raros, como tornar sua classe disponível para o código herdado que não é possível usar genéricos.</span><span class="sxs-lookup"><span data-stu-id="d4f03-119">You should declare a delegate only in rare scenarios, such as making your class available to legacy code that cannot use generics.</span></span>  
  
 [!code-csharp[EventsOverview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programwithdelegate.cs#7)]
 [!code-vb[EventsOverview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1withdelegate.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="d4f03-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d4f03-120">See Also</span></span>  
 [<span data-ttu-id="d4f03-121">Eventos</span><span class="sxs-lookup"><span data-stu-id="d4f03-121">Events</span></span>](../../../docs/standard/events/index.md)