---
title: "Método ICorConfiguration::SetGCThreadControl"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorConfiguration.SetGCThreadControl
api_location: mscoree.dll
api_type: COM
f1_keywords: SetGCThreadControl
helpviewer_keywords:
- ICorConfiguration::SetGCThreadControl method [.NET Framework hosting]
- SetGCThreadControl method [.NET Framework hosting]
ms.assetid: 72e38e61-3d56-4ae3-b8f6-0ab7922aaf11
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1dfcff8a12f808c75a9e69486f802f8b886c468b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icorconfigurationsetgcthreadcontrol-method"></a><span data-ttu-id="a69c5-102">Método ICorConfiguration::SetGCThreadControl</span><span class="sxs-lookup"><span data-stu-id="a69c5-102">ICorConfiguration::SetGCThreadControl Method</span></span>
<span data-ttu-id="a69c5-103">Define a interface de retorno de chamada para o agendamento de threads para tarefas de tempo de execução não seriam bloqueadas caso contrário, uma coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="a69c5-103">Sets the callback interface for scheduling threads for non-runtime tasks that would otherwise be blocked for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a69c5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a69c5-104">Syntax</span></span>  
  
```  
HRESULT SetGCThreadControl (  
    [in] IGCThreadControl* pGCThreadControl  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a69c5-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a69c5-105">Parameters</span></span>  
 `pGCThreadControl`  
 <span data-ttu-id="a69c5-106">[in] Um ponteiro para um [IGCThreadControl](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md) objeto que notifica o host sobre a suspensão de threads para tarefas de tempo de execução não.</span><span class="sxs-lookup"><span data-stu-id="a69c5-106">[in] A pointer to an [IGCThreadControl](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md) object that notifies the host about the suspension of threads for non-runtime tasks.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a69c5-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="a69c5-107">Remarks</span></span>  
 <span data-ttu-id="a69c5-108">O host pode escolher dentro de [Igcthreadcontrol](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-threadisblockingforsuspension-method.md) retorno de chamada se reagendar um thread.</span><span class="sxs-lookup"><span data-stu-id="a69c5-108">The host may choose within the [IGCThreadControl::ThreadIsBlockingForSuspension](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-threadisblockingforsuspension-method.md) callback whether to reschedule a thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a69c5-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a69c5-109">Requirements</span></span>  
 <span data-ttu-id="a69c5-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a69c5-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a69c5-111">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a69c5-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a69c5-112">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="a69c5-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a69c5-113">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a69c5-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a69c5-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a69c5-114">See Also</span></span>  
 [<span data-ttu-id="a69c5-115">Interface ICorConfiguration</span><span class="sxs-lookup"><span data-stu-id="a69c5-115">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)
