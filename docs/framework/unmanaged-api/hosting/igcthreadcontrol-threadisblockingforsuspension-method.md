---
title: "Método IGCThreadControl::ThreadIsBlockingForSuspension"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IGCThreadControl.ThreadIsBlockingForSuspension
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ThreadIsBlockingForSuspension
helpviewer_keywords:
- IGCThreadControl::ThreadIsBlockingForSuspension method [.NET Framework hosting]
- ThreadIsBlockingForSuspension method [.NET Framework hosting]
ms.assetid: ed5b5b58-7db7-46b5-9e2c-278db7159cee
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0cb7cfbab18334f1892c24225311160179920f81
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="igcthreadcontrolthreadisblockingforsuspension-method"></a><span data-ttu-id="237bc-102">Método IGCThreadControl::ThreadIsBlockingForSuspension</span><span class="sxs-lookup"><span data-stu-id="237bc-102">IGCThreadControl::ThreadIsBlockingForSuspension Method</span></span>
<span data-ttu-id="237bc-103">Notifica o host que o thread que está fazendo a chamada está prestes a bloquear, talvez para outros suspensão ou de uma coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="237bc-103">Notifies the host that the thread that is making the call is about to block, perhaps for a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="237bc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="237bc-104">Syntax</span></span>  
  
```  
HRESULT ThreadIsBlockingForSuspension ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="237bc-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="237bc-105">Remarks</span></span>  
 <span data-ttu-id="237bc-106">O host pode escolher dentro de `ThreadIsBlockingForSuspension` retorno de chamada se reagendar um thread.</span><span class="sxs-lookup"><span data-stu-id="237bc-106">The host may choose within the `ThreadIsBlockingForSuspension` callback whether to reschedule a thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="237bc-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="237bc-107">Requirements</span></span>  
 <span data-ttu-id="237bc-108">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="237bc-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="237bc-109">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="237bc-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="237bc-110">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="237bc-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="237bc-111">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="237bc-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="237bc-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="237bc-112">See Also</span></span>  
 [<span data-ttu-id="237bc-113">Interface IGCThreadControl</span><span class="sxs-lookup"><span data-stu-id="237bc-113">IGCThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)
