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
ms.openlocfilehash: d830635b911fa5d80382e432f283c455c41af7a8
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762676"
---
# <a name="icorruntimehostswitchinlogicalthreadstate-method"></a><span data-ttu-id="499ee-102">Método ICorRuntimeHost::SwitchInLogicalThreadState</span><span class="sxs-lookup"><span data-stu-id="499ee-102">ICorRuntimeHost::SwitchInLogicalThreadState Method</span></span>
<span data-ttu-id="499ee-103">Esse método oferece suporte a infraestrutura do .NET Framework e não se destina a ser usado diretamente do seu código.</span><span class="sxs-lookup"><span data-stu-id="499ee-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="499ee-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="499ee-104">Syntax</span></span>  
  
```cpp  
HRESULT SwitchInLogicalThreadState(  
    [in] DWORD *pFiberCookie  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="499ee-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="499ee-105">Parameters</span></span>  
 `pFiberCookie`  
 <span data-ttu-id="499ee-106">no Cookie que indica a fibra a ser usada.</span><span class="sxs-lookup"><span data-stu-id="499ee-106">[in] Cookie that indicates the fiber to use.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="499ee-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="499ee-107">Requirements</span></span>  
 <span data-ttu-id="499ee-108">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="499ee-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="499ee-109">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="499ee-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="499ee-110">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="499ee-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="499ee-111">**Versão do .NET Framework:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="499ee-111">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="499ee-112">Veja também</span><span class="sxs-lookup"><span data-stu-id="499ee-112">See also</span></span>

- [<span data-ttu-id="499ee-113">Interface ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="499ee-113">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
