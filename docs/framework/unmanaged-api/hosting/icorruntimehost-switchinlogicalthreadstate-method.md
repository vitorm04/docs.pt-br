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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59209483"
---
# <a name="icorruntimehostswitchinlogicalthreadstate-method"></a><span data-ttu-id="6bf13-102">Método ICorRuntimeHost::SwitchInLogicalThreadState</span><span class="sxs-lookup"><span data-stu-id="6bf13-102">ICorRuntimeHost::SwitchInLogicalThreadState Method</span></span>
<span data-ttu-id="6bf13-103">Esse método oferece suporte a infraestrutura do .NET Framework e não se destina a ser usado diretamente do seu código.</span><span class="sxs-lookup"><span data-stu-id="6bf13-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6bf13-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6bf13-104">Syntax</span></span>  
  
```  
HRESULT SwitchInLogicalThreadState(  
    [in] DWORD *pFiberCookie  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6bf13-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6bf13-105">Parameters</span></span>  
 `pFiberCookie`  
 <span data-ttu-id="6bf13-106">[in] Cookie que indica a fibra para usar.</span><span class="sxs-lookup"><span data-stu-id="6bf13-106">[in] Cookie that indicates the fiber to use.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6bf13-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6bf13-107">Requirements</span></span>  
 <span data-ttu-id="6bf13-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6bf13-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6bf13-109">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6bf13-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6bf13-110">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="6bf13-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6bf13-111">**Versão do .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="6bf13-111">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bf13-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6bf13-112">See also</span></span>

- [<span data-ttu-id="6bf13-113">Interface ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="6bf13-113">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
