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
ms.openlocfilehash: 8642c165c29f9ca63535a0efbb9dbb58d4660a49
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59160388"
---
# <a name="coinitializecor-function"></a><span data-ttu-id="2b100-102">Função CoInitializeCor</span><span class="sxs-lookup"><span data-stu-id="2b100-102">CoInitializeCor Function</span></span>
`CoInitializeCor` <span data-ttu-id="2b100-103">é obsoleto.</span><span class="sxs-lookup"><span data-stu-id="2b100-103">is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b100-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2b100-104">Syntax</span></span>  
  
```  
STDAPI CoInitializeCor (  
    DWORD fFlags  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="2b100-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="2b100-105">Remarks</span></span>  
 <span data-ttu-id="2b100-106">Para inicializar o common language runtime, use [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) ou [CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md).</span><span class="sxs-lookup"><span data-stu-id="2b100-106">To initialize the common language runtime, use either [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) or [CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b100-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2b100-107">Requirements</span></span>  
 <span data-ttu-id="2b100-108">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="2b100-108">**Header:** Cor.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b100-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2b100-109">See also</span></span>

- [<span data-ttu-id="2b100-110">Funções estáticas globais de metadados</span><span class="sxs-lookup"><span data-stu-id="2b100-110">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
