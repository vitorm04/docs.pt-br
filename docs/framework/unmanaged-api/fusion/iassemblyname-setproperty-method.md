---
title: Método IAssemblyName::SetProperty
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cbb04a97597982fdae7a68ba4f3ed4d7420b4189
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57488143"
---
# <a name="iassemblynamesetproperty-method"></a><span data-ttu-id="9f4e0-102">Método IAssemblyName::SetProperty</span><span class="sxs-lookup"><span data-stu-id="9f4e0-102">IAssemblyName::SetProperty Method</span></span>
<span data-ttu-id="9f4e0-103">Define o valor da propriedade referenciada pelo identificador de propriedade especificado.</span><span class="sxs-lookup"><span data-stu-id="9f4e0-103">Sets the value of the property referenced by the specified property identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f4e0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9f4e0-104">Syntax</span></span>  
  
```  
HRESULT SetProperty (  
    [in] DWORD  PropertyId,  
    [in] LPVOID pvProperty,  
    [in] DWORD  cbProperty  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9f4e0-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9f4e0-105">Parameters</span></span>  
 `PropertyId`  
 <span data-ttu-id="9f4e0-106">[in] O identificador exclusivo da propriedade cujo valor será definido.</span><span class="sxs-lookup"><span data-stu-id="9f4e0-106">[in] The unique identifier of the property whose value will be set.</span></span>  
  
 `pvProperty`  
 <span data-ttu-id="9f4e0-107">[in] O valor para o qual definir a propriedade referenciada por `PropertyId`.</span><span class="sxs-lookup"><span data-stu-id="9f4e0-107">[in] The value to which to set the property referenced by `PropertyId`.</span></span>  
  
 `cbProperty`  
 <span data-ttu-id="9f4e0-108">[in] O tamanho, em bytes, do `pvProperty`.</span><span class="sxs-lookup"><span data-stu-id="9f4e0-108">[in] The size, in bytes, of `pvProperty`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f4e0-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9f4e0-109">Requirements</span></span>  
 <span data-ttu-id="9f4e0-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9f4e0-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f4e0-111">**Cabeçalho:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="9f4e0-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="9f4e0-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9f4e0-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f4e0-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9f4e0-113">See also</span></span>
- [<span data-ttu-id="9f4e0-114">Interface IAssemblyName</span><span class="sxs-lookup"><span data-stu-id="9f4e0-114">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
