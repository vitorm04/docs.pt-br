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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c14d364320c82f061ef606a402563dacfce28139
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59186232"
---
# <a name="icorpublishappdomainenumnext-method"></a><span data-ttu-id="5af2b-102">Método ICorPublishAppDomainEnum::Next</span><span class="sxs-lookup"><span data-stu-id="5af2b-102">ICorPublishAppDomainEnum::Next Method</span></span>
<span data-ttu-id="5af2b-103">Obtém o número especificado de domínios de aplicativo que existem atualmente no processo, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="5af2b-103">Gets the specified number of application domains that currently exist in the process, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5af2b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5af2b-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]   
        ICorPublishAppDomain **objects,  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5af2b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5af2b-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="5af2b-106">[in] O número de elementos a serem recuperados.</span><span class="sxs-lookup"><span data-stu-id="5af2b-106">[in] The number of elements to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="5af2b-107">[out] Um ponteiro para a matriz de recuperados [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md) objetos, cada um deles representa um domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5af2b-107">[out] A pointer to the array of retrieved [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md) objects, each of which represents an application domain.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="5af2b-108">[out] Ponteiro para o número de domínios de aplicativo, na verdade, é retornado.</span><span class="sxs-lookup"><span data-stu-id="5af2b-108">[out] Pointer to the number of application domains actually returned.</span></span> <span data-ttu-id="5af2b-109">Esse valor pode ser nulo se `celt` é um.</span><span class="sxs-lookup"><span data-stu-id="5af2b-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5af2b-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5af2b-110">Requirements</span></span>  
 <span data-ttu-id="5af2b-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5af2b-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5af2b-112">**Cabeçalho:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="5af2b-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="5af2b-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5af2b-113">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="5af2b-114">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="5af2b-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5af2b-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5af2b-115">See also</span></span>

- [<span data-ttu-id="5af2b-116">Interface ICorPublishAppDomainEnum</span><span class="sxs-lookup"><span data-stu-id="5af2b-116">ICorPublishAppDomainEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)
