---
title: Como converter cadeias de caracteres hexadecimais em números (Visual Basic)
ms.date: 01/31/2018
helpviewer_keywords:
- numbers [Visual Basic], hexadecimals
- hexadecimals [Visual Basic], decimals
- examples [Visual Basic], string conversion
- decimals [Visual Basic], hexadecimals
- string conversion [Visual Basic], hexadecimal to numbers
ms.assetid: 76675807-eadb-4c08-bd50-e6c6ff4b8ced
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: af0e6c1e30c116709ed98240de7bf3471fa842d4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648636"
---
# <a name="how-to-convert-hexadecimal-strings-to-numbers-visual-basic"></a>Como converter cadeias de caracteres hexadecimais em números (Visual Basic)
Este exemplo converte uma cadeia de caracteres hexadecimal em um número inteiro usando o <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType> método.  
  
## <a name="to-convert-a-hexadecimal-string-to-a-number"></a>Para converter uma cadeia de caracteres hexadecimal em um número  
  
-   Use o <xref:System.Convert.ToInt32(System.String,System.Int32)> método para converter o número expressado na base-16 como um número inteiro.  
  
     O primeiro argumento do <xref:System.Convert.ToInt32(System.String,System.Int32)> método é a cadeia de caracteres para converter. O segundo argumento descreve qual base o número é expresso; hexadecimal é base 16.  
  
     [!code-vb[HexConversion](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-hexadecimal-strings-to-numbers_1.vb)]  

- Observe que a cadeia de caracteres hexadecimal tem as seguintes restrições:

   - Não é possível incluir o `&h` prefixo.
   - Não é possível incluir o `_` o separador de dígito.

   Se o prefixo ou um separador de dígito estiver presente, a chamada para o <xref:System.Convert.ToInt32(System.String,System.Int32)> método lança um <xref:System.FormatException>.

## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.Conversion.Hex%2A>  
 <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType>
