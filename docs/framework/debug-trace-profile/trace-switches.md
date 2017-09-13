---
title: "Opções de rastreamento"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- tracing [.NET Framework], trace switches
- trace switches, about trace switches
- tracing [.NET Framework], level of detail
- switches, trace
- trace switches
- trace switches, creating custom
ms.assetid: 8ab913aa-f400-4406-9436-f45bc6e54fbe
caps.latest.revision: 16
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 6a9ba07fb064444ffa0ab73183f25f7352901480
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="trace-switches"></a><span data-ttu-id="6a26e-102">Opções de rastreamento</span><span class="sxs-lookup"><span data-stu-id="6a26e-102">Trace Switches</span></span>
<span data-ttu-id="6a26e-103">As opções de rastreamento permitem habilitar, desabilitar e filtrar a saída de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="6a26e-103">Trace switches enable you to enable, disable, and filter tracing output.</span></span> <span data-ttu-id="6a26e-104">Elas são objetos que existem no código e podem ser configuradas externamente por meio do arquivo .config.</span><span class="sxs-lookup"><span data-stu-id="6a26e-104">They are objects that exist in your code and can be configured externally through the .config file.</span></span> <span data-ttu-id="6a26e-105">Há três tipos de opções de rastreamento fornecidas no .NET Framework: a classe <xref:System.Diagnostics.BooleanSwitch>, a classe <xref:System.Diagnostics.TraceSwitch> e a classe <xref:System.Diagnostics.SourceSwitch>.</span><span class="sxs-lookup"><span data-stu-id="6a26e-105">There are three types of trace switches provided in the .NET Framework: the <xref:System.Diagnostics.BooleanSwitch> class, the <xref:System.Diagnostics.TraceSwitch> class, and the <xref:System.Diagnostics.SourceSwitch> class.</span></span> <span data-ttu-id="6a26e-106">A classe <xref:System.Diagnostics.BooleanSwitch> atua como uma opção de alternância, habilitando ou desabilitando uma variedade de instruções de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="6a26e-106">The <xref:System.Diagnostics.BooleanSwitch> class acts as a toggle switch, either enabling or disabling a variety of trace statements.</span></span> <span data-ttu-id="6a26e-107">As classes <xref:System.Diagnostics.TraceSwitch> e <xref:System.Diagnostics.SourceSwitch> permitem habilitar uma opção de rastreamento para um nível de rastreamento específico, de modo que as mensagens <xref:System.Diagnostics.Trace> ou <xref:System.Diagnostics.TraceSource> especificadas para o nível e todos os níveis inferiores a ele sejam exibidas.</span><span class="sxs-lookup"><span data-stu-id="6a26e-107">The <xref:System.Diagnostics.TraceSwitch> and <xref:System.Diagnostics.SourceSwitch> classes allow you to enable a trace switch for a particular tracing level so that the <xref:System.Diagnostics.Trace> or <xref:System.Diagnostics.TraceSource> messages specified for that level and all levels below it appear.</span></span> <span data-ttu-id="6a26e-108">Se você desabilitar a opção, as mensagens de rastreamento não serão exibidas.</span><span class="sxs-lookup"><span data-stu-id="6a26e-108">If you disable the switch, the trace messages will not appear.</span></span> <span data-ttu-id="6a26e-109">Todas essas classes são derivadas da classe **Switch** abstrata (**MustInherit**), assim como todas as opções desenvolvidas pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="6a26e-109">All these classes derive from the abstract (**MustInherit**) class **Switch**, as should any user-developed switches.</span></span>  
  
 <span data-ttu-id="6a26e-110">As opções de rastreamento podem ser úteis para a filtragem de informações.</span><span class="sxs-lookup"><span data-stu-id="6a26e-110">Trace switches can be useful for filtering information.</span></span> <span data-ttu-id="6a26e-111">Por exemplo, talvez você deseje ver todas as mensagens de rastreamento em um módulo de acesso a dados, mas somente as mensagens de erro no restante do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6a26e-111">For example, you might want to see every tracing message in a data access module, but only error messages in the rest of the application.</span></span> <span data-ttu-id="6a26e-112">Nesse caso, você usará uma opção de rastreamento para o módulo de acesso a dados e uma opção para o restante do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6a26e-112">In that case, you would use one trace switch for the data access module and one switch for the rest of the application.</span></span> <span data-ttu-id="6a26e-113">Usando o arquivo .config para definir as opções com as configurações apropriadas, você pode controlar quais tipos de mensagem de rastreamento foram recebidas.</span><span class="sxs-lookup"><span data-stu-id="6a26e-113">By using the .config file to configure the switches to the appropriate settings, you could control what types of trace message you received.</span></span> <span data-ttu-id="6a26e-114">Para obter mais informações, consulte [Como criar, inicializar e configurar opções de rastreamento](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md).</span><span class="sxs-lookup"><span data-stu-id="6a26e-114">For more information, see [How to: Create, Initialize and Configure Trace Switches](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md).</span></span>  
  
 <span data-ttu-id="6a26e-115">Normalmente, um aplicativo implantado é executado com suas opções desabilitadas, de modo que os usuários não precisem observar muitas mensagens de rastreamento irrelevantes exibidas em uma tela ou enchendo um arquivo de log conforme o aplicativo é executado.</span><span class="sxs-lookup"><span data-stu-id="6a26e-115">Typically, a deployed application is executed with its switches disabled, so that users need not observe a lot of irrelevant trace messages appearing on a screen or filling up a log file as the application runs.</span></span> <span data-ttu-id="6a26e-116">Se surgir um problema durante a execução do aplicativo, pare o aplicativo, habilite as opções e reinicie o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6a26e-116">If a problem arises during application execution, you can stop the application, enable the switches, and restart the application.</span></span> <span data-ttu-id="6a26e-117">Em seguida, as mensagens de rastreamento serão exibidas.</span><span class="sxs-lookup"><span data-stu-id="6a26e-117">Then the tracing messages will be displayed.</span></span>  
  
 <span data-ttu-id="6a26e-118">Para usar uma opção, primeiro você deve criar um objeto de opção com base em uma classe **BooleanSwitch**, uma classe **TraceSwitch** ou uma classe de opção definida pelo desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="6a26e-118">To use a switch you must first create a switch object from a **BooleanSwitch** class, a **TraceSwitch** class, or a developer-defined switch class.</span></span> <span data-ttu-id="6a26e-119">Para obter mais informações sobre como criar opções definidas pelo desenvolvedor, consulte a classe <xref:System.Diagnostics.Switch> na referência do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6a26e-119">For more information about creating developer-defined switches, see the <xref:System.Diagnostics.Switch> class in the .NET Framework reference.</span></span> <span data-ttu-id="6a26e-120">Em seguida, defina um valor de configuração que especifica quando o objeto de opção deve ser usado.</span><span class="sxs-lookup"><span data-stu-id="6a26e-120">Then you set a configuration value that specifies when the switch object is to be used.</span></span> <span data-ttu-id="6a26e-121">Depois, teste a configuração do objeto de opção em vários métodos de rastreamento **Trace** (ou **Debug**).</span><span class="sxs-lookup"><span data-stu-id="6a26e-121">You then test the setting of the switch object in various **Trace** (or **Debug**) tracing methods.</span></span>  
  
## <a name="trace-levels"></a><span data-ttu-id="6a26e-122">Níveis de rastreamento</span><span class="sxs-lookup"><span data-stu-id="6a26e-122">Trace Levels</span></span>  
 <span data-ttu-id="6a26e-123">Ao usar **TraceSwitch**, há considerações adicionais.</span><span class="sxs-lookup"><span data-stu-id="6a26e-123">When you use **TraceSwitch**, there are additional considerations.</span></span> <span data-ttu-id="6a26e-124">Um objeto **TraceSwitch** tem quatro propriedades que retornam valores **boolianos**, indicando se a opção é definida com, pelo menos, um nível específico:</span><span class="sxs-lookup"><span data-stu-id="6a26e-124">A **TraceSwitch** object has four properties that return **Boolean** values indicating whether the switch is set to at least a particular level:</span></span>  
  
-   <xref:System.Diagnostics.TraceSwitch.TraceError%2A?displayProperty=fullName>  
  
-   <xref:System.Diagnostics.TraceSwitch.TraceWarning%2A?displayProperty=fullName>  
  
-   <xref:System.Diagnostics.TraceSwitch.TraceInfo%2A?displayProperty=fullName>  
  
-   <xref:System.Diagnostics.TraceSwitch.TraceVerbose%2A?displayProperty=fullName>  
  
 <span data-ttu-id="6a26e-125">Os níveis permitem limitar a quantidade de informações de rastreamento recebidas apenas às informações necessárias para solucionar um problema.</span><span class="sxs-lookup"><span data-stu-id="6a26e-125">Levels allow you to limit the amount of tracing information you receive to only that information needed to solve a problem.</span></span> <span data-ttu-id="6a26e-126">Especifique o nível de detalhe desejado na saída de rastreamento, definindo e configurando opções de rastreamento para o nível de rastreamento apropriado.</span><span class="sxs-lookup"><span data-stu-id="6a26e-126">You specify the level of detail you want in your tracing output by setting and configuring trace switches to the appropriate trace level.</span></span> <span data-ttu-id="6a26e-127">Você pode receber mensagens de erro, mensagens de aviso, mensagens informativas, mensagens de rastreamento detalhado ou nenhuma mensagem.</span><span class="sxs-lookup"><span data-stu-id="6a26e-127">You can receive error messages, warning messages, informational messages, verbose tracing messages, or no message at all.</span></span>  
  
 <span data-ttu-id="6a26e-128">Cabe inteiramente a você decidir que tipo de mensagem deve ser associada a cada nível.</span><span class="sxs-lookup"><span data-stu-id="6a26e-128">It is entirely up to you to decide what kind of message to associate with each level.</span></span> <span data-ttu-id="6a26e-129">Normalmente, o conteúdo das mensagens de rastreamento depende do que você associa a cada nível, mas você determina as diferenças entre os níveis.</span><span class="sxs-lookup"><span data-stu-id="6a26e-129">Typically, the content of tracing messages depends on what you associate with each level, but you determine the differences between levels.</span></span> <span data-ttu-id="6a26e-130">Talvez você deseje fornecer descrições detalhadas de um problema no nível 3 (**Informativo**), por exemplo, mas fornecer somente um número de referência de erro no nível 1 (**Erro**).</span><span class="sxs-lookup"><span data-stu-id="6a26e-130">You might want to provide detailed descriptions of a problem at level 3 (**Info**), for example, but provide only an error reference number at level 1 (**Error**).</span></span> <span data-ttu-id="6a26e-131">Cabe inteiramente a você decidir qual esquema funciona melhor em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6a26e-131">It is entirely up to you to decide what scheme works best in your application.</span></span>  
  
 <span data-ttu-id="6a26e-132">Essas propriedades correspondem aos valores 1 a 4 da enumeração **TraceLevel**.</span><span class="sxs-lookup"><span data-stu-id="6a26e-132">These properties correspond to the values 1 through 4 of the **TraceLevel** enumeration.</span></span> <span data-ttu-id="6a26e-133">A tabela a seguir lista os níveis da enumeração **TraceLevel** e seus valores.</span><span class="sxs-lookup"><span data-stu-id="6a26e-133">The following table lists the levels of the **TraceLevel** enumeration and their values.</span></span>  
  
|<span data-ttu-id="6a26e-134">Valor enumerado</span><span class="sxs-lookup"><span data-stu-id="6a26e-134">Enumerated value</span></span>|<span data-ttu-id="6a26e-135">Valor inteiro</span><span class="sxs-lookup"><span data-stu-id="6a26e-135">Integer value</span></span>|<span data-ttu-id="6a26e-136">Tipo de mensagem exibido (ou gravado em um destino de saída especificado)</span><span class="sxs-lookup"><span data-stu-id="6a26e-136">Type of message displayed (or written to a specified output target)</span></span>|  
|----------------------|-------------------|---------------------------------------------------------------------------|  
|<span data-ttu-id="6a26e-137">Off</span><span class="sxs-lookup"><span data-stu-id="6a26e-137">Off</span></span>|<span data-ttu-id="6a26e-138">0</span><span class="sxs-lookup"><span data-stu-id="6a26e-138">0</span></span>|<span data-ttu-id="6a26e-139">Nenhum</span><span class="sxs-lookup"><span data-stu-id="6a26e-139">None</span></span>|  
|<span data-ttu-id="6a26e-140">Erro</span><span class="sxs-lookup"><span data-stu-id="6a26e-140">Error</span></span>|<span data-ttu-id="6a26e-141">1</span><span class="sxs-lookup"><span data-stu-id="6a26e-141">1</span></span>|<span data-ttu-id="6a26e-142">Somente mensagens de erro</span><span class="sxs-lookup"><span data-stu-id="6a26e-142">Only error messages</span></span>|  
|<span data-ttu-id="6a26e-143">Aviso</span><span class="sxs-lookup"><span data-stu-id="6a26e-143">Warning</span></span>|<span data-ttu-id="6a26e-144">2</span><span class="sxs-lookup"><span data-stu-id="6a26e-144">2</span></span>|<span data-ttu-id="6a26e-145">Mensagens de aviso e mensagens de erro</span><span class="sxs-lookup"><span data-stu-id="6a26e-145">Warning messages and error messages</span></span>|  
|<span data-ttu-id="6a26e-146">Info</span><span class="sxs-lookup"><span data-stu-id="6a26e-146">Info</span></span>|<span data-ttu-id="6a26e-147">3</span><span class="sxs-lookup"><span data-stu-id="6a26e-147">3</span></span>|<span data-ttu-id="6a26e-148">Mensagens informativas, mensagens de aviso e mensagens de erro</span><span class="sxs-lookup"><span data-stu-id="6a26e-148">Informational messages, warning messages, and error messages</span></span>|  
|<span data-ttu-id="6a26e-149">Detalhado</span><span class="sxs-lookup"><span data-stu-id="6a26e-149">Verbose</span></span>|<span data-ttu-id="6a26e-150">4</span><span class="sxs-lookup"><span data-stu-id="6a26e-150">4</span></span>|<span data-ttu-id="6a26e-151">Mensagens detalhadas, mensagens informativas, mensagens de aviso e mensagens de erro</span><span class="sxs-lookup"><span data-stu-id="6a26e-151">Verbose messages, informational messages, warning messages, and error messages</span></span>|  
  
 <span data-ttu-id="6a26e-152">As propriedades **TraceSwitch** indicam o nível máximo de rastreamento da opção.</span><span class="sxs-lookup"><span data-stu-id="6a26e-152">The **TraceSwitch** properties indicate the maximum trace level for the switch.</span></span> <span data-ttu-id="6a26e-153">Ou seja, as informações de rastreamento são gravadas para o nível especificado, bem como para todos os níveis inferiores.</span><span class="sxs-lookup"><span data-stu-id="6a26e-153">That is, tracing information is written for the level specified as well as for all lower levels.</span></span> <span data-ttu-id="6a26e-154">Por exemplo, se **TraceInfo** for **true**, **TraceError** e **TraceWarning** também serão **true**, mas **TraceVerbose** poderá ser **false**.</span><span class="sxs-lookup"><span data-stu-id="6a26e-154">For example, if **TraceInfo** is **true**, then **TraceError** and **TraceWarning** are also **true** but **TraceVerbose** might well be **false**.</span></span>  
  
 <span data-ttu-id="6a26e-155">Essas propriedades são somente leitura.</span><span class="sxs-lookup"><span data-stu-id="6a26e-155">These properties are read-only.</span></span> <span data-ttu-id="6a26e-156">O objeto **TraceSwitch** define-as automaticamente quando a propriedade **TraceLevel** é definida.</span><span class="sxs-lookup"><span data-stu-id="6a26e-156">The **TraceSwitch** object automatically sets them when the **TraceLevel** property is set.</span></span> <span data-ttu-id="6a26e-157">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="6a26e-157">For example:</span></span>  
  
```vb  
Dim myTraceSwitch As New TraceSwitch("SwitchOne", "The first switch")  
myTraceSwitch.Level = TraceLevel.Info  
' This message box displays true, because setting the level to  
' TraceLevel.Info sets all lower levels to true as well.  
MessageBox.Show(myTraceSwitch.TraceWarning.ToString())  
' This messagebox displays false.  
MessageBox.Show(myTraceSwitch.TraceVerbose.ToString())  
```  
  
```csharp  
System.Diagnostics.TraceSwitch myTraceSwitch =   
   new System.Diagnostics.TraceSwitch("SwitchOne", "The first switch");  
myTraceSwitch.Level = System.Diagnostics.TraceLevel.Info;  
// This message box displays true, because setting the level to   
// TraceLevel.Info sets all lower levels to true as well.  
MessageBox.Show(myTraceSwitch.TraceWarning.ToString());  
// This message box displays false.  
MessageBox.Show(myTraceSwitch.TraceVerbose.ToString());  
```  
  
## <a name="developer-defined-switches"></a><span data-ttu-id="6a26e-158">Opções definidas pelo desenvolvedor</span><span class="sxs-lookup"><span data-stu-id="6a26e-158">Developer-Defined Switches</span></span>  
 <span data-ttu-id="6a26e-159">Além de fornecer **BooleanSwitch** e **TraceSwitch**, você pode definir suas próprias opções herdando da classe **Switch** e substituindo os métodos da classe base por métodos personalizados.</span><span class="sxs-lookup"><span data-stu-id="6a26e-159">In addition to providing **BooleanSwitch** and **TraceSwitch**, you can define your own switches by inheriting from the **Switch** class and overriding the base class methods with customized methods.</span></span> <span data-ttu-id="6a26e-160">Para obter mais informações sobre como criar opções definidas pelo desenvolvedor, consulte a classe <xref:System.Diagnostics.Switch> na referência do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6a26e-160">For more information about creating developer-defined switches, see the <xref:System.Diagnostics.Switch> class in the .NET Framework reference.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a26e-161">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6a26e-161">See Also</span></span>  
 <span data-ttu-id="6a26e-162">[Ouvintes de rastreamento](../../../docs/framework/debug-trace-profile/trace-listeners.md) </span><span class="sxs-lookup"><span data-stu-id="6a26e-162">[Trace Listeners](../../../docs/framework/debug-trace-profile/trace-listeners.md) </span></span>  
 <span data-ttu-id="6a26e-163">[Como adicionar instruções de rastreamento ao código do aplicativo](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md) </span><span class="sxs-lookup"><span data-stu-id="6a26e-163">[How to: Add Trace Statements to Application Code](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md) </span></span>  
 [<span data-ttu-id="6a26e-164">Rastreando e instrumentando aplicativos</span><span class="sxs-lookup"><span data-stu-id="6a26e-164">Tracing and Instrumenting Applications</span></span>](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)
