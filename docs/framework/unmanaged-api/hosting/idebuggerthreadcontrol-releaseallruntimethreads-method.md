---
title: "Método IDebuggerThreadControl::ReleaseAllRuntimeThreads"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IDebuggerThreadControl.ReleaseAllRuntimeThreads
api_location: mscoree.dll
api_type: COM
f1_keywords: ReleaseAllRuntimeThreads
helpviewer_keywords:
- ReleaseAllRuntimeThreads method [.NET Framework hosting]
- IDebuggerThreadControl::ReleaseAllRuntimeThreads method [.NET Framework hosting]
ms.assetid: 1a2995ff-5f02-4b49-84dc-3a5f9cfd7d55
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a087dbcff961ca1ac1cf03d30fdc336ec9ca0515
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="idebuggerthreadcontrolreleaseallruntimethreads-method"></a><span data-ttu-id="f8490-102">Método IDebuggerThreadControl::ReleaseAllRuntimeThreads</span><span class="sxs-lookup"><span data-stu-id="f8490-102">IDebuggerThreadControl::ReleaseAllRuntimeThreads Method</span></span>
<span data-ttu-id="f8490-103">Notifica o host que os serviços de depuração estão prestes a liberar todos os threads que estão bloqueados.</span><span class="sxs-lookup"><span data-stu-id="f8490-103">Notifies the host that the debugging services are about to release all threads that are blocked.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8490-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f8490-104">Syntax</span></span>  
  
```  
HRESULT ReleaseAllRuntimeThreads ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="f8490-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="f8490-105">Remarks</span></span>  
 <span data-ttu-id="f8490-106">O `ReleaseAllRuntimeThreads` método nunca será chamado em um thread de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="f8490-106">The `ReleaseAllRuntimeThreads` method will never be called on a runtime thread.</span></span> <span data-ttu-id="f8490-107">Se o host tiver um thread de tempo de execução bloqueado, ele deve liberá-lo agora.</span><span class="sxs-lookup"><span data-stu-id="f8490-107">If the host has a runtime thread blocked, it should release it now.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8490-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f8490-108">Requirements</span></span>  
 <span data-ttu-id="f8490-109">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f8490-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8490-110">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f8490-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f8490-111">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="f8490-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f8490-112">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8490-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8490-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f8490-113">See Also</span></span>  
 [<span data-ttu-id="f8490-114">Interface IDebuggerThreadControl</span><span class="sxs-lookup"><span data-stu-id="f8490-114">IDebuggerThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md)
