---
title: Método IGCThreadControl::SuspensionStarting
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7613bc744ad4c2e172fc4f6dd7bf282fb3d9072c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59179745"
---
# <a name="igcthreadcontrolsuspensionstarting-method"></a><span data-ttu-id="3c234-102">Método IGCThreadControl::SuspensionStarting</span><span class="sxs-lookup"><span data-stu-id="3c234-102">IGCThreadControl::SuspensionStarting Method</span></span>
<span data-ttu-id="3c234-103">Notifica o host que o tempo de execução está começando a uma suspensão de thread para uma coleta de lixo ou outro suspensão.</span><span class="sxs-lookup"><span data-stu-id="3c234-103">Notifies the host that the runtime is beginning a thread suspension for a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c234-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3c234-104">Syntax</span></span>  
  
```  
HRESULT SuspensionStarting ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="3c234-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="3c234-105">Remarks</span></span>  
 <span data-ttu-id="3c234-106">Não reagendar os threads durante o `SuspensionStarting` retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="3c234-106">Do not reschedule any threads during the `SuspensionStarting` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c234-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3c234-107">Requirements</span></span>  
 <span data-ttu-id="3c234-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3c234-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c234-109">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3c234-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3c234-110">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="3c234-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="3c234-111">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="3c234-111">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3c234-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3c234-112">See also</span></span>

- [<span data-ttu-id="3c234-113">Interface IGCThreadControl</span><span class="sxs-lookup"><span data-stu-id="3c234-113">IGCThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)
