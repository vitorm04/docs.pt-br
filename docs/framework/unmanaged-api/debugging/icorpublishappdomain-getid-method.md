---
title: Método ICorPublishAppDomain::GetID
ms.date: 03/30/2017
api_name:
- ICorPublishAppDomain.GetID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishAppDomain::GetID
helpviewer_keywords:
- GetID method, ICorPublishAppDomain interface [.NET Framework debugging]
- ICorPublishAppDomain::GetID method [.NET Framework debugging]
ms.assetid: 229437e3-1465-4bd8-8846-9804b2488133
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b1a557191c5649f2ed87cf4f4dfdb4167133e597
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67774262"
---
# <a name="icorpublishappdomaingetid-method"></a><span data-ttu-id="0fc28-102">Método ICorPublishAppDomain::GetID</span><span class="sxs-lookup"><span data-stu-id="0fc28-102">ICorPublishAppDomain::GetID Method</span></span>
<span data-ttu-id="0fc28-103">Obtém o identificador exclusivo para este [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md).</span><span class="sxs-lookup"><span data-stu-id="0fc28-103">Gets the unique identifier for this [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0fc28-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0fc28-104">Syntax</span></span>  
  
```cpp  
HRESULT GetID (  
    [out] ULONG32   *puId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0fc28-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0fc28-105">Parameters</span></span>  
 `puId`  
 <span data-ttu-id="0fc28-106">[out] Um ponteiro para o identificador do domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0fc28-106">[out] A pointer to the identifier of the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0fc28-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="0fc28-107">Remarks</span></span>  
 <span data-ttu-id="0fc28-108">O identificador é exclusivo somente no escopo do processo de recipiente.</span><span class="sxs-lookup"><span data-stu-id="0fc28-108">The identifier is unique only in the scope of the containing process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0fc28-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0fc28-109">Requirements</span></span>  
 <span data-ttu-id="0fc28-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0fc28-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0fc28-111">**Cabeçalho:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="0fc28-111">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="0fc28-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0fc28-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0fc28-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0fc28-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fc28-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0fc28-114">See also</span></span>

- [<span data-ttu-id="0fc28-115">Interface ICorPublishAppDomain</span><span class="sxs-lookup"><span data-stu-id="0fc28-115">ICorPublishAppDomain Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)
