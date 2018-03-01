---
title: "Método IGCThreadControl::SuspensionStarting"
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
- IGCThreadControl.SuspensionStarting
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SuspensionStarting
helpviewer_keywords:
- IGCThreadControl::SuspensionStarting method [.NET Framework hosting]
- SuspensionStarting method, IGCThreadControl interface [.NET Framework hosting]
ms.assetid: 0af312af-98e9-415e-b182-42e80a1aee51
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6da39ec675cafcd51a5d748d4cbe8f9fd376eff8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="igcthreadcontrolsuspensionstarting-method"></a><span data-ttu-id="e9669-102">Método IGCThreadControl::SuspensionStarting</span><span class="sxs-lookup"><span data-stu-id="e9669-102">IGCThreadControl::SuspensionStarting Method</span></span>
<span data-ttu-id="e9669-103">Notifica o host que o tempo de execução está começando a suspensão de um thread para uma coleta de lixo ou outros suspensão.</span><span class="sxs-lookup"><span data-stu-id="e9669-103">Notifies the host that the runtime is beginning a thread suspension for a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9669-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e9669-104">Syntax</span></span>  
  
```  
HRESULT SuspensionStarting ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="e9669-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="e9669-105">Remarks</span></span>  
 <span data-ttu-id="e9669-106">Não reagendar qualquer threads durante o `SuspensionStarting` retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="e9669-106">Do not reschedule any threads during the `SuspensionStarting` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9669-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e9669-107">Requirements</span></span>  
 <span data-ttu-id="e9669-108">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9669-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9669-109">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e9669-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e9669-110">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="e9669-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e9669-111">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9669-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9669-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e9669-112">See Also</span></span>  
 [<span data-ttu-id="e9669-113">Interface IGCThreadControl</span><span class="sxs-lookup"><span data-stu-id="e9669-113">IGCThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)
