---
title: Método IHostIoCompletionManager::InitializeHostOverlapped
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.InitializeHostOverlapped
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::InitializeHostOverlapped
helpviewer_keywords:
- IHostIoCompletionManager::InitializeHostOverlapped method [.NET Framework hosting]
- InitializeHostOverlapped method [.NET Framework hosting]
ms.assetid: c35199bf-bc47-4901-b467-4e8a37644bbb
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 023e112aa8273d99efce2e0f2116f95569ac0c3b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="ihostiocompletionmanagerinitializehostoverlapped-method"></a><span data-ttu-id="c9712-102">Método IHostIoCompletionManager::InitializeHostOverlapped</span><span class="sxs-lookup"><span data-stu-id="c9712-102">IHostIoCompletionManager::InitializeHostOverlapped Method</span></span>
<span data-ttu-id="c9712-103">Fornece o host com uma oportunidade para inicializar os dados personalizados para acrescentar a Win32 `OVERLAPPED` estrutura que é usada para solicitações de e/s assíncronas.</span><span class="sxs-lookup"><span data-stu-id="c9712-103">Provides the host with an opportunity to initialize any custom data to append to a Win32 `OVERLAPPED` structure that is used for asynchronous I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9712-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c9712-104">Syntax</span></span>  
  
```  
HRESULT InitializeHostOverlapped (  
    [in] void* pvOverlapped  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c9712-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c9712-105">Parameters</span></span>  
 `pvOverlapped`  
 <span data-ttu-id="c9712-106">[in] Um ponteiro para o Win32 `OVERLAPPED` estrutura a ser incluído na solicitação de e/s.</span><span class="sxs-lookup"><span data-stu-id="c9712-106">[in] A pointer to the Win32 `OVERLAPPED` structure to be included with the I/O request.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c9712-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="c9712-107">Return Value</span></span>  
  
|<span data-ttu-id="c9712-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c9712-108">HRESULT</span></span>|<span data-ttu-id="c9712-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="c9712-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c9712-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="c9712-110">S_OK</span></span>|<span data-ttu-id="c9712-111">`InitializeHostOverlapped` retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="c9712-111">`InitializeHostOverlapped` returned successfully.</span></span>|  
|<span data-ttu-id="c9712-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c9712-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c9712-113">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="c9712-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c9712-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c9712-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c9712-115">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="c9712-115">The call timed out.</span></span>|  
|<span data-ttu-id="c9712-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c9712-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c9712-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="c9712-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c9712-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c9712-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c9712-119">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="c9712-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c9712-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c9712-120">E_FAIL</span></span>|<span data-ttu-id="c9712-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="c9712-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c9712-122">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="c9712-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c9712-123">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="c9712-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="c9712-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="c9712-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="c9712-125">Não havia memória suficiente disponível para alocar o recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="c9712-125">Not enough memory was available to allocate the requested resource.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c9712-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="c9712-126">Remarks</span></span>  
 <span data-ttu-id="c9712-127">Use as funções da plataforma Windows o `OVERLAPPED` estrutura para armazenar o estado para solicitações de e/s assíncronas.</span><span class="sxs-lookup"><span data-stu-id="c9712-127">The Windows Platform functions use the `OVERLAPPED` structure to store state for asynchronous I/O requests.</span></span> <span data-ttu-id="c9712-128">O CLR chama o `InitializeHostOverlapped` método para fornecer o host a oportunidade de acrescentar dados personalizados para um `OVERLAPPED` instância.</span><span class="sxs-lookup"><span data-stu-id="c9712-128">The CLR calls the `InitializeHostOverlapped` method to give the host the opportunity to append custom data to an `OVERLAPPED` instance.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c9712-129">Para obter o início do seu bloco de dados personalizados, hosts devem definir o deslocamento para o tamanho do `OVERLAPPED` estrutura (`sizeof(OVERLAPPED)`).</span><span class="sxs-lookup"><span data-stu-id="c9712-129">To get to the beginning of their custom data block, hosts must set the offset to the size of the `OVERLAPPED` structure (`sizeof(OVERLAPPED)`).</span></span>  
  
 <span data-ttu-id="c9712-130">Um valor de retorno de E_OUTOFMEMORY indica que o host falhou ao inicializar seus dados personalizados.</span><span class="sxs-lookup"><span data-stu-id="c9712-130">A return value of E_OUTOFMEMORY indicates that the host has failed to initialize its custom data.</span></span> <span data-ttu-id="c9712-131">Nesse caso, o CLR relata um erro e falha da chamada.</span><span class="sxs-lookup"><span data-stu-id="c9712-131">In this case, the CLR reports an error and fails the call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9712-132">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c9712-132">Requirements</span></span>  
 <span data-ttu-id="c9712-133">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c9712-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9712-134">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c9712-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c9712-135">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="c9712-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c9712-136">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9712-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9712-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c9712-137">See Also</span></span>  
 [<span data-ttu-id="c9712-138">Interface ICLRIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="c9712-138">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [<span data-ttu-id="c9712-139">Método GetHostOverlappedSize</span><span class="sxs-lookup"><span data-stu-id="c9712-139">GetHostOverlappedSize Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-gethostoverlappedsize-method.md)  
 [<span data-ttu-id="c9712-140">Interface IHostIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="c9712-140">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
