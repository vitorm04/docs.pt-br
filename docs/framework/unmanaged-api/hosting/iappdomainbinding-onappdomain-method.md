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
ms.openlocfilehash: 798ef6a9b058d9d49019554feba63627360e6a0e
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57480033"
---
# <a name="iappdomainbindingonappdomain-method"></a><span data-ttu-id="7ff21-102">Método IAppDomainBinding::OnAppDomain</span><span class="sxs-lookup"><span data-stu-id="7ff21-102">IAppDomainBinding::OnAppDomain Method</span></span>
<span data-ttu-id="7ff21-103">Chamado pelo common language runtime (CLR) para notificar o host que um domínio de aplicativo foi criado.</span><span class="sxs-lookup"><span data-stu-id="7ff21-103">Called by the common language runtime (CLR) to notify the host that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ff21-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7ff21-104">Syntax</span></span>  
  
```  
HRESULT OnAppDomain (  
    [in] IUnknown* pAppdomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7ff21-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7ff21-105">Parameters</span></span>  
 `pAppdomain`  
 <span data-ttu-id="7ff21-106">[in] Um ponteiro para um [IUnknown](/cpp/atl/iunknown) objeto de interface que representa o novo domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7ff21-106">[in] A pointer to an [IUnknown](/cpp/atl/iunknown) interface object that represents the new application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ff21-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7ff21-107">Requirements</span></span>  
 <span data-ttu-id="7ff21-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7ff21-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ff21-109">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7ff21-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7ff21-110">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="7ff21-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7ff21-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ff21-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ff21-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7ff21-112">See also</span></span>
- [<span data-ttu-id="7ff21-113">Interface IAppDomainBinding</span><span class="sxs-lookup"><span data-stu-id="7ff21-113">IAppDomainBinding Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iappdomainbinding-interface.md)
