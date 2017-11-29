---
title: Namespaces (Entity SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 83991c21-60db-4af9-aca3-b416f6cae98e
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0ea5292d20aebdb27da726b0076179fb64631e5c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="namespaces-entity-sql"></a><span data-ttu-id="b5dda-102">Namespaces (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="b5dda-102">Namespaces (Entity SQL)</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="b5dda-103"> apresenta namespaces para evitar conflitos de nome para identificadores globais como nomes de tipo, conjuntos de entidades, funções, e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="b5dda-103"> introduces namespaces to avoid name conflicts for global identifiers such as type names, entity sets, functions, and so on.</span></span> <span data-ttu-id="b5dda-104">O suporte a namespace em [!INCLUDE[esql](../../../../../../includes/esql-md.md)] é semelhante para o suporte a namespace no [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b5dda-104">The namespace support in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] is similar to the namespace support in the [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)].</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="b5dda-105"> fornece dois formulários que a cláusula group UTILIZAÇÃO: namespaces qualificadas (onde um alias mais curtas são fornecidas para o namespace), e namespaces não qualificado, como ilustrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="b5dda-105"> provides two forms of the USING clause: qualified namespaces (where a shorter alias is provided for the namespace), and unqualified namespaces, as illustrated in the following example:</span></span>  
  
 `USING System.Data;`  
  
 `USING tsql = System.Data;`  
  
## <a name="name-resolution-rules"></a><span data-ttu-id="b5dda-106">Regras de resolução de nomes</span><span class="sxs-lookup"><span data-stu-id="b5dda-106">Name Resolution Rules</span></span>  
 <span data-ttu-id="b5dda-107">Se um identificador não pode ser resolvido em escopos locais, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tenta localizar o nome dos escopos globais (os namespaces).</span><span class="sxs-lookup"><span data-stu-id="b5dda-107">If an identifier cannot be resolved in the local scopes, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tries to locate the name in the global scopes (the namespaces).</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="b5dda-108"> tenta corresponder primeiro o identificador (prefixo) com uma namespaces qualificadas.</span><span class="sxs-lookup"><span data-stu-id="b5dda-108"> first tries to match the identifier (prefix) with one of the qualified namespaces.</span></span> <span data-ttu-id="b5dda-109">Se houver uma correspondência, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tenta resolver o resto do identificador no namespace especificado.</span><span class="sxs-lookup"><span data-stu-id="b5dda-109">If there is a match, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tries to resolve the rest of the identifier in the specified namespace.</span></span> <span data-ttu-id="b5dda-110">Se nenhuma correspondência for encontrada, uma exceção é lançada.</span><span class="sxs-lookup"><span data-stu-id="b5dda-110">If no match is found, an exception is thrown.</span></span>  
  
 <span data-ttu-id="b5dda-111">Em seguida, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tenta buscar todos os namespaces de não-qualificados (especificados no prólogo) para o identificador.</span><span class="sxs-lookup"><span data-stu-id="b5dda-111">Next, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tries to search all unqualified namespaces (specified in the prolog) for the identifier.</span></span> <span data-ttu-id="b5dda-112">Se o identificador pode ser localizado em exatamente um namespace, esse local é retornado.</span><span class="sxs-lookup"><span data-stu-id="b5dda-112">If the identifier can be located in exactly one namespace, that location is returned.</span></span> <span data-ttu-id="b5dda-113">Se mais de um namespace tiver uma correspondência para o identificador, uma exceção é lançada.</span><span class="sxs-lookup"><span data-stu-id="b5dda-113">If more than one namespace has a match for that identifier, an exception is thrown.</span></span> <span data-ttu-id="b5dda-114">Se nenhum namespace pode ser identificado para o identificador [!INCLUDE[esql](../../../../../../includes/esql-md.md)] passa o nome para o escopo para fora próximo (a <xref:System.Data.Common.DbCommand> ou <xref:System.Data.Common.DbConnection> objeto), conforme ilustrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="b5dda-114">If no namespace can be identified for the identifier, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] passes the name onto the next outward scope (the <xref:System.Data.Common.DbCommand> or <xref:System.Data.Common.DbConnection> object), as illustrated in the following example:</span></span>  
  
```  
SELECT TREAT(p AS NamespaceName.Employee)  
FROM ContainerName.Person AS p  
WHERE p IS OF (NamespaceName.Employee)  
```  
  
## <a name="differences-from-the-net-framework"></a><span data-ttu-id="b5dda-115">Diferenças do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b5dda-115">Differences from the .NET Framework</span></span>  
 <span data-ttu-id="b5dda-116">Em [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)], você pode usar namespaces parcialmente qualificadas.</span><span class="sxs-lookup"><span data-stu-id="b5dda-116">In the [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)], you can use partially qualified namespaces.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="b5dda-117"> não permite isso.</span><span class="sxs-lookup"><span data-stu-id="b5dda-117"> does not allow this.</span></span>  
  
## <a name="adonet-usage"></a><span data-ttu-id="b5dda-118">Uso do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b5dda-118">ADO.NET Usage</span></span>  
 <span data-ttu-id="b5dda-119">Consultas são expressos por meio de objetos ADO.NET <xref:System.Data.Common.DbCommand> .</span><span class="sxs-lookup"><span data-stu-id="b5dda-119">Queries are expressed through ADO.NET <xref:System.Data.Common.DbCommand> objects.</span></span> <span data-ttu-id="b5dda-120">os objetos de<xref:System.Data.Common.DbCommand> podem ser compilados sobre objetos de <xref:System.Data.Common.DbConnection> .</span><span class="sxs-lookup"><span data-stu-id="b5dda-120"><xref:System.Data.Common.DbCommand> objects can be built over <xref:System.Data.Common.DbConnection> objects.</span></span> <span data-ttu-id="b5dda-121">Namespaces também podem ser especificadas como parte de objetos de <xref:System.Data.Common.DbCommand> e de <xref:System.Data.Common.DbConnection> .</span><span class="sxs-lookup"><span data-stu-id="b5dda-121">Namespaces can also be specified as part of the <xref:System.Data.Common.DbCommand> and <xref:System.Data.Common.DbConnection> objects.</span></span> <span data-ttu-id="b5dda-122">Se [!INCLUDE[esql](../../../../../../includes/esql-md.md)] não é possível resolver um identificador dentro da consulta em si, os namespaces externos são investigados (com base nas regras semelhantes).</span><span class="sxs-lookup"><span data-stu-id="b5dda-122">If [!INCLUDE[esql](../../../../../../includes/esql-md.md)] cannot resolve an identifier within the query itself, the external namespaces are probed (based on similar rules).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5dda-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b5dda-123">See Also</span></span>  
 [<span data-ttu-id="b5dda-124">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="b5dda-124">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="b5dda-125">Visão geral do Entity SQL</span><span class="sxs-lookup"><span data-stu-id="b5dda-125">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)