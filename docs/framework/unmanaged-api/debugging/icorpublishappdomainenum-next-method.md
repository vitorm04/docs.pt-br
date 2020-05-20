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
ms.openlocfilehash: c5ac38005410ae6ed9c2f4160e926987791ad604
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421209"
---
# <a name="icorpublishappdomainenumnext-method"></a><span data-ttu-id="e5874-102">Método ICorPublishAppDomainEnum::Next</span><span class="sxs-lookup"><span data-stu-id="e5874-102">ICorPublishAppDomainEnum::Next Method</span></span>
<span data-ttu-id="e5874-103">Obtém o número especificado de domínios de aplicativo que existem atualmente no processo, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="e5874-103">Gets the specified number of application domains that currently exist in the process, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5874-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e5874-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]
        ICorPublishAppDomain **objects,  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e5874-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e5874-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="e5874-106">no O número de elementos a serem recuperados.</span><span class="sxs-lookup"><span data-stu-id="e5874-106">[in] The number of elements to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="e5874-107">fora Um ponteiro para a matriz de objetos [ICorPublishAppDomain](icorpublishappdomain-interface.md) recuperados, cada um representando um domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e5874-107">[out] A pointer to the array of retrieved [ICorPublishAppDomain](icorpublishappdomain-interface.md) objects, each of which represents an application domain.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="e5874-108">fora Aponta para o número de domínios de aplicativo realmente retornados.</span><span class="sxs-lookup"><span data-stu-id="e5874-108">[out] Pointer to the number of application domains actually returned.</span></span> <span data-ttu-id="e5874-109">Esse valor pode ser nulo se `celt` for um.</span><span class="sxs-lookup"><span data-stu-id="e5874-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5874-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e5874-110">Requirements</span></span>  
 <span data-ttu-id="e5874-111">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5874-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5874-112">**Cabeçalho:** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="e5874-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="e5874-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e5874-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e5874-114">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5874-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5874-115">Veja também</span><span class="sxs-lookup"><span data-stu-id="e5874-115">See also</span></span>

- [<span data-ttu-id="e5874-116">Interface ICorPublishAppDomainEnum</span><span class="sxs-lookup"><span data-stu-id="e5874-116">ICorPublishAppDomainEnum Interface</span></span>](icorpublishappdomainenum-interface.md)
