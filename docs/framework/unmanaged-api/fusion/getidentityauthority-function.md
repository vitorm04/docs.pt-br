---
title: Função GetIdentityAuthority
ms.date: 03/30/2017
api_name:
- GetIdentityAuthority
api_location:
- fusion.dll
- clr.dll
api_type:
- COM
f1_keywords:
- GetIdentityAuthority
helpviewer_keywords:
- GetIdentityAuthority function [.NET Framework fusion]
ms.assetid: 843cd5ab-d2b7-4ff6-86bd-e68c7a91c098
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3090887d3c670b2784b7b40c7d63832715596c3b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59141512"
---
# <a name="getidentityauthority-function"></a><span data-ttu-id="a382d-102">Função GetIdentityAuthority</span><span class="sxs-lookup"><span data-stu-id="a382d-102">GetIdentityAuthority Function</span></span>
<span data-ttu-id="a382d-103">Obtém um ponteiro para um [IIdentityAuthority](../../../../docs/framework/unmanaged-api/fusion/iidentityauthority-interface.md) instância que gerencia as chaves para objetos de código.</span><span class="sxs-lookup"><span data-stu-id="a382d-103">Gets a pointer to an [IIdentityAuthority](../../../../docs/framework/unmanaged-api/fusion/iidentityauthority-interface.md) instance that manages keys for code objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a382d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a382d-104">Syntax</span></span>  
  
```  
HRESULT GetIdentityAuthority (  
    [out] IIdentityAuthority   **ppIIdentityAuthority  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="a382d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a382d-105">Parameters</span></span>  
 `ppIIdentityAuthority`  
 <span data-ttu-id="a382d-106">[out] Retornado `IIdentityAuthority` ponteiro.</span><span class="sxs-lookup"><span data-stu-id="a382d-106">[out] The returned `IIdentityAuthority` pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a382d-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a382d-107">Requirements</span></span>  
 <span data-ttu-id="a382d-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a382d-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a382d-109">**Cabeçalho:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="a382d-109">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="a382d-110">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a382d-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a382d-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a382d-111">See also</span></span>

- [<span data-ttu-id="a382d-112">Interface IIdentityAuthority</span><span class="sxs-lookup"><span data-stu-id="a382d-112">IIdentityAuthority Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iidentityauthority-interface.md)
- [<span data-ttu-id="a382d-113">Funções estáticas globais de fusão</span><span class="sxs-lookup"><span data-stu-id="a382d-113">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
