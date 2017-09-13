---
title: "Como exibir o status de conexão usando o WIF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4d1174e4-5397-4962-9a5f-3b1ad7b3fc14
caps.latest.revision: 6
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 494e67b39187a2a38f29f994e17051430d90f708
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="how-to-display-signed-in-status-using-wif"></a><span data-ttu-id="18b8a-102">Como exibir o status de conexão usando o WIF</span><span class="sxs-lookup"><span data-stu-id="18b8a-102">How To: Display Signed In Status Using WIF</span></span>
## <a name="applies-to"></a><span data-ttu-id="18b8a-103">Aplica-se a</span><span class="sxs-lookup"><span data-stu-id="18b8a-103">Applies To</span></span>  
  
-   <span data-ttu-id="18b8a-104">Microsoft® Windows® Identity Foundation (WIF) 4.5</span><span class="sxs-lookup"><span data-stu-id="18b8a-104">Microsoft® Windows® Identity Foundation (WIF) 4.5</span></span>  
  
-   <span data-ttu-id="18b8a-105">Web Forms do ASP.NET®</span><span class="sxs-lookup"><span data-stu-id="18b8a-105">ASP.NET® Web Forms</span></span>  
  
## <a name="summary"></a><span data-ttu-id="18b8a-106">Resumo</span><span class="sxs-lookup"><span data-stu-id="18b8a-106">Summary</span></span>  
 <span data-ttu-id="18b8a-107">Este tópico descreve como exibir o status de entrada em um aplicativo ASP.NET habilitado para WIF.</span><span class="sxs-lookup"><span data-stu-id="18b8a-107">This topic describes how to display the sign in status in a WIF-enabled ASP.NET application.</span></span> <span data-ttu-id="18b8a-108">O WIF fornece o mecanismo para fazer com que seu aplicativo reconheça declarações e para gerenciar autenticação e autorização para recursos do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="18b8a-108">WIF provides the mechanism for making your application claims-aware, and managing authentication and authorization for application resources.</span></span>  
  
## <a name="contents"></a><span data-ttu-id="18b8a-109">Conteúdo</span><span class="sxs-lookup"><span data-stu-id="18b8a-109">Contents</span></span>  
  
-   <span data-ttu-id="18b8a-110">Visão Geral</span><span class="sxs-lookup"><span data-stu-id="18b8a-110">Overview</span></span>  
  
-   <span data-ttu-id="18b8a-111">Resumo das etapas</span><span class="sxs-lookup"><span data-stu-id="18b8a-111">Summary of Steps</span></span>  
  
-   <span data-ttu-id="18b8a-112">Etapa 1 – instalar a extensão de Identidade e Acesso</span><span class="sxs-lookup"><span data-stu-id="18b8a-112">Step 1 – Install the Identity and Access Extension</span></span>  
  
-   <span data-ttu-id="18b8a-113">Etapa 2 – criar um aplicativo ASP.NET de terceira parte confiável</span><span class="sxs-lookup"><span data-stu-id="18b8a-113">Step 2 – Create a Relying Party ASP.NET Application</span></span>  
  
-   <span data-ttu-id="18b8a-114">Etapa 3 – habilitar o STS de desenvolvimento local para autenticar usuários</span><span class="sxs-lookup"><span data-stu-id="18b8a-114">Step 3 – Enable Local Development STS to Authenticate Users</span></span>  
  
-   <span data-ttu-id="18b8a-115">Etapa 4 – modificar seu aplicativo ASP.NET para exibir o status de entrada</span><span class="sxs-lookup"><span data-stu-id="18b8a-115">Step 4 – Modify Your ASP.NET Application to Display Sign In Status</span></span>  
  
-   <span data-ttu-id="18b8a-116">Etapa 5 – testar a integração entre o WIF e o seu aplicativo ASP.NET</span><span class="sxs-lookup"><span data-stu-id="18b8a-116">Step 5 – Test the Integration Between WIF and Your ASP.NET Application</span></span>  
  
## <a name="overview"></a><span data-ttu-id="18b8a-117">Visão Geral</span><span class="sxs-lookup"><span data-stu-id="18b8a-117">Overview</span></span>  
 <span data-ttu-id="18b8a-118">Este tópico demonstra como criar um aplicativo com reconhecimento de declaração simples usando o WIF e como exibir facilmente se um usuário está conectado ou não.</span><span class="sxs-lookup"><span data-stu-id="18b8a-118">This topic demonstrates how to create a simple claims-aware application using WIF and how to easily display whether a user is signed in or not.</span></span> <span data-ttu-id="18b8a-119">As etapas a seguir usam o STS de desenvolvimento local que está incluído com a extensão de Identidade e Acesso do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="18b8a-119">The following steps use the Local Development STS that is included with the Identity and Access Visual Studio Extension.</span></span> <span data-ttu-id="18b8a-120">O STS de desenvolvimento local destina-se a um ambiente de teste e desenvolvimento para fornecer um método simples de integrar declarações em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="18b8a-120">The Local Development STS is intended for a testing and development environment to provide a simple method of integrating claims into your application.</span></span> <span data-ttu-id="18b8a-121">Ele nunca deve ser usado em um ambiente de produção, já que ele não executa autenticação real e credenciais não são necessárias.</span><span class="sxs-lookup"><span data-stu-id="18b8a-121">It should never be used in a production environment, as it does not perform real authentication and credentials are not required.</span></span> <span data-ttu-id="18b8a-122">No entanto, o código obrigatório nas etapas a seguir é o mesmo para um aplicativo pronto para produção usando autenticação real.</span><span class="sxs-lookup"><span data-stu-id="18b8a-122">However, the imperative code in the following steps is the same for a production-ready application using real authentication.</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="18b8a-123">Resumo das etapas</span><span class="sxs-lookup"><span data-stu-id="18b8a-123">Summary of Steps</span></span>  
  
-   <span data-ttu-id="18b8a-124">Etapa 1 – instalar a extensão de Identidade e Acesso</span><span class="sxs-lookup"><span data-stu-id="18b8a-124">Step 1 – Install the Identity and Access Extension</span></span>  
  
-   <span data-ttu-id="18b8a-125">Etapa 2 – criar um aplicativo ASP.NET de terceira parte confiável</span><span class="sxs-lookup"><span data-stu-id="18b8a-125">Step 2 – Create a Relying Party ASP.NET Application</span></span>  
  
-   <span data-ttu-id="18b8a-126">Etapa 3 – habilitar o STS de desenvolvimento local para autenticar usuários</span><span class="sxs-lookup"><span data-stu-id="18b8a-126">Step 3 – Enable Local Development STS to Authenticate Users</span></span>  
  
-   <span data-ttu-id="18b8a-127">Etapa 4 – modificar seu aplicativo ASP.NET para exibir o status de entrada</span><span class="sxs-lookup"><span data-stu-id="18b8a-127">Step 4 – Modify Your ASP.NET Application to Display Sign In Status</span></span>  
  
-   <span data-ttu-id="18b8a-128">Etapa 5 – testar a integração entre o WIF e o seu aplicativo ASP.NET</span><span class="sxs-lookup"><span data-stu-id="18b8a-128">Step 5 – Test the Integration Between WIF and Your ASP.NET Application</span></span>  
  
## <a name="step-1--install-the-identity-and-access-extension"></a><span data-ttu-id="18b8a-129">Etapa 1 – instalar a extensão de Identidade e Acesso</span><span class="sxs-lookup"><span data-stu-id="18b8a-129">Step 1 – Install the Identity and Access Extension</span></span>  
 <span data-ttu-id="18b8a-130">Essa etapa descreve como configurar a extensão de Identidade e Acesso para o Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="18b8a-130">This step describes how to configure the Identity and Access extension to Visual Studio 2012.</span></span> <span data-ttu-id="18b8a-131">Essa extensão automatiza o processo de configurar seu aplicativo para se comunicar com pontos de extremidade do STS.</span><span class="sxs-lookup"><span data-stu-id="18b8a-131">This extension automates the process of configuring your application to communicate with STS endpoints.</span></span>  
  
#### <a name="to-install-the-identity-and-access-extension"></a><span data-ttu-id="18b8a-132">Para instalar a extensão de Identidade e Acesso</span><span class="sxs-lookup"><span data-stu-id="18b8a-132">To install the Identity and Access extension</span></span>  
  
1.  <span data-ttu-id="18b8a-133">Inicie o Visual Studio em modo elevado como administrador.</span><span class="sxs-lookup"><span data-stu-id="18b8a-133">Start Visual Studio in elevated mode as administrator.</span></span>  
  
2.  <span data-ttu-id="18b8a-134">No Visual Studio, clique em **Ferramentas** e clique em **Gerenciador de Extensões**.</span><span class="sxs-lookup"><span data-stu-id="18b8a-134">In Visual Studio, click **Tools** and click **Extension Manager**.</span></span> <span data-ttu-id="18b8a-135">A janela **Gerenciador de Extensões** é exibida.</span><span class="sxs-lookup"><span data-stu-id="18b8a-135">The **Extension Manager** window appears.</span></span>  
  
3.  <span data-ttu-id="18b8a-136">Em **Gerenciador de Extensões**, clique em **Extensões Online** no menu à esquerda, então selecione **Galeria do Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="18b8a-136">In **Extension Manager**, click **Online Extensions** from the left menu, then select **Visual Studio Gallery**.</span></span>  
  
4.  <span data-ttu-id="18b8a-137">No canto superior direito do **Gerenciador de Extensões**, pesquise por *Identidade e Acesso*.</span><span class="sxs-lookup"><span data-stu-id="18b8a-137">In the top right corner of **Extension Manager**, search for *Identity and Access*.</span></span>  
  
5.  <span data-ttu-id="18b8a-138">O item **Identidade e Acesso** aparecerá nos resultados da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="18b8a-138">The **Identity and Access** item will appear in the search results.</span></span> <span data-ttu-id="18b8a-139">Clique nele e, em seguida, clique em **Baixar**.</span><span class="sxs-lookup"><span data-stu-id="18b8a-139">Click it, and then click **Download**.</span></span>  
  
6.  <span data-ttu-id="18b8a-140">A caixa de diálogo **Baixar e Instalar** aparecerá.</span><span class="sxs-lookup"><span data-stu-id="18b8a-140">The **Download and Install** dialog appears.</span></span> <span data-ttu-id="18b8a-141">Se concordar com os termos de licença, clique em **Instalar**.</span><span class="sxs-lookup"><span data-stu-id="18b8a-141">If you agree with the license terms, click **Install**.</span></span>  
  
7.  <span data-ttu-id="18b8a-142">Quando a instalação da extensão **Identidade e Acesso** for concluída, reinicie o Visual Studio no modo de administrador.</span><span class="sxs-lookup"><span data-stu-id="18b8a-142">When the **Identity and Access** extension has finished installing, restart Visual Studio in administrator mode.</span></span>  
  
## <a name="step-2--create-a-relying-party-aspnet-application"></a><span data-ttu-id="18b8a-143">Etapa 2 – criar um aplicativo ASP.NET de terceira parte confiável</span><span class="sxs-lookup"><span data-stu-id="18b8a-143">Step 2 – Create a Relying Party ASP.NET Application</span></span>  
 <span data-ttu-id="18b8a-144">Essa etapa descreve como criar um aplicativo de ASP.NET Web Forms de terceira parte confiável que integrará o WIF.</span><span class="sxs-lookup"><span data-stu-id="18b8a-144">This step describes how to create a relying party ASP.NET Web Forms application that will integrate with WIF.</span></span>  
  
#### <a name="to-create-a-simple-aspnet-application"></a><span data-ttu-id="18b8a-145">Para criar um aplicativo ASP.NET simples</span><span class="sxs-lookup"><span data-stu-id="18b8a-145">To create a simple ASP.NET application</span></span>  
  
1.  <span data-ttu-id="18b8a-146">Inicie o Visual Studio, clique em **Arquivo**, **Novo** e, depois, em **Projeto**.</span><span class="sxs-lookup"><span data-stu-id="18b8a-146">Start Visual Studio and click **File**, **New**, and then **Project**.</span></span>  
  
2.  <span data-ttu-id="18b8a-147">Na janela **Novo Projeto**, clique em **Aplicativo ASP.NET Web Forms**.</span><span class="sxs-lookup"><span data-stu-id="18b8a-147">In the **New Project** window, click **ASP.NET Web Forms Application**.</span></span>  
  
3.  <span data-ttu-id="18b8a-148">Em **Nome**, insira `TestApp` e pressione **OK**.</span><span class="sxs-lookup"><span data-stu-id="18b8a-148">In **Name**, enter `TestApp` and press **OK**.</span></span>  
  
## <a name="step-3--enable-local-development-sts-to-authenticate-users"></a><span data-ttu-id="18b8a-149">Etapa 3 – habilitar o STS de desenvolvimento local para autenticar usuários</span><span class="sxs-lookup"><span data-stu-id="18b8a-149">Step 3 – Enable Local Development STS to Authenticate Users</span></span>  
 <span data-ttu-id="18b8a-150">Essa etapa descreve como habilitar o STS de desenvolvimento local em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="18b8a-150">This step describes how to enable Local Development STS in your application.</span></span> <span data-ttu-id="18b8a-151">O STS de desenvolvimento local é habilitado usando a extensão de Identidade e Acesso para o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="18b8a-151">Local Development STS is enabled by using the Identity and Access extension for Visual Studio.</span></span>  
  
#### <a name="to-enable-local-development-sts-in-your-aspnet-application"></a><span data-ttu-id="18b8a-152">Para habilitar o STS de desenvolvimento local em seu aplicativo ASP.NET</span><span class="sxs-lookup"><span data-stu-id="18b8a-152">To enable Local Development STS in your ASP.NET application</span></span>  
  
1.  <span data-ttu-id="18b8a-153">No Visual Studio, clique com o botão direito do mouse no projeto **TestApp** em **Gerenciador de Soluções** e selecione **Identidade e Acesso**.</span><span class="sxs-lookup"><span data-stu-id="18b8a-153">In Visual Studio, right-click the **TestApp** project under **Solution Explorer**, then select **Identity and Access**.</span></span>  
  
2.  <span data-ttu-id="18b8a-154">A janela **Identidade e Acesso** é exibida.</span><span class="sxs-lookup"><span data-stu-id="18b8a-154">The **Identity and Access** window appears.</span></span> <span data-ttu-id="18b8a-155">Em **Provedores**, selecione **Testar o aplicativo com o STS de Desenvolvimento Local** e clique em **Aplicar**.</span><span class="sxs-lookup"><span data-stu-id="18b8a-155">Under **Providers**, select **Test your application with the Local Development STS**, then click **Apply**.</span></span>  
  
## <a name="step-4--modify-your-aspnet-application-to-display-sign-in-status"></a><span data-ttu-id="18b8a-156">Etapa 4 – modificar seu aplicativo ASP.NET para exibir o status de entrada</span><span class="sxs-lookup"><span data-stu-id="18b8a-156">Step 4 – Modify Your ASP.NET Application to Display Sign In Status</span></span>  
 <span data-ttu-id="18b8a-157">Essa etapa descreve como modificar seu aplicativo ASP.NET para exibir dinamicamente se o usuário atual está conectado.</span><span class="sxs-lookup"><span data-stu-id="18b8a-157">This step describes how to modify your ASP.NET application to dynamically display whether the current user is signed in.</span></span> <span data-ttu-id="18b8a-158">Depois que o provedor de STS tiver sido configurado, o WIF manipulará as declarações de entrada.</span><span class="sxs-lookup"><span data-stu-id="18b8a-158">Once your STS provider has been configured, WIF handles the incoming claims.</span></span> <span data-ttu-id="18b8a-159">Agora você precisa configurar o código do aplicativo para exibir o resultado da autenticação.</span><span class="sxs-lookup"><span data-stu-id="18b8a-159">Now you need to configure your application’s code to display the result of the authentication.</span></span>  
  
#### <a name="to-display-sign-in-status"></a><span data-ttu-id="18b8a-160">Para exibir o status de entrada</span><span class="sxs-lookup"><span data-stu-id="18b8a-160">To display sign in status</span></span>  
  
1.  <span data-ttu-id="18b8a-161">No Visual Studio, abra o arquivo **Default.aspx** no projeto **TestApp**.</span><span class="sxs-lookup"><span data-stu-id="18b8a-161">In Visual Studio, open the **Default.aspx** file under the **TestApp** project.</span></span>  
  
2.  <span data-ttu-id="18b8a-162">Substitua a marcação existente no arquivo **Default.aspx** pela seguinte:</span><span class="sxs-lookup"><span data-stu-id="18b8a-162">Replace the existing markup in the **Default.aspx** file with the following markup:</span></span>  
  
    ```  
    <%@ Page Language="C#" AutoEventWireup="true" CodeFile="Default.aspx.cs" Inherits="_Default" %>  
  
    <!DOCTYPE html>  
  
    <html>  
    <head runat="server">  
        <title>Logged In Status</title>  
    </head>  
    <body>  
        <asp:label ID="myLabel" runat="server" />  
    </body>  
    </html>  
    ```  
  
3.  <span data-ttu-id="18b8a-163">Salve **Default.aspx** e, depois, abra seu arquivo code-behind chamado **Default.aspx.cs**.</span><span class="sxs-lookup"><span data-stu-id="18b8a-163">Save **Default.aspx**, and then open its code behind file named **Default.aspx.cs**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="18b8a-164">**Default.aspx.cs** pode estar oculto sob **Default.aspx** no Gerenciador de Soluções.</span><span class="sxs-lookup"><span data-stu-id="18b8a-164">**Default.aspx.cs** may be hidden beneath **Default.aspx** in Solution Explorer.</span></span> <span data-ttu-id="18b8a-165">Se **Default.aspx.cs** não estiver visível, expanda **Default.aspx** clicando no triângulo ao lado dele.</span><span class="sxs-lookup"><span data-stu-id="18b8a-165">If **Default.aspx.cs** is not visible, expand **Default.aspx** by clicking on the triangle next to it.</span></span>  
  
4.  <span data-ttu-id="18b8a-166">Substitua o código existente em **Default.aspx.cs** pelo seguinte código:</span><span class="sxs-lookup"><span data-stu-id="18b8a-166">Replace the existing code in **Default.aspx.cs** with the following code:</span></span>  
  
    ```csharp  
    using System;  
    using System.Web.UI;  
    using System.Security.Claims;  
  
    namespace TestApp  
    {  
        protected void Page_Load(object sender, EventArgs e)  
        {  
            ClaimsPrincipal claimsPrincipal = Thread.CurrentPrincipal as ClaimsPrincipal;  
  
            if (claimsPrincipal != null)  
            {  
                myLabel.Text = "You are signed in.";  
            }  
            else  
            {  
                myLabel.Text = "You are not signed in.";  
            }  
        }  
    }  
    ```  
  
5.  <span data-ttu-id="18b8a-167">Salve **Default.aspx.cs** e compile o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="18b8a-167">Save **Default.aspx.cs**, and build the application.</span></span>  
  
## <a name="step-5--test-the-integration-between-wif-and-your-aspnet-application"></a><span data-ttu-id="18b8a-168">Etapa 5 – testar a integração entre o WIF e o seu aplicativo ASP.NET</span><span class="sxs-lookup"><span data-stu-id="18b8a-168">Step 5 – Test the Integration Between WIF and Your ASP.NET Application</span></span>  
 <span data-ttu-id="18b8a-169">Esta etapa descreve como você pode testar a integração entre o WIF e o seu aplicativo ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="18b8a-169">This step describes how you can test the integration between WIF and your ASP.NET application.</span></span>  
  
#### <a name="to-test-the-integration-between-wif-and-aspnet"></a><span data-ttu-id="18b8a-170">Para testar a integração entre o WIF e o ASP.NET</span><span class="sxs-lookup"><span data-stu-id="18b8a-170">To test the integration between WIF and ASP.NET</span></span>  
  
1.  <span data-ttu-id="18b8a-171">No Visual Studio, pressione **F5** para iniciar a depuração de seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="18b8a-171">In Visual Studio, press **F5** to start debugging your application.</span></span> <span data-ttu-id="18b8a-172">Se nenhum erro for encontrado, uma nova janela do navegador será aberta.</span><span class="sxs-lookup"><span data-stu-id="18b8a-172">If no errors are found, a new browser window will open.</span></span>  
  
2.  <span data-ttu-id="18b8a-173">Você pode perceber que o navegador redireciona silenciosamente a solicitação para o STS e, em seguida, abre a página Default.aspx.</span><span class="sxs-lookup"><span data-stu-id="18b8a-173">You may notice that the browser silently redirects your request to the STS, and then opens the Default.aspx page.</span></span> <span data-ttu-id="18b8a-174">Se o WIF estiver configurado corretamente, você deverá ver o site exibir o seguinte texto: **"Você está conectado"**.</span><span class="sxs-lookup"><span data-stu-id="18b8a-174">If WIF is properly configured, you should see the site display the following text: **"You are signed in"**.</span></span>
