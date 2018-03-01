---
title: "Método IAssemblyName::SetProperty"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IAssemblyName.SetProperty
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::SetProperty
helpviewer_keywords:
- IAssemblyName::SetProperty method [.NET Framework fusion]
- SetProperty method [.NET Framework fusion]
ms.assetid: 496c3add-f60b-4073-943f-d1bcf33330cb
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 60ef27021ec3431c90086e0dfbae56bb6e6ccc86
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="iassemblynamesetproperty-method"></a><span data-ttu-id="3ef24-102">Método IAssemblyName::SetProperty</span><span class="sxs-lookup"><span data-stu-id="3ef24-102">IAssemblyName::SetProperty Method</span></span>
<span data-ttu-id="3ef24-103">Define o valor da propriedade referenciada pelo identificador de propriedade especificado.</span><span class="sxs-lookup"><span data-stu-id="3ef24-103">Sets the value of the property referenced by the specified property identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ef24-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3ef24-104">Syntax</span></span>  
  
```  
HRESULT SetProperty (  
    [in] DWORD  PropertyId,  
    [in] LPVOID pvProperty,  
    [in] DWORD  cbProperty  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3ef24-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3ef24-105">Parameters</span></span>  
 `PropertyId`  
 <span data-ttu-id="3ef24-106">[in] O identificador exclusivo da propriedade cujo valor será definido.</span><span class="sxs-lookup"><span data-stu-id="3ef24-106">[in] The unique identifier of the property whose value will be set.</span></span>  
  
 `pvProperty`  
 <span data-ttu-id="3ef24-107">[in] O valor para o qual definir a propriedade referenciada por `PropertyId`.</span><span class="sxs-lookup"><span data-stu-id="3ef24-107">[in] The value to which to set the property referenced by `PropertyId`.</span></span>  
  
 `cbProperty`  
 <span data-ttu-id="3ef24-108">[in] O tamanho, em bytes, de `pvProperty`.</span><span class="sxs-lookup"><span data-stu-id="3ef24-108">[in] The size, in bytes, of `pvProperty`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3ef24-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3ef24-109">Requirements</span></span>  
 <span data-ttu-id="3ef24-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3ef24-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ef24-111">**Cabeçalho:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="3ef24-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="3ef24-112">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3ef24-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ef24-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3ef24-113">See Also</span></span>  
 [<span data-ttu-id="3ef24-114">Interface IAssemblyName</span><span class="sxs-lookup"><span data-stu-id="3ef24-114">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
