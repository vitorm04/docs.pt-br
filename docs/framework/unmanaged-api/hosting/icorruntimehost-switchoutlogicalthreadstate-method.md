---
title: Método ICorRuntimeHost::SwitchOutLogicalThreadState
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.SwitchOutLogicalThreadState
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::SwitchOutLogicalThreadState
helpviewer_keywords:
- ICorRuntimeHost::SwitchOutLogicalThreadState method [.NET Framework hosting]
- SwitchOutLogicalThreadState method [.NET Framework hosting]
ms.assetid: e1968f0b-2675-4dc2-8507-46164e1df154
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 671ba0a5450918b8e0bee63d1a13b3188ef2ce0f
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57501642"
---
# <a name="icorruntimehostswitchoutlogicalthreadstate-method"></a><span data-ttu-id="e295f-102">Método ICorRuntimeHost::SwitchOutLogicalThreadState</span><span class="sxs-lookup"><span data-stu-id="e295f-102">ICorRuntimeHost::SwitchOutLogicalThreadState Method</span></span>
<span data-ttu-id="e295f-103">Esse método oferece suporte a infraestrutura do .NET Framework e não se destina a ser usado diretamente do seu código.</span><span class="sxs-lookup"><span data-stu-id="e295f-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e295f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e295f-104">Syntax</span></span>  
  
```  
HRESULT SwitchOutLogicalThreadState(  
    [out] DWORD **pFiberCookie  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e295f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e295f-105">Parameters</span></span>  
 `pFiberCookie`  
 <span data-ttu-id="e295f-106">[out] Cookie que indica a que está sendo alternada de fibra.</span><span class="sxs-lookup"><span data-stu-id="e295f-106">[out] Cookie that indicates the fiber being switched out.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e295f-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e295f-107">Requirements</span></span>  
 <span data-ttu-id="e295f-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e295f-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e295f-109">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e295f-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e295f-110">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="e295f-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e295f-111">**Versão do .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="e295f-111">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e295f-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e295f-112">See also</span></span>
- [<span data-ttu-id="e295f-113">Interface ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="e295f-113">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
