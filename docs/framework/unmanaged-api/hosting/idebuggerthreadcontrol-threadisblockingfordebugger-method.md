---
title: Método IDebuggerThreadControl::ThreadIsBlockingForDebugger
ms.date: 03/30/2017
api_name:
- IDebuggerThreadControl.ThreadIsBlockingForDebugger
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ThreadIsBlockingForDebugger
helpviewer_keywords:
- ThreadIsBlockingForDebugger method [.NET Framework hosting]
- IDebuggerThreadControl::ThreadIsBlockingForDebugger method [.NET Framework hosting]
ms.assetid: d4d7cb2d-69da-48b3-879a-1a8a68c9bfa8
topic_type:
- apiref
ms.openlocfilehash: f7cdc3fe9d52db56d0280bc602d3a9f2f54e8246
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805261"
---
# <a name="idebuggerthreadcontrolthreadisblockingfordebugger-method"></a><span data-ttu-id="57b68-102">Método IDebuggerThreadControl::ThreadIsBlockingForDebugger</span><span class="sxs-lookup"><span data-stu-id="57b68-102">IDebuggerThreadControl::ThreadIsBlockingForDebugger Method</span></span>
<span data-ttu-id="57b68-103">Notifica o host que o thread que está enviando esse retorno de chamada está prestes a ser bloqueado nos serviços de depuração.</span><span class="sxs-lookup"><span data-stu-id="57b68-103">Notifies the host that the thread that is sending this callback is about to block within the debugging services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57b68-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="57b68-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadIsBlockingForDebugger ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="57b68-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="57b68-105">Remarks</span></span>  
 <span data-ttu-id="57b68-106">O `ThreadIsBlockingForDebugger` método sempre será chamado em um thread de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="57b68-106">The `ThreadIsBlockingForDebugger` method will always be called on a runtime thread.</span></span>  
  
 <span data-ttu-id="57b68-107">O `ThreadIsBlockingForDebugger` método dá ao host uma oportunidade de executar outra ação enquanto o thread é bloqueado.</span><span class="sxs-lookup"><span data-stu-id="57b68-107">The `ThreadIsBlockingForDebugger` method gives the host an opportunity to perform another action while the thread blocks.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57b68-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="57b68-108">Requirements</span></span>  
 <span data-ttu-id="57b68-109">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="57b68-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57b68-110">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="57b68-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="57b68-111">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="57b68-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="57b68-112">**Versões do .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57b68-112">**NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57b68-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="57b68-113">See also</span></span>

- [<span data-ttu-id="57b68-114">Interface IDebuggerThreadControl</span><span class="sxs-lookup"><span data-stu-id="57b68-114">IDebuggerThreadControl Interface</span></span>](idebuggerthreadcontrol-interface.md)
