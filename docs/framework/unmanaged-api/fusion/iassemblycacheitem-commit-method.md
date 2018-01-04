---
title: "Método IAssemblyCacheItem::Commit"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IAssemblyCacheItem.Commit
api_location: fusion.dll
api_type: COM
f1_keywords: IAssemblyCacheItem::Commit
helpviewer_keywords:
- IAssemblyCacheItem::Commit method [.NET Framework fusion]
- Commit method, IAssemblyCacheItem interface [.NET Framework fusion]
ms.assetid: c2321f17-f46f-4815-ae41-b28678753613
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3e1907fa3be4992573f84b4810f7504f3af78397
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="iassemblycacheitemcommit-method"></a><span data-ttu-id="4a563-102">Método IAssemblyCacheItem::Commit</span><span class="sxs-lookup"><span data-stu-id="4a563-102">IAssemblyCacheItem::Commit Method</span></span>
<span data-ttu-id="4a563-103">Confirma a referência de assembly em cache na memória.</span><span class="sxs-lookup"><span data-stu-id="4a563-103">Commits the cached assembly reference to memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a563-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4a563-104">Syntax</span></span>  
  
```  
HRESULT Commit (  
    [in] DWORD dwFlags,   
    [out, optional] ULONG *pulDisposition  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4a563-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4a563-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="4a563-106">[in] Sinalizadores definidos no Fusion.idl.</span><span class="sxs-lookup"><span data-stu-id="4a563-106">[in] Flags defined in Fusion.idl.</span></span>  
  
 `pulDisposition`  
 <span data-ttu-id="4a563-107">[out, opcional] Um valor que indica o resultado da operação.</span><span class="sxs-lookup"><span data-stu-id="4a563-107">[out, optional] A value that indicates the result of the operation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a563-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4a563-108">Requirements</span></span>  
 <span data-ttu-id="4a563-109">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a563-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a563-110">**Cabeçalho:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="4a563-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="4a563-111">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a563-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a563-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4a563-112">See Also</span></span>  
 [<span data-ttu-id="4a563-113">Interface IAssemblyCacheItem</span><span class="sxs-lookup"><span data-stu-id="4a563-113">IAssemblyCacheItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)
