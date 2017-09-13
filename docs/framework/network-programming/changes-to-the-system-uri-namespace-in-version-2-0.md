---
title: "Alterações no namespace System.Uri na versão 2.0"
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
ms.assetid: 35883fe9-2d09-4d8b-80ca-cf23a941e459
caps.latest.revision: 9
author: mcleblanc
ms.author: markl
manager: markl
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 7ce81e348b3e5de285a3517d70b8bc477198d3e4
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="changes-to-the-systemuri-namespace-in-version-20"></a><span data-ttu-id="e1df7-102">Alterações no namespace System.Uri na versão 2.0</span><span class="sxs-lookup"><span data-stu-id="e1df7-102">Changes to the System.Uri namespace in Version 2.0</span></span>
<span data-ttu-id="e1df7-103">Várias alterações foram feitas na classe <xref:System.Uri?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="e1df7-103">Several changes were made to the <xref:System.Uri?displayProperty=fullName> class.</span></span> <span data-ttu-id="e1df7-104">Essas alterações corrigiram comportamentos incorretos, além de melhorarem a usabilidade e a segurança.</span><span class="sxs-lookup"><span data-stu-id="e1df7-104">These changes fixed incorrect behavior, enhanced usability, and enhanced security.</span></span>  
  
## <a name="obsolete-and-deprecated-members"></a><span data-ttu-id="e1df7-105">Membros obsoletos e preteridos</span><span class="sxs-lookup"><span data-stu-id="e1df7-105">Obsolete and Deprecated Members</span></span>  
 <span data-ttu-id="e1df7-106">Construtores:</span><span class="sxs-lookup"><span data-stu-id="e1df7-106">Constructors:</span></span>  
  
-   <span data-ttu-id="e1df7-107">Todos os construtores que têm um parâmetro `dontEscape`.</span><span class="sxs-lookup"><span data-stu-id="e1df7-107">All constructors that have a `dontEscape` parameter.</span></span>  
  
 <span data-ttu-id="e1df7-108">Métodos:</span><span class="sxs-lookup"><span data-stu-id="e1df7-108">Methods:</span></span>  
  
-   <xref:System.Uri.CheckSecurity%2A>  
  
-   <xref:System.Uri.Escape%2A>  
  
-   <xref:System.Uri.Canonicalize%2A>  
  
-   <xref:System.Uri.Parse%2A>  
  
-   <xref:System.Uri.IsReservedCharacter%2A>  
  
-   <xref:System.Uri.IsBadFileSystemCharacter%2A>  
  
-   <xref:System.Uri.IsExcludedCharacter%2A>  
  
-   <xref:System.Uri.EscapeString%2A>  
  
## <a name="changes"></a><span data-ttu-id="e1df7-109">Alterações</span><span class="sxs-lookup"><span data-stu-id="e1df7-109">Changes</span></span>  
  
-   <span data-ttu-id="e1df7-110">Para esquemas de URI (Uniform Resource Identifier) conhecidos por não terem uma parte da consulta (arquivo, ftp e outros), o caractere “?” é sempre ignorado e não é considerado o início de uma parte <xref:System.Uri.Query%2A>.</span><span class="sxs-lookup"><span data-stu-id="e1df7-110">For URI schemes that are known to not have a query part (file, ftp, and others), the '?' character is always escaped and is not considered the beginning of a <xref:System.Uri.Query%2A> part.</span></span>  
  
-   <span data-ttu-id="e1df7-111">Para URIs de arquivo implícitos (no formato “c:\directory\file@name.txt”), o caractere de fragmento (“#”) é sempre seguido por caracteres de escape, a menos que seja solicitado que ele seja desfeito totalmente o escape ou se <xref:System.Uri.LocalPath%2A> for `true`.</span><span class="sxs-lookup"><span data-stu-id="e1df7-111">For implicit file URIs (of the form "c:\directory\file@name.txt"), the fragment character ('#') is always escaped unless full unescaping is requested or <xref:System.Uri.LocalPath%2A> is `true`.</span></span>  
  
-   <span data-ttu-id="e1df7-112">O suporte ao nome do host UNC foi removido; a especificação de IDN para representar nomes de host internacionais foi adotada.</span><span class="sxs-lookup"><span data-stu-id="e1df7-112">UNC hostname support was removed; the IDN specification for representing international hostnames was adopted.</span></span>  
  
-   <span data-ttu-id="e1df7-113"><xref:System.Uri.LocalPath%2A> sempre retorna uma cadeia de caracteres totalmente sem escape.</span><span class="sxs-lookup"><span data-stu-id="e1df7-113"><xref:System.Uri.LocalPath%2A> always returns a completely unescaped string.</span></span>  
  
-   <span data-ttu-id="e1df7-114"><xref:System.Uri.ToString%2A> não desfaz o escape de um caractere “%”, “?” ou “#” seguido por um caractere de escape.</span><span class="sxs-lookup"><span data-stu-id="e1df7-114"><xref:System.Uri.ToString%2A> does not unescape an escaped '%', '?', or '#' character.</span></span>  
  
-   <span data-ttu-id="e1df7-115"><xref:System.Uri.Equals%2A> agora inclui a parte <xref:System.Uri.Query%2A> na verificação de igualdade.</span><span class="sxs-lookup"><span data-stu-id="e1df7-115"><xref:System.Uri.Equals%2A> now includes the <xref:System.Uri.Query%2A> part in the equality check.</span></span>  
  
-   <span data-ttu-id="e1df7-116">Os operadores “==” e “!=” foram substituídos e vinculados ao método <xref:System.Uri.Equals%2A>.</span><span class="sxs-lookup"><span data-stu-id="e1df7-116">Operators "==" and "!=" are overridden and linked to the <xref:System.Uri.Equals%2A> method.</span></span>  
  
-   <span data-ttu-id="e1df7-117"><xref:System.Uri.IsLoopback%2A> agora produz resultados consistentes.</span><span class="sxs-lookup"><span data-stu-id="e1df7-117"><xref:System.Uri.IsLoopback%2A> now produces consistent results.</span></span>  
  
-   <span data-ttu-id="e1df7-118">O URI “`file:///path`” não é mais convertido em “file://path”.</span><span class="sxs-lookup"><span data-stu-id="e1df7-118">The URI "`file:///path`" is no longer translated into "file://path".</span></span>  
  
-   <span data-ttu-id="e1df7-119">“#” agora é reconhecido como um terminador de nome do host.</span><span class="sxs-lookup"><span data-stu-id="e1df7-119">"#" is now recognized as a host name terminator.</span></span> <span data-ttu-id="e1df7-120">Ou seja, “http://consoto.com#fragment” agora é convertido em “http://contoso.com/#fragment”.</span><span class="sxs-lookup"><span data-stu-id="e1df7-120">That is, "http://consoto.com#fragment" is now converted to "http://contoso.com/#fragment".</span></span>  
  
-   <span data-ttu-id="e1df7-121">Foi corrigido um bug que ocorria durante a combinação de um URI de base com um fragmento.</span><span class="sxs-lookup"><span data-stu-id="e1df7-121">A bug when combining a base URI with a fragment has been fixed.</span></span>  
  
-   <span data-ttu-id="e1df7-122">Foi corrigido um bug no <xref:System.Uri.HostNameType%2A>.</span><span class="sxs-lookup"><span data-stu-id="e1df7-122">A bug in <xref:System.Uri.HostNameType%2A> is fixed.</span></span>  
  
-   <span data-ttu-id="e1df7-123">Foi corrigido um bug na análise NNTP.</span><span class="sxs-lookup"><span data-stu-id="e1df7-123">A bug in NNTP parsing is fixed.</span></span>  
  
-   <span data-ttu-id="e1df7-124">Um URI no formato HTTP:contoso.com agora gera uma exceção de análise.</span><span class="sxs-lookup"><span data-stu-id="e1df7-124">A URI of the form HTTP:contoso.com now throws a parsing exception.</span></span>  
  
-   <span data-ttu-id="e1df7-125">O Framework manipula corretamente userinfo em um URI.</span><span class="sxs-lookup"><span data-stu-id="e1df7-125">The Framework correctly handles userinfo in a URI.</span></span>  
  
-   <span data-ttu-id="e1df7-126">A compactação de caminho do URI foi corrigida, de modo que um URI desfeito não possa percorrer o sistema de arquivos acima da raiz.</span><span class="sxs-lookup"><span data-stu-id="e1df7-126">URI path compression is fixed so that a broken URI cannot traverse the file system above the root.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1df7-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e1df7-127">See Also</span></span>  
 <xref:System.Uri?displayProperty=fullName>
