---
title: Método ICorPublishProcessEnum::Next
ms.date: 03/30/2017
api_name:
- ICorPublishProcessEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcessEnum::Next
helpviewer_keywords:
- ICorPublishProcessEnum::Next method [.NET Framework debugging]
- Next method, ICorPublishProcessEnum interface [.NET Framework debugging]
ms.assetid: 6c399f37-1e38-4ca1-b70d-8ae41f7228b7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b39e0b85b80618afed80d65430ba18cb1128352d
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466694"
---
# <a name="icorpublishprocessenumnext-method"></a><span data-ttu-id="cbe3a-102">Método ICorPublishProcessEnum::Next</span><span class="sxs-lookup"><span data-stu-id="cbe3a-102">ICorPublishProcessEnum::Next Method</span></span>
<span data-ttu-id="cbe3a-103">Obtém o número de processos especificado da coleção, começando na posição atual do cursor.</span><span class="sxs-lookup"><span data-stu-id="cbe3a-103">Gets the specified number of processes from the collection, starting at the current cursor position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cbe3a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cbe3a-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorPublishProcess **objects,  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cbe3a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cbe3a-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="cbe3a-106">[in] O número de processos a serem recuperados.</span><span class="sxs-lookup"><span data-stu-id="cbe3a-106">[in] The number of processes to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="cbe3a-107">[out] Um ponteiro para a matriz de recuperados [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) objetos, cada um deles representa um processo.</span><span class="sxs-lookup"><span data-stu-id="cbe3a-107">[out] A pointer to the array of retrieved [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) objects, each of which represents a process.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="cbe3a-108">[out] Ponteiro para o número de processos, na verdade, é retornado.</span><span class="sxs-lookup"><span data-stu-id="cbe3a-108">[out] Pointer to the number of processes actually returned.</span></span> <span data-ttu-id="cbe3a-109">Esse valor pode ser nulo se `celt` é um.</span><span class="sxs-lookup"><span data-stu-id="cbe3a-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cbe3a-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cbe3a-110">Requirements</span></span>  
 <span data-ttu-id="cbe3a-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cbe3a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cbe3a-112">**Cabeçalho:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="cbe3a-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="cbe3a-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cbe3a-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cbe3a-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cbe3a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbe3a-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cbe3a-115">See also</span></span>
- [<span data-ttu-id="cbe3a-116">Interface ICorPublishProcessEnum</span><span class="sxs-lookup"><span data-stu-id="cbe3a-116">ICorPublishProcessEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)
