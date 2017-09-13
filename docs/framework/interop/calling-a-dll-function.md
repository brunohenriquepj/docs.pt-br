---
title: "Chamando uma função de DLL"
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
- unmanaged functions, calling
- unmanaged functions
- COM interop, platform invoke
- platform invoke, calling unmanaged functions
- interoperation with unmanaged code, platform invoke
- DLL functions
ms.assetid: 113646de-7ea0-4f0e-8df0-c46dab3e8733
caps.latest.revision: 12
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: b676599513b923ae46d6ec27d7506435d9cbfcd2
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="calling-a-dll-function"></a><span data-ttu-id="477c0-102">Chamando uma função de DLL</span><span class="sxs-lookup"><span data-stu-id="477c0-102">Calling a DLL Function</span></span>
<span data-ttu-id="477c0-103">Embora a chamada a funções de DLL não gerenciadas seja quase idêntica à chamada de outro código gerenciado, há diferenças que podem fazer com que as funções de DLL pareçam confusas a princípio.</span><span class="sxs-lookup"><span data-stu-id="477c0-103">Although calling unmanaged DLL functions is nearly identical to calling other managed code, there are differences that can make DLL functions seem confusing at first.</span></span> <span data-ttu-id="477c0-104">Esta seção apresenta tópicos que descrevem alguns dos problemas incomuns relacionados a chamadas.</span><span class="sxs-lookup"><span data-stu-id="477c0-104">This section introduces topics that describe some of the unusual calling-related issues.</span></span>  
  
 <span data-ttu-id="477c0-105">Estruturas retornadas de chamadas de invocação de plataforma devem ser tipos de dados que têm a mesma representação em um código gerenciado e não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="477c0-105">Structures that are returned from platform invoke calls must be data types that have the same representation in managed and unmanaged code.</span></span> <span data-ttu-id="477c0-106">Esses tipos são chamados de *tipos blittable* porque não exigem conversão (consulte [Tipos blittable e não blittable](../../../docs/framework/interop/blittable-and-non-blittable-types.md)).</span><span class="sxs-lookup"><span data-stu-id="477c0-106">Such types are called *blittable types* because they do not require conversion (see [Blittable and Non-Blittable Types](../../../docs/framework/interop/blittable-and-non-blittable-types.md)).</span></span> <span data-ttu-id="477c0-107">Para chamar uma função que tem uma estrutura não blittable como seu tipo de retorno, é possível definir um tipo de auxiliar blittable do mesmo tamanho do tipo não blittable e converter os dados depois que a função é retornada.</span><span class="sxs-lookup"><span data-stu-id="477c0-107">To call a function that has a non-blittable structure as its return type, you can define a blittable helper type of the same size as the non-blittable type and convert the data after the function returns.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="477c0-108">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="477c0-108">In This Section</span></span>  
 [<span data-ttu-id="477c0-109">Passando estruturas</span><span class="sxs-lookup"><span data-stu-id="477c0-109">Passing Structures</span></span>](../../../docs/framework/interop/passing-structures.md)  
 <span data-ttu-id="477c0-110">Identifica os problemas de passar estruturas de dados com um layout predefinido.</span><span class="sxs-lookup"><span data-stu-id="477c0-110">Identifies the issues of passing data structures with a predefined layout.</span></span>  
  
 [<span data-ttu-id="477c0-111">Funções de retorno de chamada</span><span class="sxs-lookup"><span data-stu-id="477c0-111">Callback Functions</span></span>](../../../docs/framework/interop/callback-functions.md)  
 <span data-ttu-id="477c0-112">Fornece informações básicas sobre as funções de retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="477c0-112">Provides basic information about callback functions.</span></span>  
  
 [<span data-ttu-id="477c0-113">Como implementar funções de retorno de chamada</span><span class="sxs-lookup"><span data-stu-id="477c0-113">How to: Implement Callback Functions</span></span>](../../../docs/framework/interop/how-to-implement-callback-functions.md)  
 <span data-ttu-id="477c0-114">Descreve como implementar funções de retorno de chamada em um código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="477c0-114">Describes how to implement callback functions in managed code.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="477c0-115">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="477c0-115">Related Sections</span></span>  
 [<span data-ttu-id="477c0-116">Consumindo funções de DLL não gerenciadas</span><span class="sxs-lookup"><span data-stu-id="477c0-116">Consuming Unmanaged DLL Functions</span></span>](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)  
 <span data-ttu-id="477c0-117">Descreve como chamar funções de DLL não gerenciadas usando a invocação de plataforma.</span><span class="sxs-lookup"><span data-stu-id="477c0-117">Describes how to call unmanaged DLL functions using platform invoke.</span></span>  
  
 [<span data-ttu-id="477c0-118">Marshaling de dados com a invocação de plataforma</span><span class="sxs-lookup"><span data-stu-id="477c0-118">Marshaling Data with Platform Invoke</span></span>](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)  
 <span data-ttu-id="477c0-119">Descreve como declarar parâmetros de método e passar argumentos para funções exportadas por bibliotecas não gerenciadas.</span><span class="sxs-lookup"><span data-stu-id="477c0-119">Describes how to declare method parameters and pass arguments to functions exported by unmanaged libraries.</span></span>
