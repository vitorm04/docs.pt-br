---
title: Método ICorThreadpool::CorGetAvailableThreads
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorGetAvailableThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorGetAvailableThreads
helpviewer_keywords:
- CorGetAvailableThreads method [.NET Framework hosting]
- ICorThreadpool::CorGetAvailableThreads method [.NET Framework hosting]
ms.assetid: 0b09b750-0b86-4ba4-9621-041857cfe8ba
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 20b600eb50ca4992e20b991406d18a91feae5c54
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54574440"
---
# <a name="icorthreadpoolcorgetavailablethreads-method"></a><span data-ttu-id="9ed13-102">Método ICorThreadpool::CorGetAvailableThreads</span><span class="sxs-lookup"><span data-stu-id="9ed13-102">ICorThreadpool::CorGetAvailableThreads Method</span></span>
<span data-ttu-id="9ed13-103">Esse método oferece suporte a infraestrutura do .NET Framework e não se destina a ser usado diretamente do seu código.</span><span class="sxs-lookup"><span data-stu-id="9ed13-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ed13-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9ed13-104">Syntax</span></span>  
  
```  
HRESULT CorGetAvailableThreads (  
    [out] DWORD *AvailableWorkerThreads,  
    [out] DWORD *AvailableIOCompletionThreads  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="9ed13-105">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9ed13-105">Requirements</span></span>  
 <span data-ttu-id="9ed13-106">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ed13-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ed13-107">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9ed13-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9ed13-108">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="9ed13-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9ed13-109">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ed13-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ed13-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9ed13-110">See also</span></span>
- [<span data-ttu-id="9ed13-111">Interface ICorThreadpool</span><span class="sxs-lookup"><span data-stu-id="9ed13-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)
