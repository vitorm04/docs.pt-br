---
title: Método IAssemblyCacheItem::Commit
ms.date: 03/30/2017
api_name:
- IAssemblyCacheItem.Commit
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCacheItem::Commit
helpviewer_keywords:
- IAssemblyCacheItem::Commit method [.NET Framework fusion]
- Commit method, IAssemblyCacheItem interface [.NET Framework fusion]
ms.assetid: c2321f17-f46f-4815-ae41-b28678753613
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9b39cdec6d5cc10256c2911c98f94b7565295408
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54537992"
---
# <a name="iassemblycacheitemcommit-method"></a><span data-ttu-id="708f8-102">Método IAssemblyCacheItem::Commit</span><span class="sxs-lookup"><span data-stu-id="708f8-102">IAssemblyCacheItem::Commit Method</span></span>
<span data-ttu-id="708f8-103">Confirma a referência de assembly em cache na memória.</span><span class="sxs-lookup"><span data-stu-id="708f8-103">Commits the cached assembly reference to memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="708f8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="708f8-104">Syntax</span></span>  
  
```  
HRESULT Commit (  
    [in] DWORD dwFlags,   
    [out, optional] ULONG *pulDisposition  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="708f8-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="708f8-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="708f8-106">[in] Sinalizadores definidos no Fusion.idl.</span><span class="sxs-lookup"><span data-stu-id="708f8-106">[in] Flags defined in Fusion.idl.</span></span>  
  
 `pulDisposition`  
 <span data-ttu-id="708f8-107">[out, opcional] Um valor que indica o resultado da operação.</span><span class="sxs-lookup"><span data-stu-id="708f8-107">[out, optional] A value that indicates the result of the operation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="708f8-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="708f8-108">Requirements</span></span>  
 <span data-ttu-id="708f8-109">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="708f8-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="708f8-110">**Cabeçalho:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="708f8-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="708f8-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="708f8-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="708f8-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="708f8-112">See also</span></span>
- [<span data-ttu-id="708f8-113">Interface IAssemblyCacheItem</span><span class="sxs-lookup"><span data-stu-id="708f8-113">IAssemblyCacheItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)
