---
title: Como associar um ContextMenuStrip a um controle
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- context menus [Windows Forms], relating
- ContextMenuStrips [Windows Forms], associating with controls
- context menus [Windows Forms], associating with controls
- ContextMenuStrips [Windows Forms], relating
ms.assetid: 6fc40a42-5d69-427f-aa30-0a146193226b
ms.openlocfilehash: 4014324d83e4de634ff7b42204d50fa11dff7ea3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33526404"
---
# <a name="how-to-associate-a-contextmenustrip-with-a-control"></a>Como associar um ContextMenuStrip a um controle
Depois de criar os controles e menus de atalho, use os procedimentos a seguir para exibir um menu de atalho fornecido quando o usuário clica no controle. Esses procedimentos associar um <xref:System.Windows.Forms.ContextMenuStrip> com um formulário do Windows e um <xref:System.Windows.Forms.ToolStrip> controle.  
  
### <a name="to-associate-a-contextmenustrip-with-a-windows-form"></a>Para associar um ContextMenuStrip um formulário do Windows  
  
1.  Definir o <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> propriedade para o nome do associado <xref:System.Windows.Forms.ContextMenuStrip>.  
  
### <a name="to-associate-a-contextmenustrip-with-a-toolstrip-control"></a>Para associar um ContextMenuStrip um controle ToolStrip  
  
1.  Definir o controle <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> propriedade para o nome do associado <xref:System.Windows.Forms.ContextMenuStrip>.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir cria um formulário do Windows e um <xref:System.Windows.Forms.ToolStrip>e associa um diferentes <xref:System.Windows.Forms.ContextMenuStrip> controle com cada um deles.  
  
 [!code-csharp[System.Windows.Forms.ContextMenuStrip#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ContextMenuStrip/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ContextMenuStrip#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ContextMenuStrip/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Referências aos assemblies System, System.Data, System.Drawing e System.Windows.Forms.  
  
 Para obter informações sobre como criar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [Compilando a partir da linha de comando](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.  Consulte também [Como compilar e executar um exemplo completo de código do Windows Forms usando o Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.ContextMenuStrip>  
 <xref:System.Windows.Forms.Control.ContextMenuStrip%2A>  
 <xref:System.Windows.Forms.ToolStrip>  
 [Como adicionar itens de menu a um ContextMenuStrip](../../../../docs/framework/winforms/controls/how-to-add-menu-items-to-a-contextmenustrip.md)  
 [Controle ContextMenuStrip](../../../../docs/framework/winforms/controls/contextmenustrip-control.md)
