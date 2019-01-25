---
title: Método ICorThreadpool::CorCreateTimer
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorCreateTimer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorCreateTimer
helpviewer_keywords:
- CorCreateTimer method [.NET Framework hosting]
- ICorThreadpool::CorCreateTimer method [.NET Framework hosting]
ms.assetid: 0d56ef25-30f1-4499-8a1f-76e7654ec614
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 53b44a265e6bb4a2836b4ec053a5bc052afa6b1d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54526997"
---
# <a name="icorthreadpoolcorcreatetimer-method"></a><span data-ttu-id="4308a-102">Método ICorThreadpool::CorCreateTimer</span><span class="sxs-lookup"><span data-stu-id="4308a-102">ICorThreadpool::CorCreateTimer Method</span></span>
<span data-ttu-id="4308a-103">Esse método oferece suporte a infraestrutura do .NET Framework e não se destina a ser usado diretamente do seu código.</span><span class="sxs-lookup"><span data-stu-id="4308a-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4308a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4308a-104">Syntax</span></span>  
  
```  
HRESULT CorCreateTimer (  
    [in]  HANDLE*             phNewTimer,  
    [in]  WAITORTIMERCALLBACK Callback,  
    [in]  PVOID               Parameter,  
    [in]  DWORD               DueTime,  
    [in]  DWORD               Period,  
    [out] BOOL*               result  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="4308a-105">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4308a-105">Requirements</span></span>  
 <span data-ttu-id="4308a-106">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4308a-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4308a-107">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4308a-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4308a-108">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="4308a-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4308a-109">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4308a-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4308a-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4308a-110">See also</span></span>
- [<span data-ttu-id="4308a-111">Interface ICorThreadpool</span><span class="sxs-lookup"><span data-stu-id="4308a-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)
