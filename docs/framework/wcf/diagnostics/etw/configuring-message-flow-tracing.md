---
title: Configurando rastreamento de fluxo de mensagem
ms.date: 03/30/2017
ms.assetid: 15571ca2-bee2-47fb-ba10-fcbc09152ad0
ms.openlocfilehash: 02c43b152cb1aef1684185e56eb7f172036ac46b
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33804840"
---
# <a name="configuring-message-flow-tracing"></a>Configurando rastreamento de fluxo de mensagem
Quando o rastreamento de atividades do Windows Communication Foundation (WCF) estiver habilitado, as IDs de atividade de ponta a ponta são atribuídas a lógicas atividades em toda a pilha do WCF. Em [!INCLUDE[netfx_current_short](../../../../../includes/netfx-current-short-md.md)], agora há uma versão de desempenho superior desse recurso que funciona com evento rastreamento do Windows (ETW) chamado de rastreamento de fluxo de mensagem. Quando habilitada, IDs de atividade de ponta a ponta são obtidas (ou atribuídos ao se vazia) mensagens de entrada e são propagadas para todos os eventos de rastreamento que são emitidos depois que a mensagem tem sido decodificada pelo canal. Os clientes podem usar esse recurso para reconstruir os fluxos de mensagens com logs de rastreamento de serviços diferentes após a decodificação.  
  
 O rastreamento pode ser ativado depois que for detectado um problema com o aplicativo e, em seguida, desabilitado quando o problema for resolvido.  
  
## <a name="enabling-tracing"></a>A habilitação do rastreamento  
 Você pode habilitar o rastreamento de fluxo de mensagens, definindo o .NET Framework 4 `messageFlowTracing` elemento de configuração para `true`, conforme mostrado no exemplo a seguir.  
  
```xml  
<system.servicemodel>  
  <diagnostics>  
    <endToEndTracing propagateActivity="true" messageFlowTracing="true" />  
  </diagnostics>  
</system.servicemodel>  
```  
  
> [!NOTE]
>  Porque o `endToEndTracing` elemento de configuração reside em um arquivo Web. config, não pode ser configurado dinamicamente da mesma maneira como o ETW. Para o `endToEndTracing` elemento de configuração entrem em vigor, o aplicativo deve ser reciclado.  
  
 As atividades estão correlacionadas, a troca de um identificador chamado ID de atividade. Esse identificador é um GUID e é gerado pela classe System.Diagnostics.CorrelationManager. Se você manipular System.Diagnostics.Trace.CorrelationManager.ActivityID, certifique-se de que o valor é definido como original quando transfere o controle de execução com código WCF.  Além disso, se você usar um modelo de programação WCF assíncrono Certifique-se de que System.Diagnostics.Trace.CorrelationManager.ActivityID são transferidos entre os threads.  
  
## <a name="message-flow-tracing-and-rest-services"></a>Rastreamento de fluxo de mensagens e serviços REST  
 Rastreamento de fluxo de mensagem permite que você rastrear uma solicitação de ponta a ponta.  Serviços baseados em SOAP é enviada uma ID de atividade em um cabeçalho de mensagem SOAP. Solicitações REST não contêm esse cabeçalho para que um cabeçalho de evento HTTP especial é usado em vez disso. O trecho de código a seguir mostra como você pode recuperar programaticamente o valor de ID da atividade:  
  
```csharp
Object output = null;
if (OperationContext.Current.IncomingMessageProperties.TryGetValue(HttpRequestMessageProperty.Name, out output))
{
   HttpRequestMessageProperty httpHeaders = output as HttpRequestMessageProperty;
   // Retrieve the Activity Id from the HTTP header    string e2eId = httpHeaders.Headers["E2EActivity"];
   // ...
}
```

 Você pode adicionar programaticamente o cabeçalho usando o seguinte código:  
  
```csharp  
HttpContent content = new StreamContent(contentStream);  
Guid correlation = Guid.NewGuid();  
content.Headers.Add("E2EActivity", Convert.ToBase64String(correlation.ToByteArray()));  
```
