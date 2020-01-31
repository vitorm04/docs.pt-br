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
ms.openlocfilehash: 8d6e130981693268ae5c2cd615036b84ca8ed2d8
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790693"
---
# <a name="icorpublishappdomaingetid-method"></a><span data-ttu-id="8a10c-102">Método ICorPublishAppDomain::GetID</span><span class="sxs-lookup"><span data-stu-id="8a10c-102">ICorPublishAppDomain::GetID Method</span></span>
<span data-ttu-id="8a10c-103">Obtém o identificador exclusivo para este [ICorPublishAppDomain](icorpublishappdomain-interface.md).</span><span class="sxs-lookup"><span data-stu-id="8a10c-103">Gets the unique identifier for this [ICorPublishAppDomain](icorpublishappdomain-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a10c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8a10c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetID (  
    [out] ULONG32   *puId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8a10c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8a10c-105">Parameters</span></span>  
 `puId`  
 <span data-ttu-id="8a10c-106">fora Um ponteiro para o identificador do domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8a10c-106">[out] A pointer to the identifier of the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8a10c-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="8a10c-107">Remarks</span></span>  
 <span data-ttu-id="8a10c-108">O identificador é exclusivo somente no escopo do processo que o contém.</span><span class="sxs-lookup"><span data-stu-id="8a10c-108">The identifier is unique only in the scope of the containing process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a10c-109">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="8a10c-109">Requirements</span></span>  
 <span data-ttu-id="8a10c-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a10c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a10c-111">**Cabeçalho:** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="8a10c-111">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="8a10c-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8a10c-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8a10c-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a10c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a10c-114">Veja também</span><span class="sxs-lookup"><span data-stu-id="8a10c-114">See also</span></span>

- [<span data-ttu-id="8a10c-115">Interface ICorPublishAppDomain</span><span class="sxs-lookup"><span data-stu-id="8a10c-115">ICorPublishAppDomain Interface</span></span>](icorpublishappdomain-interface.md)
