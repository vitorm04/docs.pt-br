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
ms.openlocfilehash: 6f7f400c51ded0b98c0c2286cb6f90bbd77e47d7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178392"
---
# <a name="icorpublishappdomainenumnext-method"></a><span data-ttu-id="94a02-102">Método ICorPublishAppDomainEnum::Next</span><span class="sxs-lookup"><span data-stu-id="94a02-102">ICorPublishAppDomainEnum::Next Method</span></span>
<span data-ttu-id="94a02-103">Obtém o número especificado de domínios de aplicativos que existem atualmente no processo, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="94a02-103">Gets the specified number of application domains that currently exist in the process, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94a02-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="94a02-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]
        ICorPublishAppDomain **objects,  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="94a02-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="94a02-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="94a02-106">[em] O número de elementos a serem recuperados.</span><span class="sxs-lookup"><span data-stu-id="94a02-106">[in] The number of elements to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="94a02-107">[fora] Um ponteiro para a matriz de objetos [ICorPublishAppDomain](icorpublishappdomain-interface.md) recuperados, cada um dos quais representa um domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="94a02-107">[out] A pointer to the array of retrieved [ICorPublishAppDomain](icorpublishappdomain-interface.md) objects, each of which represents an application domain.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="94a02-108">[fora] Ponteiro para o número de domínios do aplicativo realmente retornado.</span><span class="sxs-lookup"><span data-stu-id="94a02-108">[out] Pointer to the number of application domains actually returned.</span></span> <span data-ttu-id="94a02-109">Este valor pode `celt` ser nulo se for um.</span><span class="sxs-lookup"><span data-stu-id="94a02-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94a02-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="94a02-110">Requirements</span></span>  
 <span data-ttu-id="94a02-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="94a02-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94a02-112">**Cabeçalho:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="94a02-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="94a02-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="94a02-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="94a02-114">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94a02-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94a02-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="94a02-115">See also</span></span>

- [<span data-ttu-id="94a02-116">Interface ICorPublishAppDomainEnum</span><span class="sxs-lookup"><span data-stu-id="94a02-116">ICorPublishAppDomainEnum Interface</span></span>](icorpublishappdomainenum-interface.md)
