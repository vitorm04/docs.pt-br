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
ms.openlocfilehash: ca2d7fe73fc749296f76e18ecce75b7fdd0795d3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54585585"
---
# <a name="iassemblynamesetproperty-method"></a><span data-ttu-id="0f92a-102">Método IAssemblyName::SetProperty</span><span class="sxs-lookup"><span data-stu-id="0f92a-102">IAssemblyName::SetProperty Method</span></span>
<span data-ttu-id="0f92a-103">Define o valor da propriedade referenciada pelo identificador de propriedade especificado.</span><span class="sxs-lookup"><span data-stu-id="0f92a-103">Sets the value of the property referenced by the specified property identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f92a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0f92a-104">Syntax</span></span>  
  
```  
HRESULT SetProperty (  
    [in] DWORD  PropertyId,  
    [in] LPVOID pvProperty,  
    [in] DWORD  cbProperty  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0f92a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0f92a-105">Parameters</span></span>  
 `PropertyId`  
 <span data-ttu-id="0f92a-106">[in] O identificador exclusivo da propriedade cujo valor será definido.</span><span class="sxs-lookup"><span data-stu-id="0f92a-106">[in] The unique identifier of the property whose value will be set.</span></span>  
  
 `pvProperty`  
 <span data-ttu-id="0f92a-107">[in] O valor para o qual definir a propriedade referenciada por `PropertyId`.</span><span class="sxs-lookup"><span data-stu-id="0f92a-107">[in] The value to which to set the property referenced by `PropertyId`.</span></span>  
  
 `cbProperty`  
 <span data-ttu-id="0f92a-108">[in] O tamanho, em bytes, do `pvProperty`.</span><span class="sxs-lookup"><span data-stu-id="0f92a-108">[in] The size, in bytes, of `pvProperty`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f92a-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0f92a-109">Requirements</span></span>  
 <span data-ttu-id="0f92a-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0f92a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f92a-111">**Cabeçalho:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="0f92a-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="0f92a-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f92a-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f92a-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0f92a-113">See also</span></span>
- [<span data-ttu-id="0f92a-114">Interface IAssemblyName</span><span class="sxs-lookup"><span data-stu-id="0f92a-114">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
