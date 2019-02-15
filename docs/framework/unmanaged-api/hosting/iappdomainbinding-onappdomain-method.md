---
title: Método IAppDomainBinding::OnAppDomain
ms.date: 03/30/2017
api_name:
- IAppDomainBinding.OnAppDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- OnAppDomain
helpviewer_keywords:
- IAppDomainBinding::OnAppDomain method [.NET Framework hosting]
- OnAppDomain method [.NET Framework hosting]
ms.assetid: b419dcc9-e8aa-484b-af0d-0f40358edb99
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c1c22ee61769fdcbb92a73ca0dd55299ebbcf934
ms.sourcegitcommit: bef803e2025642df39f2f1e046767d89031e0304
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/15/2019
ms.locfileid: "56305760"
---
# <a name="iappdomainbindingonappdomain-method"></a><span data-ttu-id="a400f-102">Método IAppDomainBinding::OnAppDomain</span><span class="sxs-lookup"><span data-stu-id="a400f-102">IAppDomainBinding::OnAppDomain Method</span></span>
<span data-ttu-id="a400f-103">Chamado pelo common language runtime (CLR) para notificar o host que um domínio de aplicativo foi criado.</span><span class="sxs-lookup"><span data-stu-id="a400f-103">Called by the common language runtime (CLR) to notify the host that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a400f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a400f-104">Syntax</span></span>  
  
```  
HRESULT OnAppDomain (  
    [in] IUnknown* pAppdomain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a400f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a400f-105">Parameters</span></span>  
 `pAppdomain`  
 <span data-ttu-id="a400f-106">[in] Um ponteiro para um [IUnknown](/cpp/atl/iunknown) objeto de interface que representa o novo domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a400f-106">[in] A pointer to an [IUnknown](/cpp/atl/iunknown) interface object that represents the new application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a400f-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a400f-107">Requirements</span></span>  
 <span data-ttu-id="a400f-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a400f-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a400f-109">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a400f-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a400f-110">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="a400f-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a400f-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a400f-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a400f-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a400f-112">See also</span></span>
- [<span data-ttu-id="a400f-113">Interface IAppDomainBinding</span><span class="sxs-lookup"><span data-stu-id="a400f-113">IAppDomainBinding Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iappdomainbinding-interface.md)
