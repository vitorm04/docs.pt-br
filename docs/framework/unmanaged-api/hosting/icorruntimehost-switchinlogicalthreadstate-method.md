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
ms.openlocfilehash: b6569b5dab89a88a24cf2dfc873da9740e5af505
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133386"
---
# <a name="icorruntimehostswitchinlogicalthreadstate-method"></a><span data-ttu-id="ccb98-102">Método ICorRuntimeHost::SwitchInLogicalThreadState</span><span class="sxs-lookup"><span data-stu-id="ccb98-102">ICorRuntimeHost::SwitchInLogicalThreadState Method</span></span>
<span data-ttu-id="ccb98-103">Esse método oferece suporte a infraestrutura do .NET Framework e não se destina a ser usado diretamente do seu código.</span><span class="sxs-lookup"><span data-stu-id="ccb98-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ccb98-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ccb98-104">Syntax</span></span>  
  
```cpp  
HRESULT SwitchInLogicalThreadState(  
    [in] DWORD *pFiberCookie  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ccb98-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ccb98-105">Parameters</span></span>  
 `pFiberCookie`  
 <span data-ttu-id="ccb98-106">no Cookie que indica a fibra a ser usada.</span><span class="sxs-lookup"><span data-stu-id="ccb98-106">[in] Cookie that indicates the fiber to use.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ccb98-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ccb98-107">Requirements</span></span>  
 <span data-ttu-id="ccb98-108">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ccb98-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ccb98-109">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ccb98-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ccb98-110">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ccb98-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ccb98-111">**Versão do .NET Framework:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="ccb98-111">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccb98-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ccb98-112">See also</span></span>

- [<span data-ttu-id="ccb98-113">Interface ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="ccb98-113">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
