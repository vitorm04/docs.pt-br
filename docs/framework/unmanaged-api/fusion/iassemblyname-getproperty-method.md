---
title: Método IAssemblyName::GetProperty
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5d131e9d8c7a1a2b4e4def75ecfb65bb8235a65e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54550663"
---
# <a name="iassemblynamegetproperty-method"></a><span data-ttu-id="a56f3-102">Método IAssemblyName::GetProperty</span><span class="sxs-lookup"><span data-stu-id="a56f3-102">IAssemblyName::GetProperty Method</span></span>
<span data-ttu-id="a56f3-103">Obtém um ponteiro para a propriedade referenciada pelo identificador de propriedade especificado.</span><span class="sxs-lookup"><span data-stu-id="a56f3-103">Gets a pointer to the property referenced by the specified property identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a56f3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a56f3-104">Syntax</span></span>  
  
```  
HRESULT GetProperty (  
    [in]      DWORD    PropertyId,  
    [out]     LPVOID   pvProperty,  
    [in, out] LPDWORD  pcbProperty  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a56f3-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a56f3-105">Parameters</span></span>  
 `PropertyId`  
 <span data-ttu-id="a56f3-106">[in] O identificador exclusivo para a propriedade solicitada.</span><span class="sxs-lookup"><span data-stu-id="a56f3-106">[in] The unique identifier for the requested property.</span></span>  
  
 `pvProperty`  
 <span data-ttu-id="a56f3-107">[out] Os dados de propriedade retornada.</span><span class="sxs-lookup"><span data-stu-id="a56f3-107">[out] The returned property data.</span></span>  
  
 `pcbProperty`  
 <span data-ttu-id="a56f3-108">[no, out] O tamanho, em bytes, do `pvProperty`.</span><span class="sxs-lookup"><span data-stu-id="a56f3-108">[in, out] The size, in bytes, of `pvProperty`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a56f3-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a56f3-109">Requirements</span></span>  
 <span data-ttu-id="a56f3-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a56f3-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a56f3-111">**Cabeçalho:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="a56f3-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="a56f3-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a56f3-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a56f3-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a56f3-113">See also</span></span>
- [<span data-ttu-id="a56f3-114">Interface IAssemblyName</span><span class="sxs-lookup"><span data-stu-id="a56f3-114">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
