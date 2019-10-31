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
ms.openlocfilehash: 37c02b878cd52034603ab6cafe4d8aaca594cbe9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126881"
---
# <a name="iappdomainbindingonappdomain-method"></a><span data-ttu-id="964fb-102">Método IAppDomainBinding::OnAppDomain</span><span class="sxs-lookup"><span data-stu-id="964fb-102">IAppDomainBinding::OnAppDomain Method</span></span>
<span data-ttu-id="964fb-103">Chamado pelo Common Language Runtime (CLR) para notificar o host de que um domínio de aplicativo foi criado.</span><span class="sxs-lookup"><span data-stu-id="964fb-103">Called by the common language runtime (CLR) to notify the host that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="964fb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="964fb-104">Syntax</span></span>  
  
```cpp  
HRESULT OnAppDomain (  
    [in] IUnknown* pAppdomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="964fb-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="964fb-105">Parameters</span></span>  
 `pAppdomain`  
 <span data-ttu-id="964fb-106">no Um ponteiro para um objeto de interface [IUnknown](/cpp/atl/iunknown) que representa o novo domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="964fb-106">[in] A pointer to an [IUnknown](/cpp/atl/iunknown) interface object that represents the new application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="964fb-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="964fb-107">Requirements</span></span>  
 <span data-ttu-id="964fb-108">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="964fb-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="964fb-109">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="964fb-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="964fb-110">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="964fb-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="964fb-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="964fb-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="964fb-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="964fb-112">See also</span></span>

- [<span data-ttu-id="964fb-113">Interface IAppDomainBinding</span><span class="sxs-lookup"><span data-stu-id="964fb-113">IAppDomainBinding Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iappdomainbinding-interface.md)
