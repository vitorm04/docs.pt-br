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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 262895d64b80ca5f382aad66d6cc6a4ca95b53c3
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57499219"
---
# <a name="icorruntimehostlocksheldbylogicalthread-method"></a><span data-ttu-id="7fbd5-102">Método ICorRuntimeHost::LocksHeldByLogicalThread</span><span class="sxs-lookup"><span data-stu-id="7fbd5-102">ICorRuntimeHost::LocksHeldByLogicalThread Method</span></span>
<span data-ttu-id="7fbd5-103">Recupera o número de bloqueios que o thread atual mantém.</span><span class="sxs-lookup"><span data-stu-id="7fbd5-103">Retrieves the number of locks that current thread holds.</span></span>  
  
 <span data-ttu-id="7fbd5-104">Esse método oferece suporte a infraestrutura do .NET Framework e não se destina a ser usado diretamente do seu código.</span><span class="sxs-lookup"><span data-stu-id="7fbd5-104">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7fbd5-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7fbd5-105">Syntax</span></span>  
  
```  
HRESULT LocksHeldByLogicalThread(  
    [out] DWORD *pCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7fbd5-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7fbd5-106">Parameters</span></span>  
 `pCount`  
 <span data-ttu-id="7fbd5-107">[out] Um ponteiro para o número de bloqueios que mantém o thread atual.</span><span class="sxs-lookup"><span data-stu-id="7fbd5-107">[out] A pointer to the number of locks that the current thread holds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7fbd5-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7fbd5-108">Requirements</span></span>  
 <span data-ttu-id="7fbd5-109">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7fbd5-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7fbd5-110">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7fbd5-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7fbd5-111">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="7fbd5-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7fbd5-112">**Versões do .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="7fbd5-112">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fbd5-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7fbd5-113">See also</span></span>
- [<span data-ttu-id="7fbd5-114">Interface ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="7fbd5-114">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
