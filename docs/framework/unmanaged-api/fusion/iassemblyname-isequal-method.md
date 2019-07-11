---
title: Método IAssemblyName::IsEqual
ms.date: 03/30/2017
api_name:
- IAssemblyName.IsEqual
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::IsEqual
helpviewer_keywords:
- IsEqual method [.NET Framework fusion]
- IAssemblyName::IsEqual method [.NET Framework fusion]
ms.assetid: 6dfc220f-d0d4-45b3-bfce-5829f817766f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f1fc128d15c56981f4bc6122e38e0514d006e29e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768613"
---
# <a name="iassemblynameisequal-method"></a><span data-ttu-id="5254a-102">Método IAssemblyName::IsEqual</span><span class="sxs-lookup"><span data-stu-id="5254a-102">IAssemblyName::IsEqual Method</span></span>
<span data-ttu-id="5254a-103">Determina se um especificado [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) objeto é igual a este `IAssemblyName`, com base nos sinalizadores de comparação especificado.</span><span class="sxs-lookup"><span data-stu-id="5254a-103">Determines whether a specified [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) object is equal to this `IAssemblyName`, based on the specified comparison flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5254a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5254a-104">Syntax</span></span>  
  
```cpp  
HRESULT IsEqual (  
    [in] IAssemblyName  *pName,  
    [in] DWORD          dwCmpFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5254a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5254a-105">Parameters</span></span>  
 `pName`  
 <span data-ttu-id="5254a-106">[in] O `IAssemblyName` objeto ao qual comparar este `IAssemblyName`.</span><span class="sxs-lookup"><span data-stu-id="5254a-106">[in] The `IAssemblyName` object to which to compare this `IAssemblyName`.</span></span>  
  
 `dwCmpFlags`  
 <span data-ttu-id="5254a-107">[in] Uma combinação bit a bit de [ASM_CMP_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cmp-flags-enumeration.md) valores que influenciam a comparação.</span><span class="sxs-lookup"><span data-stu-id="5254a-107">[in] A bitwise combination of [ASM_CMP_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cmp-flags-enumeration.md) values that influence the comparison.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5254a-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5254a-108">Requirements</span></span>  
 <span data-ttu-id="5254a-109">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5254a-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5254a-110">**Cabeçalho:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="5254a-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="5254a-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5254a-111">**NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5254a-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5254a-112">See also</span></span>

- [<span data-ttu-id="5254a-113">Interface IAssemblyName</span><span class="sxs-lookup"><span data-stu-id="5254a-113">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
- [<span data-ttu-id="5254a-114">Enumerações de fusão</span><span class="sxs-lookup"><span data-stu-id="5254a-114">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
