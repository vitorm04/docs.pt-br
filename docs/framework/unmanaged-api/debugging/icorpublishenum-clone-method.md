---
title: Método ICorPublishEnum::Clone
ms.date: 03/30/2017
api_name:
- ICorPublishEnum.Clone
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishEnum::Clone
helpviewer_keywords:
- Clone method, ICorPublishEnum interface [.NET Framework debugging]
- ICorPublishEnum::Clone method [.NET Framework debugging]
ms.assetid: c9a26ea3-b8eb-4b8e-854f-9a2ca26b3b39
topic_type:
- apiref
ms.openlocfilehash: afd16f1f31be9148422dd6d0be748036a8e5d99a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790653"
---
# <a name="icorpublishenumclone-method"></a><span data-ttu-id="713a9-102">Método ICorPublishEnum::Clone</span><span class="sxs-lookup"><span data-stu-id="713a9-102">ICorPublishEnum::Clone Method</span></span>
<span data-ttu-id="713a9-103">Cria uma cópia deste objeto [ICorPublishEnum](icorpublishenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="713a9-103">Creates a copy of this [ICorPublishEnum](icorpublishenum-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="713a9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="713a9-104">Syntax</span></span>  
  
```cpp  
HRESULT Clone (  
    [out] ICorPublishEnum   **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="713a9-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="713a9-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="713a9-106">fora Um ponteiro para o endereço de um objeto de `ICorPublishEnum` que é uma cópia desse objeto `ICorPublishEnum`.</span><span class="sxs-lookup"><span data-stu-id="713a9-106">[out] A pointer to the address of an `ICorPublishEnum` object that is a copy of this `ICorPublishEnum` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="713a9-107">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="713a9-107">Requirements</span></span>  
 <span data-ttu-id="713a9-108">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="713a9-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="713a9-109">**Cabeçalho:** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="713a9-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="713a9-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="713a9-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="713a9-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="713a9-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="713a9-112">Veja também</span><span class="sxs-lookup"><span data-stu-id="713a9-112">See also</span></span>

- [<span data-ttu-id="713a9-113">Interface ICorPublishEnum</span><span class="sxs-lookup"><span data-stu-id="713a9-113">ICorPublishEnum Interface</span></span>](icorpublishenum-interface.md)
