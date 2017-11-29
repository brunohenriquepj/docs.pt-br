---
title: "Funções de servidor e banco de dados no SQL Server"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5482dfdb-e498-4614-8652-b174829eed13
caps.latest.revision: "9"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0bcb42e018f5e62179924634bfa49fcbfc4c7d16
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="server-and-database-roles-in-sql-server"></a><span data-ttu-id="16303-102">Funções de servidor e banco de dados no SQL Server</span><span class="sxs-lookup"><span data-stu-id="16303-102">Server and Database Roles in SQL Server</span></span>
<span data-ttu-id="16303-103">Todas as versões do SQL Server usam segurança baseada em função, o que permite que você atribua permissões para uma função ou grupo de usuários, em vez de usuários individuais.</span><span class="sxs-lookup"><span data-stu-id="16303-103">All versions of SQL Server use role-based security, which allows you to assign permissions to a role, or group of users, instead of to individual users.</span></span> <span data-ttu-id="16303-104">O servidor fixo e as funções de banco de dados fixas têm um conjunto fixo de permissões atribuídas a eles.</span><span class="sxs-lookup"><span data-stu-id="16303-104">Fixed server and fixed database roles have a fixed set of permissions assigned to them.</span></span>  
  
## <a name="fixed-server-roles"></a><span data-ttu-id="16303-105">Funções de servidor fixas</span><span class="sxs-lookup"><span data-stu-id="16303-105">Fixed Server Roles</span></span>  
 <span data-ttu-id="16303-106">As funções de servidor fixas têm um conjunto fixo de permissões e escopo no servidor.</span><span class="sxs-lookup"><span data-stu-id="16303-106">Fixed server roles have a fixed set of permissions and server-wide scope.</span></span> <span data-ttu-id="16303-107">Elas são destinadas para uso em administrar o SQL Server e as permissões atribuídas a elas não podem ser modificadas.</span><span class="sxs-lookup"><span data-stu-id="16303-107">They are intended for use in administering SQL Server and the permissions assigned to them cannot be changed.</span></span> <span data-ttu-id="16303-108">Os logons podem ser atribuídos às funções de servidor fixas sem ter uma conta de usuário em um banco de dados.</span><span class="sxs-lookup"><span data-stu-id="16303-108">Logins can be assigned to fixed server roles without having a user account in a database.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="16303-109">A função de servidor fixa `sysadmin` aborda todas as outras funções e tem escopo ilimitado.</span><span class="sxs-lookup"><span data-stu-id="16303-109">The `sysadmin` fixed server role encompasses all other roles and has unlimited scope.</span></span> <span data-ttu-id="16303-110">Não adicione entidades de segurança a essa função a menos que elas sejam altamente confiáveis.</span><span class="sxs-lookup"><span data-stu-id="16303-110">Do not add principals to this role unless they are highly trusted.</span></span> <span data-ttu-id="16303-111">Os membros de função `sysadmin` têm privilégios administrativos irrevogáveis em todos os bancos de dados e recursos do servidor.</span><span class="sxs-lookup"><span data-stu-id="16303-111">`sysadmin` role members have irrevocable administrative privileges on all server databases and resources.</span></span>  
  
 <span data-ttu-id="16303-112">Seja seletivo ao adicionar usuários a funções de servidor fixas.</span><span class="sxs-lookup"><span data-stu-id="16303-112">Be selective when you add users to fixed server roles.</span></span> <span data-ttu-id="16303-113">Por exemplo, a função `bulkadmin` permite que os usuários insiram o conteúdo do qualquer arquivo local em uma tabela, o que pode prejudicar a integridade de dados.</span><span class="sxs-lookup"><span data-stu-id="16303-113">For example, the `bulkadmin` role allows users to insert the contents of any local file into a table, which could jeopardize data integrity.</span></span> <span data-ttu-id="16303-114">Consulte os Manuais Online do [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] para obter uma lista completa de funções de servidor fixas e permissões.</span><span class="sxs-lookup"><span data-stu-id="16303-114">See [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Books Online for the complete list of fixed server roles and permissions.</span></span>  
  
## <a name="fixed-database-roles"></a><span data-ttu-id="16303-115">Funções de banco de dados fixas</span><span class="sxs-lookup"><span data-stu-id="16303-115">Fixed Database Roles</span></span>  
 <span data-ttu-id="16303-116">As funções de banco de dados fixas têm um conjunto pré-definido de permissões que são criadas para permitir que você gerencie grupos de permissões com facilidade.</span><span class="sxs-lookup"><span data-stu-id="16303-116">Fixed database roles have a pre-defined set of permissions that are designed to allow you to easily manage groups of permissions.</span></span> <span data-ttu-id="16303-117">Os membros da função `db_owner` podem executar todas as atividades de configuração e manutenção no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="16303-117">Members of the `db_owner` role can perform all configuration and maintenance activities on the database.</span></span>  
  
 <span data-ttu-id="16303-118">Para obter mais informações sobre as funções predefinidas do SQL Server, consulte os seguintes recursos.</span><span class="sxs-lookup"><span data-stu-id="16303-118">For more information about SQL Server predefined roles, see the following resources.</span></span>  
  
|<span data-ttu-id="16303-119">Recurso</span><span class="sxs-lookup"><span data-stu-id="16303-119">Resource</span></span>|<span data-ttu-id="16303-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="16303-120">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="16303-121">[Funções de nível de servidor](http://msdn.microsoft.com/library/ms188659.aspx) e [permissões de funções de servidor fixas](http://msdn.microsoft.com/library/ms175892.aspx) na [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Manuais Online</span><span class="sxs-lookup"><span data-stu-id="16303-121">[Server-Level Roles](http://msdn.microsoft.com/library/ms188659.aspx) and [Permissions of Fixed Server Roles](http://msdn.microsoft.com/library/ms175892.aspx) in [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Books Online</span></span>|<span data-ttu-id="16303-122">Descreve funções de servidor fixas e as permissões associadas a elas no [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="16303-122">Describes fixed server roles and the permissions associated with them in [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].</span></span>|  
|<span data-ttu-id="16303-123">[Funções de nível de banco de dados](http://msdn.microsoft.com/library/ms189121.aspx) e [permissões de funções de banco de dados fixa](http://msdn.microsoft.com/library/ms189612.aspx) na [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Manuais Online</span><span class="sxs-lookup"><span data-stu-id="16303-123">[Database-Level Roles](http://msdn.microsoft.com/library/ms189121.aspx) and [Permissions of Fixed Database Roles](http://msdn.microsoft.com/library/ms189612.aspx) in [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Books Online</span></span>|<span data-ttu-id="16303-124">Descreve funções de banco de dados fixas e as permissões associadas a elas</span><span class="sxs-lookup"><span data-stu-id="16303-124">Describes fixed database roles and the permissions associated with them</span></span>|  
  
## <a name="database-roles-and-users"></a><span data-ttu-id="16303-125">Funções e usuários do banco de dados</span><span class="sxs-lookup"><span data-stu-id="16303-125">Database Roles and Users</span></span>  
 <span data-ttu-id="16303-126">Os logons devem ser mapeados para contas de usuário do banco de dados para funcionar com objetos de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="16303-126">Logins must be mapped to database user accounts in order to work with database objects.</span></span> <span data-ttu-id="16303-127">Os usuários do banco de dados podem então ser adicionados às funções de banco de dados, herdando todos os conjuntos de permissões associados a essas funções.</span><span class="sxs-lookup"><span data-stu-id="16303-127">Database users can then be added to database roles, inheriting any permission sets associated with those roles.</span></span> <span data-ttu-id="16303-128">Todas as permissões podem ser concedidas.</span><span class="sxs-lookup"><span data-stu-id="16303-128">All permissions can be granted.</span></span>  
  
 <span data-ttu-id="16303-129">Você também deve considerar a função `public`, a conta de usuário `dbo` e a conta `guest` ao projetar a segurança de seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="16303-129">You must also consider the `public` role, the `dbo` user account, and the `guest` account when you design security for your application.</span></span>  
  
### <a name="the-public-role"></a><span data-ttu-id="16303-130">A função pública</span><span class="sxs-lookup"><span data-stu-id="16303-130">The public Role</span></span>  
 <span data-ttu-id="16303-131">A função `public` está contida em cada banco de dados, incluindo bancos de dados do sistema.</span><span class="sxs-lookup"><span data-stu-id="16303-131">The `public` role is contained in every database, which includes system databases.</span></span> <span data-ttu-id="16303-132">Ela não pode ser descartada e você não pode adicionar ou remover usuários dela.</span><span class="sxs-lookup"><span data-stu-id="16303-132">It cannot be dropped and you cannot add or remove users from it.</span></span> <span data-ttu-id="16303-133">As permissões concedidas à função `public` são herdadas por todos os outros usuários e funções porque pertencem à função `public` por padrão.</span><span class="sxs-lookup"><span data-stu-id="16303-133">Permissions granted to the `public` role are inherited by all other users and roles because they belong to the `public` role by default.</span></span> <span data-ttu-id="16303-134">Conceda a `public` somente as permissões que você deseja que todos os usuários tenham.</span><span class="sxs-lookup"><span data-stu-id="16303-134">Grant `public` only the permissions you want all users to have.</span></span>  
  
### <a name="the-dbo-user-account"></a><span data-ttu-id="16303-135">A conta de usuário dbo</span><span class="sxs-lookup"><span data-stu-id="16303-135">The dbo User Account</span></span>  
 <span data-ttu-id="16303-136">O `dbo`, ou o proprietário do banco de dados, é uma conta de usuário que tem permissões implícitas para executar todas as atividades no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="16303-136">The `dbo`, or database owner, is a user account that has implied permissions to perform all activities in the database.</span></span> <span data-ttu-id="16303-137">Os membros da função de servidor fixa `sysadmin` são mapeados automaticamente para `dbo`.</span><span class="sxs-lookup"><span data-stu-id="16303-137">Members of the `sysadmin` fixed server role are automatically mapped to `dbo`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="16303-138">`dbo`também é o nome de um esquema, conforme discutido em [propriedade e separação do esquema de usuário no SQL Server](../../../../../docs/framework/data/adonet/sql/ownership-and-user-schema-separation-in-sql-server.md).</span><span class="sxs-lookup"><span data-stu-id="16303-138">`dbo` is also the name of a schema, as discussed in [Ownership and User-Schema Separation in SQL Server](../../../../../docs/framework/data/adonet/sql/ownership-and-user-schema-separation-in-sql-server.md).</span></span>  
  
 <span data-ttu-id="16303-139">A conta de usuário `dbo` é confundida frequentemente com a função de banco de dados fixa `db_owner`.</span><span class="sxs-lookup"><span data-stu-id="16303-139">The `dbo` user account is frequently confused with the `db_owner` fixed database role.</span></span> <span data-ttu-id="16303-140">O escopo do `db_owner` é um banco de dados; o escopo do `sysadmin` é o servidor inteiro.</span><span class="sxs-lookup"><span data-stu-id="16303-140">The scope of `db_owner` is a database; the scope of `sysadmin` is the whole server.</span></span> <span data-ttu-id="16303-141">A associação na função de `db_owner` não confere privilégios do usuário de `dbo`.</span><span class="sxs-lookup"><span data-stu-id="16303-141">Membership in the `db_owner` role does not confer `dbo` user privileges.</span></span>  
  
### <a name="the-guest-user-account"></a><span data-ttu-id="16303-142">A conta de usuário guest</span><span class="sxs-lookup"><span data-stu-id="16303-142">The guest User Account</span></span>  
 <span data-ttu-id="16303-143">Após um usuário ter sido autenticado e permitido fazer logon em uma instância do SQL Server, uma conta de usuário separada deve existir em cada banco de dados que o usuário precise acessar.</span><span class="sxs-lookup"><span data-stu-id="16303-143">After a user has been authenticated and allowed to log in to an instance of SQL Server, a separate user account must exist in each database the user has to access.</span></span> <span data-ttu-id="16303-144">Exigir uma conta de usuário em cada banco de dados impede que os usuários se conectem a uma instância do SQL Server e acessem todos os bancos de dados em um servidor.</span><span class="sxs-lookup"><span data-stu-id="16303-144">Requiring a user account in each database prevents users from connecting to an instance of SQL Server and accessing all the databases on a server.</span></span> <span data-ttu-id="16303-145">A existência de uma conta de usuário `guest` no banco de dados contorna esse requisito permitindo que um logon sem uma conta de usuário do banco de dados acesse um banco de dados.</span><span class="sxs-lookup"><span data-stu-id="16303-145">The existence of a `guest` user account in the database circumvents this requirement by allowing a login without a database user account to access a database.</span></span>  
  
 <span data-ttu-id="16303-146">A conta `guest` é uma conta interna em todas as versões do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="16303-146">The `guest` account is a built-in account in all versions of SQL Server.</span></span> <span data-ttu-id="16303-147">Por padrão, ela é desabilitada em novos bancos de dados.</span><span class="sxs-lookup"><span data-stu-id="16303-147">By default, it is disabled in new databases.</span></span> <span data-ttu-id="16303-148">Se estiver ativada, você poderá desativá-la revogando sua permissão CONNECT executando a instrução REVOKE CONNECT FROM GUEST do Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="16303-148">If it is enabled, you can disable it by revoking its CONNECT permission by executing the Transact-SQL REVOKE CONNECT FROM GUEST statement.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="16303-149">Evite usar a conta `guest`; todos os logons sem suas próprias permissões de banco de dados obtêm as permissões de banco de dados concedidas a essa conta.</span><span class="sxs-lookup"><span data-stu-id="16303-149">Avoid using the `guest` account; all logins without their own database permissions obtain the database permissions granted to this account.</span></span> <span data-ttu-id="16303-150">Se você usar a conta `guest`, conceda permissões mínimas.</span><span class="sxs-lookup"><span data-stu-id="16303-150">If you must use the `guest` account, grant it minimum permissions.</span></span>  
  
 <span data-ttu-id="16303-151">Para obter mais informações sobre logons, usuários e funções do SQL Server, consulte os seguintes recursos.</span><span class="sxs-lookup"><span data-stu-id="16303-151">For more information about SQL Server logins, users and roles, see the following resources.</span></span>  
  
|<span data-ttu-id="16303-152">Recurso</span><span class="sxs-lookup"><span data-stu-id="16303-152">Resource</span></span>|<span data-ttu-id="16303-153">Descrição</span><span class="sxs-lookup"><span data-stu-id="16303-153">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="16303-154">[Controle de acesso e identidade](http://msdn.microsoft.com/library/bb510418.aspx) nos Manuais Online do SQL Server</span><span class="sxs-lookup"><span data-stu-id="16303-154">[Identity and Access Control](http://msdn.microsoft.com/library/bb510418.aspx) in SQL Server Books Online</span></span>|<span data-ttu-id="16303-155">Contém links para tópicos que descrevem entidades de segurança, funções, credenciais, protegíveis e permissões.</span><span class="sxs-lookup"><span data-stu-id="16303-155">Contains links to topics that describe principals, roles, credentials, securables and permissions.</span></span>|  
|<span data-ttu-id="16303-156">[Entidades](http://msdn.microsoft.com/library/ms181127.aspx) na [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Manuais Online</span><span class="sxs-lookup"><span data-stu-id="16303-156">[Principals](http://msdn.microsoft.com/library/ms181127.aspx) in [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Books Online</span></span>|<span data-ttu-id="16303-157">Descreve as entidades de segurança e contém links para tópicos que descrevem funções de servidor e banco de dados.</span><span class="sxs-lookup"><span data-stu-id="16303-157">Describes principals and contains links to topics that describe server and database roles.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="16303-158">Consulte também</span><span class="sxs-lookup"><span data-stu-id="16303-158">See Also</span></span>  
 <span data-ttu-id="16303-159">[Securing ADO.NET Applications](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md) (Protegendo aplicativos ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="16303-159">[Securing ADO.NET Applications](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)</span></span>  
 [<span data-ttu-id="16303-160">Cenários de segurança do aplicativo no SQL Server</span><span class="sxs-lookup"><span data-stu-id="16303-160">Application Security Scenarios in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [<span data-ttu-id="16303-161">Autenticação no SQL Server</span><span class="sxs-lookup"><span data-stu-id="16303-161">Authentication in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/authentication-in-sql-server.md)  
 [<span data-ttu-id="16303-162">Propriedade e separação do esquema de usuário no SQL Server</span><span class="sxs-lookup"><span data-stu-id="16303-162">Ownership and User-Schema Separation in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/ownership-and-user-schema-separation-in-sql-server.md)  
 [<span data-ttu-id="16303-163">Autorização e permissões no SQL Server</span><span class="sxs-lookup"><span data-stu-id="16303-163">Authorization and Permissions in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/authorization-and-permissions-in-sql-server.md)  
 <span data-ttu-id="16303-164">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="16303-164">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>