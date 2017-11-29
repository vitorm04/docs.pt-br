---
title: Interface IHostIoCompletionManager
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostIoCompletionManager
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostIoCompletionManager
helpviewer_keywords: IHostIoCompletionManager interface [.NET Framework hosting]
ms.assetid: c28d1983-83f7-46e2-990f-dbb9dc07c818
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 847d4c3aa3e3da94b4aac4679ada047577379f82
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="ihostiocompletionmanager-interface"></a><span data-ttu-id="3a21c-102">Interface IHostIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="3a21c-102">IHostIoCompletionManager Interface</span></span>
<span data-ttu-id="3a21c-103">Fornece métodos que permitem que o common language runtime (CLR) para interagir com portas de conclusão de e/s fornecidas pelo host.</span><span class="sxs-lookup"><span data-stu-id="3a21c-103">Provides methods that allow the common language runtime (CLR) to interact with I/O completion ports provided by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3a21c-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="3a21c-104">Methods</span></span>  
  
|<span data-ttu-id="3a21c-105">Método</span><span class="sxs-lookup"><span data-stu-id="3a21c-105">Method</span></span>|<span data-ttu-id="3a21c-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="3a21c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3a21c-107">Método Bind</span><span class="sxs-lookup"><span data-stu-id="3a21c-107">Bind Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md)|<span data-ttu-id="3a21c-108">Associa um identificador para uma porta de conclusão de e/s.</span><span class="sxs-lookup"><span data-stu-id="3a21c-108">Binds a handle to an I/O completion port.</span></span>|  
|[<span data-ttu-id="3a21c-109">Método CloseIoCompletionPort</span><span class="sxs-lookup"><span data-stu-id="3a21c-109">CloseIoCompletionPort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-closeiocompletionport-method.md)|<span data-ttu-id="3a21c-110">Fecha uma porta que foi criada por meio de uma chamada anterior para `CreateIoCompletionPort`.</span><span class="sxs-lookup"><span data-stu-id="3a21c-110">Closes a port that was created through an earlier call to `CreateIoCompletionPort`.</span></span>|  
|[<span data-ttu-id="3a21c-111">Método CreateIoCompletionPort</span><span class="sxs-lookup"><span data-stu-id="3a21c-111">CreateIoCompletionPort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md)|<span data-ttu-id="3a21c-112">Solicita que o host de cria uma nova porta de conclusão de e/s.</span><span class="sxs-lookup"><span data-stu-id="3a21c-112">Requests that the host create a new I/O completion port.</span></span>|  
|[<span data-ttu-id="3a21c-113">Método GetAvailableThreads</span><span class="sxs-lookup"><span data-stu-id="3a21c-113">GetAvailableThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getavailablethreads-method.md)|<span data-ttu-id="3a21c-114">Obtém o número de threads de conclusão de e/s que não estão atualmente processando solicitações.</span><span class="sxs-lookup"><span data-stu-id="3a21c-114">Gets the number of I/O completion threads that are not currently processing requests.</span></span>|  
|[<span data-ttu-id="3a21c-115">Método GetHostOverlappedSize</span><span class="sxs-lookup"><span data-stu-id="3a21c-115">GetHostOverlappedSize Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-gethostoverlappedsize-method.md)|<span data-ttu-id="3a21c-116">Obtém o tamanho de qualquer host pretende anexar a solicitações de e/s de dados personalizados.</span><span class="sxs-lookup"><span data-stu-id="3a21c-116">Gets the size of any custom data the host intends to append to I/O requests.</span></span>|  
|[<span data-ttu-id="3a21c-117">Método GetMaxThreads</span><span class="sxs-lookup"><span data-stu-id="3a21c-117">GetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getmaxthreads-method.md)|<span data-ttu-id="3a21c-118">Obtém o número máximo de threads que o host pode alocar solicitações de e/s.</span><span class="sxs-lookup"><span data-stu-id="3a21c-118">Gets the maximum number of threads that the host can allot to service I/O requests.</span></span>|  
|[<span data-ttu-id="3a21c-119">Método GetMinThreads</span><span class="sxs-lookup"><span data-stu-id="3a21c-119">GetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getminthreads-method.md)|<span data-ttu-id="3a21c-120">Obtém o número mínimo de threads que fornece o host para atender a solicitações de e/s.</span><span class="sxs-lookup"><span data-stu-id="3a21c-120">Gets the minimum number of threads that the host provides to service I/O requests.</span></span>|  
|[<span data-ttu-id="3a21c-121">Método InitializeHostOverlapped</span><span class="sxs-lookup"><span data-stu-id="3a21c-121">InitializeHostOverlapped Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-initializehostoverlapped-method.md)|<span data-ttu-id="3a21c-122">Fornece o host com uma oportunidade para inicializar os dados personalizados sobre uma solicitação de e/s.</span><span class="sxs-lookup"><span data-stu-id="3a21c-122">Provides the host with an opportunity to initialize any custom data about an I/O request.</span></span>|  
|[<span data-ttu-id="3a21c-123">Método SetCLRIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="3a21c-123">SetCLRIoCompletionManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setclriocompletionmanager-method.md)|<span data-ttu-id="3a21c-124">Fornece o host com um ponteiro de interface para um [ICLRIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md) instância implementada pelo CLR.</span><span class="sxs-lookup"><span data-stu-id="3a21c-124">Provides the host with an interface pointer to an [ICLRIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md) instance implemented by the CLR.</span></span>|  
|[<span data-ttu-id="3a21c-125">Método SetMaxThreads</span><span class="sxs-lookup"><span data-stu-id="3a21c-125">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setmaxthreads-method.md)|<span data-ttu-id="3a21c-126">Define o número máximo de threads que o host aloca solicitações de e/s.</span><span class="sxs-lookup"><span data-stu-id="3a21c-126">Sets the maximum number of threads that the host allots to service I/O requests.</span></span>|  
|[<span data-ttu-id="3a21c-127">Método SetMinThreads</span><span class="sxs-lookup"><span data-stu-id="3a21c-127">SetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setminthreads-method.md)|<span data-ttu-id="3a21c-128">Define o número mínimo de threads que o host deve alocar até a conclusão de e/s.</span><span class="sxs-lookup"><span data-stu-id="3a21c-128">Sets the minimum number of threads that the host should allot to I/O completion.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3a21c-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="3a21c-129">Remarks</span></span>  
 <span data-ttu-id="3a21c-130">`IHostIoCompletionManager`corresponde do `ICLRIoCompletionManager` interface implementada pelo CLR.</span><span class="sxs-lookup"><span data-stu-id="3a21c-130">`IHostIoCompletionManager` corresponds to the `ICLRIoCompletionManager` interface implemented by the CLR.</span></span> <span data-ttu-id="3a21c-131">O CLR chama os métodos de `IHostIoCompletionManager` para associar as alças para as portas que fornece o host e o host chama os métodos de `ICLRIoCompletionManager` para relatar a conclusão das solicitações de e/s.</span><span class="sxs-lookup"><span data-stu-id="3a21c-131">The CLR calls the methods of `IHostIoCompletionManager` to bind handles to the ports that the host provides, and the host calls the methods of `ICLRIoCompletionManager` to report the completion of I/O requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a21c-132">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3a21c-132">Requirements</span></span>  
 <span data-ttu-id="3a21c-133">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3a21c-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a21c-134">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3a21c-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3a21c-135">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="3a21c-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3a21c-136">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a21c-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a21c-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3a21c-137">See Also</span></span>  
 [<span data-ttu-id="3a21c-138">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="3a21c-138">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
