---
title: "Método IAssemblyName::GetDisplayName"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IAssemblyName.GetDisplayName
api_location: fusion.dll
api_type: COM
f1_keywords: IAssemblyName::GetDisplayName
helpviewer_keywords:
- GetDisplayName method, IAssemblyName interface [.NET Framework fusion]
- IAssemblyName::GetDisplayName method [.NET Framework fusion]
ms.assetid: 9a26547a-9a34-4284-a463-78a7d4b496cf
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 810192848e15a200a4b2eb33eaf60ddbd7c7c607
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="iassemblynamegetdisplayname-method"></a><span data-ttu-id="95a3c-102">Método IAssemblyName::GetDisplayName</span><span class="sxs-lookup"><span data-stu-id="95a3c-102">IAssemblyName::GetDisplayName Method</span></span>
<span data-ttu-id="95a3c-103">Obtém o nome legível do assembly referenciado por essa [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) objeto.</span><span class="sxs-lookup"><span data-stu-id="95a3c-103">Gets the human-readable name of the assembly referenced by this [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95a3c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="95a3c-104">Syntax</span></span>  
  
```  
HRESULT GetDisplayName (  
        [out]      LPOLESTR  szDisplayName,  
        [in, out]  LPDWORD   pccDisplayName,  
        [in]       DWORD     dwDisplayFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="95a3c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="95a3c-105">Parameters</span></span>  
 `szDisplayName`  
 <span data-ttu-id="95a3c-106">[out] O buffer de cadeia de caracteres que contém o nome do assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="95a3c-106">[out] The string buffer that contains the name of the referenced assembly.</span></span>  
  
 `pccDisplayName`  
 <span data-ttu-id="95a3c-107">[out no] O tamanho de `szDisplayName` em caracteres largos, incluindo um caractere terminador nulo.</span><span class="sxs-lookup"><span data-stu-id="95a3c-107">[in, out] The size of `szDisplayName` in wide characters, including a null terminator character.</span></span>  
  
 `dwDisplayFlags`  
 <span data-ttu-id="95a3c-108">[in] Uma combinação bit a bit de [ASM_DISPLAY_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-display-flags-enumeration.md) valores que influenciam os recursos do `szDisplayName`.</span><span class="sxs-lookup"><span data-stu-id="95a3c-108">[in] A bitwise combination of [ASM_DISPLAY_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-display-flags-enumeration.md) values that influence the features of `szDisplayName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95a3c-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="95a3c-109">Requirements</span></span>  
 <span data-ttu-id="95a3c-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="95a3c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95a3c-111">**Cabeçalho:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="95a3c-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="95a3c-112">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95a3c-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95a3c-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="95a3c-113">See Also</span></span>  
 [<span data-ttu-id="95a3c-114">Interface IAssemblyName</span><span class="sxs-lookup"><span data-stu-id="95a3c-114">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)  
 [<span data-ttu-id="95a3c-115">Enumerações de fusão</span><span class="sxs-lookup"><span data-stu-id="95a3c-115">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
