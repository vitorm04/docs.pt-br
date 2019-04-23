---
title: Método IDebuggerThreadControl::ReleaseAllRuntimeThreads
ms.date: 03/30/2017
api_name:
- IDebuggerThreadControl.ReleaseAllRuntimeThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ReleaseAllRuntimeThreads
helpviewer_keywords:
- ReleaseAllRuntimeThreads method [.NET Framework hosting]
- IDebuggerThreadControl::ReleaseAllRuntimeThreads method [.NET Framework hosting]
ms.assetid: 1a2995ff-5f02-4b49-84dc-3a5f9cfd7d55
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 136dab5c05c310d85a5e18bcdc6da0de901d3ace
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59227464"
---
# <a name="idebuggerthreadcontrolreleaseallruntimethreads-method"></a><span data-ttu-id="c97f9-102">Método IDebuggerThreadControl::ReleaseAllRuntimeThreads</span><span class="sxs-lookup"><span data-stu-id="c97f9-102">IDebuggerThreadControl::ReleaseAllRuntimeThreads Method</span></span>
<span data-ttu-id="c97f9-103">Notifica o host que os serviços de depuração estão prestes a liberar todos os threads que estão bloqueados.</span><span class="sxs-lookup"><span data-stu-id="c97f9-103">Notifies the host that the debugging services are about to release all threads that are blocked.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c97f9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c97f9-104">Syntax</span></span>  
  
```  
HRESULT ReleaseAllRuntimeThreads ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="c97f9-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="c97f9-105">Remarks</span></span>  
 <span data-ttu-id="c97f9-106">O `ReleaseAllRuntimeThreads` método nunca será chamado em um segmento de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="c97f9-106">The `ReleaseAllRuntimeThreads` method will never be called on a runtime thread.</span></span> <span data-ttu-id="c97f9-107">Se o host tiver um segmento de tempo de execução bloqueado, ele deverá liberá-lo agora.</span><span class="sxs-lookup"><span data-stu-id="c97f9-107">If the host has a runtime thread blocked, it should release it now.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c97f9-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c97f9-108">Requirements</span></span>  
 <span data-ttu-id="c97f9-109">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c97f9-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c97f9-110">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c97f9-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c97f9-111">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="c97f9-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c97f9-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c97f9-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c97f9-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c97f9-113">See also</span></span>

- [<span data-ttu-id="c97f9-114">Interface IDebuggerThreadControl</span><span class="sxs-lookup"><span data-stu-id="c97f9-114">IDebuggerThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md)
