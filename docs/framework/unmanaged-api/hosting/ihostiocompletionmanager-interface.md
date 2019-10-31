---
title: Interface IHostIoCompletionManager
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager
helpviewer_keywords:
- IHostIoCompletionManager interface [.NET Framework hosting]
ms.assetid: c28d1983-83f7-46e2-990f-dbb9dc07c818
topic_type:
- apiref
ms.openlocfilehash: 51d79c398c94ec355528140325da2c25422cbad9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133854"
---
# <a name="ihostiocompletionmanager-interface"></a><span data-ttu-id="9b00c-102">Interface IHostIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="9b00c-102">IHostIoCompletionManager Interface</span></span>
<span data-ttu-id="9b00c-103">Fornece métodos que permitem que o Common Language Runtime (CLR) interaja com portas de conclusão de e/s fornecidas pelo host.</span><span class="sxs-lookup"><span data-stu-id="9b00c-103">Provides methods that allow the common language runtime (CLR) to interact with I/O completion ports provided by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9b00c-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="9b00c-104">Methods</span></span>  
  
|<span data-ttu-id="9b00c-105">Método</span><span class="sxs-lookup"><span data-stu-id="9b00c-105">Method</span></span>|<span data-ttu-id="9b00c-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="9b00c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9b00c-107">Método Bind</span><span class="sxs-lookup"><span data-stu-id="9b00c-107">Bind Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md)|<span data-ttu-id="9b00c-108">Associa um identificador a uma porta de conclusão de e/s.</span><span class="sxs-lookup"><span data-stu-id="9b00c-108">Binds a handle to an I/O completion port.</span></span>|  
|[<span data-ttu-id="9b00c-109">Método CloseIoCompletionPort</span><span class="sxs-lookup"><span data-stu-id="9b00c-109">CloseIoCompletionPort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-closeiocompletionport-method.md)|<span data-ttu-id="9b00c-110">Fecha uma porta que foi criada por meio de uma chamada anterior para `CreateIoCompletionPort`.</span><span class="sxs-lookup"><span data-stu-id="9b00c-110">Closes a port that was created through an earlier call to `CreateIoCompletionPort`.</span></span>|  
|[<span data-ttu-id="9b00c-111">Método CreateIoCompletionPort</span><span class="sxs-lookup"><span data-stu-id="9b00c-111">CreateIoCompletionPort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md)|<span data-ttu-id="9b00c-112">Solicita que o host crie uma nova porta de conclusão de e/s.</span><span class="sxs-lookup"><span data-stu-id="9b00c-112">Requests that the host create a new I/O completion port.</span></span>|  
|[<span data-ttu-id="9b00c-113">Método GetAvailableThreads</span><span class="sxs-lookup"><span data-stu-id="9b00c-113">GetAvailableThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getavailablethreads-method.md)|<span data-ttu-id="9b00c-114">Obtém o número de threads de conclusão de e/s que não estão processando solicitações no momento.</span><span class="sxs-lookup"><span data-stu-id="9b00c-114">Gets the number of I/O completion threads that are not currently processing requests.</span></span>|  
|[<span data-ttu-id="9b00c-115">Método GetHostOverlappedSize</span><span class="sxs-lookup"><span data-stu-id="9b00c-115">GetHostOverlappedSize Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-gethostoverlappedsize-method.md)|<span data-ttu-id="9b00c-116">Obtém o tamanho de qualquer dado personalizado que o host pretende acrescentar às solicitações de e/s.</span><span class="sxs-lookup"><span data-stu-id="9b00c-116">Gets the size of any custom data the host intends to append to I/O requests.</span></span>|  
|[<span data-ttu-id="9b00c-117">Método GetMaxThreads</span><span class="sxs-lookup"><span data-stu-id="9b00c-117">GetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getmaxthreads-method.md)|<span data-ttu-id="9b00c-118">Obtém o número máximo de threads que o host pode alocar para solicitações de e/s de serviço.</span><span class="sxs-lookup"><span data-stu-id="9b00c-118">Gets the maximum number of threads that the host can allot to service I/O requests.</span></span>|  
|[<span data-ttu-id="9b00c-119">Método GetMinThreads</span><span class="sxs-lookup"><span data-stu-id="9b00c-119">GetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getminthreads-method.md)|<span data-ttu-id="9b00c-120">Obtém o número mínimo de threads que o host fornece para atender solicitações de e/s.</span><span class="sxs-lookup"><span data-stu-id="9b00c-120">Gets the minimum number of threads that the host provides to service I/O requests.</span></span>|  
|[<span data-ttu-id="9b00c-121">Método InitializeHostOverlapped</span><span class="sxs-lookup"><span data-stu-id="9b00c-121">InitializeHostOverlapped Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-initializehostoverlapped-method.md)|<span data-ttu-id="9b00c-122">Fornece ao host uma oportunidade de inicializar quaisquer dados personalizados sobre uma solicitação de e/s.</span><span class="sxs-lookup"><span data-stu-id="9b00c-122">Provides the host with an opportunity to initialize any custom data about an I/O request.</span></span>|  
|[<span data-ttu-id="9b00c-123">Método SetCLRIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="9b00c-123">SetCLRIoCompletionManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setclriocompletionmanager-method.md)|<span data-ttu-id="9b00c-124">Fornece ao host um ponteiro de interface para uma instância [ICLRIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md) implementada pelo CLR.</span><span class="sxs-lookup"><span data-stu-id="9b00c-124">Provides the host with an interface pointer to an [ICLRIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md) instance implemented by the CLR.</span></span>|  
|[<span data-ttu-id="9b00c-125">Método SetMaxThreads</span><span class="sxs-lookup"><span data-stu-id="9b00c-125">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setmaxthreads-method.md)|<span data-ttu-id="9b00c-126">Define o número máximo de threads que o host aloca para atender às solicitações de e/s.</span><span class="sxs-lookup"><span data-stu-id="9b00c-126">Sets the maximum number of threads that the host allots to service I/O requests.</span></span>|  
|[<span data-ttu-id="9b00c-127">Método SetMinThreads</span><span class="sxs-lookup"><span data-stu-id="9b00c-127">SetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setminthreads-method.md)|<span data-ttu-id="9b00c-128">Define o número mínimo de threads que o host deve alocar para a conclusão de e/s.</span><span class="sxs-lookup"><span data-stu-id="9b00c-128">Sets the minimum number of threads that the host should allot to I/O completion.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9b00c-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="9b00c-129">Remarks</span></span>  
 <span data-ttu-id="9b00c-130">`IHostIoCompletionManager` corresponde à interface `ICLRIoCompletionManager` implementada pelo CLR.</span><span class="sxs-lookup"><span data-stu-id="9b00c-130">`IHostIoCompletionManager` corresponds to the `ICLRIoCompletionManager` interface implemented by the CLR.</span></span> <span data-ttu-id="9b00c-131">O CLR chama os métodos de `IHostIoCompletionManager` para associar identificadores às portas que o host fornece, e o host chama os métodos de `ICLRIoCompletionManager` para relatar a conclusão de solicitações de e/s.</span><span class="sxs-lookup"><span data-stu-id="9b00c-131">The CLR calls the methods of `IHostIoCompletionManager` to bind handles to the ports that the host provides, and the host calls the methods of `ICLRIoCompletionManager` to report the completion of I/O requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b00c-132">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9b00c-132">Requirements</span></span>  
 <span data-ttu-id="9b00c-133">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9b00c-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b00c-134">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9b00c-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9b00c-135">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9b00c-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9b00c-136">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b00c-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b00c-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9b00c-137">See also</span></span>

- [<span data-ttu-id="9b00c-138">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="9b00c-138">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
