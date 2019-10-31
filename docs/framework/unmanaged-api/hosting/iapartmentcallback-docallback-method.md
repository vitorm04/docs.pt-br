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
ms.openlocfilehash: 9bb257a3d84d5022b9ae13c89a34572485d3033b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126952"
---
# <a name="iapartmentcallbackdocallback-method"></a><span data-ttu-id="fef88-102">Método IApartmentCallback::DoCallback</span><span class="sxs-lookup"><span data-stu-id="fef88-102">IApartmentCallback::DoCallback Method</span></span>
<span data-ttu-id="fef88-103">Executa a função especificada em um apartamento.</span><span class="sxs-lookup"><span data-stu-id="fef88-103">Executes the specified function within an apartment.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fef88-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fef88-104">Syntax</span></span>  
  
```cpp  
HRESULT _stdcall DoCallback(  
    [in] SIZE_T pFunc,  
    [in] SIZE_T pData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fef88-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="fef88-105">Parameters</span></span>  
 `pFunc`  
 <span data-ttu-id="fef88-106">no Um ponteiro para a função a ser executada dentro do apartamento.</span><span class="sxs-lookup"><span data-stu-id="fef88-106">[in] A pointer to the function to be executed within the apartment.</span></span>  
  
 `pData`  
 <span data-ttu-id="fef88-107">no Um ponteiro para o argumento da função.</span><span class="sxs-lookup"><span data-stu-id="fef88-107">[in] A pointer to the function's argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fef88-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fef88-108">Requirements</span></span>  
 <span data-ttu-id="fef88-109">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fef88-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fef88-110">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="fef88-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fef88-111">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="fef88-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fef88-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fef88-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fef88-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fef88-113">See also</span></span>

- [<span data-ttu-id="fef88-114">Interface IApartmentCallback</span><span class="sxs-lookup"><span data-stu-id="fef88-114">IApartmentCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iapartmentcallback-interface.md)
