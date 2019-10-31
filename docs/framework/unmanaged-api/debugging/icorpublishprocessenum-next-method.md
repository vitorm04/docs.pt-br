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
ms.openlocfilehash: d79b642735543ff84f6211fe5ca2e5b424be1f2e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73103440"
---
# <a name="icorpublishprocessenumnext-method"></a><span data-ttu-id="3a98b-102">Método ICorPublishProcessEnum::Next</span><span class="sxs-lookup"><span data-stu-id="3a98b-102">ICorPublishProcessEnum::Next Method</span></span>
<span data-ttu-id="3a98b-103">Obtém o número especificado de processos da coleção, começando na posição atual do cursor.</span><span class="sxs-lookup"><span data-stu-id="3a98b-103">Gets the specified number of processes from the collection, starting at the current cursor position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a98b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3a98b-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorPublishProcess **objects,  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3a98b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3a98b-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="3a98b-106">no O número de processos a serem recuperados.</span><span class="sxs-lookup"><span data-stu-id="3a98b-106">[in] The number of processes to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="3a98b-107">fora Um ponteiro para a matriz de objetos [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) recuperados, cada um deles representa um processo.</span><span class="sxs-lookup"><span data-stu-id="3a98b-107">[out] A pointer to the array of retrieved [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) objects, each of which represents a process.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="3a98b-108">fora Aponta para o número de processos realmente retornados.</span><span class="sxs-lookup"><span data-stu-id="3a98b-108">[out] Pointer to the number of processes actually returned.</span></span> <span data-ttu-id="3a98b-109">Esse valor pode ser nulo se `celt` for um.</span><span class="sxs-lookup"><span data-stu-id="3a98b-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a98b-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3a98b-110">Requirements</span></span>  
 <span data-ttu-id="3a98b-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3a98b-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a98b-112">**Cabeçalho:** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="3a98b-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="3a98b-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3a98b-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3a98b-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a98b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a98b-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3a98b-115">See also</span></span>

- [<span data-ttu-id="3a98b-116">Interface ICorPublishProcessEnum</span><span class="sxs-lookup"><span data-stu-id="3a98b-116">ICorPublishProcessEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)
