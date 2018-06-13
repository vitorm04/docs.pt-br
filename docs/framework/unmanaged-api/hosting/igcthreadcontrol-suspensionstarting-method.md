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
ms.openlocfilehash: 95cbda3729c02b95557f9f700f1ea7c68aa450a1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33438009"
---
# <a name="igcthreadcontrolsuspensionstarting-method"></a><span data-ttu-id="d6614-102">Método IGCThreadControl::SuspensionStarting</span><span class="sxs-lookup"><span data-stu-id="d6614-102">IGCThreadControl::SuspensionStarting Method</span></span>
<span data-ttu-id="d6614-103">Notifica o host que o tempo de execução está começando a suspensão de um thread para uma coleta de lixo ou outros suspensão.</span><span class="sxs-lookup"><span data-stu-id="d6614-103">Notifies the host that the runtime is beginning a thread suspension for a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6614-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d6614-104">Syntax</span></span>  
  
```  
HRESULT SuspensionStarting ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="d6614-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="d6614-105">Remarks</span></span>  
 <span data-ttu-id="d6614-106">Não reagendar qualquer threads durante o `SuspensionStarting` retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="d6614-106">Do not reschedule any threads during the `SuspensionStarting` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6614-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d6614-107">Requirements</span></span>  
 <span data-ttu-id="d6614-108">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6614-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6614-109">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d6614-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d6614-110">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="d6614-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d6614-111">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6614-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6614-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d6614-112">See Also</span></span>  
 [<span data-ttu-id="d6614-113">Interface IGCThreadControl</span><span class="sxs-lookup"><span data-stu-id="d6614-113">IGCThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)
