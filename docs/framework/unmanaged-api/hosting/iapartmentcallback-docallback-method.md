---
title: "Método IApartmentCallback::DoCallback"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IApartmentCallback.DoCallback
api_location: mscoree.dll
api_type: COM
f1_keywords: DoCallback
helpviewer_keywords:
- IApartmentCallback::DoCallback method [.NET Framework hosting]
- DoCallback method [.NET Framework hosting]
ms.assetid: 8edad30c-30ff-4bee-813c-75525a82fc93
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 03c72af5fba0871433e46c2b8045c55bbf0a5ff6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="iapartmentcallbackdocallback-method"></a><span data-ttu-id="32ece-102">Método IApartmentCallback::DoCallback</span><span class="sxs-lookup"><span data-stu-id="32ece-102">IApartmentCallback::DoCallback Method</span></span>
<span data-ttu-id="32ece-103">Executa a função especificada em um apartment.</span><span class="sxs-lookup"><span data-stu-id="32ece-103">Executes the specified function within an apartment.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32ece-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="32ece-104">Syntax</span></span>  
  
```  
HRESULT _stdcall DoCallback(  
    [in] SIZE_T pFunc,  
    [in] SIZE_T pData  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="32ece-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="32ece-105">Parameters</span></span>  
 `pFunc`  
 <span data-ttu-id="32ece-106">[in] Um ponteiro para a função a ser executada dentro do compartimento.</span><span class="sxs-lookup"><span data-stu-id="32ece-106">[in] A pointer to the function to be executed within the apartment.</span></span>  
  
 `pData`  
 <span data-ttu-id="32ece-107">[in] Um ponteiro para o argumento da função.</span><span class="sxs-lookup"><span data-stu-id="32ece-107">[in] A pointer to the function's argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32ece-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="32ece-108">Requirements</span></span>  
 <span data-ttu-id="32ece-109">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="32ece-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32ece-110">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="32ece-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="32ece-111">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="32ece-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="32ece-112">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32ece-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32ece-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="32ece-113">See Also</span></span>  
 [<span data-ttu-id="32ece-114">Interface IApartmentCallback</span><span class="sxs-lookup"><span data-stu-id="32ece-114">IApartmentCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iapartmentcallback-interface.md)
