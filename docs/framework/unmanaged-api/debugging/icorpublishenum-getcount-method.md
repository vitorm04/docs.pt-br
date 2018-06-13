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
ms.openlocfilehash: f191c31ec5333fbea52c298f477c8c624beb92b2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33424502"
---
# <a name="icorpublishenumgetcount-method"></a><span data-ttu-id="86358-102">Método ICorPublishEnum::GetCount</span><span class="sxs-lookup"><span data-stu-id="86358-102">ICorPublishEnum::GetCount Method</span></span>
<span data-ttu-id="86358-103">Obtém o número de itens na enumeração.</span><span class="sxs-lookup"><span data-stu-id="86358-103">Gets the number of items in the enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86358-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="86358-104">Syntax</span></span>  
  
```  
HRESULT GetCount (  
    [out] ULONG   *pcelt  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="86358-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="86358-105">Parameters</span></span>  
 `pcelt`  
 <span data-ttu-id="86358-106">[out] Um ponteiro para o número de itens na enumeração.</span><span class="sxs-lookup"><span data-stu-id="86358-106">[out] A pointer to the number of items in the enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86358-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="86358-107">Requirements</span></span>  
 <span data-ttu-id="86358-108">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86358-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86358-109">**Cabeçalho:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="86358-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="86358-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="86358-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="86358-111">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86358-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86358-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="86358-112">See Also</span></span>  
 [<span data-ttu-id="86358-113">Interface ICorPublishEnum</span><span class="sxs-lookup"><span data-stu-id="86358-113">ICorPublishEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)
