---
title: Método ICorPublishAppDomainEnum::Next
ms.date: 03/30/2017
api_name:
- ICorPublishAppDomainEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishAppDomainEnum::Next
helpviewer_keywords:
- Next method, ICorPublishAppDomainEnum interface [.NET Framework debugging]
- ICorPublishAppDomainEnum::Next method [.NET Framework debugging]
ms.assetid: ad37cd10-0339-4d08-9b0e-4b3428bb4dc3
topic_type:
- apiref
ms.openlocfilehash: 0553d8b07e3a16dc31474b5470ba2dd8ba365cb2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140506"
---
# <a name="icorpublishappdomainenumnext-method"></a><span data-ttu-id="7891d-102">Método ICorPublishAppDomainEnum::Next</span><span class="sxs-lookup"><span data-stu-id="7891d-102">ICorPublishAppDomainEnum::Next Method</span></span>
<span data-ttu-id="7891d-103">Obtém o número especificado de domínios de aplicativo que existem atualmente no processo, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="7891d-103">Gets the specified number of application domains that currently exist in the process, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7891d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7891d-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]   
        ICorPublishAppDomain **objects,  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7891d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7891d-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="7891d-106">no O número de elementos a serem recuperados.</span><span class="sxs-lookup"><span data-stu-id="7891d-106">[in] The number of elements to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="7891d-107">fora Um ponteiro para a matriz de objetos [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md) recuperados, cada um representando um domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7891d-107">[out] A pointer to the array of retrieved [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md) objects, each of which represents an application domain.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="7891d-108">fora Aponta para o número de domínios de aplicativo realmente retornados.</span><span class="sxs-lookup"><span data-stu-id="7891d-108">[out] Pointer to the number of application domains actually returned.</span></span> <span data-ttu-id="7891d-109">Esse valor pode ser nulo se `celt` for um.</span><span class="sxs-lookup"><span data-stu-id="7891d-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7891d-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7891d-110">Requirements</span></span>  
 <span data-ttu-id="7891d-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7891d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7891d-112">**Cabeçalho:** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="7891d-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="7891d-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7891d-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7891d-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7891d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7891d-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7891d-115">See also</span></span>

- [<span data-ttu-id="7891d-116">Interface ICorPublishAppDomainEnum</span><span class="sxs-lookup"><span data-stu-id="7891d-116">ICorPublishAppDomainEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)
