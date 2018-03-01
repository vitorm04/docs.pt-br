---
title: "Método IAssemblyName::GetDisplayName"
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 32b75a0d9cbe783778678585a98b453418920e21
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="iassemblynamegetdisplayname-method"></a><span data-ttu-id="53361-102">Método IAssemblyName::GetDisplayName</span><span class="sxs-lookup"><span data-stu-id="53361-102">IAssemblyName::GetDisplayName Method</span></span>
<span data-ttu-id="53361-103">Obtém o nome legível do assembly referenciado por essa [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) objeto.</span><span class="sxs-lookup"><span data-stu-id="53361-103">Gets the human-readable name of the assembly referenced by this [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53361-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="53361-104">Syntax</span></span>  
  
```  
HRESULT GetDisplayName (  
        [out]      LPOLESTR  szDisplayName,  
        [in, out]  LPDWORD   pccDisplayName,  
        [in]       DWORD     dwDisplayFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="53361-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="53361-105">Parameters</span></span>  
 `szDisplayName`  
 <span data-ttu-id="53361-106">[out] O buffer de cadeia de caracteres que contém o nome do assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="53361-106">[out] The string buffer that contains the name of the referenced assembly.</span></span>  
  
 `pccDisplayName`  
 <span data-ttu-id="53361-107">[out no] O tamanho de `szDisplayName` em caracteres largos, incluindo um caractere terminador nulo.</span><span class="sxs-lookup"><span data-stu-id="53361-107">[in, out] The size of `szDisplayName` in wide characters, including a null terminator character.</span></span>  
  
 `dwDisplayFlags`  
 <span data-ttu-id="53361-108">[in] Uma combinação bit a bit de [ASM_DISPLAY_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-display-flags-enumeration.md) valores que influenciam os recursos do `szDisplayName`.</span><span class="sxs-lookup"><span data-stu-id="53361-108">[in] A bitwise combination of [ASM_DISPLAY_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-display-flags-enumeration.md) values that influence the features of `szDisplayName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53361-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="53361-109">Requirements</span></span>  
 <span data-ttu-id="53361-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="53361-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53361-111">**Cabeçalho:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="53361-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="53361-112">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53361-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53361-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="53361-113">See Also</span></span>  
 [<span data-ttu-id="53361-114">Interface IAssemblyName</span><span class="sxs-lookup"><span data-stu-id="53361-114">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)  
 [<span data-ttu-id="53361-115">Enumerações de fusão</span><span class="sxs-lookup"><span data-stu-id="53361-115">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
