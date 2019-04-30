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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61992752"
---
# <a name="igcthreadcontrolsuspensionstarting-method"></a><span data-ttu-id="ce63f-102">Método IGCThreadControl::SuspensionStarting</span><span class="sxs-lookup"><span data-stu-id="ce63f-102">IGCThreadControl::SuspensionStarting Method</span></span>
<span data-ttu-id="ce63f-103">Notifica o host que o tempo de execução está começando a uma suspensão de thread para uma coleta de lixo ou outro suspensão.</span><span class="sxs-lookup"><span data-stu-id="ce63f-103">Notifies the host that the runtime is beginning a thread suspension for a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce63f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ce63f-104">Syntax</span></span>  
  
```  
HRESULT SuspensionStarting ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="ce63f-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="ce63f-105">Remarks</span></span>  
 <span data-ttu-id="ce63f-106">Não reagendar os threads durante o `SuspensionStarting` retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="ce63f-106">Do not reschedule any threads during the `SuspensionStarting` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce63f-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ce63f-107">Requirements</span></span>  
 <span data-ttu-id="ce63f-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ce63f-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce63f-109">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ce63f-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ce63f-110">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="ce63f-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ce63f-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce63f-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce63f-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ce63f-112">See also</span></span>

- [<span data-ttu-id="ce63f-113">Interface IGCThreadControl</span><span class="sxs-lookup"><span data-stu-id="ce63f-113">IGCThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)
