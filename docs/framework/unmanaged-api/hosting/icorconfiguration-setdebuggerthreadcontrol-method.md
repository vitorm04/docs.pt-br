---
title: Método ICorConfiguration::SetDebuggerThreadControl
ms.date: 03/30/2017
api_name:
- ICorConfiguration.SetDebuggerThreadControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SetDebuggerThreadControl
helpviewer_keywords:
- SetDebuggerThreadControl method [.NET Framework hosting]
- ICorConfiguration::SetDebuggerThreadControl method [.NET Framework hosting]
ms.assetid: 1ded7639-dacb-4db1-961c-d1ceaec01959
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1cecbbd7509fcd4f79aeb6e2711e8b7604c2f3a9
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57489683"
---
# <a name="icorconfigurationsetdebuggerthreadcontrol-method"></a><span data-ttu-id="677ec-102">Método ICorConfiguration::SetDebuggerThreadControl</span><span class="sxs-lookup"><span data-stu-id="677ec-102">ICorConfiguration::SetDebuggerThreadControl Method</span></span>
<span data-ttu-id="677ec-103">Define a interface de retorno de chamada que os serviços de depuração chamará como threads de runtime (CLR) do common language são bloqueadas e desbloqueadas para depuração.</span><span class="sxs-lookup"><span data-stu-id="677ec-103">Sets the callback interface that the debugging services will call as common language runtime (CLR) threads are blocked and unblocked for debugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="677ec-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="677ec-104">Syntax</span></span>  
  
```  
HRESULT SetDebuggerThreadControl (  
    [in] IDebuggerThreadControl* pDebuggerThreadControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="677ec-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="677ec-105">Parameters</span></span>  
 `pDebuggerThreadControl`  
 <span data-ttu-id="677ec-106">[in] Um ponteiro para um [IDebuggerThreadControl](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md) objeto que notifica o host sobre o bloqueio e desbloqueio de segmentos pelos serviços de depuração.</span><span class="sxs-lookup"><span data-stu-id="677ec-106">[in] A pointer to an [IDebuggerThreadControl](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md) object that notifies the host about the blocking and unblocking of threads by the debugging services.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="677ec-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="677ec-107">Requirements</span></span>  
 <span data-ttu-id="677ec-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="677ec-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="677ec-109">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="677ec-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="677ec-110">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="677ec-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="677ec-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="677ec-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="677ec-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="677ec-112">See also</span></span>
- [<span data-ttu-id="677ec-113">Interface ICorConfiguration</span><span class="sxs-lookup"><span data-stu-id="677ec-113">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)
