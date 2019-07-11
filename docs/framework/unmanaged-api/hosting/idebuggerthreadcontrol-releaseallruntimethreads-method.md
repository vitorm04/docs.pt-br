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
ms.openlocfilehash: 09895294c4678cdb1dd033076cfb42853aa06b2e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780500"
---
# <a name="idebuggerthreadcontrolreleaseallruntimethreads-method"></a><span data-ttu-id="44e33-102">Método IDebuggerThreadControl::ReleaseAllRuntimeThreads</span><span class="sxs-lookup"><span data-stu-id="44e33-102">IDebuggerThreadControl::ReleaseAllRuntimeThreads Method</span></span>
<span data-ttu-id="44e33-103">Notifica o host que os serviços de depuração estão prestes a liberar todos os threads que estão bloqueados.</span><span class="sxs-lookup"><span data-stu-id="44e33-103">Notifies the host that the debugging services are about to release all threads that are blocked.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44e33-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="44e33-104">Syntax</span></span>  
  
```cpp  
HRESULT ReleaseAllRuntimeThreads ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="44e33-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="44e33-105">Remarks</span></span>  
 <span data-ttu-id="44e33-106">O `ReleaseAllRuntimeThreads` método nunca será chamado em um segmento de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="44e33-106">The `ReleaseAllRuntimeThreads` method will never be called on a runtime thread.</span></span> <span data-ttu-id="44e33-107">Se o host tiver um segmento de tempo de execução bloqueado, ele deverá liberá-lo agora.</span><span class="sxs-lookup"><span data-stu-id="44e33-107">If the host has a runtime thread blocked, it should release it now.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44e33-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="44e33-108">Requirements</span></span>  
 <span data-ttu-id="44e33-109">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="44e33-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44e33-110">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="44e33-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="44e33-111">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="44e33-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="44e33-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44e33-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44e33-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="44e33-113">See also</span></span>

- [<span data-ttu-id="44e33-114">Interface IDebuggerThreadControl</span><span class="sxs-lookup"><span data-stu-id="44e33-114">IDebuggerThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md)
