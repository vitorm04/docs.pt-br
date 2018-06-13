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
ms.openlocfilehash: d46881b76685fd04f8bc5e3a67830e58f85cd774
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436670"
---
# <a name="icorruntimehostlocksheldbylogicalthread-method"></a><span data-ttu-id="3e7f1-102">Método ICorRuntimeHost::LocksHeldByLogicalThread</span><span class="sxs-lookup"><span data-stu-id="3e7f1-102">ICorRuntimeHost::LocksHeldByLogicalThread Method</span></span>
<span data-ttu-id="3e7f1-103">Recupera o número de bloqueios que mantém o thread atual.</span><span class="sxs-lookup"><span data-stu-id="3e7f1-103">Retrieves the number of locks that current thread holds.</span></span>  
  
 <span data-ttu-id="3e7f1-104">Esse método oferece suporte a infraestrutura do .NET Framework e não se destina a ser usado diretamente do seu código.</span><span class="sxs-lookup"><span data-stu-id="3e7f1-104">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e7f1-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3e7f1-105">Syntax</span></span>  
  
```  
HRESULT LocksHeldByLogicalThread(  
    [out] DWORD *pCount  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3e7f1-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3e7f1-106">Parameters</span></span>  
 `pCount`  
 <span data-ttu-id="3e7f1-107">[out] Um ponteiro para o número de bloqueios que contém o segmento atual.</span><span class="sxs-lookup"><span data-stu-id="3e7f1-107">[out] A pointer to the number of locks that the current thread holds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e7f1-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3e7f1-108">Requirements</span></span>  
 <span data-ttu-id="3e7f1-109">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3e7f1-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e7f1-110">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3e7f1-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3e7f1-111">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="3e7f1-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3e7f1-112">**Versões do .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="3e7f1-112">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e7f1-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3e7f1-113">See Also</span></span>  
 [<span data-ttu-id="3e7f1-114">Interface ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="3e7f1-114">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
