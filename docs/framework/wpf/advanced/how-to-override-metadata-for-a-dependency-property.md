---
title: "Como substituir metadados para uma propriedade de dependência"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- metadata [WPF], overriding for dependency properties
- dependency properties [WPF], overriding metadata for
- overriding metadata for dependency properties [WPF]
ms.assetid: f90f026e-60d8-428a-933d-edf0dba4441f
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8e7cb01c81b5fb24830cbe0cc39befbadaf4405e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-override-metadata-for-a-dependency-property"></a>Como substituir metadados para uma propriedade de dependência
Este exemplo mostra como substituir os metadados de propriedade de dependência padrão que vêm de uma classe herdada, chamando o <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> método e fornecendo metadados específicos do tipo.  
  
## <a name="example"></a>Exemplo  
 Definindo seu <xref:System.Windows.PropertyMetadata>, uma classe pode definir os comportamentos da propriedade de dependência, como seus padrão valor e sistema retornos de chamada. Muitas classes de propriedades de dependência já tem metadados padrão estabelecido como parte do processo de registro. Isso inclui as propriedades de dependência que fazem parte do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)]. Uma classe que herda a propriedade de dependência por meio da herança de sua classe pode substituir os metadados originais para que as características da propriedade que podem ser alteradas por meio de metadados corresponderão a qualquer requisito específico de subclasse.  
  
 A substituição de metadados em uma propriedade de dependência deve ser realizada antes da propriedade que está sendo colocada em uso pelo sistema de propriedades (isso é igual ao momento em que instâncias específicas de objetos que registram a propriedade são instanciadas). Chamadas para <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> devem ser executadas em construtores estáticos do tipo que fornece a próprio como o `forType` parâmetro <xref:System.Windows.DependencyProperty.OverrideMetadata%2A>. Se você tentar alterar os metadados quando existem instâncias do tipo proprietário, isso não gerará exceções, mas resultará em comportamentos inconsistentes no sistema de propriedade. Além disso, metadados só podem ser substituído uma vez por tipo. Tentativas subsequentes de substituir os metadados no mesmo tipo gerarão uma exceção.  
  
 No exemplo a seguir, a classe personalizada `MyAdvancedStateControl` substitui os metadados fornecidos para `StateProperty` por `MyAdvancedStateControl` com os novos metadados de propriedade. Por exemplo, o valor padrão do `StateProperty` agora é `true` quando a propriedade é consultada em uma instância `MyAdvancedStateControl` recém construída.  
  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
[!code-csharp[PropertySystemEsoterics#MyAdvancedStateControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#myadvancedstatecontrol)]
[!code-vb[PropertySystemEsoterics#MyAdvancedStateControl](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#myadvancedstatecontrol)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.DependencyProperty>  
 [Visão geral das propriedades da dependência](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [Propriedades de dependência personalizadas](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)  
 [Tópicos explicativos](../../../../docs/framework/wpf/advanced/properties-how-to-topics.md)