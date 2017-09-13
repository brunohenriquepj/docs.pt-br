---
title: "Colaboração ponto a ponto"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: b6216d88-bccb-4a59-9f1c-9f751708e811
caps.latest.revision: 7
author: mcleblanc
ms.author: markl
manager: markl
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: b17fc74b2143f7307316a167330d06c87b9d4c3d
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="peer-to-peer-collaboration"></a><span data-ttu-id="b6aee-102">Colaboração ponto a ponto</span><span class="sxs-lookup"><span data-stu-id="b6aee-102">Peer-to-Peer Collaboration</span></span>
<span data-ttu-id="b6aee-103">A rede ponto a ponto é a utilização dos computadores relativamente poderosos (computadores pessoais) que existem na borda da Internet para mais do que apenas tarefas de computação baseadas no cliente.</span><span class="sxs-lookup"><span data-stu-id="b6aee-103">Peer-to-peer networking is the utilization of the relatively powerful computers (personal computers) that exist at the edge of the Internet for more than just client-based computing tasks.</span></span> <span data-ttu-id="b6aee-104">O PC (computador pessoal) moderno tem um processador muito rápido, ampla memória e um disco rígido grande, nenhum dos quais está sendo totalmente utilizado ao executar tarefas comuns de computação, como email e navegação na Web.</span><span class="sxs-lookup"><span data-stu-id="b6aee-104">The modern personal computer (PC) has a very fast processor, vast memory, and a large hard disk, none of which are being fully utilized when performing common computing tasks such as e-mail and Web browsing.</span></span> <span data-ttu-id="b6aee-105">O PC moderno pode facilmente atuar como um cliente e um servidor (um par) para vários tipos de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="b6aee-105">The modern PC can easily act as both a client and server (a peer) for many types of applications.</span></span>  
  
-   <span data-ttu-id="b6aee-106">A infraestrutura de colaboração ponto a ponto é uma implementação simplificada da infraestrutura de ponto a ponto do Microsoft Windows que aproveita o serviço Pessoas ao meu Redor no Windows Vista e em plataformas posteriores.</span><span class="sxs-lookup"><span data-stu-id="b6aee-106">The Peer-to-Peer Collaboration Infrastructure is a simplified implementation of the Microsoft Windows Peer-to-Peer Infrastructure that leverages the People Near Me service in Windows Vista and later platforms.</span></span> <span data-ttu-id="b6aee-107">Ele é mais adequado para aplicativos habilitados para par dentro de uma sub-rede para a qual o serviço Pessoas ao meu Redor opera, embora ele também possa atender a pontos de extremidade de Internet ou contatos.</span><span class="sxs-lookup"><span data-stu-id="b6aee-107">It is best used for peer-enabled applications within a subnet for which the People Near Me service operates, although it can service internet endpoints or contacts as well.</span></span> <span data-ttu-id="b6aee-108">Ele incorpora o Gerenciador de Contatos comum que é usado pelo Live Messenger e outros aplicativos que reconhecem o Live para determinar pontos de extremidade de contato, presença e disponibilidade.</span><span class="sxs-lookup"><span data-stu-id="b6aee-108">It incorporates the common Contact Manager that is used by Live Messenger and other Live-aware applications to determine contact endpoints, availability, and presence.</span></span>  
  
-  
  
## <a name="collaboration-applications"></a><span data-ttu-id="b6aee-109">Aplicativos de colaboração</span><span class="sxs-lookup"><span data-stu-id="b6aee-109">Collaboration Applications</span></span>  
 <span data-ttu-id="b6aee-110">Um aplicativo de colaboração ponto a ponto típico é composto das seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="b6aee-110">A typical peer-to-peer collaboration application is comprised of the following steps:</span></span>  
  
-   <span data-ttu-id="b6aee-111">O par determina a identidade de um par que está interessado em hospedar uma sessão de colaboração</span><span class="sxs-lookup"><span data-stu-id="b6aee-111">Peer determines the identity of a peer who is interested in hosting a collaboration session</span></span>  
  
-   <span data-ttu-id="b6aee-112">Uma solicitação para hospedar uma sessão é enviada de alguma forma e o par de host concorda em gerenciar a atividade de colaboração.</span><span class="sxs-lookup"><span data-stu-id="b6aee-112">A request to host a session is sent, somehow, and the host peer agrees to manage collaboration activity.</span></span>  
  
-   <span data-ttu-id="b6aee-113">O host convida contatos na sub-rede (incluindo o solicitante) para uma sessão.</span><span class="sxs-lookup"><span data-stu-id="b6aee-113">The host invites contacts on the subnet (including the requestor) to a session.</span></span>  
  
-   <span data-ttu-id="b6aee-114">Todos os pares que desejam colaborar podem adicionar o host aos respectivos gerenciadores de contatos.</span><span class="sxs-lookup"><span data-stu-id="b6aee-114">All peers who want to collaborate may add the host to their contact managers.</span></span>  
  
-   <span data-ttu-id="b6aee-115">A maioria dos pares enviará respostas ao convite, aceito ou recusado, de volta para o par de host de maneira oportuna.</span><span class="sxs-lookup"><span data-stu-id="b6aee-115">Most peers will send invitation responses, whether accepted or declined, back to the host peer in a timely fashion.</span></span>  
  
-   <span data-ttu-id="b6aee-116">Todos os pares que desejam colaborar assinarão o par de host.</span><span class="sxs-lookup"><span data-stu-id="b6aee-116">All peers who want to collaborate will subscribe to the host peer.</span></span>  
  
-   <span data-ttu-id="b6aee-117">Enquanto os pares estiverem executando a atividade de colaboração inicial, o par de host poderá adicionar pares remotos a seu gerenciador de contatos.</span><span class="sxs-lookup"><span data-stu-id="b6aee-117">While the peers are performing their initial collaboration activity, the host peer may add remote peers to its contact manager.</span></span> <span data-ttu-id="b6aee-118">Ele também processa todas as respostas de convite para determinar quem aceitou, quem recusou e que não foi atendido.</span><span class="sxs-lookup"><span data-stu-id="b6aee-118">It also processes all invitation responses to determine who has accepted, who has declined, and who has not answered.</span></span>  <span data-ttu-id="b6aee-119">Ele pode cancelar convites para aqueles que não responderam ou executar alguma outra atividade.</span><span class="sxs-lookup"><span data-stu-id="b6aee-119">It may cancel invitations to those who have not answered, or perform some other activity.</span></span>  
  
-   <span data-ttu-id="b6aee-120">Neste ponto, o par de host pode iniciar uma sessão de colaboração com todos os pares convidados ou registrar um aplicativo com a infraestrutura de colaboração.</span><span class="sxs-lookup"><span data-stu-id="b6aee-120">At this point, the host peer can start a collaboration session with all invited peers, or register an application with the collaboration infrastructure.</span></span>  <span data-ttu-id="b6aee-121">Aplicativos P2P usam a infraestrutura de colaboração ponto a ponto e o namespace <xref:System.Net.PeerToPeer.Collaboration> para coordenar as comunicações para jogos, BBS, conferência e outros aplicativos de presença sem servidor.</span><span class="sxs-lookup"><span data-stu-id="b6aee-121">P2P applications use the Peer-to-Peer Collaboration Infrastructure and the <xref:System.Net.PeerToPeer.Collaboration> namespace to coordinate communications for games, bulletin boards, conferencing, and other serverless presence applications.</span></span>  
  
-  
  
## <a name="peer-to-peer-networking-security"></a><span data-ttu-id="b6aee-122">Segurança de rede ponto a ponto</span><span class="sxs-lookup"><span data-stu-id="b6aee-122">Peer-to-Peer Networking Security</span></span>  
 <span data-ttu-id="b6aee-123">Em um domínio do Active Directory, os controladores de domínio fornecem serviços de autenticação usando o Kerberos.</span><span class="sxs-lookup"><span data-stu-id="b6aee-123">In an Active Directory domain, domain controllers provide authentication services using Kerberos.</span></span> <span data-ttu-id="b6aee-124">Em um ambiente de par sem servidor, os pares devem fornecer sua própria autenticação.</span><span class="sxs-lookup"><span data-stu-id="b6aee-124">In a serverless peer environment, the peers must provide their own authentication.</span></span> <span data-ttu-id="b6aee-125">Para rede ponto a ponto, qualquer nó pode agir como uma AC, removendo a necessidade de um certificado raiz no repositório de raiz confiável do cada par.</span><span class="sxs-lookup"><span data-stu-id="b6aee-125">For Peer-to-Peer Networking, any node can act as a CA, removing the requirement of a root certificate in each peer's trusted root store.</span></span> <span data-ttu-id="b6aee-126">A autenticação é fornecida usando certificados autoassinados, formatados como certificados X.509.</span><span class="sxs-lookup"><span data-stu-id="b6aee-126">Authentication is provided using self-signed certificates, formatted as X.509 certificates.</span></span> <span data-ttu-id="b6aee-127">Esses são os certificados que são criados por cada par, o que gera o par de chaves pública/privada e o certificado é assinado usando a chave privada.</span><span class="sxs-lookup"><span data-stu-id="b6aee-127">These are certificates that are created by each peer, which generates the public key/private key pair and the certificate that is signed using the private key.</span></span> <span data-ttu-id="b6aee-128">O certificado autoassinado é usado para autenticação e para fornecer informações sobre a entidade de par.</span><span class="sxs-lookup"><span data-stu-id="b6aee-128">The self-signed certificate is used for authentication and to provide information about the peer entity.</span></span> <span data-ttu-id="b6aee-129">Assim como a autenticação X.509, a autenticação de rede ponto a ponto depende de uma cadeia de certificados ser rastreada de volta para uma chave pública confiável.</span><span class="sxs-lookup"><span data-stu-id="b6aee-129">Like X.509 authentication, peer networking authentication relies upon a chain of certificates tracing back to a public key that is trusted.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6aee-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b6aee-130">See Also</span></span>  
 <span data-ttu-id="b6aee-131"><xref:System.Net.PeerToPeer.Collaboration></span><span class="sxs-lookup"><span data-stu-id="b6aee-131"><xref:System.Net.PeerToPeer.Collaboration></span></span>   
 [<span data-ttu-id="b6aee-132">Sobre o namespace System.Net.PeerToPeer.Collaboration</span><span class="sxs-lookup"><span data-stu-id="b6aee-132">About the System.Net.PeerToPeer.Collaboration Namespace</span></span>](../../../docs/framework/network-programming/about-the-system-net-peertopeer-collaboration-namespace.md)
