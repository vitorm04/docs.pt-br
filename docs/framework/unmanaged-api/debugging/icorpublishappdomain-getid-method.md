---
title: "Método ICorPublishAppDomain::GetID"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorPublishAppDomain.GetID
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorPublishAppDomain::GetID
helpviewer_keywords:
- GetID method, ICorPublishAppDomain interface [.NET Framework debugging]
- ICorPublishAppDomain::GetID method [.NET Framework debugging]
ms.assetid: 229437e3-1465-4bd8-8846-9804b2488133
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bfbde806f409f2639b2468e0ba962b1659d1ffc3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icorpublishappdomaingetid-method"></a><span data-ttu-id="11916-102">Método ICorPublishAppDomain::GetID</span><span class="sxs-lookup"><span data-stu-id="11916-102">ICorPublishAppDomain::GetID Method</span></span>
<span data-ttu-id="11916-103">Obtém o identificador exclusivo para este [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md).</span><span class="sxs-lookup"><span data-stu-id="11916-103">Gets the unique identifier for this [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11916-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="11916-104">Syntax</span></span>  
  
```  
HRESULT GetID (  
    [out] ULONG32   *puId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="11916-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="11916-105">Parameters</span></span>  
 `puId`  
 <span data-ttu-id="11916-106">[out] Um ponteiro para o identificador do domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="11916-106">[out] A pointer to the identifier of the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="11916-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="11916-107">Remarks</span></span>  
 <span data-ttu-id="11916-108">O identificador é exclusivo somente no escopo do processo de recipiente.</span><span class="sxs-lookup"><span data-stu-id="11916-108">The identifier is unique only in the scope of the containing process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11916-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="11916-109">Requirements</span></span>  
 <span data-ttu-id="11916-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="11916-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11916-111">**Cabeçalho:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="11916-111">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="11916-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="11916-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="11916-113">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11916-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11916-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="11916-114">See Also</span></span>  
 [<span data-ttu-id="11916-115">Interface ICorPublishAppDomain</span><span class="sxs-lookup"><span data-stu-id="11916-115">ICorPublishAppDomain Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)
