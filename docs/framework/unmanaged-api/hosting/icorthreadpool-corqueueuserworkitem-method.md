---
title: Método ICorThreadpool::CorQueueUserWorkItem
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorQueueUserWorkItem
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorQueueUserWorkItem
helpviewer_keywords:
- ICorThreadpool::CorQueueUserWorkItem method [.NET Framework hosting]
- CorQueueUserWorkItem method [.NET Framework hosting]
ms.assetid: 29ac7898-a7c7-433e-8f79-cd5237e0bab8
topic_type:
- apiref
ms.openlocfilehash: e4a62cc35de18f91324bfd428c24bb329fc9783b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133259"
---
# <a name="icorthreadpoolcorqueueuserworkitem-method"></a><span data-ttu-id="c97cc-102">Método ICorThreadpool::CorQueueUserWorkItem</span><span class="sxs-lookup"><span data-stu-id="c97cc-102">ICorThreadpool::CorQueueUserWorkItem Method</span></span>
<span data-ttu-id="c97cc-103">Esse método oferece suporte a infraestrutura do .NET Framework e não se destina a ser usado diretamente do seu código.</span><span class="sxs-lookup"><span data-stu-id="c97cc-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c97cc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c97cc-104">Syntax</span></span>  
  
```cpp  
HRESULT CorQueueUserWorkItem (  
    [in] LPTHREAD_START_ROUTINE Function,  
    [in] PVOID                  Context,  
    [in] BOOL                   executeOnlyOnce,  
    [out] BOOL*                 result  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="c97cc-105">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c97cc-105">Requirements</span></span>  
 <span data-ttu-id="c97cc-106">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c97cc-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c97cc-107">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c97cc-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c97cc-108">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c97cc-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c97cc-109">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c97cc-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c97cc-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c97cc-110">See also</span></span>

- [<span data-ttu-id="c97cc-111">Interface ICorThreadpool</span><span class="sxs-lookup"><span data-stu-id="c97cc-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)
