---
title: Método IGCThreadControl::SuspensionEnding
ms.date: 03/30/2017
api_name:
- IGCThreadControl.SuspensionEnding
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SuspensionEnding
helpviewer_keywords:
- IGCThreadControl::SuspensionEnding method [.NET Framework hosting]
- SuspensionEnding method, IGCThreadControl interface [.NET Framework hosting]
ms.assetid: 70814265-c734-4ddc-9502-fe8b28d2b414
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ffee1550c64f1ce7c438580ce78a497aeeb99f3a
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57468761"
---
# <a name="igcthreadcontrolsuspensionending-method"></a><span data-ttu-id="695aa-102">Método IGCThreadControl::SuspensionEnding</span><span class="sxs-lookup"><span data-stu-id="695aa-102">IGCThreadControl::SuspensionEnding Method</span></span>
<span data-ttu-id="695aa-103">Notifica o host que o tempo de execução está retomando threads após uma coleta de lixo ou outro suspensão.</span><span class="sxs-lookup"><span data-stu-id="695aa-103">Notifies the host that the runtime is resuming threads after a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="695aa-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="695aa-104">Syntax</span></span>  
  
```  
HRESULT SuspensionEnding (  
    [in] DWORD Generation  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="695aa-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="695aa-105">Parameters</span></span>  
 `Generation`  
 <span data-ttu-id="695aa-106">[in] A geração no qual uma coleta de lixo foi executada.</span><span class="sxs-lookup"><span data-stu-id="695aa-106">[in] The generation on which a garbage collection has been performed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="695aa-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="695aa-107">Remarks</span></span>  
 <span data-ttu-id="695aa-108">Não reagendar os threads durante o `SuspensionEnding` retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="695aa-108">Do not reschedule any threads during the `SuspensionEnding` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="695aa-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="695aa-109">Requirements</span></span>  
 <span data-ttu-id="695aa-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="695aa-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="695aa-111">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="695aa-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="695aa-112">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="695aa-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="695aa-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="695aa-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="695aa-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="695aa-114">See also</span></span>
- [<span data-ttu-id="695aa-115">Interface IGCThreadControl</span><span class="sxs-lookup"><span data-stu-id="695aa-115">IGCThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)
