---
title: '* Operador (Referência de C#)'
ms.date: 04/04/2018
f1_keywords:
- '*_CSharpKeyword'
helpviewer_keywords:
- multiplication operator (*) [C#]
- '* operator [C#]'
ms.assetid: abd9a5f0-9b24-431e-971a-09ee1c45c50e
ms.openlocfilehash: 6c5d4de587b67e5ade158c163a87e8dea6bece5a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33275835"
---
# <a name="-operator-c-reference"></a>Operador * (Referência de C#)
O operador de multiplicação (`*`) calcula o produto dos operandos. Todos os tipos numéricos têm operadores de multiplicação predefinidos.  

`*` também atua como o operador de desreferenciamento, que permite a leitura e a gravação em um ponteiro.
  
## <a name="remarks"></a>Comentários  
 O operador `*` também é usado para declarar tipos de ponteiro e para desreferenciar ponteiros. Esse operador pode ser usado somente em contextos não seguros, indicado pelo uso da palavra-chave [unsafe](../../../csharp/language-reference/keywords/unsafe.md) e exigindo a opção do compilador [/unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md).  O operador de desreferenciamento é também conhecido como operador de indireção.  
  
 Tipos definidos pelo usuário podem sobrecarregar o operador binário `*` (consulte [operador](../../../csharp/language-reference/keywords/operator.md)). Quando um operador binário está sobrecarregado, o operador de atribuição correspondente, se houver, também estará implicitamente sobrecarregado.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[csRefOperators#50](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-operator_1.cs)]  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[csRefOperators#51](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-operator_2.cs)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Código não seguro e ponteiros](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [Operadores do C#](../../../csharp/language-reference/operators/index.md)
