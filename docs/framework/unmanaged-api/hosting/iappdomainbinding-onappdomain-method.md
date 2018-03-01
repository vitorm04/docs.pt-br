---
title: "Método IAppDomainBinding::OnAppDomain"
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 131e4af5d8c410f625d2c119097f07f5facd4300
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="iappdomainbindingonappdomain-method"></a><span data-ttu-id="fb6ed-102">Método IAppDomainBinding::OnAppDomain</span><span class="sxs-lookup"><span data-stu-id="fb6ed-102">IAppDomainBinding::OnAppDomain Method</span></span>
<span data-ttu-id="fb6ed-103">Chamado pelo common language runtime (CLR) para notificar o host que um domínio de aplicativo foi criado.</span><span class="sxs-lookup"><span data-stu-id="fb6ed-103">Called by the common language runtime (CLR) to notify the host that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb6ed-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fb6ed-104">Syntax</span></span>  
  
```  
HRESULT OnAppDomain (  
    [in] IUnknown* pAppdomain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fb6ed-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="fb6ed-105">Parameters</span></span>  
 `pAppdomain`  
 <span data-ttu-id="fb6ed-106">[in] Um ponteiro para um [IUnknown](https://msdn.microsoft.com/library/94as6ehy(v=vs.110).aspx) objeto de interface que representa o novo domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fb6ed-106">[in] A pointer to an [IUnknown](https://msdn.microsoft.com/library/94as6ehy(v=vs.110).aspx) interface object that represents the new application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb6ed-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fb6ed-107">Requirements</span></span>  
 <span data-ttu-id="fb6ed-108">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb6ed-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb6ed-109">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="fb6ed-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fb6ed-110">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="fb6ed-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fb6ed-111">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb6ed-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb6ed-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fb6ed-112">See Also</span></span>  
 [<span data-ttu-id="fb6ed-113">Interface IAppDomainBinding</span><span class="sxs-lookup"><span data-stu-id="fb6ed-113">IAppDomainBinding Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iappdomainbinding-interface.md)
