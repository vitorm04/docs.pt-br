---
title: "Método ICorPublishEnum::GetCount"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorPublishEnum.GetCount
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorPublishEnum::GetCount
helpviewer_keywords:
- GetCount method, ICorPublishEnum interface [.NET Framework debugging]
- ICorPublishEnum::GetCount method [.NET Framework debugging]
ms.assetid: d228f684-2be3-4029-93ae-31fe02213c1f
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 023965489530e70deb7dc9460418ef0d56654081
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icorpublishenumgetcount-method"></a><span data-ttu-id="16871-102">Método ICorPublishEnum::GetCount</span><span class="sxs-lookup"><span data-stu-id="16871-102">ICorPublishEnum::GetCount Method</span></span>
<span data-ttu-id="16871-103">Obtém o número de itens na enumeração.</span><span class="sxs-lookup"><span data-stu-id="16871-103">Gets the number of items in the enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16871-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="16871-104">Syntax</span></span>  
  
```  
HRESULT GetCount (  
    [out] ULONG   *pcelt  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="16871-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="16871-105">Parameters</span></span>  
 `pcelt`  
 <span data-ttu-id="16871-106">[out] Um ponteiro para o número de itens na enumeração.</span><span class="sxs-lookup"><span data-stu-id="16871-106">[out] A pointer to the number of items in the enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16871-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="16871-107">Requirements</span></span>  
 <span data-ttu-id="16871-108">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="16871-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16871-109">**Cabeçalho:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="16871-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="16871-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="16871-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="16871-111">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16871-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16871-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="16871-112">See Also</span></span>  
 [<span data-ttu-id="16871-113">Interface ICorPublishEnum</span><span class="sxs-lookup"><span data-stu-id="16871-113">ICorPublishEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)
