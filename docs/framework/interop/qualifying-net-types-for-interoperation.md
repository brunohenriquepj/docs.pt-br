---
title: "Qualificando tipos do .NET para interoperação"
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
- exposing .NET Framework components to COM
- COM interop, qualifying .NET types
- qualifying .NET types for interoperation
- interoperation with unmanaged code, qualifying .NET types
- interoperation with unmanaged code, exposing .NET Framework components
- COM interop, exposing COM components
ms.assetid: 4b8afb52-fb8d-4e65-b47c-fd82956a3cdd
caps.latest.revision: 10
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 68ecd5e4c562f1eecb31ee539adb70d67455a584
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="qualifying-net-types-for-interoperation"></a><span data-ttu-id="af192-102">Qualificando tipos do .NET para interoperação</span><span class="sxs-lookup"><span data-stu-id="af192-102">Qualifying .NET Types for Interoperation</span></span>
<span data-ttu-id="af192-103">Se você pretende expor os tipos em um assembly para aplicativos COM, considere os requisitos de interoperabilidade COM em tempo de design.</span><span class="sxs-lookup"><span data-stu-id="af192-103">If you intend to expose types in an assembly to COM applications, consider the requirements of COM interop at design time.</span></span> <span data-ttu-id="af192-104">Tipos gerenciados (classe, interface, estrutura e enumeração) se integram perfeitamente com tipos COM quando você obedece às seguintes diretrizes:</span><span class="sxs-lookup"><span data-stu-id="af192-104">Managed types (class, interface, structure, and enumeration) seamlessly integrate with COM types when you adhere to the following guidelines:</span></span>  
  
-   <span data-ttu-id="af192-105">As classes devem implementar interfaces explicitamente.</span><span class="sxs-lookup"><span data-stu-id="af192-105">Classes should implement interfaces explicitly.</span></span>  
  
     <span data-ttu-id="af192-106">Embora a interoperabilidade COM forneça um mecanismo para gerar automaticamente uma interface contendo todos os membros da classe e os membros da respectiva classe base, é muito melhor fornecer interfaces explícitas.</span><span class="sxs-lookup"><span data-stu-id="af192-106">Although COM interop provides a mechanism to automatically generate an interface containing all members of the class and the members of its base class, it is far better to provide explicit interfaces.</span></span> <span data-ttu-id="af192-107">A interface gerada automaticamente é chamada de interface de classe.</span><span class="sxs-lookup"><span data-stu-id="af192-107">The automatically generated interface is called the class interface.</span></span> <span data-ttu-id="af192-108">Para obter diretrizes, consulte [Introdução à interface de classe](http://msdn.microsoft.com/en-us/733c0dd2-12e5-46e6-8de1-39d5b25df024).</span><span class="sxs-lookup"><span data-stu-id="af192-108">For guidelines, see [Introducing the Class Interface](http://msdn.microsoft.com/en-us/733c0dd2-12e5-46e6-8de1-39d5b25df024).</span></span>  
  
     <span data-ttu-id="af192-109">Você pode usar [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], C# e C++ para incorporar as definições de interface no seu código, em vez de usar a linguagem IDL ou um equivalente dela.</span><span class="sxs-lookup"><span data-stu-id="af192-109">You can use [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], C#, and C++ to incorporate interface definitions in your code, instead of having to use Interface Definition Language (IDL) or its equivalent.</span></span> <span data-ttu-id="af192-110">Para obter detalhes da sintaxe, consulte a documentação da linguagem.</span><span class="sxs-lookup"><span data-stu-id="af192-110">For syntax details, see your language documentation.</span></span>  
  
-   <span data-ttu-id="af192-111">Os tipos gerenciados devem ser públicos.</span><span class="sxs-lookup"><span data-stu-id="af192-111">Managed types must be public.</span></span>  
  
     <span data-ttu-id="af192-112">Somente os tipos públicos em um assembly são registrados e exportados para a biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="af192-112">Only public types in an assembly are registered and exported to the type library.</span></span> <span data-ttu-id="af192-113">Como resultado, somente os tipos públicos são visíveis para COM.</span><span class="sxs-lookup"><span data-stu-id="af192-113">As a result, only public types are visible to COM.</span></span>  
  
     <span data-ttu-id="af192-114">Tipos gerenciados expõem recursos para outro código gerenciado que pode não ser exposto a COM.</span><span class="sxs-lookup"><span data-stu-id="af192-114">Managed types expose features to other managed code that might not be exposed to COM.</span></span> <span data-ttu-id="af192-115">Por exemplo, campos de constantes, construtores com parâmetros e métodos estáticos não são expostos a clientes COM.</span><span class="sxs-lookup"><span data-stu-id="af192-115">For instance, parameterized constructors, static methods, and constant fields are not exposed to COM clients.</span></span> <span data-ttu-id="af192-116">Além disso, como o tempo de execução realiza marshaling de dados dentro e fora de um tipo, os dados podem ser copiados ou transformados.</span><span class="sxs-lookup"><span data-stu-id="af192-116">Further, as the runtime marshals data in and out of a type, the data might be copied or transformed.</span></span>  
  
-   <span data-ttu-id="af192-117">Propriedades, métodos, campos e eventos devem ser públicos.</span><span class="sxs-lookup"><span data-stu-id="af192-117">Methods, properties, fields, and events must be public.</span></span>  
  
     <span data-ttu-id="af192-118">Membros de tipos públicos também devem ser públicos para ser visíveis para COM.</span><span class="sxs-lookup"><span data-stu-id="af192-118">Members of public types must also be public if they are to be visible to COM.</span></span> <span data-ttu-id="af192-119">Você pode restringir a visibilidade de um assembly, um tipo público ou membros públicos de um tipo público aplicando o <xref:System.Runtime.InteropServices.ComVisibleAttribute>.</span><span class="sxs-lookup"><span data-stu-id="af192-119">You can restrict the visibility of an assembly, a public type, or public members of a public type by applying the <xref:System.Runtime.InteropServices.ComVisibleAttribute>.</span></span> <span data-ttu-id="af192-120">Por padrão, todos os membros e tipos públicos são visíveis.</span><span class="sxs-lookup"><span data-stu-id="af192-120">By default, all public types and members are visible.</span></span>  
  
-   <span data-ttu-id="af192-121">Os tipos devem ter um construtor padrão público para serem ativados do COM.</span><span class="sxs-lookup"><span data-stu-id="af192-121">Types must have a public default constructor to be activated from COM.</span></span>  
  
     <span data-ttu-id="af192-122">Tipos públicos gerenciados são visíveis para o COM.</span><span class="sxs-lookup"><span data-stu-id="af192-122">Managed, public types are visible to COM.</span></span> <span data-ttu-id="af192-123">No entanto, sem um construtor público padrão (um construtor sem argumentos), clientes COM não podem criar o tipo.</span><span class="sxs-lookup"><span data-stu-id="af192-123">However, without a public default constructor (a constructor with no arguments), COM clients cannot create the type.</span></span> <span data-ttu-id="af192-124">Clientes COM ainda podem usar o tipo se ele é ativado por outros meios.</span><span class="sxs-lookup"><span data-stu-id="af192-124">COM clients can still use the type if it is activated by some other means.</span></span>  
  
-   <span data-ttu-id="af192-125">Os tipos não podem ser abstratos.</span><span class="sxs-lookup"><span data-stu-id="af192-125">Types cannot be abstract.</span></span>  
  
     <span data-ttu-id="af192-126">Nem clientes COM, tampouco clientes .NET podem criar tipos abstratos.</span><span class="sxs-lookup"><span data-stu-id="af192-126">Neither COM clients nor .NET clients can create abstract types.</span></span>  
  
 <span data-ttu-id="af192-127">Quando exportados para COM, a hierarquia de herança de um tipo gerenciado é nivelada.</span><span class="sxs-lookup"><span data-stu-id="af192-127">When exported to COM, the inheritance hierarchy of a managed type is flattened.</span></span> <span data-ttu-id="af192-128">O controle de versão também difere entre ambientes gerenciados e não gerenciados.</span><span class="sxs-lookup"><span data-stu-id="af192-128">Versioning also differs between managed and unmanaged environments.</span></span> <span data-ttu-id="af192-129">Os tipos expostos ao COM não têm as mesmas características de controle de versão de outros tipos gerenciados.</span><span class="sxs-lookup"><span data-stu-id="af192-129">Types exposed to COM do not have the same versioning characteristics as other managed types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af192-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="af192-130">See Also</span></span>  
 <span data-ttu-id="af192-131"><xref:System.Runtime.InteropServices.ComVisibleAttribute></span><span class="sxs-lookup"><span data-stu-id="af192-131"><xref:System.Runtime.InteropServices.ComVisibleAttribute></span></span>   
 <span data-ttu-id="af192-132">[Expondo componentes do .NET Framework para COM](../../../docs/framework/interop/exposing-dotnet-components-to-com.md) </span><span class="sxs-lookup"><span data-stu-id="af192-132">[Exposing .NET Framework Components to COM](../../../docs/framework/interop/exposing-dotnet-components-to-com.md) </span></span>  
 <span data-ttu-id="af192-133">[Introdução à Interface de Classe](http://msdn.microsoft.com/en-us/733c0dd2-12e5-46e6-8de1-39d5b25df024) </span><span class="sxs-lookup"><span data-stu-id="af192-133">[Introducing the Class Interface](http://msdn.microsoft.com/en-us/733c0dd2-12e5-46e6-8de1-39d5b25df024) </span></span>  
 <span data-ttu-id="af192-134">[Aplicando atributos de interoperabilidade](../../../docs/framework/interop/applying-interop-attributes.md) </span><span class="sxs-lookup"><span data-stu-id="af192-134">[Applying Interop Attributes](../../../docs/framework/interop/applying-interop-attributes.md) </span></span>  
 [<span data-ttu-id="af192-135">Empacotando um assembly para COM</span><span class="sxs-lookup"><span data-stu-id="af192-135">Packaging an Assembly for COM</span></span>](../../../docs/framework/interop/packaging-an-assembly-for-com.md)
