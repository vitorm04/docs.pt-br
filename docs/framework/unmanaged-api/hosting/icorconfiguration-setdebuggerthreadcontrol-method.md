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
ms.openlocfilehash: 6fc141cbebe08f8d0974788409d5aef0f68d2878
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59205115"
---
# <a name="icorconfigurationsetdebuggerthreadcontrol-method"></a><span data-ttu-id="d34df-102">Método ICorConfiguration::SetDebuggerThreadControl</span><span class="sxs-lookup"><span data-stu-id="d34df-102">ICorConfiguration::SetDebuggerThreadControl Method</span></span>
<span data-ttu-id="d34df-103">Define a interface de retorno de chamada que os serviços de depuração chamará como threads de runtime (CLR) do common language são bloqueadas e desbloqueadas para depuração.</span><span class="sxs-lookup"><span data-stu-id="d34df-103">Sets the callback interface that the debugging services will call as common language runtime (CLR) threads are blocked and unblocked for debugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d34df-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d34df-104">Syntax</span></span>  
  
```  
HRESULT SetDebuggerThreadControl (  
    [in] IDebuggerThreadControl* pDebuggerThreadControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d34df-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d34df-105">Parameters</span></span>  
 `pDebuggerThreadControl`  
 <span data-ttu-id="d34df-106">[in] Um ponteiro para um [IDebuggerThreadControl](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md) objeto que notifica o host sobre o bloqueio e desbloqueio de segmentos pelos serviços de depuração.</span><span class="sxs-lookup"><span data-stu-id="d34df-106">[in] A pointer to an [IDebuggerThreadControl](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md) object that notifies the host about the blocking and unblocking of threads by the debugging services.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d34df-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d34df-107">Requirements</span></span>  
 <span data-ttu-id="d34df-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d34df-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d34df-109">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d34df-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d34df-110">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="d34df-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="d34df-111">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="d34df-111">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d34df-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d34df-112">See also</span></span>

- [<span data-ttu-id="d34df-113">Interface ICorConfiguration</span><span class="sxs-lookup"><span data-stu-id="d34df-113">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)
