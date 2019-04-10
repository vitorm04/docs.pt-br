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
ms.openlocfilehash: 323c883b4010f3ddd4c575e5d5fc40a3419e57c2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59214358"
---
# <a name="iassemblynamegetdisplayname-method"></a><span data-ttu-id="ba4fa-102">Método IAssemblyName::GetDisplayName</span><span class="sxs-lookup"><span data-stu-id="ba4fa-102">IAssemblyName::GetDisplayName Method</span></span>
<span data-ttu-id="ba4fa-103">Obtém o nome legível do assembly referenciado por este [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) objeto.</span><span class="sxs-lookup"><span data-stu-id="ba4fa-103">Gets the human-readable name of the assembly referenced by this [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba4fa-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ba4fa-104">Syntax</span></span>  
  
```  
HRESULT GetDisplayName (  
        [out]      LPOLESTR  szDisplayName,  
        [in, out]  LPDWORD   pccDisplayName,  
        [in]       DWORD     dwDisplayFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ba4fa-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ba4fa-105">Parameters</span></span>  
 `szDisplayName`  
 <span data-ttu-id="ba4fa-106">[out] O buffer de cadeia de caracteres que contém o nome do assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="ba4fa-106">[out] The string buffer that contains the name of the referenced assembly.</span></span>  
  
 `pccDisplayName`  
 <span data-ttu-id="ba4fa-107">[no, out] O tamanho de `szDisplayName` em caracteres largos, incluindo um caractere terminador nulo.</span><span class="sxs-lookup"><span data-stu-id="ba4fa-107">[in, out] The size of `szDisplayName` in wide characters, including a null terminator character.</span></span>  
  
 `dwDisplayFlags`  
 <span data-ttu-id="ba4fa-108">[in] Uma combinação bit a bit de [ASM_DISPLAY_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-display-flags-enumeration.md) valores que influenciam os recursos do `szDisplayName`.</span><span class="sxs-lookup"><span data-stu-id="ba4fa-108">[in] A bitwise combination of [ASM_DISPLAY_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-display-flags-enumeration.md) values that influence the features of `szDisplayName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba4fa-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ba4fa-109">Requirements</span></span>  
 <span data-ttu-id="ba4fa-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ba4fa-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba4fa-111">**Cabeçalho:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="ba4fa-111">**Header:** Fusion.h</span></span>  
  
 **<span data-ttu-id="ba4fa-112">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="ba4fa-112">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ba4fa-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ba4fa-113">See also</span></span>

- [<span data-ttu-id="ba4fa-114">Interface IAssemblyName</span><span class="sxs-lookup"><span data-stu-id="ba4fa-114">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
- [<span data-ttu-id="ba4fa-115">Enumerações Fusion</span><span class="sxs-lookup"><span data-stu-id="ba4fa-115">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
