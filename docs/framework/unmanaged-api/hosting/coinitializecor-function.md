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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 556d26ac7e4fb8847f132d19bd2e749aff345abf
ms.sourcegitcommit: 79066169e93d9d65203028b21983574ad9dcf6b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57211839"
---
# <a name="coinitializecor-function"></a><span data-ttu-id="a84c3-102">Função CoInitializeCor</span><span class="sxs-lookup"><span data-stu-id="a84c3-102">CoInitializeCor Function</span></span>
<span data-ttu-id="a84c3-103">`CoInitializeCor` é obsoleto.</span><span class="sxs-lookup"><span data-stu-id="a84c3-103">`CoInitializeCor` is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a84c3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a84c3-104">Syntax</span></span>  
  
```  
STDAPI CoInitializeCor (  
    DWORD fFlags  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="a84c3-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="a84c3-105">Remarks</span></span>  
 <span data-ttu-id="a84c3-106">Para inicializar o common language runtime, use [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) ou [CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md).</span><span class="sxs-lookup"><span data-stu-id="a84c3-106">To initialize the common language runtime, use either [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) or [CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a84c3-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a84c3-107">Requirements</span></span>  
 <span data-ttu-id="a84c3-108">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a84c3-108">**Header:** Cor.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a84c3-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a84c3-109">See also</span></span>
- [<span data-ttu-id="a84c3-110">Funções estáticas globais de metadados</span><span class="sxs-lookup"><span data-stu-id="a84c3-110">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
