---
title: Como exibir subitens em colunas com o controle ListView dos Windows Forms
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- list items
- Details view
- ListView control [Windows Forms], adding ListSubItems
- subitems
ms.assetid: e465f044-cde7-4fd9-a687-788a73a0f554
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: be1b055c8ea0e7a7c6466033735431a17ecc32f6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-subitems-in-columns-with-the-windows-forms-listview-control"></a><span data-ttu-id="9d6c2-102">Como exibir subitens em colunas com o controle ListView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9d6c2-102">How to: Display Subitems in Columns with the Windows Forms ListView Control</span></span>
<span data-ttu-id="9d6c2-103">Windows Forms <xref:System.Windows.Forms.ListView> controle pode exibir o texto adicional ou subitens, para cada item na exibição de detalhes.</span><span class="sxs-lookup"><span data-stu-id="9d6c2-103">The Windows Forms <xref:System.Windows.Forms.ListView> control can display additional text, or subitems, for each item in the Details view.</span></span> <span data-ttu-id="9d6c2-104">A primeira coluna exibe o texto do item, por exemplo, o número de um funcionário.</span><span class="sxs-lookup"><span data-stu-id="9d6c2-104">The first column displays the item text, for example an employee number.</span></span> <span data-ttu-id="9d6c2-105">A segunda, terceira e colunas seguintes exibem o primeiro, segundo e subitens associados seguintes.</span><span class="sxs-lookup"><span data-stu-id="9d6c2-105">The second, third, and subsequent columns display the first, second, and subsequent associated subitems.</span></span>  
  
### <a name="to-add-subitems-to-a-list-item"></a><span data-ttu-id="9d6c2-106">Para adicionar subitens a um item de lista</span><span class="sxs-lookup"><span data-stu-id="9d6c2-106">To add subitems to a list item</span></span>  
  
1.  <span data-ttu-id="9d6c2-107">Adicione as colunas necessárias.</span><span class="sxs-lookup"><span data-stu-id="9d6c2-107">Add any columns needed.</span></span> <span data-ttu-id="9d6c2-108">Como a primeira coluna exibirá o item <xref:System.Windows.Forms.ListView.Text%2A> propriedade, você precisa de mais uma coluna que há subitens.</span><span class="sxs-lookup"><span data-stu-id="9d6c2-108">Because the first column will display the item's <xref:System.Windows.Forms.ListView.Text%2A> property, you need one more column than there are subitems.</span></span> <span data-ttu-id="9d6c2-109">Para obter mais informações sobre como adicionar colunas, veja [Como adicionar colunas ao controle ListView dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md).</span><span class="sxs-lookup"><span data-stu-id="9d6c2-109">For more information on adding columns, see [How to: Add Columns to the Windows Forms ListView Control](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md).</span></span>  
  
2.  <span data-ttu-id="9d6c2-110">Chamar o <xref:System.Windows.Forms.ListViewItem.ListViewSubItemCollection.Add%2A> coleção retornada pelo método de <xref:System.Windows.Forms.ListViewItem.SubItems%2A> propriedade de um item.</span><span class="sxs-lookup"><span data-stu-id="9d6c2-110">Call the <xref:System.Windows.Forms.ListViewItem.ListViewSubItemCollection.Add%2A> method of the collection returned by the <xref:System.Windows.Forms.ListViewItem.SubItems%2A> property of an item.</span></span> <span data-ttu-id="9d6c2-111">O exemplo de código a seguir define o nome do funcionário e o departamento para um item de lista.</span><span class="sxs-lookup"><span data-stu-id="9d6c2-111">The code example below sets the employee name and department for a list item.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#61)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#61)]  
  
## <a name="see-also"></a><span data-ttu-id="9d6c2-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9d6c2-112">See Also</span></span>  
 [<span data-ttu-id="9d6c2-113">Visão geral do controle ListView</span><span class="sxs-lookup"><span data-stu-id="9d6c2-113">ListView Control Overview</span></span>](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 [<span data-ttu-id="9d6c2-114">Como Adicionar e Remover Itens com o Controle ListView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9d6c2-114">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)  
 [<span data-ttu-id="9d6c2-115">Como Adicionar Colunas ao Controle ListView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9d6c2-115">How to: Add Columns to the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)  
 [<span data-ttu-id="9d6c2-116">Como Exibir Ícones do Controle ListView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9d6c2-116">How to: Display Icons for the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-display-icons-for-the-windows-forms-listview-control.md)  
 [<span data-ttu-id="9d6c2-117">Como adicionar informações personalizadas a um controle TreeView ou ListView (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="9d6c2-117">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)