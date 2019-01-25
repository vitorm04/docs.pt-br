---
title: Método ICorThreadpool::CorUnregisterWait
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorUnregisterWait
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorUnregisterWait
helpviewer_keywords:
- CorUnregisterWait method [.NET Framework hosting]
- ICorThreadpool::CorUnregisterWait method [.NET Framework hosting]
ms.assetid: 42c933f1-30a8-4011-bdea-e117f3c3265e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eacc9152200b9b57e8a1c5506ecac2e0010fbe9f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54698967"
---
# <a name="icorthreadpoolcorunregisterwait-method"></a><span data-ttu-id="73d80-102">Método ICorThreadpool::CorUnregisterWait</span><span class="sxs-lookup"><span data-stu-id="73d80-102">ICorThreadpool::CorUnregisterWait Method</span></span>
<span data-ttu-id="73d80-103">Esse método oferece suporte a infraestrutura do .NET Framework e não se destina a ser usado diretamente do seu código.</span><span class="sxs-lookup"><span data-stu-id="73d80-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73d80-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="73d80-104">Syntax</span></span>  
  
```  
HRESULT CorUnregisterWait (  
    [in] HANDLE hWaitObject,  
    [in] HANDLE CompletionEvent,  
    [out] BOOL* result  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="73d80-105">Requisitos</span><span class="sxs-lookup"><span data-stu-id="73d80-105">Requirements</span></span>  
 <span data-ttu-id="73d80-106">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73d80-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73d80-107">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="73d80-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="73d80-108">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="73d80-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="73d80-109">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73d80-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73d80-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="73d80-110">See also</span></span>
- [<span data-ttu-id="73d80-111">Interface ICorThreadpool</span><span class="sxs-lookup"><span data-stu-id="73d80-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)
