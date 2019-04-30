---
title: Método IApartmentCallback::DoCallback
ms.date: 03/30/2017
api_name:
- IApartmentCallback.DoCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- DoCallback
helpviewer_keywords:
- IApartmentCallback::DoCallback method [.NET Framework hosting]
- DoCallback method [.NET Framework hosting]
ms.assetid: 8edad30c-30ff-4bee-813c-75525a82fc93
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 77a2ccaf6f972fadd8396378dc7777ec4c85120d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61970047"
---
# <a name="iapartmentcallbackdocallback-method"></a><span data-ttu-id="e0782-102">Método IApartmentCallback::DoCallback</span><span class="sxs-lookup"><span data-stu-id="e0782-102">IApartmentCallback::DoCallback Method</span></span>
<span data-ttu-id="e0782-103">Executa a função especificada em um apartment.</span><span class="sxs-lookup"><span data-stu-id="e0782-103">Executes the specified function within an apartment.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0782-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e0782-104">Syntax</span></span>  
  
```  
HRESULT _stdcall DoCallback(  
    [in] SIZE_T pFunc,  
    [in] SIZE_T pData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e0782-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e0782-105">Parameters</span></span>  
 `pFunc`  
 <span data-ttu-id="e0782-106">[in] Um ponteiro para a função a ser executada dentro do apartment.</span><span class="sxs-lookup"><span data-stu-id="e0782-106">[in] A pointer to the function to be executed within the apartment.</span></span>  
  
 `pData`  
 <span data-ttu-id="e0782-107">[in] Um ponteiro para o argumento da função.</span><span class="sxs-lookup"><span data-stu-id="e0782-107">[in] A pointer to the function's argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0782-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e0782-108">Requirements</span></span>  
 <span data-ttu-id="e0782-109">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e0782-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0782-110">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e0782-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e0782-111">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="e0782-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e0782-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0782-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0782-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e0782-113">See also</span></span>

- [<span data-ttu-id="e0782-114">Interface IApartmentCallback</span><span class="sxs-lookup"><span data-stu-id="e0782-114">IApartmentCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iapartmentcallback-interface.md)
