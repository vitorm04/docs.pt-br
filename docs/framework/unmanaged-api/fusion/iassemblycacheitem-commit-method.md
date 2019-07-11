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
ms.openlocfilehash: 6d1f5988266fcbfc18ee937b6e7fdb1829646fa9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778681"
---
# <a name="iassemblycacheitemcommit-method"></a><span data-ttu-id="c7817-102">Método IAssemblyCacheItem::Commit</span><span class="sxs-lookup"><span data-stu-id="c7817-102">IAssemblyCacheItem::Commit Method</span></span>
<span data-ttu-id="c7817-103">Confirma a referência de assembly em cache na memória.</span><span class="sxs-lookup"><span data-stu-id="c7817-103">Commits the cached assembly reference to memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7817-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c7817-104">Syntax</span></span>  
  
```cpp  
HRESULT Commit (  
    [in] DWORD dwFlags,   
    [out, optional] ULONG *pulDisposition  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c7817-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c7817-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="c7817-106">[in] Sinalizadores definidos no Fusion.idl.</span><span class="sxs-lookup"><span data-stu-id="c7817-106">[in] Flags defined in Fusion.idl.</span></span>  
  
 `pulDisposition`  
 <span data-ttu-id="c7817-107">[out, opcional] Um valor que indica o resultado da operação.</span><span class="sxs-lookup"><span data-stu-id="c7817-107">[out, optional] A value that indicates the result of the operation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7817-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c7817-108">Requirements</span></span>  
 <span data-ttu-id="c7817-109">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7817-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7817-110">**Cabeçalho:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="c7817-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="c7817-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7817-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7817-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c7817-112">See also</span></span>

- [<span data-ttu-id="c7817-113">Interface IAssemblyCacheItem</span><span class="sxs-lookup"><span data-stu-id="c7817-113">IAssemblyCacheItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)
