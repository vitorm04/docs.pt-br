---
title: Método ICorPublishEnum::GetCount
ms.date: 03/30/2017
api_name:
- ICorPublishEnum.GetCount
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishEnum::GetCount
helpviewer_keywords:
- GetCount method, ICorPublishEnum interface [.NET Framework debugging]
- ICorPublishEnum::GetCount method [.NET Framework debugging]
ms.assetid: d228f684-2be3-4029-93ae-31fe02213c1f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0424d929f40da1faabd7456cdd85e39a59246d48
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59103240"
---
# <a name="icorpublishenumgetcount-method"></a><span data-ttu-id="87910-102">Método ICorPublishEnum::GetCount</span><span class="sxs-lookup"><span data-stu-id="87910-102">ICorPublishEnum::GetCount Method</span></span>
<span data-ttu-id="87910-103">Obtém o número de itens na enumeração.</span><span class="sxs-lookup"><span data-stu-id="87910-103">Gets the number of items in the enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87910-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="87910-104">Syntax</span></span>  
  
```  
HRESULT GetCount (  
    [out] ULONG   *pcelt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="87910-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="87910-105">Parameters</span></span>  
 `pcelt`  
 <span data-ttu-id="87910-106">[out] Um ponteiro para o número de itens na enumeração.</span><span class="sxs-lookup"><span data-stu-id="87910-106">[out] A pointer to the number of items in the enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87910-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="87910-107">Requirements</span></span>  
 <span data-ttu-id="87910-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="87910-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87910-109">**Cabeçalho:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="87910-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="87910-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="87910-110">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="87910-111">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="87910-111">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="87910-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="87910-112">See also</span></span>

- [<span data-ttu-id="87910-113">Interface ICorPublishEnum</span><span class="sxs-lookup"><span data-stu-id="87910-113">ICorPublishEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)
