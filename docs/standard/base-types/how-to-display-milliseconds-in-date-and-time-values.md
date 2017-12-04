---
title: Como exibir milissegundos em valores de data e hora
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DateTime.ToString method
- displaying date and time data
- time [.NET Framework], milliseconds
- dates [.NET Framework], milliseconds
- milliseconds [.NET Framework]
ms.assetid: ae1a0610-90b9-4877-8eb6-4e30bc5e00cf
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 260d202eb0a218a6657bc719e36da6f39138e54e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-milliseconds-in-date-and-time-values"></a><span data-ttu-id="6648f-102">Como exibir milissegundos em valores de data e hora</span><span class="sxs-lookup"><span data-stu-id="6648f-102">How to: Display Milliseconds in Date and Time Values</span></span>
<span data-ttu-id="6648f-103">A data padrão e a hora formatação métodos, como <xref:System.DateTime.ToString?displayProperty=nameWithType>, incluem horas, minutos e segundos de um valor de tempo, mas exclui seu componente de milissegundos.</span><span class="sxs-lookup"><span data-stu-id="6648f-103">The default date and time formatting methods, such as <xref:System.DateTime.ToString?displayProperty=nameWithType>, include the hours, minutes, and seconds of a time value but exclude its milliseconds component.</span></span> <span data-ttu-id="6648f-104">Este tópico mostra como incluir um componente de milissegundos de uma data e hora em cadeias de caracteres de data e hora formatadas.</span><span class="sxs-lookup"><span data-stu-id="6648f-104">This topic shows how to include a date and time's millisecond component in formatted date and time strings.</span></span>  
  
### <a name="to-display-the-millisecond-component-of-a-datetime-value"></a><span data-ttu-id="6648f-105">Para exibir o componente de milissegundos de um valor DateTime</span><span class="sxs-lookup"><span data-stu-id="6648f-105">To display the millisecond component of a DateTime value</span></span>  
  
1.  <span data-ttu-id="6648f-106">Se você estiver trabalhando na representação da cadeia de caracteres de uma data, converta-a para um valor <xref:System.DateTime> ou <xref:System.DateTimeOffset> usando a estatística <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> ou o método <xref:System.DateTimeOffset.Parse%28System.String%29?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6648f-106">If you are working with the string representation of a date, convert it to a <xref:System.DateTime> or a <xref:System.DateTimeOffset> value by using the static <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> or <xref:System.DateTimeOffset.Parse%28System.String%29?displayProperty=nameWithType> method.</span></span>  
  
2.  <span data-ttu-id="6648f-107">Para extrair a representação de cadeia de caracteres do componente tempo de milissegundo, chame a data e hora do valor <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> ou <xref:System.DateTimeOffset.ToString%2A> método e passar o `fff` ou `FFF` padrões de formato personalizado sozinho ou com outro formato personalizado especificadores de como o `format` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="6648f-107">To extract the string representation of a time's millisecond component, call the date and time value's <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> or <xref:System.DateTimeOffset.ToString%2A> method, and pass the `fff` or `FFF` custom format pattern either alone or with other custom format specifiers as the `format` parameter.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6648f-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6648f-108">Example</span></span>  
 <span data-ttu-id="6648f-109">O exemplo exibe o componente de milissegundo de um <xref:System.DateTime> e um <xref:System.DateTimeOffset> valor no console sozinho e incluído em uma cadeia de caracteres de data e hora mais.</span><span class="sxs-lookup"><span data-stu-id="6648f-109">The example displays the millisecond component of a <xref:System.DateTime> and a <xref:System.DateTimeOffset> value to the console, both alone and included in a longer date and time string.</span></span>  
  
 [!code-csharp[Formatting.HowTo.Millisecond#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Millisecond/cs/Millisecond.cs#1)]
 [!code-vb[Formatting.HowTo.Millisecond#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Millisecond/vb/Millisecond.vb#1)]  
  
 <span data-ttu-id="6648f-110">O padrão de formato `fff` inclui os zeros à direita no valor de milissegundos.</span><span class="sxs-lookup"><span data-stu-id="6648f-110">The `fff` format pattern includes any trailing zeros in the millisecond value.</span></span> <span data-ttu-id="6648f-111">O padrão de formato `FFF` os suprime.</span><span class="sxs-lookup"><span data-stu-id="6648f-111">The `FFF` format pattern suppresses them.</span></span> <span data-ttu-id="6648f-112">A diferença é ilustrada no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="6648f-112">The difference is illustrated in the following example.</span></span>  
  
 [!code-csharp[Formatting.HowTo.Millisecond#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Millisecond/cs/Millisecond.cs#2)]
 [!code-vb[Formatting.HowTo.Millisecond#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Millisecond/vb/Millisecond.vb#2)]  
  
 <span data-ttu-id="6648f-113">Um problema ao definir um especificador de formato personalizado completo que inclui o componente de milissegundos de uma data e hora é que ele define um formato embutido em código que pode não corresponder à organização de elementos de hora na cultura atual do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6648f-113">A problem with defining a complete custom format specifier that includes the millisecond component of a date and time is that it defines a hard-coded format that may not correspond to the arrangement of time elements in the application's current culture.</span></span> <span data-ttu-id="6648f-114">É uma alternativa melhor recuperar uma data e hora padrões de exibição definidos a cultura atual <xref:System.Globalization.DateTimeFormatInfo> de objeto e modificá-lo para incluir milissegundos.</span><span class="sxs-lookup"><span data-stu-id="6648f-114">A better alternative is to retrieve one of the date and time display patterns defined by the current culture's <xref:System.Globalization.DateTimeFormatInfo> object and modify it to include milliseconds.</span></span> <span data-ttu-id="6648f-115">O exemplo também ilustra esta abordagem.</span><span class="sxs-lookup"><span data-stu-id="6648f-115">The example also illustrates this approach.</span></span> <span data-ttu-id="6648f-116">Recupera a cultura atual total padrão de data e hora do <xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A?displayProperty=nameWithType> propriedade e, em seguida, insere o padrão personalizado `.ffff` após seu padrão de segundos.</span><span class="sxs-lookup"><span data-stu-id="6648f-116">It retrieves the current culture's full date and time pattern from the <xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A?displayProperty=nameWithType> property, and then inserts the custom pattern `.ffff` after its seconds pattern.</span></span> <span data-ttu-id="6648f-117">Observe que o exemplo usa uma expressão regular para executar esta operação em uma única chamada de método.</span><span class="sxs-lookup"><span data-stu-id="6648f-117">Note that the example uses a regular expression to perform this operation in a single method call.</span></span>  
  
 <span data-ttu-id="6648f-118">Você também pode usar um especificador de formato personalizado para exibir uma parte fracionária dos segundos que não sejam milissegundos.</span><span class="sxs-lookup"><span data-stu-id="6648f-118">You can also use a custom format specifier to display a fractional part of seconds other than milliseconds.</span></span> <span data-ttu-id="6648f-119">Por exemplo, o especificador de formato personalizado `f` ou `F` exibe décimos de segundo, o especificador de formato personalizado `ff` ou `FF` exibe centésimos de segundo e o especificador de formato personalizado `ffff` ou `FFFF` exibe décimos de milésimos de segundo.</span><span class="sxs-lookup"><span data-stu-id="6648f-119">For example, the `f` or `F` custom format specifier displays tenths of a second, the `ff` or `FF` custom format specifier displays hundredths of a second, and the `ffff` or `FFFF` custom format specifier displays ten thousandths of a second.</span></span> <span data-ttu-id="6648f-120">Partes fracionárias de um milissegundo são truncadas em vez de arredondadas na cadeia de caracteres retornada.</span><span class="sxs-lookup"><span data-stu-id="6648f-120">Fractional parts of a millisecond are truncated instead of rounded in the returned string.</span></span> <span data-ttu-id="6648f-121">Esses especificadores de formato são usados no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="6648f-121">These format specifiers are used in the following example.</span></span>  
  
 [!code-csharp[Formatting.HowTo.Millisecond#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Millisecond/cs/Millisecond.cs#3)]
 [!code-vb[Formatting.HowTo.Millisecond#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Millisecond/vb/Millisecond.vb#3)]  
  
> [!NOTE]
>  <span data-ttu-id="6648f-122">É possível exibir unidades fracionárias muito pequenas de um segundo, como dez milésimos de segundo ou centésimos de milésimos de segundo.</span><span class="sxs-lookup"><span data-stu-id="6648f-122">It is possible to display very small fractional units of a second, such as ten thousandths of a second or hundred-thousandths of a second.</span></span> <span data-ttu-id="6648f-123">No entanto, esses valores podem não ser significativos.</span><span class="sxs-lookup"><span data-stu-id="6648f-123">However, these values may not be meaningful.</span></span> <span data-ttu-id="6648f-124">A precisão dos valores de data e hora depende da resolução do relação ao relógio do sistema.</span><span class="sxs-lookup"><span data-stu-id="6648f-124">The precision of date and time values depends on the resolution of the system clock.</span></span> <span data-ttu-id="6648f-125">No Windows NT 3.5 e versões posteriores, e [!INCLUDE[windowsver](../../../includes/windowsver-md.md)] sistemas operacionais, a resolução do relógio é aproximadamente 10 a 15 milissegundos.</span><span class="sxs-lookup"><span data-stu-id="6648f-125">On Windows NT 3.5 and later, and [!INCLUDE[windowsver](../../../includes/windowsver-md.md)] operating systems, the clock's resolution is approximately 10-15 milliseconds.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6648f-126">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="6648f-126">Compiling the Code</span></span>  
 <span data-ttu-id="6648f-127">Compile o código na linha de comando com csc.exe ou vb.exe.</span><span class="sxs-lookup"><span data-stu-id="6648f-127">Compile the code at the command line using csc.exe or vb.exe.</span></span> <span data-ttu-id="6648f-128">Para compilar o código em [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], coloque-o em um modelo de projeto de aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="6648f-128">To compile the code in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], put it in a console application project template.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6648f-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6648f-129">See Also</span></span>  
 <xref:System.Globalization.DateTimeFormatInfo>  
 [<span data-ttu-id="6648f-130">Cadeias de caracteres de formato de data e hora personalizado</span><span class="sxs-lookup"><span data-stu-id="6648f-130">Custom Date and Time Format Strings</span></span>](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)