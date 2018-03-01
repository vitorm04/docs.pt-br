---
title: "Método IAssemblyName::GetProperty"
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
- IAssemblyName.GetProperty
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::GetProperty
helpviewer_keywords:
- IAssemblyName::GetProperty method [.NET Framework fusion]
- GetProperty method [.NET Framework fusion]
ms.assetid: e59fda62-77d5-4e37-89cb-ce7ae4627975
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3311cc79cd010f59d707283fa555a2ebf66e53db
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="iassemblynamegetproperty-method"></a><span data-ttu-id="68692-102">Método IAssemblyName::GetProperty</span><span class="sxs-lookup"><span data-stu-id="68692-102">IAssemblyName::GetProperty Method</span></span>
<span data-ttu-id="68692-103">Obtém um ponteiro para a propriedade referenciada pelo identificador de propriedade especificado.</span><span class="sxs-lookup"><span data-stu-id="68692-103">Gets a pointer to the property referenced by the specified property identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68692-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="68692-104">Syntax</span></span>  
  
```  
HRESULT GetProperty (  
    [in]      DWORD    PropertyId,  
    [out]     LPVOID   pvProperty,  
    [in, out] LPDWORD  pcbProperty  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="68692-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="68692-105">Parameters</span></span>  
 `PropertyId`  
 <span data-ttu-id="68692-106">[in] O identificador exclusivo para a propriedade solicitada.</span><span class="sxs-lookup"><span data-stu-id="68692-106">[in] The unique identifier for the requested property.</span></span>  
  
 `pvProperty`  
 <span data-ttu-id="68692-107">[out] Os dados de propriedade retornado.</span><span class="sxs-lookup"><span data-stu-id="68692-107">[out] The returned property data.</span></span>  
  
 `pcbProperty`  
 <span data-ttu-id="68692-108">[out no] O tamanho, em bytes, de `pvProperty`.</span><span class="sxs-lookup"><span data-stu-id="68692-108">[in, out] The size, in bytes, of `pvProperty`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68692-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="68692-109">Requirements</span></span>  
 <span data-ttu-id="68692-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="68692-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68692-111">**Cabeçalho:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="68692-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="68692-112">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68692-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68692-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="68692-113">See Also</span></span>  
 [<span data-ttu-id="68692-114">Interface IAssemblyName</span><span class="sxs-lookup"><span data-stu-id="68692-114">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
