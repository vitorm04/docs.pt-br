---
title: Método ICorRuntimeHost::SwitchInLogicalThreadState
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.SwitchInLogicalThreadState
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::SwitchInLogicalThreadState
helpviewer_keywords:
- ICorRuntimeHost::SwitchInLogicalThreadState method [.NET Framework hosting]
- SwitchInLogicalThreadState method [.NET Framework hosting]
ms.assetid: 7df1e492-8014-43ea-80d1-a4743e9b1c17
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fc6cd8d2d0ab4648ad20392ef0968907917677e9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59209483"
---
# <a name="icorruntimehostswitchinlogicalthreadstate-method"></a><span data-ttu-id="ea1a5-102">Método ICorRuntimeHost::SwitchInLogicalThreadState</span><span class="sxs-lookup"><span data-stu-id="ea1a5-102">ICorRuntimeHost::SwitchInLogicalThreadState Method</span></span>
<span data-ttu-id="ea1a5-103">Esse método oferece suporte a infraestrutura do .NET Framework e não se destina a ser usado diretamente do seu código.</span><span class="sxs-lookup"><span data-stu-id="ea1a5-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea1a5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ea1a5-104">Syntax</span></span>  
  
```  
HRESULT SwitchInLogicalThreadState(  
    [in] DWORD *pFiberCookie  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ea1a5-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ea1a5-105">Parameters</span></span>  
 `pFiberCookie`  
 <span data-ttu-id="ea1a5-106">[in] Cookie que indica a fibra para usar.</span><span class="sxs-lookup"><span data-stu-id="ea1a5-106">[in] Cookie that indicates the fiber to use.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea1a5-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ea1a5-107">Requirements</span></span>  
 <span data-ttu-id="ea1a5-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ea1a5-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea1a5-109">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ea1a5-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ea1a5-110">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="ea1a5-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ea1a5-111">**Versão do .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="ea1a5-111">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea1a5-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ea1a5-112">See also</span></span>

- [<span data-ttu-id="ea1a5-113">Interface ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="ea1a5-113">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
