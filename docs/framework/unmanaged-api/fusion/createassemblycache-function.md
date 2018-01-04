---
title: "Função CreateAssemblyCache"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CreateAssemblyCache
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type: DLLExport
f1_keywords: CreateAssemblyCache
helpviewer_keywords: CreateAssemblyCache function [.NET Framework fusion]
ms.assetid: 348c7c8c-8578-46ae-97cf-480d6015c3c6
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5e730ea9f83a40d92cb6a865fcdd87ebf523fe7c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="createassemblycache-function"></a><span data-ttu-id="186aa-102">Função CreateAssemblyCache</span><span class="sxs-lookup"><span data-stu-id="186aa-102">CreateAssemblyCache Function</span></span>
<span data-ttu-id="186aa-103">Obtém um ponteiro para um novo [IAssemblyCache](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md) instância que representa o cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="186aa-103">Gets a pointer to a new [IAssemblyCache](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md) instance that represents the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="186aa-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="186aa-104">Syntax</span></span>  
  
```  
HRESULT CreateAssemblyCache (  
    [out] IAssemblyCache  **ppAsmCache,  
    [in]  DWORD           dwReserved  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="186aa-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="186aa-105">Parameters</span></span>  
 `ppAsmCache`  
 <span data-ttu-id="186aa-106">[out] Retornado `IAssemblyCache` ponteiro.</span><span class="sxs-lookup"><span data-stu-id="186aa-106">[out] The returned `IAssemblyCache` pointer.</span></span>  
  
 `dwReserved`  
 <span data-ttu-id="186aa-107">[in] Reservado para extensibilidade futura.</span><span class="sxs-lookup"><span data-stu-id="186aa-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="186aa-108">`dwReserved`deve ser 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="186aa-108">`dwReserved` must be 0 (zero).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="186aa-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="186aa-109">Requirements</span></span>  
 <span data-ttu-id="186aa-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="186aa-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="186aa-111">**Cabeçalho:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="186aa-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="186aa-112">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="186aa-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="186aa-113">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="186aa-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="186aa-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="186aa-114">See Also</span></span>  
 [<span data-ttu-id="186aa-115">Interface IAssemblyCache</span><span class="sxs-lookup"><span data-stu-id="186aa-115">IAssemblyCache Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)  
 [<span data-ttu-id="186aa-116">Funções estáticas globais de fusão</span><span class="sxs-lookup"><span data-stu-id="186aa-116">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)  
 [<span data-ttu-id="186aa-117">Cache de assembly global</span><span class="sxs-lookup"><span data-stu-id="186aa-117">Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/gac.md)
