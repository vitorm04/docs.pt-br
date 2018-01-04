---
title: "Método ICorRuntimeHost::SwitchInLogicalThreadState"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorRuntimeHost.SwitchInLogicalThreadState
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorRuntimeHost::SwitchInLogicalThreadState
helpviewer_keywords:
- ICorRuntimeHost::SwitchInLogicalThreadState method [.NET Framework hosting]
- SwitchInLogicalThreadState method [.NET Framework hosting]
ms.assetid: 7df1e492-8014-43ea-80d1-a4743e9b1c17
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 065a2347be2587265471d707988e90a01482c5a9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icorruntimehostswitchinlogicalthreadstate-method"></a><span data-ttu-id="cd765-102">Método ICorRuntimeHost::SwitchInLogicalThreadState</span><span class="sxs-lookup"><span data-stu-id="cd765-102">ICorRuntimeHost::SwitchInLogicalThreadState Method</span></span>
<span data-ttu-id="cd765-103">Esse método oferece suporte a infraestrutura do .NET Framework e não se destina a ser usado diretamente do seu código.</span><span class="sxs-lookup"><span data-stu-id="cd765-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd765-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cd765-104">Syntax</span></span>  
  
```  
HRESULT SwitchInLogicalThreadState(  
    [in] DWORD *pFiberCookie  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cd765-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cd765-105">Parameters</span></span>  
 `pFiberCookie`  
 <span data-ttu-id="cd765-106">[in] Cookie que indica a fibra para usar.</span><span class="sxs-lookup"><span data-stu-id="cd765-106">[in] Cookie that indicates the fiber to use.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd765-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cd765-107">Requirements</span></span>  
 <span data-ttu-id="cd765-108">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cd765-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd765-109">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="cd765-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cd765-110">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="cd765-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cd765-111">**Versão do .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="cd765-111">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd765-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cd765-112">See Also</span></span>  
 [<span data-ttu-id="cd765-113">Interface ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="cd765-113">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
