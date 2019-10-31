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
ms.openlocfilehash: 72f7bee79e74c69acff90861ceada8a91afe2157
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134914"
---
# <a name="idebuggerthreadcontrolstartblockingfordebugger-method"></a><span data-ttu-id="0832c-102">Método IDebuggerThreadControl::StartBlockingForDebugger</span><span class="sxs-lookup"><span data-stu-id="0832c-102">IDebuggerThreadControl::StartBlockingForDebugger Method</span></span>
<span data-ttu-id="0832c-103">Notifica o host de que os serviços de depuração estão prestes a começar a bloquear todos os threads.</span><span class="sxs-lookup"><span data-stu-id="0832c-103">Notifies the host that the debugging services are about to start blocking all threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0832c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0832c-104">Syntax</span></span>  
  
```cpp  
HRESULT StartBlockingForDebugger (  
    [in] DWORD dwUnused  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0832c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0832c-105">Parameters</span></span>  
 `dwUnused`  
 <span data-ttu-id="0832c-106">no Reservado para uso futuro.</span><span class="sxs-lookup"><span data-stu-id="0832c-106">[in] Reserved for future use.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0832c-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="0832c-107">Remarks</span></span>  
 <span data-ttu-id="0832c-108">O método `StartBlockingForDebugger` pode ser chamado em um thread de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="0832c-108">The `StartBlockingForDebugger` method could be called on a runtime thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0832c-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0832c-109">Requirements</span></span>  
 <span data-ttu-id="0832c-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0832c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0832c-111">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0832c-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0832c-112">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="0832c-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0832c-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0832c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0832c-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0832c-114">See also</span></span>

- [<span data-ttu-id="0832c-115">Interface IDebuggerThreadControl</span><span class="sxs-lookup"><span data-stu-id="0832c-115">IDebuggerThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md)
