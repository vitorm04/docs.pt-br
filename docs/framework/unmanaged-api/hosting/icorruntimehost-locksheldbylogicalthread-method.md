---
title: Método ICorRuntimeHost::LocksHeldByLogicalThread
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.LocksHeldByLogicalThread
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::LocksHeldByLogicalThread
helpviewer_keywords:
- ICorRuntimeHost::LocksHeldByLogicalThread method [.NET Framework hosting]
- LocksHeldByLogicalThread method [.NET Framework hosting]
ms.assetid: c3601255-d894-4d7c-b1df-c31334551700
topic_type:
- apiref
ms.openlocfilehash: f6ef7e06d94cb22d266949927cb15105b1602d3a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139534"
---
# <a name="icorruntimehostlocksheldbylogicalthread-method"></a><span data-ttu-id="e3aef-102">Método ICorRuntimeHost::LocksHeldByLogicalThread</span><span class="sxs-lookup"><span data-stu-id="e3aef-102">ICorRuntimeHost::LocksHeldByLogicalThread Method</span></span>
<span data-ttu-id="e3aef-103">Recupera o número de bloqueios que o thread atual mantém.</span><span class="sxs-lookup"><span data-stu-id="e3aef-103">Retrieves the number of locks that current thread holds.</span></span>  
  
 <span data-ttu-id="e3aef-104">Esse método oferece suporte a infraestrutura do .NET Framework e não se destina a ser usado diretamente do seu código.</span><span class="sxs-lookup"><span data-stu-id="e3aef-104">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3aef-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e3aef-105">Syntax</span></span>  
  
```cpp  
HRESULT LocksHeldByLogicalThread(  
    [out] DWORD *pCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e3aef-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e3aef-106">Parameters</span></span>  
 `pCount`  
 <span data-ttu-id="e3aef-107">fora Um ponteiro para o número de bloqueios que o thread atual mantém.</span><span class="sxs-lookup"><span data-stu-id="e3aef-107">[out] A pointer to the number of locks that the current thread holds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3aef-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e3aef-108">Requirements</span></span>  
 <span data-ttu-id="e3aef-109">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3aef-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3aef-110">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e3aef-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e3aef-111">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e3aef-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e3aef-112">**Versões do .NET Framework:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="e3aef-112">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3aef-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e3aef-113">See also</span></span>

- [<span data-ttu-id="e3aef-114">Interface ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="e3aef-114">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
