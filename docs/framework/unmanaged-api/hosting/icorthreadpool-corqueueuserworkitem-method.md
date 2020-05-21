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
ms.openlocfilehash: 5500f2b84f00e039cbc3f669b49be467789955f0
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762728"
---
# <a name="icorthreadpoolcorqueueuserworkitem-method"></a><span data-ttu-id="e9c54-102">Método ICorThreadpool::CorQueueUserWorkItem</span><span class="sxs-lookup"><span data-stu-id="e9c54-102">ICorThreadpool::CorQueueUserWorkItem Method</span></span>
<span data-ttu-id="e9c54-103">Esse método oferece suporte a infraestrutura do .NET Framework e não se destina a ser usado diretamente do seu código.</span><span class="sxs-lookup"><span data-stu-id="e9c54-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9c54-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e9c54-104">Syntax</span></span>  
  
```cpp  
HRESULT CorQueueUserWorkItem (  
    [in] LPTHREAD_START_ROUTINE Function,  
    [in] PVOID                  Context,  
    [in] BOOL                   executeOnlyOnce,  
    [out] BOOL*                 result  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="e9c54-105">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e9c54-105">Requirements</span></span>  
 <span data-ttu-id="e9c54-106">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9c54-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9c54-107">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e9c54-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e9c54-108">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e9c54-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e9c54-109">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9c54-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9c54-110">Veja também</span><span class="sxs-lookup"><span data-stu-id="e9c54-110">See also</span></span>

- [<span data-ttu-id="e9c54-111">Interface ICorThreadpool</span><span class="sxs-lookup"><span data-stu-id="e9c54-111">ICorThreadpool Interface</span></span>](icorthreadpool-interface.md)
