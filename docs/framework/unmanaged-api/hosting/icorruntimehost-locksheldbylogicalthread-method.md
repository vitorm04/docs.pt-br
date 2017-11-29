---
title: "Método ICorRuntimeHost::LocksHeldByLogicalThread"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorRuntimeHost.LocksHeldByLogicalThread
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorRuntimeHost::LocksHeldByLogicalThread
helpviewer_keywords:
- ICorRuntimeHost::LocksHeldByLogicalThread method [.NET Framework hosting]
- LocksHeldByLogicalThread method [.NET Framework hosting]
ms.assetid: c3601255-d894-4d7c-b1df-c31334551700
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 82fa031e4842d81f7ddec3e7eeb64c9d7b02e566
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icorruntimehostlocksheldbylogicalthread-method"></a><span data-ttu-id="8124a-102">Método ICorRuntimeHost::LocksHeldByLogicalThread</span><span class="sxs-lookup"><span data-stu-id="8124a-102">ICorRuntimeHost::LocksHeldByLogicalThread Method</span></span>
<span data-ttu-id="8124a-103">Recupera o número de bloqueios que mantém o thread atual.</span><span class="sxs-lookup"><span data-stu-id="8124a-103">Retrieves the number of locks that current thread holds.</span></span>  
  
 <span data-ttu-id="8124a-104">Esse método oferece suporte a infraestrutura do .NET Framework e não se destina a ser usado diretamente do seu código.</span><span class="sxs-lookup"><span data-stu-id="8124a-104">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8124a-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8124a-105">Syntax</span></span>  
  
```  
HRESULT LocksHeldByLogicalThread(  
    [out] DWORD *pCount  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8124a-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8124a-106">Parameters</span></span>  
 `pCount`  
 <span data-ttu-id="8124a-107">[out] Um ponteiro para o número de bloqueios que contém o segmento atual.</span><span class="sxs-lookup"><span data-stu-id="8124a-107">[out] A pointer to the number of locks that the current thread holds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8124a-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8124a-108">Requirements</span></span>  
 <span data-ttu-id="8124a-109">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8124a-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8124a-110">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8124a-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8124a-111">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="8124a-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8124a-112">**Versões do .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="8124a-112">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8124a-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8124a-113">See Also</span></span>  
 [<span data-ttu-id="8124a-114">Interface ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="8124a-114">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
