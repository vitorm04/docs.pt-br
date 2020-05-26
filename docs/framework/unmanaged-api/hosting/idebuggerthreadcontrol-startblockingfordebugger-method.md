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
ms.openlocfilehash: 878dba37728734a777d2f95226b60bfbe9aae16a
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805266"
---
# <a name="idebuggerthreadcontrolstartblockingfordebugger-method"></a><span data-ttu-id="6f336-102">Método IDebuggerThreadControl::StartBlockingForDebugger</span><span class="sxs-lookup"><span data-stu-id="6f336-102">IDebuggerThreadControl::StartBlockingForDebugger Method</span></span>
<span data-ttu-id="6f336-103">Notifica o host de que os serviços de depuração estão prestes a começar a bloquear todos os threads.</span><span class="sxs-lookup"><span data-stu-id="6f336-103">Notifies the host that the debugging services are about to start blocking all threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f336-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6f336-104">Syntax</span></span>  
  
```cpp  
HRESULT StartBlockingForDebugger (  
    [in] DWORD dwUnused  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6f336-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6f336-105">Parameters</span></span>  
 `dwUnused`  
 <span data-ttu-id="6f336-106">no Reservado para uso futuro.</span><span class="sxs-lookup"><span data-stu-id="6f336-106">[in] Reserved for future use.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6f336-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="6f336-107">Remarks</span></span>  
 <span data-ttu-id="6f336-108">O `StartBlockingForDebugger` método pode ser chamado em um thread de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="6f336-108">The `StartBlockingForDebugger` method could be called on a runtime thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f336-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6f336-109">Requirements</span></span>  
 <span data-ttu-id="6f336-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6f336-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f336-111">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="6f336-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6f336-112">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="6f336-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6f336-113">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f336-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f336-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="6f336-114">See also</span></span>

- [<span data-ttu-id="6f336-115">Interface IDebuggerThreadControl</span><span class="sxs-lookup"><span data-stu-id="6f336-115">IDebuggerThreadControl Interface</span></span>](idebuggerthreadcontrol-interface.md)
