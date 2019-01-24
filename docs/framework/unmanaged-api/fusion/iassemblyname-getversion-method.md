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
ms.openlocfilehash: ad71e0f19d4019f8fc919008b9a5c46f6586f9f8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54674499"
---
# <a name="iassemblynamegetversion-method"></a><span data-ttu-id="f7733-102">Método IAssemblyName::GetVersion</span><span class="sxs-lookup"><span data-stu-id="f7733-102">IAssemblyName::GetVersion Method</span></span>
<span data-ttu-id="f7733-103">Obtém as informações de versão do assembly referenciado por este [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) objeto.</span><span class="sxs-lookup"><span data-stu-id="f7733-103">Gets the version information for the assembly referenced by this [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7733-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f7733-104">Syntax</span></span>  
  
```  
HRESULT GetVersion (  
    [out] LPDWORD pdwVersionHi,  
    [out] LPDWORD pdwVersionLow  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f7733-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f7733-105">Parameters</span></span>  
 `pdwVersionHi`  
 <span data-ttu-id="f7733-106">[out] Os 32 bits altos da versão.</span><span class="sxs-lookup"><span data-stu-id="f7733-106">[out] The high 32 bits of the version.</span></span>  
  
 `pdwVersionLow`  
 <span data-ttu-id="f7733-107">[out] Os 32 bits baixos da versão.</span><span class="sxs-lookup"><span data-stu-id="f7733-107">[out] The low 32 bits of the version.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7733-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f7733-108">Requirements</span></span>  
 <span data-ttu-id="f7733-109">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7733-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7733-110">**Cabeçalho:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="f7733-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="f7733-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7733-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7733-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f7733-112">See also</span></span>
- [<span data-ttu-id="f7733-113">Interface IAssemblyName</span><span class="sxs-lookup"><span data-stu-id="f7733-113">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
