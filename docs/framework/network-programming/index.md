---
title: "Programação de rede no .NET Framework"
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
helpviewer_keywords:
- Networking
- Internet
- Internet, .NET Framework Internet services
- Network Resources
ms.assetid: 8d455610-67a0-4fa8-a62f-7747064a9256
caps.latest.revision: 24
author: mcleblanc
ms.author: markl
manager: markl
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 4b63aeadb795e5457266bd75d1f2bf0e695eac7f
ms.contentlocale: pt-br
ms.lasthandoff: 09/08/2017

---
# <a name="network-programming-in-the-net-framework"></a><span data-ttu-id="d0e65-102">Programação de rede no .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d0e65-102">Network Programming in the .NET Framework</span></span>
<span data-ttu-id="d0e65-103">O Microsoft .NET Framework fornece uma implementação dos serviços de Internet em camadas, extensível e gerenciada que pode ser rápida e facilmente integrada aos aplicativos.</span><span class="sxs-lookup"><span data-stu-id="d0e65-103">The Microsoft .NET Framework provides a layered, extensible, and managed implementation of Internet services that can be quickly and easily integrated into your applications.</span></span> <span data-ttu-id="d0e65-104">Os aplicativos de rede podem compilar em protocolos conectáveis para usufruir automaticamente de novos protocolos da Internet ou podem usar uma implementação gerenciada da interface de soquete do Windows para trabalhar com a rede a nível de soquete.</span><span class="sxs-lookup"><span data-stu-id="d0e65-104">Your network applications can build on pluggable protocols to automatically take advantage of new Internet protocols, or they can use a managed implementation of the Windows socket interface to work with the network on the socket level.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d0e65-105">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="d0e65-105">In This Section</span></span>  
 [<span data-ttu-id="d0e65-106">Apresentando protocolos conectáveis</span><span class="sxs-lookup"><span data-stu-id="d0e65-106">Introducing Pluggable Protocols</span></span>](../../../docs/framework/network-programming/introducing-pluggable-protocols.md)  
 <span data-ttu-id="d0e65-107">Descreve como acessar um recurso da Internet sem considerar o protocolo de acesso necessário.</span><span class="sxs-lookup"><span data-stu-id="d0e65-107">Describes how to access an Internet resource without regard to the access protocol that it requires.</span></span>  
  
 [<span data-ttu-id="d0e65-108">Solicitando dados</span><span class="sxs-lookup"><span data-stu-id="d0e65-108">Requesting Data</span></span>](../../../docs/framework/network-programming/requesting-data.md)  
 <span data-ttu-id="d0e65-109">Explica como usar protocolos conectáveis para carregar e baixar dados dos recursos da Internet.</span><span class="sxs-lookup"><span data-stu-id="d0e65-109">Explains how to use pluggable protocols to upload and download data from Internet resources.</span></span>  
  
 [<span data-ttu-id="d0e65-110">Programando protocolos conectáveis</span><span class="sxs-lookup"><span data-stu-id="d0e65-110">Programming Pluggable Protocols</span></span>](../../../docs/framework/network-programming/programming-pluggable-protocols.md)  
 <span data-ttu-id="d0e65-111">Explica como derivar classes específicas de protocolo para implementar protocolos conectáveis.</span><span class="sxs-lookup"><span data-stu-id="d0e65-111">Explains how to derive protocol-specific classes to implement pluggable protocols.</span></span>  
  
 [<span data-ttu-id="d0e65-112">Usando protocolos de aplicativo</span><span class="sxs-lookup"><span data-stu-id="d0e65-112">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)  
 <span data-ttu-id="d0e65-113">Descreve aplicativos de programação que se beneficiam de protocolos de rede como o TCP, UDP e HTTP.</span><span class="sxs-lookup"><span data-stu-id="d0e65-113">Describes programming applications that take advantage of network protocols such as TCP, UDP, and HTTP.</span></span>  
  
 [<span data-ttu-id="d0e65-114">Protocolo IP versão 6</span><span class="sxs-lookup"><span data-stu-id="d0e65-114">Internet Protocol Version 6</span></span>](../../../docs/framework/network-programming/internet-protocol-version-6.md)  
 <span data-ttu-id="d0e65-115">Descreve as vantagens do Protocolo de Internet versão 6 (IPv6) sob a versão atual do pacote do Protocolo de Internet (IPv4), descreve o endereçamento do IPv6, o roteamento e a configuração automática e também como habilitar e desabilitar o IPv6.</span><span class="sxs-lookup"><span data-stu-id="d0e65-115">Describes the advantages of Internet Protocol version 6 (IPv6) over the current version of the Internet Protocol suite (IPv4), describes IPv6 addressing, routing and auto-configuration, and how to enable and disable IPv6.</span></span>  
  
 [<span data-ttu-id="d0e65-116">Configurando aplicativos da Internet</span><span class="sxs-lookup"><span data-stu-id="d0e65-116">Configuring Internet Applications</span></span>](../../../docs/framework/network-programming/configuring-internet-applications.md)  
 <span data-ttu-id="d0e65-117">Explica como usar os arquivos de configuração do .NET Framework para configurar aplicativos da Internet.</span><span class="sxs-lookup"><span data-stu-id="d0e65-117">Explains how to use the .NET Framework configuration files to configure Internet applications.</span></span>  
  
 [<span data-ttu-id="d0e65-118">Rastreamento de rede no .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d0e65-118">Network Tracing in the .NET Framework</span></span>](../../../docs/framework/network-programming/network-tracing.md)  
 <span data-ttu-id="d0e65-119">Explica como usar o rastreamento de rede para obter informações sobre invocações de método e tráfego de rede geradas por um aplicativo gerenciado.</span><span class="sxs-lookup"><span data-stu-id="d0e65-119">Explains how to use network tracing to get information about method invocations and network traffic generated by a managed application.</span></span>  
  
 [<span data-ttu-id="d0e65-120">Gerenciamento de cache para aplicativos de rede</span><span class="sxs-lookup"><span data-stu-id="d0e65-120">Cache Management for Network Applications</span></span>](../../../docs/framework/network-programming/cache-management-for-network-applications.md)  
 <span data-ttu-id="d0e65-121">Descreve como usar o cachê para aplicativos que usam as classes <xref:System.Net.WebClient?displayProperty=fullName>, <xref:System.Net.WebRequest?displayProperty=fullName> e <xref:System.Net.HttpWebRequest?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="d0e65-121">Describes how to use caching for applications that use the <xref:System.Net.WebClient?displayProperty=fullName>, <xref:System.Net.WebRequest?displayProperty=fullName>, and <xref:System.Net.HttpWebRequest?displayProperty=fullName> classes.</span></span>  
  
 [<span data-ttu-id="d0e65-122">Segurança na programação de rede</span><span class="sxs-lookup"><span data-stu-id="d0e65-122">Security in Network Programming</span></span>](../../../docs/framework/network-programming/security-in-network-programming.md)  
 <span data-ttu-id="d0e65-123">Descreve como usar técnicas padrão de segurança e autenticação da Internet.</span><span class="sxs-lookup"><span data-stu-id="d0e65-123">Describes how to use standard Internet security and authentication techniques.</span></span>  
  
 [<span data-ttu-id="d0e65-124">Melhores práticas para classes System.Net</span><span class="sxs-lookup"><span data-stu-id="d0e65-124">Best Practices for System.Net Classes</span></span>](../../../docs/framework/network-programming/best-practices-for-system-net-classes.md)  
 <span data-ttu-id="d0e65-125">Fornece dicas e truques para obter o máximo dos aplicativos da Internet.</span><span class="sxs-lookup"><span data-stu-id="d0e65-125">Provides tips and tricks for getting the most out of your Internet applications.</span></span>  
  
 [<span data-ttu-id="d0e65-126">Acessando a Internet por meio de um proxy</span><span class="sxs-lookup"><span data-stu-id="d0e65-126">Accessing the Internet Through a Proxy</span></span>](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)  
 <span data-ttu-id="d0e65-127">Descreve como configurar proxies.</span><span class="sxs-lookup"><span data-stu-id="d0e65-127">Describes how to configure proxies.</span></span>  
  
 [<span data-ttu-id="d0e65-128">NetworkInformation</span><span class="sxs-lookup"><span data-stu-id="d0e65-128">NetworkInformation</span></span>](../../../docs/framework/network-programming/networkinformation.md)  
 <span data-ttu-id="d0e65-129">Descreve como coletar informações sobre eventos, alterações, estatísticas e propriedades de rede e também explica como determinar se um host remoto é acessível usando a classe <xref:System.Net.NetworkInformation.Ping?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="d0e65-129">Describes how to gather information about network events, changes, statistics, and properties and also explains how to determine whether a remote host is reachable by using the <xref:System.Net.NetworkInformation.Ping?displayProperty=fullName> class.</span></span>  
  
 [<span data-ttu-id="d0e65-130">Alterações no namespace System.Uri na versão 2.0</span><span class="sxs-lookup"><span data-stu-id="d0e65-130">Changes to the System.Uri namespace in Version 2.0</span></span>](../../../docs/framework/network-programming/changes-to-the-system-uri-namespace-in-version-2-0.md)  
 <span data-ttu-id="d0e65-131">Descreve várias alterações feitas na classe <xref:System.Uri?displayProperty=fullName> na versão 2.0 para comportamento fixo incorreto; aprimora a usabilidade e a segurança.</span><span class="sxs-lookup"><span data-stu-id="d0e65-131">Describes several changes made to the <xref:System.Uri?displayProperty=fullName> class in Version 2.0 to fixed incorrect behavior, enhance usability, and enhance security.</span></span>  
  
 [<span data-ttu-id="d0e65-132">Suporte ao International Resource Identifier em System.Uri</span><span class="sxs-lookup"><span data-stu-id="d0e65-132">International Resource Identifier Support in System.Uri</span></span>](../../../docs/framework/network-programming/international-resource-identifier-support-in-system-uri.md)  
 <span data-ttu-id="d0e65-133">Descreve aprimoramentos na classe <xref:System.Uri?displayProperty=fullName> na versão 3.5, 3.0 SP1 e 2.0 SP1 para o Identificador Internacional de Recursos (IRI) e o suporte de Nome de Domínio Internacionalizado (IDN).</span><span class="sxs-lookup"><span data-stu-id="d0e65-133">Describes enhancements to the <xref:System.Uri?displayProperty=fullName> class in Version 3.5, 3.0 SP1, and 2.0 SP1 for International Resource Identifier (IRI) and Internationalized Domain Name (IDN) support.</span></span>  
  
 [<span data-ttu-id="d0e65-134">Melhorias do desempenho de soquete na versão 3.5</span><span class="sxs-lookup"><span data-stu-id="d0e65-134">Socket Performance Enhancements in Version 3.5</span></span>](../../../docs/framework/network-programming/socket-performance-enhancements-in-version-3-5.md)  
 <span data-ttu-id="d0e65-135">Descreve um conjunto de aprimoramentos na classe <xref:System.Net.Sockets.Socket?displayProperty=fullName> na versão 3.5, 3.0 SP1 e 2.0 SP1, que fornece um padrão assíncrono alternativo, o qual pode ser usado por aplicativos de alto desempenho especializados em soquete.</span><span class="sxs-lookup"><span data-stu-id="d0e65-135">Describes a set of enhancements to the <xref:System.Net.Sockets.Socket?displayProperty=fullName> class in Version 3.5, 3.0 SP1, and 2.0 SP1 that provide an alternative asynchronous pattern that can be used by specialized high-performance socket applications.</span></span>  
  
 [<span data-ttu-id="d0e65-136">Protocolo PNRP</span><span class="sxs-lookup"><span data-stu-id="d0e65-136">Peer Name Resolution Protocol</span></span>](../../../docs/framework/network-programming/peer-name-resolution-protocol.md)  
 <span data-ttu-id="d0e65-137">Descreve o suporte adicionado à versão 3.5 para oferecer suporte ao Protocolo de Resolução de Nomes de Ponto (PNRP), um protocolo de resolução de nome e um registro de nome dinâmico sem servidor.</span><span class="sxs-lookup"><span data-stu-id="d0e65-137">Describes support added in Version 3.5 to support the Peer Name Resolution Protocol (PNRP), a serverless and dynamic name registration and name resolution protocol.</span></span> <span data-ttu-id="d0e65-138">Esses novos recursos têm suporte pelo namespace <xref:System.Net.PeerToPeer?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="d0e65-138">These new features are supported by the <xref:System.Net.PeerToPeer?displayProperty=fullName> namespace.</span></span>  
  
 [<span data-ttu-id="d0e65-139">Colaboração ponto a ponto</span><span class="sxs-lookup"><span data-stu-id="d0e65-139">Peer-to-Peer Collaboration</span></span>](../../../docs/framework/network-programming/peer-to-peer-collaboration.md)  
 <span data-ttu-id="d0e65-140">Descreve o suporte adicionado à versão 3.5 para dar suporte à Colaboração Ponto a Ponto que compila no PNRP.</span><span class="sxs-lookup"><span data-stu-id="d0e65-140">Describes support added in Version 3.5 to support the Peer-to-Peer Collaboration that builds on PNRP.</span></span> <span data-ttu-id="d0e65-141">Esses novos recursos têm suporte pelo namespace <xref:System.Net.PeerToPeer.Collaboration?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="d0e65-141">These new features are supported by the <xref:System.Net.PeerToPeer.Collaboration?displayProperty=fullName> namespace.</span></span>  
  
 [<span data-ttu-id="d0e65-142">Alterações na autenticação NTLM para HttpWebRequest na versão 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="d0e65-142">Changes to NTLM authentication for HttpWebRequest in Version 3.5 SP1</span></span>](../../../docs/framework/network-programming/changes-to-ntlm-authentication-for-httpwebrequest-in-version-3-5-sp1.md)  
 <span data-ttu-id="d0e65-143">Descreve as alterações de segurança feitas na versão 3.5 SP1 que afetam a maneira como a autenticação integrada do Windows é controlada por <xref:System.Net.HttpWebRequest?displayProperty=fullName>, <xref:System.Net.HttpListener?displayProperty=fullName>, <xref:System.Net.Security.NegotiateStream?displayProperty=fullName> e por classes relacionadas no namespace do System.Net.</span><span class="sxs-lookup"><span data-stu-id="d0e65-143">Describes security changes made in Version 3.5 SP1 that affect how integrated Windows authentication is handled by the <xref:System.Net.HttpWebRequest?displayProperty=fullName>, <xref:System.Net.HttpListener?displayProperty=fullName>, <xref:System.Net.Security.NegotiateStream?displayProperty=fullName>, and related classes in the System.Net namespace.</span></span>  
  
 [<span data-ttu-id="d0e65-144">Autenticação Integrada do Windows com proteção estendida</span><span class="sxs-lookup"><span data-stu-id="d0e65-144">Integrated Windows Authentication with Extended Protection</span></span>](../../../docs/framework/network-programming/integrated-windows-authentication-with-extended-protection.md)  
 <span data-ttu-id="d0e65-145">Descreve aprimoramentos para a proteção estendida que afetam a maneira como a autenticação integrada do Windows é controlada por <xref:System.Net.HttpWebRequest?displayProperty=fullName>, <xref:System.Net.HttpListener?displayProperty=fullName>, <xref:System.Net.Mail.SmtpClient?displayProperty=fullName>, <xref:System.Net.Security.SslStream?displayProperty=fullName>, <xref:System.Net.Security.NegotiateStream?displayProperty=fullName> e por classes relacionadas no <xref:System.Net?displayProperty=fullName> e por namespaces relacionados.</span><span class="sxs-lookup"><span data-stu-id="d0e65-145">Describes enhancements for extended protection that affect how integrated Windows authentication is handled by the <xref:System.Net.HttpWebRequest?displayProperty=fullName>, <xref:System.Net.HttpListener?displayProperty=fullName>, <xref:System.Net.Mail.SmtpClient?displayProperty=fullName>, <xref:System.Net.Security.SslStream?displayProperty=fullName>, <xref:System.Net.Security.NegotiateStream?displayProperty=fullName>, and related classes in the <xref:System.Net?displayProperty=fullName> and related namespaces.</span></span>  
  
 [<span data-ttu-id="d0e65-146">Passagem de NAT usando IPv6 e Teredo</span><span class="sxs-lookup"><span data-stu-id="d0e65-146">NAT Traversal using IPv6 and Teredo</span></span>](../../../docs/framework/network-programming/nat-traversal-using-ipv6-and-teredo.md)  
 <span data-ttu-id="d0e65-147">Descreve os aprimoramentos adicionados ao <xref:System.Net?displayProperty=fullName>, <xref:System.Net.NetworkInformation?displayProperty=fullName> e namespaces <xref:System.Net.Sockets?displayProperty=fullName> para oferecer suporte à NAT transversal usando o IPv6 e o Teredo.</span><span class="sxs-lookup"><span data-stu-id="d0e65-147">Describes enhancements added to the <xref:System.Net?displayProperty=fullName>, <xref:System.Net.NetworkInformation?displayProperty=fullName>, and <xref:System.Net.Sockets?displayProperty=fullName> namespaces to support NAT traversal using IPv6 and Teredo.</span></span>  
  
 [<span data-ttu-id="d0e65-148">Isolamento de rede para Aplicativos da Windows Store</span><span class="sxs-lookup"><span data-stu-id="d0e65-148">Network Isolation for Windows Store Apps</span></span>](../../../docs/framework/network-programming/network-isolation-for-windows-store-apps.md)  
 <span data-ttu-id="d0e65-149">Descreve o impacto do isolamento de rede quando as classes nos namespaces <xref:System.Net>, <xref:System.Net.Http> e <xref:System.Net.Http.Headers> são usadas em aplicativos [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d0e65-149">Describes the impact of network isolation when classes in the <xref:System.Net>, <xref:System.Net.Http>, and <xref:System.Net.Http.Headers> namespaces are used in [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps.</span></span>  
  
 [<span data-ttu-id="d0e65-150">Amostras de programação de rede</span><span class="sxs-lookup"><span data-stu-id="d0e65-150">Network Programming Samples</span></span>](../../../docs/framework/network-programming/network-programming-samples.md)  
 <span data-ttu-id="d0e65-151">Vincula-se a amostras para download de programação de rede que usam classes nos namespaces <xref:System.Net>, <xref:System.Net.Cache>, <xref:System.Net.Configuration>, <xref:System.Net.Mail>, <xref:System.Net.Mime>, <xref:System.Net.NetworkInformation>, <xref:System.Net.PeerToPeer>, <xref:System.Net.Security>, <xref:System.Net.Sockets>.</span><span class="sxs-lookup"><span data-stu-id="d0e65-151">Links to downloadable network programming samples that use classes in the <xref:System.Net>, <xref:System.Net.Cache>, <xref:System.Net.Configuration>, <xref:System.Net.Mail>, <xref:System.Net.Mime>, <xref:System.Net.NetworkInformation>, <xref:System.Net.PeerToPeer>, <xref:System.Net.Security>, <xref:System.Net.Sockets> namespaces.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="d0e65-152">Referência</span><span class="sxs-lookup"><span data-stu-id="d0e65-152">Reference</span></span>  
 <xref:System.Net?displayProperty=fullName>  
 <span data-ttu-id="d0e65-153">Fornece uma interface de programação simples para muitos dos protocolos usados nas redes de hoje.</span><span class="sxs-lookup"><span data-stu-id="d0e65-153">Provides a simple programming interface for many of the protocols used on networks today.</span></span> <span data-ttu-id="d0e65-154">As classes <xref:System.Net.WebRequest?displayProperty=fullName> e <xref:System.Net.WebResponse?displayProperty=fullName> nesse namespace são a base para protocolos conectáveis.</span><span class="sxs-lookup"><span data-stu-id="d0e65-154">The <xref:System.Net.WebRequest?displayProperty=fullName> and <xref:System.Net.WebResponse?displayProperty=fullName> classes in this namespace are the basis for pluggable protocols.</span></span>  
  
 <xref:System.Net.Cache?displayProperty=fullName>  
 <span data-ttu-id="d0e65-155">Define tipos e enumerações usados para definir políticas de cache para os recursos obtidos usando as classes <xref:System.Net.WebRequest?displayProperty=fullName> e <xref:System.Net.HttpWebRequest?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="d0e65-155">Defines the types and enumerations used to define cache policies for resources obtained using the <xref:System.Net.WebRequest?displayProperty=fullName> and <xref:System.Net.HttpWebRequest?displayProperty=fullName> classes.</span></span>  
  
 <xref:System.Net.Configuration?displayProperty=fullName>  
 <span data-ttu-id="d0e65-156">Classes que os aplicativos usam para acessar e atualizar programaticamente definições de configuração dos namespaces do System.Net.</span><span class="sxs-lookup"><span data-stu-id="d0e65-156">Classes that applications use to programmatically access and update configuration settings for the System.Net namespaces.</span></span>  
  
 <xref:System.Net.Http?displayProperty=fullName>  
 <span data-ttu-id="d0e65-157">Classes que fornecem uma interface de programação para aplicativos HTTP modernos.</span><span class="sxs-lookup"><span data-stu-id="d0e65-157">Classes that provides a programming interface for modern HTTP applications.</span></span>  
  
 <xref:System.Net.Http.Headers?displayProperty=fullName>  
 <span data-ttu-id="d0e65-158">Fornece suporte para coleções de cabeçalhos HTTP usados pelo namespace <xref:System.Net.Http?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="d0e65-158">Provides support for collections of HTTP headers used by the <xref:System.Net.Http?displayProperty=fullName> namespace</span></span>  
  
 <xref:System.Net.Mail?displayProperty=fullName>  
 <span data-ttu-id="d0e65-159">Classes para compor e enviar email usando o protocolo SMTP.</span><span class="sxs-lookup"><span data-stu-id="d0e65-159">Classes to compose and send mail using the SMTP protocol.</span></span>  
  
 <xref:System.Net.Mime?displayProperty=fullName>  
 <span data-ttu-id="d0e65-160">Define os tipos usados para representar os cabeçalhos MIME (Multipurpose Internet Mail Exchange) usado por classes no namespace <xref:System.Net.Mail?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="d0e65-160">Defines types that are used to represent Multipurpose Internet Mail Exchange (MIME) headers used by classes in the <xref:System.Net.Mail?displayProperty=fullName> namespace.</span></span>  
  
 <xref:System.Net.NetworkInformation?displayProperty=fullName>  
 <span data-ttu-id="d0e65-161">Classes para coletar programaticamente informações sobre eventos, alterações, estatísticas e propriedades de rede.</span><span class="sxs-lookup"><span data-stu-id="d0e65-161">Classes to programmatically gather information about network events, changes, statistics, and properties.</span></span>  
  
 <xref:System.Net.PeerToPeer?displayProperty=fullName>  
 <span data-ttu-id="d0e65-162">Fornece uma implementação gerenciada do Protocolo de Resolução de Nomes de Ponto (PNRP) para desenvolvedores.</span><span class="sxs-lookup"><span data-stu-id="d0e65-162">Provides a managed implementation of the Peer Name Resolution Protocol (PNRP) for developers.</span></span>  
  
 <xref:System.Net.PeerToPeer.Collaboration?displayProperty=fullName>  
 <span data-ttu-id="d0e65-163">Fornece uma implementação gerenciada da interface de Colaboração Ponto a Ponto para desenvolvedores.</span><span class="sxs-lookup"><span data-stu-id="d0e65-163">Provides a managed implementation of the Peer-to-Peer Collaboration interface for developers.</span></span>  
  
 <xref:System.Net.Security?displayProperty=fullName>  
 <span data-ttu-id="d0e65-164">Classes para fornecer fluxos de rede para proteger comunicações entre hosts.</span><span class="sxs-lookup"><span data-stu-id="d0e65-164">Classes to provide network streams for secure communications between hosts.</span></span>  
  
 <xref:System.Net.Sockets?displayProperty=fullName>  
 <span data-ttu-id="d0e65-165">Fornece uma implementação gerenciada da interface dos Soquetes do Windows (Winsock) para desenvolvedores que precisam ajudar a controlar o acesso à rede.</span><span class="sxs-lookup"><span data-stu-id="d0e65-165">Provides a managed implementation of the Windows Sockets (Winsock) interface for developers who need to help control access to the network.</span></span>  
  
 <xref:System.Net.WebSockets?displayProperty=fullName>  
 <span data-ttu-id="d0e65-166">Fornece uma implementação gerenciada da interface de WebSocket para desenvolvedores.</span><span class="sxs-lookup"><span data-stu-id="d0e65-166">Provides a managed implementation of the WebSocket interface for developers.</span></span>  
  
 <xref:System.Uri?displayProperty=fullName>  
 <span data-ttu-id="d0e65-167">Fornece uma representação de objeto de um URI (Uniform Resource Identifier) e fácil acesso às partes do URI.</span><span class="sxs-lookup"><span data-stu-id="d0e65-167">Provides an object representation of a uniform resource identifier (URI) and easy access to the parts of the URI.</span></span>  
  
 <xref:System.Security.Authentication.ExtendedProtection?displayProperty=fullName>  
 <span data-ttu-id="d0e65-168">Fornece suporte à autenticação usando proteção estendida para aplicativos.</span><span class="sxs-lookup"><span data-stu-id="d0e65-168">Provides support for authentication using extended protection for applications.</span></span>  
  
 <xref:System.Security.Authentication.ExtendedProtection.Configuration?displayProperty=fullName>  
 <span data-ttu-id="d0e65-169">Fornece suporte à configuração da autenticação usando proteção estendida para aplicativos.</span><span class="sxs-lookup"><span data-stu-id="d0e65-169">Provides support for configuration of authentication using extended protection for applications.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0e65-170">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d0e65-170">See Also</span></span>  
 <span data-ttu-id="d0e65-171">[Tópicos explicativos de programação de rede](../../../docs/framework/network-programming/network-programming-how-to-topics.md) </span><span class="sxs-lookup"><span data-stu-id="d0e65-171">[Network Programming How-to Topics](../../../docs/framework/network-programming/network-programming-how-to-topics.md) </span></span>  
 <span data-ttu-id="d0e65-172">[Amostras de programação de rede](../../../docs/framework/network-programming/network-programming-samples.md) </span><span class="sxs-lookup"><span data-stu-id="d0e65-172">[Network Programming Samples](../../../docs/framework/network-programming/network-programming-samples.md) </span></span>  
 <span data-ttu-id="d0e65-173">[Exemplos de rede do .NET na Galeria de Códigos do MSDN](http://code.msdn.microsoft.com/Wiki/View.aspx?ProjectName=nclsamples) </span><span class="sxs-lookup"><span data-stu-id="d0e65-173">[Networking Samples for .NET on MSDN Code Gallery](http://code.msdn.microsoft.com/Wiki/View.aspx?ProjectName=nclsamples) </span></span>  
 [<span data-ttu-id="d0e65-174">Amostra de HttpClient</span><span class="sxs-lookup"><span data-stu-id="d0e65-174">HttpClient Sample</span></span>](http://go.microsoft.com/fwlink/?LinkId=242550)
