---
title: Método ICorPublishEnum::Skip
ms.date: 03/30/2017
api_name:
- ICorPublishEnum.Skip
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishEnum::Skip
helpviewer_keywords:
- ICorPublishEnum::Skip method [.NET Framework debugging]
- Skip method, ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: 1680ec06-4ab0-447e-93ad-cdb8693fde5c
topic_type:
- apiref
ms.openlocfilehash: b68a9ec1e8fee4fdecd2114af28c75c4a236cb3a
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421134"
---
# <a name="icorpublishenumskip-method"></a><span data-ttu-id="d396f-102">Método ICorPublishEnum::Skip</span><span class="sxs-lookup"><span data-stu-id="d396f-102">ICorPublishEnum::Skip Method</span></span>
<span data-ttu-id="d396f-103">Move o cursor para a frente na enumeração pelo número especificado de itens.</span><span class="sxs-lookup"><span data-stu-id="d396f-103">Moves the cursor forward in the enumeration by the specified number of items.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d396f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d396f-104">Syntax</span></span>  
  
```cpp  
HRESULT Skip (  
    [in] ULONG   celt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d396f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d396f-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="d396f-106">no O número de itens pelos quais mover o cursor para a frente.</span><span class="sxs-lookup"><span data-stu-id="d396f-106">[in] The number of items by which to move the cursor forward.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d396f-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d396f-107">Requirements</span></span>  
 <span data-ttu-id="d396f-108">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d396f-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d396f-109">**Cabeçalho:** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="d396f-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="d396f-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d396f-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d396f-111">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d396f-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d396f-112">Veja também</span><span class="sxs-lookup"><span data-stu-id="d396f-112">See also</span></span>

- [<span data-ttu-id="d396f-113">Interface ICorPublishEnum</span><span class="sxs-lookup"><span data-stu-id="d396f-113">ICorPublishEnum Interface</span></span>](icorpublishenum-interface.md)
