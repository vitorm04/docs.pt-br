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
ms.openlocfilehash: 17e96f56c57d896397489e27bcc072d8e7df05ec
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796543"
---
# <a name="iassemblynamesetproperty-method"></a><span data-ttu-id="ea983-102">Método IAssemblyName::SetProperty</span><span class="sxs-lookup"><span data-stu-id="ea983-102">IAssemblyName::SetProperty Method</span></span>
<span data-ttu-id="ea983-103">Define o valor da propriedade referenciada pelo identificador de propriedade especificado.</span><span class="sxs-lookup"><span data-stu-id="ea983-103">Sets the value of the property referenced by the specified property identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea983-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ea983-104">Syntax</span></span>  
  
```cpp  
HRESULT SetProperty (  
    [in] DWORD  PropertyId,  
    [in] LPVOID pvProperty,  
    [in] DWORD  cbProperty  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ea983-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ea983-105">Parameters</span></span>  
 `PropertyId`  
 <span data-ttu-id="ea983-106">no O identificador exclusivo da propriedade cujo valor será definido.</span><span class="sxs-lookup"><span data-stu-id="ea983-106">[in] The unique identifier of the property whose value will be set.</span></span>  
  
 `pvProperty`  
 <span data-ttu-id="ea983-107">no O valor para o qual definir a propriedade referenciada `PropertyId`.</span><span class="sxs-lookup"><span data-stu-id="ea983-107">[in] The value to which to set the property referenced by `PropertyId`.</span></span>  
  
 `cbProperty`  
 <span data-ttu-id="ea983-108">no O tamanho, em bytes, de `pvProperty`.</span><span class="sxs-lookup"><span data-stu-id="ea983-108">[in] The size, in bytes, of `pvProperty`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea983-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ea983-109">Requirements</span></span>  
 <span data-ttu-id="ea983-110">**Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ea983-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea983-111">**Cabeçalho:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="ea983-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="ea983-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea983-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea983-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ea983-113">See also</span></span>

- [<span data-ttu-id="ea983-114">Interface IAssemblyName</span><span class="sxs-lookup"><span data-stu-id="ea983-114">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
