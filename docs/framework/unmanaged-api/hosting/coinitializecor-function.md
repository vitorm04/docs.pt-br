---
title: Função CoInitializeCor
ms.date: 03/30/2017
api_name:
- CoInitializeCor
api_location:
- mscoree.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CoInitializeCor
helpviewer_keywords:
- CoInitializeCor function [.NET Framework hosting]
ms.assetid: 9b9079fb-579e-4141-b3f0-791072dd40dc
topic_type:
- apiref
ms.openlocfilehash: 188f98504fa73c4a85615a4e688bae02d966b9b6
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616743"
---
# <a name="coinitializecor-function"></a><span data-ttu-id="fe48e-102">Função CoInitializeCor</span><span class="sxs-lookup"><span data-stu-id="fe48e-102">CoInitializeCor Function</span></span>
<span data-ttu-id="fe48e-103">`CoInitializeCor` é obsoleto.</span><span class="sxs-lookup"><span data-stu-id="fe48e-103">`CoInitializeCor` is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe48e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fe48e-104">Syntax</span></span>  
  
```cpp  
STDAPI CoInitializeCor (  
    DWORD fFlags  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="fe48e-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="fe48e-105">Remarks</span></span>  
 <span data-ttu-id="fe48e-106">Para inicializar o Common Language Runtime, use [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) ou [CorBindToCurrentRuntime](corbindtocurrentruntime-function.md).</span><span class="sxs-lookup"><span data-stu-id="fe48e-106">To initialize the common language runtime, use either [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) or [CorBindToCurrentRuntime](corbindtocurrentruntime-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe48e-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fe48e-107">Requirements</span></span>  
 <span data-ttu-id="fe48e-108">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="fe48e-108">**Header:** Cor.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe48e-109">Veja também</span><span class="sxs-lookup"><span data-stu-id="fe48e-109">See also</span></span>

- [<span data-ttu-id="fe48e-110">Funções estáticas globais de metadados</span><span class="sxs-lookup"><span data-stu-id="fe48e-110">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)
