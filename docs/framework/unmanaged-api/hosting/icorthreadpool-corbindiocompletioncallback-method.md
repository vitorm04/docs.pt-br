---
title: Método ICorThreadpool::CorBindIoCompletionCallback
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorBindIoCompletionCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorBindIoCompletionCallback
helpviewer_keywords:
- CorBindIoCompletionCallback method [.NET Framework hosting]
- ICorThreadpool::CorBindIoCompletionCallback method [.NET Framework hosting]
ms.assetid: 2b159225-f09c-42f1-aa7c-44087e121249
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b3faffbf9dc85c563dac84fc2e4e4d849db5d42d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59148519"
---
# <a name="icorthreadpoolcorbindiocompletioncallback-method"></a><span data-ttu-id="fb0d2-102">Método ICorThreadpool::CorBindIoCompletionCallback</span><span class="sxs-lookup"><span data-stu-id="fb0d2-102">ICorThreadpool::CorBindIoCompletionCallback Method</span></span>
<span data-ttu-id="fb0d2-103">Esse método oferece suporte a infraestrutura do .NET Framework e não se destina a ser usado diretamente do seu código.</span><span class="sxs-lookup"><span data-stu-id="fb0d2-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb0d2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fb0d2-104">Syntax</span></span>  
  
```  
HRESULT CorBindIoCompletionCallback (  
    [in] HANDLE                          fileHandle,  
    [in] LPOVERLAPPED_COMPLETION_ROUTINE callback  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="fb0d2-105">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fb0d2-105">Requirements</span></span>  
 <span data-ttu-id="fb0d2-106">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb0d2-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb0d2-107">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="fb0d2-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fb0d2-108">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="fb0d2-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="fb0d2-109">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="fb0d2-109">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="fb0d2-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fb0d2-110">See also</span></span>

- [<span data-ttu-id="fb0d2-111">Interface ICorThreadpool</span><span class="sxs-lookup"><span data-stu-id="fb0d2-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)
