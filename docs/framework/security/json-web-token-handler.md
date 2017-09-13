---
title: Manipulador de Token da Web JSON
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9968f12e-e05d-4e6a-9b65-6896c0e31ab1
caps.latest.revision: 5
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 6772d484fa4d0ed3948ecee26adb2cf886340f11
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="json-web-token-handler"></a><span data-ttu-id="4661d-102">Manipulador de Token da Web JSON</span><span class="sxs-lookup"><span data-stu-id="4661d-102">JSON Web Token Handler</span></span>
<span data-ttu-id="4661d-103">A extensão do Manipulador de Tokens da Web JSON para Windows Identity Foundation permite que você crie e valide JWT (Tokens da Web JSON) em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="4661d-103">The JSON Web Token Handler extension for Windows Identity Foundation enables you to create and validate JSON Web Tokens (JWT) in your applications.</span></span> <span data-ttu-id="4661d-104">O Manipulador de Tokens JWT pode ser configurado para ser executado no pipeline WIF como outros manipuladores de tokens de segurança internos, mas também pode ser usado de forma independente para executar a validação do token em aplicativos leves.</span><span class="sxs-lookup"><span data-stu-id="4661d-104">The JWT Token Handler can be configured to run in the WIF pipeline like other built-in security token handlers, but it can also be used independently to perform token validation in lightweight applications.</span></span> <span data-ttu-id="4661d-105">O Manipulador de Tokens JWT é particularmente útil ao usar um esquema de token portador OAuth 2.0, como a autenticação no Active Directory do Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="4661d-105">The JWT Token Handler is particularly useful when using an OAuth 2.0 bearer token scheme, such as authenticating to Windows Azure Active Directory.</span></span>  
  
 <span data-ttu-id="4661d-106">O Manipulador de Tokens JWT está disponível como um pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="4661d-106">The JWT Token Handler is available as a NuGet package.</span></span> <span data-ttu-id="4661d-107">Consulte [Baixando o pacote do manipulador de token Web JSON](../../../docs/framework/security/downloading-the-json-web-token-handler-package.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="4661d-107">See [Downloading the JSON Web Token Handler Package](../../../docs/framework/security/downloading-the-json-web-token-handler-package.md) for more information.</span></span>  
  
## <a name="scenarios"></a><span data-ttu-id="4661d-108">Cenários</span><span class="sxs-lookup"><span data-stu-id="4661d-108">Scenarios</span></span>  
 <span data-ttu-id="4661d-109">O Manipulador de Tokens JWT permite os seguintes cenários principais:</span><span class="sxs-lookup"><span data-stu-id="4661d-109">The JWT Token Handler enables the following key scenarios:</span></span>  
  
-   <span data-ttu-id="4661d-110">**Validar um token JWT em um aplicativo para servidores**: nesse cenário, uma empresa chamada Litware tem um aplicativo para servidores que usa WIF para manipular solicitações de logon da Web.</span><span class="sxs-lookup"><span data-stu-id="4661d-110">**Validate a JWT Token in a Server Application**: In this scenario, a company named Litware has a server application that uses WIF to handle web sign-on requests.</span></span> <span data-ttu-id="4661d-111">A Litware deseja permitir que seu aplicativo use tokens JWT para autenticação.</span><span class="sxs-lookup"><span data-stu-id="4661d-111">Litware wants to enable their application to use JWT tokens for authentication.</span></span> <span data-ttu-id="4661d-112">O aplicativo é atualizado com o Manipulador de Tokens JWT e depois a configuração do aplicativo é atualizada para adicionar o Manipulador de Tokens JWT no pipeline WIF.</span><span class="sxs-lookup"><span data-stu-id="4661d-112">The application is updated with the JWT Token Handler, and then the application configuration is updated to add the JWT Token Handler in the WIF pipeline.</span></span> <span data-ttu-id="4661d-113">Depois que as atualizações são feitas e uma nova solicitação entra no pipeline WIF, o token do JWT é validado usando o novo manipulador, e a autenticação bem-sucedida ocorre.</span><span class="sxs-lookup"><span data-stu-id="4661d-113">After the updates have been made and a new request enters the WIF pipeline, the JWT token is validated using the new handler and successful authentication occurs.</span></span>  
  
-   <span data-ttu-id="4661d-114">**Validar um token JWT em um serviço Web REST**: nesse cenário, uma empresa chamada Litware tem um serviço Web REST que é protegido pelo Microsoft Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="4661d-114">**Validate a JWT Token in a REST Web Service**: In this scenario, a company named Litware has a REST web service that is secured by Windows Azure Active Directory.</span></span> <span data-ttu-id="4661d-115">As solicitações para o serviço Web devem ser autenticadas pelo AD do Microsoft Azure, que emite um token JWT na autenticação bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="4661d-115">Requests to the web service must be authenticated by Windows Azure AD, which issues a JWT token upon successful authentication.</span></span> <span data-ttu-id="4661d-116">A Litware tem um aplicativo cliente que precisa acessar o serviço Web.</span><span class="sxs-lookup"><span data-stu-id="4661d-116">Litware has a client application that needs to access the web service.</span></span> <span data-ttu-id="4661d-117">O cliente faz uma solicitação ao serviço Web e apresenta seu token JWT do AD do Microsoft Azure, que é validado pelo serviço Web usando o Manipulador de Tokens JWT.</span><span class="sxs-lookup"><span data-stu-id="4661d-117">The client makes a request to the web service and presents its JWT token from Windows Azure AD, which is then validated by the web service using the JWT Token Handler.</span></span> <span data-ttu-id="4661d-118">Depois que o Manipulador de Tokens JWT valida o token, o recurso desejado é retornado para o cliente pelo serviço Web.</span><span class="sxs-lookup"><span data-stu-id="4661d-118">After the JWT Token Handler has validated the token, the desired resource is returned to the client by the web service.</span></span>  
  
## <a name="features"></a><span data-ttu-id="4661d-119">Recursos</span><span class="sxs-lookup"><span data-stu-id="4661d-119">Features</span></span>  
 <span data-ttu-id="4661d-120">O Manipulador de Tokens JWT oferece os seguintes recursos:</span><span class="sxs-lookup"><span data-stu-id="4661d-120">The JWT Token Handler offers the following features:</span></span>  
  
-   <span data-ttu-id="4661d-121">**Validar um Token JWT**: os tokens JWT podem ser facilmente validados pela lógica de validação do manipulador de tokens, como uma parte do pipeline WIF do aplicativo ou chamados independentemente do WIF</span><span class="sxs-lookup"><span data-stu-id="4661d-121">**Validate a JWT Token**: JWT tokens can be easily validated by the token handler’s validation logic, either as a part of the application’s WIF pipeline or called independently of WIF</span></span>  
  
-   <span data-ttu-id="4661d-122">**Criar um Token JWT**: o Manipulador de Tokens JWT pode ser usado para criar tokens JWT para autorização em serviços de downstream</span><span class="sxs-lookup"><span data-stu-id="4661d-122">**Create a JWT Token**: The JWT Token Handler can be used to create JWT tokens for authorization in downstream services</span></span>
