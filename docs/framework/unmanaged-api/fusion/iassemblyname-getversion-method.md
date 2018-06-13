---
title: Método IAssemblyName::GetVersion
ms.date: 03/30/2017
api_name:
- IAssemblyName.GetVersion
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::GetVersion
helpviewer_keywords:
- IAssemblyName::GetVersion method [.NET Framework fusion]
- GetVersion method, IAssemblyName interface [.NET Framework fusion]
ms.assetid: 42230928-2c33-41fd-9519-d96efef6c7af
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 71b9eb6cc5640913c5723f088034d9bcd86c4a43
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33428867"
---
# <a name="iassemblynamegetversion-method"></a><span data-ttu-id="f09cb-102">Método IAssemblyName::GetVersion</span><span class="sxs-lookup"><span data-stu-id="f09cb-102">IAssemblyName::GetVersion Method</span></span>
<span data-ttu-id="f09cb-103">Obtém as informações de versão do assembly referenciado por essa [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) objeto.</span><span class="sxs-lookup"><span data-stu-id="f09cb-103">Gets the version information for the assembly referenced by this [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f09cb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f09cb-104">Syntax</span></span>  
  
```  
HRESULT GetVersion (  
    [out] LPDWORD pdwVersionHi,  
    [out] LPDWORD pdwVersionLow  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f09cb-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f09cb-105">Parameters</span></span>  
 `pdwVersionHi`  
 <span data-ttu-id="f09cb-106">[out] Os 32 bits altos da versão.</span><span class="sxs-lookup"><span data-stu-id="f09cb-106">[out] The high 32 bits of the version.</span></span>  
  
 `pdwVersionLow`  
 <span data-ttu-id="f09cb-107">[out] Os 32 bits baixos da versão.</span><span class="sxs-lookup"><span data-stu-id="f09cb-107">[out] The low 32 bits of the version.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f09cb-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f09cb-108">Requirements</span></span>  
 <span data-ttu-id="f09cb-109">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f09cb-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f09cb-110">**Cabeçalho:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="f09cb-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="f09cb-111">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f09cb-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f09cb-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f09cb-112">See Also</span></span>  
 [<span data-ttu-id="f09cb-113">Interface IAssemblyName</span><span class="sxs-lookup"><span data-stu-id="f09cb-113">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
