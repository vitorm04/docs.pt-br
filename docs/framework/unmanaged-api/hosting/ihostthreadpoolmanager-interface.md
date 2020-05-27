---
title: Interface IHostThreadPoolManager
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager
helpviewer_keywords:
- IHostThreadPoolManager interface [.NET Framework hosting]
ms.assetid: c3a2cd90-7c4e-4374-bb87-b41befb8344f
topic_type:
- apiref
ms.openlocfilehash: bac29b5950f1547c5c60ac716d40d2ef4b1a2cc2
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842473"
---
# <a name="ihostthreadpoolmanager-interface"></a><span data-ttu-id="6c682-102">Interface IHostThreadPoolManager</span><span class="sxs-lookup"><span data-stu-id="6c682-102">IHostThreadPoolManager Interface</span></span>
<span data-ttu-id="6c682-103">Fornece métodos que permitem que o Common Language Runtime (CLR) Configure o pool de threads e enfileirar itens de trabalho para o pool de threads.</span><span class="sxs-lookup"><span data-stu-id="6c682-103">Provides methods that enable the common language runtime (CLR) to configure the thread pool and to queue work items to the thread pool.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6c682-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="6c682-104">Methods</span></span>  
  
|<span data-ttu-id="6c682-105">Método</span><span class="sxs-lookup"><span data-stu-id="6c682-105">Method</span></span>|<span data-ttu-id="6c682-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="6c682-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6c682-107">Método GetAvailableThreads</span><span class="sxs-lookup"><span data-stu-id="6c682-107">GetAvailableThreads Method</span></span>](ihostthreadpoolmanager-getavailablethreads-method.md)|<span data-ttu-id="6c682-108">Obtém o número de threads no pool de threads que não estão processando itens de trabalho no momento.</span><span class="sxs-lookup"><span data-stu-id="6c682-108">Gets the number of threads in the thread pool that are not currently processing work items.</span></span>|  
|[<span data-ttu-id="6c682-109">Método GetMaxThreads</span><span class="sxs-lookup"><span data-stu-id="6c682-109">GetMaxThreads Method</span></span>](ihostthreadpoolmanager-getmaxthreads-method.md)|<span data-ttu-id="6c682-110">Obtém o número máximo de threads que o host mantém simultaneamente no pool de threads.</span><span class="sxs-lookup"><span data-stu-id="6c682-110">Gets the maximum number of threads that the host maintains concurrently in the thread pool.</span></span>|  
|[<span data-ttu-id="6c682-111">Método GetMinThreads</span><span class="sxs-lookup"><span data-stu-id="6c682-111">GetMinThreads Method</span></span>](ihostthreadpoolmanager-getminthreads-method.md)|<span data-ttu-id="6c682-112">Obtém o número mínimo de threads ociosos que o host mantém em antecipação de solicitações.</span><span class="sxs-lookup"><span data-stu-id="6c682-112">Gets the minimum number of idle threads that the host maintains in anticipation of requests.</span></span>|  
|[<span data-ttu-id="6c682-113">Método QueueUserWorkItem</span><span class="sxs-lookup"><span data-stu-id="6c682-113">QueueUserWorkItem Method</span></span>](ihostthreadpoolmanager-queueuserworkitem-method.md)|<span data-ttu-id="6c682-114">Enfileira uma função para execução e fornece um objeto que contém dados a serem usados pela função.</span><span class="sxs-lookup"><span data-stu-id="6c682-114">Queues a function for execution, and provides an object containing data to be used by the function.</span></span>|  
|[<span data-ttu-id="6c682-115">Método SetMaxThreads</span><span class="sxs-lookup"><span data-stu-id="6c682-115">SetMaxThreads Method</span></span>](ihostthreadpoolmanager-setmaxthreads-method.md)|<span data-ttu-id="6c682-116">Define o número máximo de threads que o host pode manter no pool de threads.</span><span class="sxs-lookup"><span data-stu-id="6c682-116">Sets the maximum number of threads that the host can maintain in the thread pool.</span></span>|  
|[<span data-ttu-id="6c682-117">Método SetMinThreads</span><span class="sxs-lookup"><span data-stu-id="6c682-117">SetMinThreads Method</span></span>](ihostthreadpoolmanager-setminthreads-method.md)|<span data-ttu-id="6c682-118">Define o número mínimo de threads ociosos que o host deve manter em antecipação de solicitações.</span><span class="sxs-lookup"><span data-stu-id="6c682-118">Sets the minimum number of idle threads that the host must maintain in anticipation of requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6c682-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="6c682-119">Remarks</span></span>  
 <span data-ttu-id="6c682-120">O host não é necessário para configurar o pool de threads usando os valores especificados em chamadas para `SetMaxThreads` os `SetMinThreads` métodos e.</span><span class="sxs-lookup"><span data-stu-id="6c682-120">The host is not required to configure the thread pool by using the values specified in calls to the `SetMaxThreads` and `SetMinThreads` methods.</span></span> <span data-ttu-id="6c682-121">Nesse caso, o host deve retornar um valor HRESULT de E_NOTIMPL desses métodos.</span><span class="sxs-lookup"><span data-stu-id="6c682-121">In this case, the host should return an HRESULT value of E_NOTIMPL from these methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c682-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6c682-122">Requirements</span></span>  
 <span data-ttu-id="6c682-123">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c682-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c682-124">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="6c682-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6c682-125">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="6c682-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6c682-126">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c682-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c682-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6c682-127">See also</span></span>

- <xref:System.Threading>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="6c682-128">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="6c682-128">Hosting Interfaces</span></span>](hosting-interfaces.md)
