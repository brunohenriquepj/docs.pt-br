---
title: Como adicionar e remover colunas no controle DataGridView dos Windows Forms usando o designer
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.DataGridViewAddColumnDialog
helpviewer_keywords:
- DataGridView control [Windows Forms], adding columns
- DataGridView control [Windows Forms], removing columns
ms.assetid: 9e709f35-0a8c-4e7e-b4c4-bacb7a834077
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 71b02124dd68299552737df35163e3b766d4df73
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-and-remove-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a>Como adicionar e remover colunas no controle DataGridView dos Windows Forms usando o designer
Windows Forms <xref:System.Windows.Forms.DataGridView> controle deve conter colunas para exibir os dados. Para preencher o controle manualmente é preciso adicionar as colunas. De forma alternativa, é possível associar o controle a uma fonte de dados, que gera e preenche as colunas automaticamente. Se a fonte de dados contém mais colunas do que se deseja exibir, remova as colunas indesejadas.  
  
 Os procedimentos a seguir exigem uma **aplicativo do Windows** projeto com um formulário que contém um <xref:System.Windows.Forms.DataGridView> controle. Para obter informações sobre como configurar um projeto desse tipo, consulte [Como Criar um Projeto de Aplicativo do Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) e [Como Adicionar Controles ao Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-add-a-column-using-the-designer"></a>Para adicionar uma coluna usando o designer  
  
1.  Clique na marca inteligente (![marca inteligente](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) no canto superior direito do <xref:System.Windows.Forms.DataGridView> de controle e, em seguida, selecione **adicionar coluna**.  
  
2.  Na caixa de diálogo **Adicionar Coluna**, escolha a opção **Coluna de Associação de Dados** e selecione uma coluna da fonte de dados, ou escolha a opção **Coluna Não Associada** e defina a coluna usando os campos fornecidos.  
  
3.  Clique no botão **Adicionar** para adicionar a coluna, fazendo com que ela apareça no designer se as colunas existentes não preencherem ainda o controle da área de exibição.  
  
    > [!NOTE]
    >  É possível modificar propriedades da coluna na caixa de diálogo **Editar Colunas**, que pode ser acessada na marca inteligente do controle.  
  
### <a name="to-remove-a-column-using-the-designer"></a>Para remover uma coluna usando o designer  
  
1.  Escolha **Editar Colunas** na marca inteligente do controle.  
  
2.  Selecione uma coluna na lista **Colunas Selecionadas**.  
  
3.  Clique no botão **Remover** para excluir a coluna, fazendo com que ela desapareça do designer.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.DataGridView>  
 [Como: criar um projeto de aplicativo do Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa)  
 [Como Adicionar Controles ao Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)