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
ms.openlocfilehash: 2d5dbd003d0ea5decae0025d47e6bd5c1fb1ed4a
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83617068"
---
# <a name="iappdomainbindingonappdomain-method"></a><span data-ttu-id="5d7ff-102">Método IAppDomainBinding::OnAppDomain</span><span class="sxs-lookup"><span data-stu-id="5d7ff-102">IAppDomainBinding::OnAppDomain Method</span></span>
<span data-ttu-id="5d7ff-103">Chamado pelo Common Language Runtime (CLR) para notificar o host de que um domínio de aplicativo foi criado.</span><span class="sxs-lookup"><span data-stu-id="5d7ff-103">Called by the common language runtime (CLR) to notify the host that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d7ff-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5d7ff-104">Syntax</span></span>  
  
```cpp  
HRESULT OnAppDomain (  
    [in] IUnknown* pAppdomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5d7ff-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5d7ff-105">Parameters</span></span>  
 `pAppdomain`  
 <span data-ttu-id="5d7ff-106">no Um ponteiro para um objeto de interface [IUnknown](/cpp/atl/iunknown) que representa o novo domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5d7ff-106">[in] A pointer to an [IUnknown](/cpp/atl/iunknown) interface object that represents the new application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d7ff-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5d7ff-107">Requirements</span></span>  
 <span data-ttu-id="5d7ff-108">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5d7ff-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d7ff-109">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="5d7ff-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5d7ff-110">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="5d7ff-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5d7ff-111">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d7ff-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d7ff-112">Veja também</span><span class="sxs-lookup"><span data-stu-id="5d7ff-112">See also</span></span>

- [<span data-ttu-id="5d7ff-113">Interface IAppDomainBinding</span><span class="sxs-lookup"><span data-stu-id="5d7ff-113">IAppDomainBinding Interface</span></span>](iappdomainbinding-interface.md)
