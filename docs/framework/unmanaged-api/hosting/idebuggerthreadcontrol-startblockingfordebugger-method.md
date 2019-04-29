---
title: Método IDebuggerThreadControl::StartBlockingForDebugger
ms.date: 03/30/2017
api_name:
- IDebuggerThreadControl.StartBlockingForDebugger
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StartBlockingForDebugger
helpviewer_keywords:
- IDebuggerThreadControl::StartBlockingForDebugger method [.NET Framework hosting]
- StartBlockingForDebugger method [.NET Framework hosting]
ms.assetid: 5c8f11b4-35d3-4c39-9bbd-58b896ba5ba6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dfc94c2de1a14842cc017e5c4ef6023154c20f2a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61699897"
---
# <a name="idebuggerthreadcontrolstartblockingfordebugger-method"></a><span data-ttu-id="6cd53-102">Método IDebuggerThreadControl::StartBlockingForDebugger</span><span class="sxs-lookup"><span data-stu-id="6cd53-102">IDebuggerThreadControl::StartBlockingForDebugger Method</span></span>
<span data-ttu-id="6cd53-103">Notifica o host que os serviços de depuração estão prestes a começar a bloquear todos os threads.</span><span class="sxs-lookup"><span data-stu-id="6cd53-103">Notifies the host that the debugging services are about to start blocking all threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6cd53-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6cd53-104">Syntax</span></span>  
  
```  
HRESULT StartBlockingForDebugger (  
    [in] DWORD dwUnused  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6cd53-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6cd53-105">Parameters</span></span>  
 `dwUnused`  
 <span data-ttu-id="6cd53-106">[in] Reservado para uso futuro.</span><span class="sxs-lookup"><span data-stu-id="6cd53-106">[in] Reserved for future use.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6cd53-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="6cd53-107">Remarks</span></span>  
 <span data-ttu-id="6cd53-108">O `StartBlockingForDebugger` método poderia ser chamado em um segmento de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="6cd53-108">The `StartBlockingForDebugger` method could be called on a runtime thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6cd53-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6cd53-109">Requirements</span></span>  
 <span data-ttu-id="6cd53-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6cd53-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6cd53-111">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6cd53-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6cd53-112">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="6cd53-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6cd53-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6cd53-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cd53-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6cd53-114">See also</span></span>

- [<span data-ttu-id="6cd53-115">Interface IDebuggerThreadControl</span><span class="sxs-lookup"><span data-stu-id="6cd53-115">IDebuggerThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md)
