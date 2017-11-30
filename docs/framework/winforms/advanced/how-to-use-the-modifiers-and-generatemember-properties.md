---
title: Como usar os modificadores e as propriedades GenerateMember
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
f1_keywords:
- Designer_GenerateMember
- Designer_Modifiers
helpviewer_keywords:
- base forms
- inheritance [Windows Forms], forms
- inherited forms [Windows Forms], Windows Forms
- inherited forms
- form inheritance
- Windows Forms, inheritance
ms.assetid: 3381a5e4-e1a3-44e2-a765-a0b758937b85
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bcb79525e557a66ed471bc38dcbdd444d75ba6b4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-the-modifiers-and-generatemember-properties"></a>Como usar os modificadores e as propriedades GenerateMember
Quando você coloca um componente em um Windows Form, duas propriedades são fornecidas pelo ambiente de design: `GenerateMember` e `Modifiers`. A propriedade `GenerateMember` especifica quando o Designer de Formulários do Windows gera uma variável de membro de um componente. A propriedade `Modifiers` é o modificador de acesso atribuído a essa variável de membro. Se o valor da propriedade `GenerateMember` for `false`, o valor da propriedade `Modifiers` não terá efeito.  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-specify-whether-a-component-is-a-member-of-the-form"></a>Para especificar se um componente é um membro do formulário  
  
1.  No Designer de Formulários do Windows, abra o formulário.  
  
2.  Abra o **caixa de ferramentas**e no formulário, coloque três <xref:System.Windows.Forms.Button> controles.  
  
3.  Definir o `GenerateMember` e `Modifiers` propriedades para cada <xref:System.Windows.Forms.Button> controle de acordo com a tabela a seguir.  
  
    |Nome do botão|Valor GenerateMember|Valor de modificadores|  
    |-----------------|--------------------------|---------------------|  
    |`button1`|`true`|`private`|  
    |`button2`|`true`|`protected`|  
    |`button3`|`false`|Nenhuma alteração|  
  
4.  Compile a solução.  
  
5.  Em **Gerenciador de Soluções**, clique no botão **Mostrar Todos os Arquivos**.  
  
6.  Abra o nó **Form1** e no **Editor de Códigos**, abra o arquivo **Form1.Designer.vb** ou **Form1. Designer.cs**. Esse arquivo contém o código emitido pelo Designer de Formulários do Windows.  
  
7.  Localize as declarações dos três botões. O exemplo de código a seguir mostra as diferenças especificadas pelas propriedades `GenerateMember` e `Modifiers`.  
  
     [!code-csharp[System.Windows.Forms.GenerateMember#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.GenerateMember#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/VB/Form1.vb#3)]  
  
     [!code-csharp[System.Windows.Forms.GenerateMember#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.GenerateMember#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/VB/Form1.vb#2)]  
  
> [!NOTE]
>  Por padrão, o Windows Forms Designer atribui o `private` (`Friend` no Visual Basic) modificador para controles de contêiner, como <xref:System.Windows.Forms.Panel>. Se sua base de <xref:System.Windows.Forms.UserControl> ou <xref:System.Windows.Forms.Form> tem um controle de contêiner, ele não aceitará novos filhos em controles em formulários herdados. A solução é alterar o modificador da caixa de controles de base para `protected` ou `public`.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.Button>  
 [Herança Visual dos Windows Forms](../../../../docs/framework/winforms/advanced/windows-forms-visual-inheritance.md)  
 [Instruções passo a passo: demonstrando herança visual](../../../../docs/framework/winforms/advanced/walkthrough-demonstrating-visual-inheritance.md)  
 [Como Herdar Windows Forms](../../../../docs/framework/winforms/advanced/how-to-inherit-windows-forms.md)