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
ms.openlocfilehash: f32381dc40a744157e46780e59b83efd63e58dcb
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762637"
---
# <a name="icorruntimehostswitchoutlogicalthreadstate-method"></a><span data-ttu-id="032e5-102">Método ICorRuntimeHost::SwitchOutLogicalThreadState</span><span class="sxs-lookup"><span data-stu-id="032e5-102">ICorRuntimeHost::SwitchOutLogicalThreadState Method</span></span>
<span data-ttu-id="032e5-103">Esse método oferece suporte a infraestrutura do .NET Framework e não se destina a ser usado diretamente do seu código.</span><span class="sxs-lookup"><span data-stu-id="032e5-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="032e5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="032e5-104">Syntax</span></span>  
  
```cpp  
HRESULT SwitchOutLogicalThreadState(  
    [out] DWORD **pFiberCookie  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="032e5-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="032e5-105">Parameters</span></span>  
 `pFiberCookie`  
 <span data-ttu-id="032e5-106">fora Cookie que indica a fibra que está sendo desativada.</span><span class="sxs-lookup"><span data-stu-id="032e5-106">[out] Cookie that indicates the fiber being switched out.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="032e5-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="032e5-107">Requirements</span></span>  
 <span data-ttu-id="032e5-108">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="032e5-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="032e5-109">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="032e5-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="032e5-110">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="032e5-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="032e5-111">**Versão do .NET Framework:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="032e5-111">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="032e5-112">Veja também</span><span class="sxs-lookup"><span data-stu-id="032e5-112">See also</span></span>

- [<span data-ttu-id="032e5-113">Interface ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="032e5-113">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
