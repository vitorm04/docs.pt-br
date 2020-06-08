---
title: Interface ICLRIoCompletionManager
ms.date: 03/30/2017
api_name:
- ICLRIoCompletionManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRIoCompletionManager
helpviewer_keywords:
- ICLRIoCompletionManager interface [.NET Framework hosting]
ms.assetid: c6c3ace6-e5e7-4450-8cc5-a9a48208c493
topic_type:
- apiref
ms.openlocfilehash: 71afc5e9772f82b922e8f428e6d808e46d092704
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504206"
---
# <a name="iclriocompletionmanager-interface"></a><span data-ttu-id="d6180-102">Interface ICLRIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="d6180-102">ICLRIoCompletionManager Interface</span></span>
<span data-ttu-id="d6180-103">Implementa um método de retorno de chamada que permite ao host notificar o Common Language Runtime (CLR) do status de solicitações de e/s especificadas.</span><span class="sxs-lookup"><span data-stu-id="d6180-103">Implements a callback method that allows the host to notify the common language runtime (CLR) of the status of specified I/O requests.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d6180-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="d6180-104">Methods</span></span>  
  
|<span data-ttu-id="d6180-105">Método</span><span class="sxs-lookup"><span data-stu-id="d6180-105">Method</span></span>|<span data-ttu-id="d6180-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="d6180-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d6180-107">Método OnComplete</span><span class="sxs-lookup"><span data-stu-id="d6180-107">OnComplete Method</span></span>](iclriocompletionmanager-oncomplete-method.md)|<span data-ttu-id="d6180-108">Notifica o CLR sobre o status de uma solicitação de e/s que foi feita usando uma chamada para o método [IHostIoCompletionManager:: bind](ihostiocompletionmanager-bind-method.md) .</span><span class="sxs-lookup"><span data-stu-id="d6180-108">Notifies the CLR of the status of an I/O request that was made by using a call to the [IHostIoCompletionManager::Bind](ihostiocompletionmanager-bind-method.md) method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d6180-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="d6180-109">Remarks</span></span>  
 <span data-ttu-id="d6180-110">O host implementa a abstração de conclusão de e/s usando a interface [IHostIoCompletionManager](ihostiocompletionmanager-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="d6180-110">The host implements the I/O completion abstraction by using the [IHostIoCompletionManager](ihostiocompletionmanager-interface.md) interface.</span></span> <span data-ttu-id="d6180-111">O CLR faz solicitações de e/s por meio dessa interface, e o host notifica o tempo de execução do resultado de tais solicitações usando a `ICLRIoCompletionManager` interface.</span><span class="sxs-lookup"><span data-stu-id="d6180-111">The CLR makes I/O requests through this interface, and the host notifies the runtime of the outcome of such requests by using the `ICLRIoCompletionManager` interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6180-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d6180-112">Requirements</span></span>  
 <span data-ttu-id="d6180-113">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6180-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6180-114">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d6180-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d6180-115">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d6180-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d6180-116">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6180-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6180-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="d6180-117">See also</span></span>

- [<span data-ttu-id="d6180-118">Interface IHostIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="d6180-118">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
- [<span data-ttu-id="d6180-119">Interface IHostThreadPoolManager</span><span class="sxs-lookup"><span data-stu-id="d6180-119">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)
- [<span data-ttu-id="d6180-120">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="d6180-120">Hosting Interfaces</span></span>](hosting-interfaces.md)
