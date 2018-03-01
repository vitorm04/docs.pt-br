---
title: "Método ICorPublishAppDomainEnum::Next"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7c9823c0e4a471a398285c5960f3ce7bfc60fb23
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icorpublishappdomainenumnext-method"></a><span data-ttu-id="f436f-102">Método ICorPublishAppDomainEnum::Next</span><span class="sxs-lookup"><span data-stu-id="f436f-102">ICorPublishAppDomainEnum::Next Method</span></span>
<span data-ttu-id="f436f-103">Obtém o número especificado de domínios de aplicativo que existem atualmente no processo, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="f436f-103">Gets the specified number of application domains that currently exist in the process, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f436f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f436f-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]   
        ICorPublishAppDomain **objects,  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f436f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f436f-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="f436f-106">[in] O número de elementos a serem recuperados.</span><span class="sxs-lookup"><span data-stu-id="f436f-106">[in] The number of elements to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="f436f-107">[out] Um ponteiro para a matriz de recuperados [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md) objetos, cada um deles representa um domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f436f-107">[out] A pointer to the array of retrieved [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md) objects, each of which represents an application domain.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="f436f-108">[out] Ponteiro para o número de domínios de aplicativo, na verdade, retornadas.</span><span class="sxs-lookup"><span data-stu-id="f436f-108">[out] Pointer to the number of application domains actually returned.</span></span> <span data-ttu-id="f436f-109">Esse valor pode ser null se `celt` é um.</span><span class="sxs-lookup"><span data-stu-id="f436f-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f436f-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f436f-110">Requirements</span></span>  
 <span data-ttu-id="f436f-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f436f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f436f-112">**Cabeçalho:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="f436f-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="f436f-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f436f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f436f-114">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f436f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f436f-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f436f-115">See Also</span></span>  
 [<span data-ttu-id="f436f-116">Interface ICorPublishAppDomainEnum</span><span class="sxs-lookup"><span data-stu-id="f436f-116">ICorPublishAppDomainEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)
