---
title: Interpretando o rastreamento de rede
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
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
- TraceMode attribute
- hexidecimal data, network tracing output
- network tracing, analyzing
- protocolonly
- text, network tracing output
- includehex
ms.assetid: ad22b4b8-00af-4778-9cca-cb609ce1f8ff
caps.latest.revision: 9
author: mcleblanc
ms.author: markl
manager: markl
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: e8c451a84117208457942d1c3794628963a49e93
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="interpreting-network-tracing"></a><span data-ttu-id="1a4c0-102">Interpretando o rastreamento de rede</span><span class="sxs-lookup"><span data-stu-id="1a4c0-102">Interpreting Network Tracing</span></span>
<span data-ttu-id="1a4c0-103">Quando o rastreamento de rede está habilitado, você pode usar o rastreamento para capturar as chamadas que seu aplicativo faz para membros de classe <xref:System.Net> diversos.</span><span class="sxs-lookup"><span data-stu-id="1a4c0-103">When network tracing is enabled, you can use tracing to capture calls your application makes to various <xref:System.Net> class members.</span></span> <span data-ttu-id="1a4c0-104">A saída dessas chamadas pode ser semelhante aos exemplos a seguir.</span><span class="sxs-lookup"><span data-stu-id="1a4c0-104">The output from these calls may be similar to the following examples.</span></span>  
  
```  
[588]   (4357)   Entering Socket#33574638::Send()  
[588]   (4387)   Exiting Socket#33574638::Send()-> 61#61  
```  
  
 <span data-ttu-id="1a4c0-105">No exemplo anterior, [588] é o identificador exclusivo do thread atual.</span><span class="sxs-lookup"><span data-stu-id="1a4c0-105">In the preceding example, [588] is the current thread's unique identifier.</span></span> <span data-ttu-id="1a4c0-106">(4357) e (4387) são os carimbos de data/hora que indicam o número de milissegundos decorridos desde que o aplicativo foi iniciado.</span><span class="sxs-lookup"><span data-stu-id="1a4c0-106">(4357) and (4387) are timestamps denoting the number of milliseconds that have elapsed since the application started.</span></span> <span data-ttu-id="1a4c0-107">Os dados após o carimbo de data/hora mostram o aplicativo entrando e saindo do método **Socket.Send**.</span><span class="sxs-lookup"><span data-stu-id="1a4c0-107">The data following the timestamp shows the application entering and exiting the method **Socket.Send**.</span></span> <span data-ttu-id="1a4c0-108">O objeto executando o método **Send** tem 33574638 como seu identificador exclusivo.</span><span class="sxs-lookup"><span data-stu-id="1a4c0-108">The object executing the **Send** method has 33574638 as its unique identifier.</span></span> <span data-ttu-id="1a4c0-109">O rastreamento de saída do método inclui o valor retornado (que é 61 no exemplo anterior).</span><span class="sxs-lookup"><span data-stu-id="1a4c0-109">The method exit trace includes the return value (61 in the preceding example).</span></span>  
  
 <span data-ttu-id="1a4c0-110">Rastreamentos de rede podem capturar o tráfego de rede que é enviado e recebido pelo seu aplicativo usando os protocolos de nível de aplicativo como o protocolo HTTP.</span><span class="sxs-lookup"><span data-stu-id="1a4c0-110">Network traces can capture network traffic that is sent from or received by your application using application-level protocols such as Hypertext Transfer Protocol (HTTP).</span></span> <span data-ttu-id="1a4c0-111">Esses dados podem ser capturados como texto e, opcionalmente, como dados hexadecimais.</span><span class="sxs-lookup"><span data-stu-id="1a4c0-111">This data can be captured as text and, optionally, hexadecimal data.</span></span> <span data-ttu-id="1a4c0-112">Dados hexadecimais estão disponíveis quando você especifica **includehex** como o valor do atributo **tracemode**.</span><span class="sxs-lookup"><span data-stu-id="1a4c0-112">Hexadecimal data is available when you specify **includehex** as the value of the **tracemode** attribute.</span></span> <span data-ttu-id="1a4c0-113">(Para obter informações detalhadas sobre esse atributo, consulte [Como configurar o rastreamento de rede](../../../docs/framework/network-programming/how-to-configure-network-tracing.md).) O rastreamento de exemplo a seguir foi gerado usando **includehex**.</span><span class="sxs-lookup"><span data-stu-id="1a4c0-113">(For detailed information about this attribute, see [How to: Configure Network Tracing](../../../docs/framework/network-programming/how-to-configure-network-tracing.md).) The following example trace was generated using **includehex**.</span></span>  
  
 `[1692]   (1142)   00000000 : 47 45 54 20 2F 77 70 61-64 2E 64 61 74 20 48 54 : GET /wpad.dat HT`  
  
 `[1692]   (1142)   00000010 : 54 50 2F 31 2E 31 0D 0A-48 6F 73 74 3A 20 69 74 : TP/1.1..Host: it`  
  
 `[1692]   (1142)   00000020 : 67 70 72 6F 78 79 0D 0A-43 6F 6E 6E 65 63 74 69 : gproxy..Connecti`  
  
 `[1692]   (1142)   00000030 : 6F 6E 3A 20 43 6C 6F 73-65 0D 0A 0D 0A     : on: Close....`  
  
 <span data-ttu-id="1a4c0-114">Para omitir dados hexadecimais, especifique **protocolonly** como o valor para o atributo **tracemode**.</span><span class="sxs-lookup"><span data-stu-id="1a4c0-114">To omit hexadecimal data, specify **protocolonly** as the value for the **tracemode** attribute.</span></span> <span data-ttu-id="1a4c0-115">O exemplo a seguir mostra o rastreamento quando **protocolonly** é especificado.</span><span class="sxs-lookup"><span data-stu-id="1a4c0-115">The following example shows the trace when **protocolonly** is specified.</span></span>  
  
 `[2444]   (594)   Data from ConnectStream#33574638::WriteHeaders<<GET /wpad.dat HTTP/1.1`  
  
 `Host: itgproxy`  
  
 `Connection: Close`  
  
## <a name="see-also"></a><span data-ttu-id="1a4c0-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1a4c0-116">See Also</span></span>  
 <span data-ttu-id="1a4c0-117">[Habilitando o rastreamento de rede](../../../docs/framework/network-programming/enabling-network-tracing.md) </span><span class="sxs-lookup"><span data-stu-id="1a4c0-117">[Enabling Network Tracing](../../../docs/framework/network-programming/enabling-network-tracing.md) </span></span>  
 <span data-ttu-id="1a4c0-118">[Como configurar o rastreamento de rede](../../../docs/framework/network-programming/how-to-configure-network-tracing.md) </span><span class="sxs-lookup"><span data-stu-id="1a4c0-118">[How to: Configure Network Tracing](../../../docs/framework/network-programming/how-to-configure-network-tracing.md) </span></span>  
 [<span data-ttu-id="1a4c0-119">Rastreamento de rede no .NET Framework</span><span class="sxs-lookup"><span data-stu-id="1a4c0-119">Network Tracing in the .NET Framework</span></span>](../../../docs/framework/network-programming/network-tracing.md)
