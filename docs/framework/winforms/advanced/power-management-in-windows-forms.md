---
title: Gerenciamento de energia no Windows Forms
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
- battery states
- power states
ms.assetid: ad04a801-5682-4d88-92c5-26eb9cdb209a
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e12f39a63a4f81e6deec4512a4e18ad2bda7e5e0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="power-management-in-windows-forms"></a><span data-ttu-id="2e837-102">Gerenciamento de energia no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2e837-102">Power Management in Windows Forms</span></span>
<span data-ttu-id="2e837-103">Seus aplicativos Windows Forms podem tirar proveito dos recursos de gerenciamento de energia no sistema operacional Windows.</span><span class="sxs-lookup"><span data-stu-id="2e837-103">Your Windows Forms applications can take advantage of the power management features in the Windows operating system.</span></span> <span data-ttu-id="2e837-104">Os aplicativos podem monitorar o status de energia de um computador e agir quando ocorre uma alteração de status.</span><span class="sxs-lookup"><span data-stu-id="2e837-104">Your applications can monitor the power status of a computer and take action when a status change occurs.</span></span> <span data-ttu-id="2e837-105">Por exemplo, se o aplicativo é executado em um computador portátil, convém desabilitar determinados recursos do seu aplicativo quando a carga da bateria do computador fica abaixo de um determinado nível.</span><span class="sxs-lookup"><span data-stu-id="2e837-105">For example, if your application is running on a portable computer, you might want to disable certain features in your application when the computer's battery charge falls under a certain level.</span></span>  
  
 <span data-ttu-id="2e837-106">O [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] fornece um <xref:Microsoft.Win32.SystemEvents.PowerModeChanged> evento que ocorre sempre que houver uma alteração no status de energia, como quando um usuário suspende ou reinicia o sistema operacional, ou quando altera o status de energia AC ou o status da bateria.</span><span class="sxs-lookup"><span data-stu-id="2e837-106">The [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] provides a <xref:Microsoft.Win32.SystemEvents.PowerModeChanged> event that occurs whenever there is a change in power status, such as when a user suspends or resumes the operating system, or when the AC power status or battery status changes.</span></span> <span data-ttu-id="2e837-107">O <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A> propriedade o <xref:System.Windows.Forms.SystemInformation> classe pode ser usada para consultar o status atual, conforme mostrado no exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="2e837-107">The <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A> property of the <xref:System.Windows.Forms.SystemInformation> class can be used to query for the current status, as shown in the following code example.</span></span>  
  
 [!code-csharp[PowerMode#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/powermode/cs/form1.cs#1)]
 [!code-vb[PowerMode#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/powermode/vb/form1.vb#1)]  
  
 <span data-ttu-id="2e837-108">Além de <xref:System.Windows.Forms.BatteryChargeStatus> enumerações, o <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A> propriedade também contém enumerações para determinar a capacidade da bateria (<xref:System.Windows.Forms.PowerStatus.BatteryFullLifetime%2A>) e porcentagem carga da bateria (<xref:System.Windows.Forms.PowerStatus.BatteryLifePercent%2A>, <xref:System.Windows.Forms.PowerStatus.BatteryLifeRemaining%2A>).</span><span class="sxs-lookup"><span data-stu-id="2e837-108">Besides the <xref:System.Windows.Forms.BatteryChargeStatus> enumerations, the <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A> property also contains enumerations for determining battery capacity (<xref:System.Windows.Forms.PowerStatus.BatteryFullLifetime%2A>) and battery charge percentage (<xref:System.Windows.Forms.PowerStatus.BatteryLifePercent%2A>, <xref:System.Windows.Forms.PowerStatus.BatteryLifeRemaining%2A>).</span></span>  
  
 <span data-ttu-id="2e837-109">Você pode usar o <xref:System.Windows.Forms.Application.SetSuspendState%2A> método o <xref:System.Windows.Forms.Application> para colocar um computador em hibernação ou modo de suspensão.</span><span class="sxs-lookup"><span data-stu-id="2e837-109">You can use the <xref:System.Windows.Forms.Application.SetSuspendState%2A> method of the <xref:System.Windows.Forms.Application> to put a computer into hibernation or suspend mode.</span></span> <span data-ttu-id="2e837-110">Se o argumento `force` for definido para `false`, o sistema operacional transmitirá um evento para todos os aplicativos solicitando permissão para suspender.</span><span class="sxs-lookup"><span data-stu-id="2e837-110">If the `force` argument is set to `false`, the operating system will broadcast an event to all applications requesting permission to suspend.</span></span> <span data-ttu-id="2e837-111">Se o argumento `disableWakeEvent` é definido para `true`, o sistema operacional desabilita todos os eventos de ativação.</span><span class="sxs-lookup"><span data-stu-id="2e837-111">If the `disableWakeEvent` argument is set to `true`, the operating system disables all wake events.</span></span>  
  
 <span data-ttu-id="2e837-112">O exemplo de código a seguir demonstra como colocar um computador em hibernação.</span><span class="sxs-lookup"><span data-stu-id="2e837-112">The following code example demonstrates how to put a computer into hibernation.</span></span>  
  
 [!code-csharp[PowerMode#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/powermode/cs/form1.cs#2)]
 [!code-vb[PowerMode#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/powermode/vb/form1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="2e837-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2e837-113">See Also</span></span>  
 <xref:Microsoft.Win32.SystemEvents.PowerModeChanged>  
 <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A>  
 <xref:System.Windows.Forms.Application.SetSuspendState%2A>  
 <xref:Microsoft.Win32.SystemEvents.SessionSwitch>