---
title: 'Como: criar um formulário mestre / detalhes usando dois controles DataRepeater (Visual Studio)'
ms.date: 07/20/2015
helpviewer_keywords:
- DataRepeater, master/detail tables
ms.assetid: eec43ae3-05d8-45a1-8d41-3803c6359dbe
ms.openlocfilehash: 84639a5d49a3fa4a8c6845793c39fc8a67c31e02
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33590901"
---
# <a name="how-to-create-a-masterdetail-form-by-using-two-datarepeater-controls-visual-studio"></a>Como criar um formulário mestre/detalhado usando dois controles DataRepeater (Visual Studio)
Você pode exibir dados relacionados usando dois ou mais <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controles para criar um formulário mestre/detalhes. Por exemplo, você talvez queira exibir uma lista de clientes em um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>e quando o usuário seleciona um cliente, exibir uma lista de pedidos do cliente em um segundo <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.  
  
 Você pode exibir dados relacionados, arrastando os itens de detalhe que compartilham o mesmo nó de tabela mestre do **fontes de dados** window para um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle. Por exemplo, se você tiver uma fonte de dados que tenha uma tabela clientes e uma tabela relacionada Orders, você ver ambas as tabelas como nós de nível superior na exibição da árvore de **fontes de dados** janela. Expanda o nó de clientes para que você possa ver as colunas. Observe que a última coluna na lista é um nó expansível que representa a tabela Orders. Este nó representa os pedidos relacionados para um cliente.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-display-related-data-in-two-datarepeater-controls"></a>Para exibir dados relacionados em dois controles DataRepeater  
  
1.  Arraste dois <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controla do **Visual Basic PowerPacks** guia o **caixa de ferramentas** a um controle de formulário ou contêiner.  
  
2.  Arraste as alças de dimensionamento e a posição para dimensionar os controles e posicioná-los lado a lado.  
  
3.  Sobre o **dados** menu, clique em **Mostrar fontes de dados**.  
  
    > [!NOTE]
    >  Se o **fontes de dados** janela estiver vazia, adicionar uma fonte de dados a ele. Para obter mais informações, consulte [Adicionar novas fontes de dados](/visualstudio/data-tools/add-new-data-sources).  
  
4.  No **fontes de dados** janela, selecione o nó de nível superior para a tabela principal.  
  
5.  Altere o tipo subjacente da tabela de dados mestre para detalhes clicando **detalhes** na lista suspensa no nó da tabela.  
  
6.  Arraste o nó tabela mestre para a região de modelo de item do primeiro <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.  
  
7.  Expanda o nó de tabela mestre e selecione o nó de detalhes para a tabela relacionada.  
  
8.  Alterar o tipo subjacente da tabela de detalhes para obter detalhes clicando **detalhes** na lista suspensa no nó da tabela.  
  
9. Selecione este nó de tabela e arraste-o para a região de modelo de item do segundo <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 [Introdução ao Controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [Como exibir dados associados em um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)  
 [Como exibir dados relacionados em um Aplicativo do Windows Forms](/visualstudio/data-tools/bind-windows-forms-controls-to-data-in-visual-studio)  
 [Como alterar a aparência de um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)  
 [Solução de problemas do controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
