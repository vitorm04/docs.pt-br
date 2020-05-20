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
ms.openlocfilehash: 1a56c3ebe4b1c528f9c6555bdfbf1270a438410d
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83617107"
---
# <a name="iapartmentcallbackdocallback-method"></a><span data-ttu-id="b9eaa-102">Método IApartmentCallback::DoCallback</span><span class="sxs-lookup"><span data-stu-id="b9eaa-102">IApartmentCallback::DoCallback Method</span></span>
<span data-ttu-id="b9eaa-103">Executa a função especificada em um apartamento.</span><span class="sxs-lookup"><span data-stu-id="b9eaa-103">Executes the specified function within an apartment.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9eaa-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b9eaa-104">Syntax</span></span>  
  
```cpp  
HRESULT _stdcall DoCallback(  
    [in] SIZE_T pFunc,  
    [in] SIZE_T pData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b9eaa-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b9eaa-105">Parameters</span></span>  
 `pFunc`  
 <span data-ttu-id="b9eaa-106">no Um ponteiro para a função a ser executada dentro do apartamento.</span><span class="sxs-lookup"><span data-stu-id="b9eaa-106">[in] A pointer to the function to be executed within the apartment.</span></span>  
  
 `pData`  
 <span data-ttu-id="b9eaa-107">no Um ponteiro para o argumento da função.</span><span class="sxs-lookup"><span data-stu-id="b9eaa-107">[in] A pointer to the function's argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9eaa-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b9eaa-108">Requirements</span></span>  
 <span data-ttu-id="b9eaa-109">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b9eaa-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9eaa-110">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b9eaa-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b9eaa-111">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b9eaa-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b9eaa-112">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9eaa-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9eaa-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="b9eaa-113">See also</span></span>

- [<span data-ttu-id="b9eaa-114">Interface IApartmentCallback</span><span class="sxs-lookup"><span data-stu-id="b9eaa-114">IApartmentCallback Interface</span></span>](iapartmentcallback-interface.md)
