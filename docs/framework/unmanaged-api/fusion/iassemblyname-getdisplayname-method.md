---
title: Método IAssemblyName::GetDisplayName
ms.date: 03/30/2017
api_name:
- IAssemblyName.GetDisplayName
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::GetDisplayName
helpviewer_keywords:
- GetDisplayName method, IAssemblyName interface [.NET Framework fusion]
- IAssemblyName::GetDisplayName method [.NET Framework fusion]
ms.assetid: 9a26547a-9a34-4284-a463-78a7d4b496cf
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c434595414fd5bdabeae96d959aaa6be6d84af2b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67753970"
---
# <a name="iassemblynamegetdisplayname-method"></a><span data-ttu-id="8c66d-102">Método IAssemblyName::GetDisplayName</span><span class="sxs-lookup"><span data-stu-id="8c66d-102">IAssemblyName::GetDisplayName Method</span></span>
<span data-ttu-id="8c66d-103">Obtém o nome legível do assembly referenciado por este [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) objeto.</span><span class="sxs-lookup"><span data-stu-id="8c66d-103">Gets the human-readable name of the assembly referenced by this [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c66d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8c66d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDisplayName (  
        [out]      LPOLESTR  szDisplayName,  
        [in, out]  LPDWORD   pccDisplayName,  
        [in]       DWORD     dwDisplayFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8c66d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8c66d-105">Parameters</span></span>  
 `szDisplayName`  
 <span data-ttu-id="8c66d-106">[out] O buffer de cadeia de caracteres que contém o nome do assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="8c66d-106">[out] The string buffer that contains the name of the referenced assembly.</span></span>  
  
 `pccDisplayName`  
 <span data-ttu-id="8c66d-107">[no, out] O tamanho de `szDisplayName` em caracteres largos, incluindo um caractere terminador nulo.</span><span class="sxs-lookup"><span data-stu-id="8c66d-107">[in, out] The size of `szDisplayName` in wide characters, including a null terminator character.</span></span>  
  
 `dwDisplayFlags`  
 <span data-ttu-id="8c66d-108">[in] Uma combinação bit a bit de [ASM_DISPLAY_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-display-flags-enumeration.md) valores que influenciam os recursos do `szDisplayName`.</span><span class="sxs-lookup"><span data-stu-id="8c66d-108">[in] A bitwise combination of [ASM_DISPLAY_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-display-flags-enumeration.md) values that influence the features of `szDisplayName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c66d-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8c66d-109">Requirements</span></span>  
 <span data-ttu-id="8c66d-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c66d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c66d-111">**Cabeçalho:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="8c66d-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="8c66d-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c66d-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c66d-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8c66d-113">See also</span></span>

- [<span data-ttu-id="8c66d-114">Interface IAssemblyName</span><span class="sxs-lookup"><span data-stu-id="8c66d-114">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
- [<span data-ttu-id="8c66d-115">Enumerações de fusão</span><span class="sxs-lookup"><span data-stu-id="8c66d-115">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
