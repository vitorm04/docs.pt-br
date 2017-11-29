---
title: "Método ICorThreadpool::CorUnregisterWait"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorThreadpool.CorUnregisterWait
api_location: mscoree.dll
api_type: COM
f1_keywords: CorUnregisterWait
helpviewer_keywords:
- CorUnregisterWait method [.NET Framework hosting]
- ICorThreadpool::CorUnregisterWait method [.NET Framework hosting]
ms.assetid: 42c933f1-30a8-4011-bdea-e117f3c3265e
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: db8de73324073f9b2e970a7ee17ba7c9ba23f84e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icorthreadpoolcorunregisterwait-method"></a><span data-ttu-id="f2cac-102">Método ICorThreadpool::CorUnregisterWait</span><span class="sxs-lookup"><span data-stu-id="f2cac-102">ICorThreadpool::CorUnregisterWait Method</span></span>
<span data-ttu-id="f2cac-103">Esse método oferece suporte a infraestrutura do .NET Framework e não se destina a ser usado diretamente do seu código.</span><span class="sxs-lookup"><span data-stu-id="f2cac-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2cac-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f2cac-104">Syntax</span></span>  
  
```  
HRESULT CorUnregisterWait (  
    [in] HANDLE hWaitObject,  
    [in] HANDLE CompletionEvent,  
    [out] BOOL* result  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="f2cac-105">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f2cac-105">Requirements</span></span>  
 <span data-ttu-id="f2cac-106">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2cac-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2cac-107">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f2cac-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f2cac-108">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="f2cac-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f2cac-109">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2cac-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2cac-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f2cac-110">See Also</span></span>  
 [<span data-ttu-id="f2cac-111">Interface ICorThreadpool</span><span class="sxs-lookup"><span data-stu-id="f2cac-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)
