---
title: "Controle de versão com as palavras-chave override e new (Guia de Programação em C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- C# language, versioning
- C# language, override and new
ms.assetid: 88247d07-bd0d-49e9-a619-45ccbbfdf0c5
caps.latest.revision: 25
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: b464b4c395af093bb9124bb671c5c212c750f497
ms.lasthandoff: 03/13/2017

---
# <a name="versioning-with-the-override-and-new-keywords-c-programming-guide"></a>Controle de versão com as palavras-chave override e new (Guia de Programação em C#)
A linguagem C# foi projetada para que o controle de versão entre classes derivadas e [base](../../../csharp/language-reference/keywords/base.md) em diferentes bibliotecas possa evoluir e manter a compatibilidade com versões anteriores. Isso significa, por exemplo, que a introdução de um novo membro em uma [classe](../../../csharp/language-reference/keywords/class.md) base com o mesmo nome que um membro em uma classe derivada tem suporte completo pelo C# e não leva a comportamento inesperado. Isso também significa que uma classe deve declarar explicitamente se um método destina-se a substituir um método herdado ou se um método é um novo método que oculta um método herdado de nome semelhante.  
  
 No C#, as classes derivadas podem conter métodos com o mesmo nome que os métodos da classe base.  
  
-   O método de classe base deve ser definido como [virtual](../../../csharp/language-reference/keywords/virtual.md).  
  
-   Se o método na classe derivada não for precedido pelas palavras-chave [new](../../../csharp/language-reference/keywords/new.md) ou [override](../../../csharp/language-reference/keywords/override.md), o compilador emitirá um aviso e o método se comportará como se a palavra-chave `new` estivesse presente.  
  
-   Se o método na classe derivada for precedido pela palavra-chave `new`, o método será definido como sendo independente do método na classe base.  
  
-   Se o método na classe derivada for precedido pela palavra-chave `override`, os objetos da classe derivada chamarão esse método em vez do método da classe base.  
  
-   O método da classe base pode ser chamado de dentro da classe derivada usando a palavra-chave `base`.  
  
-   As palavras-chave `override`, `virtual` e `new` também podem ser aplicadas a propriedades, indexadores e eventos.  
  
 Por padrão, os métodos C# não são virtuais. Se um método for declarado como virtual, qualquer classe que herdar o método pode implementar sua própria versão. Para tornar um método virtual, o modificador `virtual` é usado na declaração de método da classe base. A classe derivada pode, em seguida, substituir o método virtual base usando a palavra-chave `override` ou ocultar o método virtual na classe base usando a palavra-chave `new`. Se nem a palavra-chave `override` nem a `new` for especificada, o compilador emitirá um aviso e o método na classe derivada ocultará o método na classe base.  
  
 Para demonstrar isso na prática, suponha por um momento que a Empresa A tenha criado uma classe chamada `GraphicsClass`, que seu programa usa. A seguir está `GraphicsClass`:  
  
 [!code-cs[csProgGuideInheritance#27](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_1.cs)]  
  
 Sua empresa usa essa classe e você a usa para derivar sua própria classe, adicionando um novo método:  
  
 [!code-cs[csProgGuideInheritance#28](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_2.cs)]  
  
 Seu aplicativo é usado sem problemas, até a Empresa A lançar uma nova versão de `GraphicsClass`, que se parece com o seguinte código:  
  
 [!code-cs[csProgGuideInheritance#29](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_3.cs)]  
  
 A nova versão de `GraphicsClass` agora contém um método chamado `DrawRectangle`. Inicialmente, nada ocorre. A nova versão ainda é compatível em relação ao binário com a versão antiga. Qualquer software que você implantou continuará a funcionar, mesmo se a nova classe for instalada nesses sistemas de computador. Todas as chamadas existentes para o método `DrawRectangle` continuarão a fazer referência à sua versão, em sua classe derivada.  
  
 No entanto, assim que você recompilar seu aplicativo usando a nova versão do `GraphicsClass`, você receberá um aviso do compilador, CS0108. Este aviso informa que você deve considerar como deseja que seu método `DrawRectangle` se comporte em seu aplicativo.  
  
 Se desejar que seu método substitua o novo método de classe base, use a palavra-chave `override`:  
  
 [!code-cs[csProgGuideInheritance#30](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_4.cs)]  
  
 A palavra-chave `override` garante que todos os objetos derivados de `YourDerivedGraphicsClass` usarão a versão da classe derivada de `DrawRectangle`. Os objetos derivados de `YourDerivedGraphicsClass` ainda poderão acessar a versão da classe base de `DrawRectangle` usando a palavra-chave base:  
  
 [!code-cs[csProgGuideInheritance#44](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_5.cs)]  
  
 Se você não quiser que seu método substitua o novo método de classe base, as seguintes considerações se aplicam. Para evitar confusão entre os dois métodos, você pode renomear seu método. Isso pode ser demorado e propenso a erros e simplesmente não ser prático em alguns casos. No entanto, se seu projeto for relativamente pequeno, você poderá usar opções de Refatoração do Visual Studio para renomear o método. Para obter mais informações, consulte [Refatorando classes e tipos (Designer de Classe)](https://docs.microsoft.com/visualstudio/ide/refactoring-classes-and-types-class-designer).  
  
 Como alternativa, você pode evitar o aviso usando a palavra-chave `new` na definição da classe derivada:  
  
 [!code-cs[csProgGuideInheritance#31](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_6.cs)]  
  
 Usando a palavra-chave `new` informa ao compilador que sua definição oculta a definição que está contida na classe base. Este é o comportamento padrão.  
  
## <a name="override-and-method-selection"></a>Seleção de método e substituição  
 Quando um método é chamado em uma classe, o compilador C# seleciona o melhor método a ser chamado se mais de um método for compatível com a chamada, como quando há dois métodos com o mesmo nome e parâmetros que são compatíveis com o parâmetro passado. Os métodos a seguir seriam compatíveis:  
  
 [!code-cs[csProgGuideInheritance#32](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_7.cs)]  
  
 Quando `DoWork` é chamado em uma instância do `Derived`, o compilador C# tenta primeiro tornar a chamada compatível com as versões do `DoWork` originalmente declarado em `Derived`. Os métodos de substituição não são considerados como declarados em uma classe, eles são novas implementações de um método declarado em uma classe base. Somente se o compilador C# não puder corresponder a chamada de método a um método original no `Derived` ele tentará corresponder a chamada a um método com o mesmo nome e parâmetros compatíveis. Por exemplo:  
  
 [!code-cs[csProgGuideInheritance#33](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_8.cs)]  
  
 Como a variável `val` pode ser convertida para um duplo implicitamente, o compilador C# chama `DoWork(double)` em vez de `DoWork(int)`. Há duas formas de evitar isso. Primeiro, evite declarar novos métodos com o mesmo nome que os métodos virtuais. Segundo, você pode instruir o compilador C# para chamar o método virtual fazendo-o pesquisar a lista do método de classe base convertendo a instância do `Derived` para `Base`. Como o método é virtual, a implementação de `DoWork(int)` em `Derived` será chamada. Por exemplo:  
  
 [!code-cs[csProgGuideInheritance#34](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_9.cs)]  
  
 Para obter mais exemplos de `new` e `override`, consulte [Quando usar as palavras-chave override e new](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).  
  
## <a name="see-also"></a>Consulte também  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Classes e structs](../../../csharp/programming-guide/classes-and-structs/index.md)   
 [Métodos](../../../csharp/programming-guide/classes-and-structs/methods.md)   
 [Herança](../../../csharp/programming-guide/classes-and-structs/inheritance.md)