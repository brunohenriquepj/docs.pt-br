---
title: '#Diretiva const'
ms.date: 07/20/2015
f1_keywords:
- vb.#Const
- '#vb.Const'
- '#Const'
helpviewer_keywords:
- '#Const directive'
- conditional compilation [Visual Basic], directives
- Const directive (#Const)
- Visual Basic compiler, compiler directives
- constants [Visual Basic], Const directive
- constants [Visual Basic], declaring
- Const statement [Visual Basic], directive (#Const)
- 'declaring constants [Visual Basic], #const directive'
ms.assetid: 707669e5-23f9-4f17-8622-a0d534429386
ms.openlocfilehash: a3b3318f6b44f7d1798e08195be5aeb920b61c0c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588061"
---
# <a name="const-directive"></a>Diretiva #Const
Define constantes condicionais de compilador do Visual Basic.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
#Const constname = expression  
```  
  
## <a name="parts"></a>Partes  
 `constname`  
 Necessário. Nome da constante sendo definida.  
  
 `expression`  
 Necessário. Literal, outra constante condicional de compilador ou qualquer combinação que inclua qualquer ou todos os operadores aritméticos ou lógicos exceto `Is`.  
  
## <a name="remarks"></a>Comentários  
 Constantes condicionais de compilador são sempre privadas para o arquivo em que aparecem. Você não pode criar constantes de compilador públicas usando o `#Const` diretiva; você pode criá-los apenas na interface do usuário ou com o `/define` opção de compilador.  
  
 Você pode usar apenas constantes condicionais de compilador e literais em `expression`. Usar uma condição padrão definida com `Const` causa um erro. Por outro lado, você pode usar constantes definidas com o `#Const` palavra-chave para compilação condicional. Constantes também podem ser indefinidas, caso em que eles têm um valor de `Nothing`.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o `#Const` diretiva.  
  
 [!code-vb[VbVbalrConditionalComp#3](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/const-directive_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [/Define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)  
 [Diretivas #If...Then...#Else](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
 [Instrução Const](../../../visual-basic/language-reference/statements/const-statement.md)  
 [Compilação Condicional](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 [Instrução If...Then...Else](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
