---
title: "Método ICorPublishEnum::Skip"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorPublishEnum.Skip
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorPublishEnum::Skip
helpviewer_keywords:
- ICorPublishEnum::Skip method [.NET Framework debugging]
- Skip method, ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: 1680ec06-4ab0-447e-93ad-cdb8693fde5c
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6f75681237ff00b61cf584fb99c7ee6bbda6df48
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icorpublishenumskip-method"></a><span data-ttu-id="f5249-102">Método ICorPublishEnum::Skip</span><span class="sxs-lookup"><span data-stu-id="f5249-102">ICorPublishEnum::Skip Method</span></span>
<span data-ttu-id="f5249-103">Move o cursor para a frente na enumeração pelo número especificado de itens.</span><span class="sxs-lookup"><span data-stu-id="f5249-103">Moves the cursor forward in the enumeration by the specified number of items.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5249-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f5249-104">Syntax</span></span>  
  
```  
HRESULT Skip (  
    [in] ULONG   celt  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f5249-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f5249-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="f5249-106">[in] O número de itens com o qual mover o cursor para frente.</span><span class="sxs-lookup"><span data-stu-id="f5249-106">[in] The number of items by which to move the cursor forward.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5249-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f5249-107">Requirements</span></span>  
 <span data-ttu-id="f5249-108">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5249-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5249-109">**Cabeçalho:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="f5249-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="f5249-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f5249-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f5249-111">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5249-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5249-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f5249-112">See Also</span></span>  
 [<span data-ttu-id="f5249-113">Interface ICorPublishEnum</span><span class="sxs-lookup"><span data-stu-id="f5249-113">ICorPublishEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)