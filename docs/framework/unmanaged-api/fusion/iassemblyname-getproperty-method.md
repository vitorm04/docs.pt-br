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
ms.openlocfilehash: 351d540d226f46f180b46323e83eb1bcc71da4f0
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796594"
---
# <a name="iassemblynamegetproperty-method"></a><span data-ttu-id="b2b5f-102">Método IAssemblyName::GetProperty</span><span class="sxs-lookup"><span data-stu-id="b2b5f-102">IAssemblyName::GetProperty Method</span></span>
<span data-ttu-id="b2b5f-103">Obtém um ponteiro para a propriedade referenciada pelo identificador de propriedade especificado.</span><span class="sxs-lookup"><span data-stu-id="b2b5f-103">Gets a pointer to the property referenced by the specified property identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2b5f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b2b5f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProperty (  
    [in]      DWORD    PropertyId,  
    [out]     LPVOID   pvProperty,  
    [in, out] LPDWORD  pcbProperty  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b2b5f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b2b5f-105">Parameters</span></span>  
 `PropertyId`  
 <span data-ttu-id="b2b5f-106">no O identificador exclusivo para a propriedade solicitada.</span><span class="sxs-lookup"><span data-stu-id="b2b5f-106">[in] The unique identifier for the requested property.</span></span>  
  
 `pvProperty`  
 <span data-ttu-id="b2b5f-107">fora Os dados de propriedade retornados.</span><span class="sxs-lookup"><span data-stu-id="b2b5f-107">[out] The returned property data.</span></span>  
  
 `pcbProperty`  
 <span data-ttu-id="b2b5f-108">[entrada, saída] O tamanho, em bytes, de `pvProperty`.</span><span class="sxs-lookup"><span data-stu-id="b2b5f-108">[in, out] The size, in bytes, of `pvProperty`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2b5f-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b2b5f-109">Requirements</span></span>  
 <span data-ttu-id="b2b5f-110">**Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2b5f-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2b5f-111">**Cabeçalho:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="b2b5f-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="b2b5f-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2b5f-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2b5f-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b2b5f-113">See also</span></span>

- [<span data-ttu-id="b2b5f-114">Interface IAssemblyName</span><span class="sxs-lookup"><span data-stu-id="b2b5f-114">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
