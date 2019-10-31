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
ms.openlocfilehash: 9fd299ad25166bcbcf0202da13a5b4cbdd20d7d7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133798"
---
# <a name="ihostiocompletionmanagerinitializehostoverlapped-method"></a><span data-ttu-id="17595-102">Método IHostIoCompletionManager::InitializeHostOverlapped</span><span class="sxs-lookup"><span data-stu-id="17595-102">IHostIoCompletionManager::InitializeHostOverlapped Method</span></span>
<span data-ttu-id="17595-103">Fornece ao host uma oportunidade de inicializar quaisquer dados personalizados para acrescentar a uma estrutura de `OVERLAPPED` do Win32 que é usada para solicitações de e/s assíncronas.</span><span class="sxs-lookup"><span data-stu-id="17595-103">Provides the host with an opportunity to initialize any custom data to append to a Win32 `OVERLAPPED` structure that is used for asynchronous I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17595-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="17595-104">Syntax</span></span>  
  
```cpp  
HRESULT InitializeHostOverlapped (  
    [in] void* pvOverlapped  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="17595-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="17595-105">Parameters</span></span>  
 `pvOverlapped`  
 <span data-ttu-id="17595-106">no Um ponteiro para a estrutura de `OVERLAPPED` do Win32 a ser incluído com a solicitação de e/s.</span><span class="sxs-lookup"><span data-stu-id="17595-106">[in] A pointer to the Win32 `OVERLAPPED` structure to be included with the I/O request.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="17595-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="17595-107">Return Value</span></span>  
  
|<span data-ttu-id="17595-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="17595-108">HRESULT</span></span>|<span data-ttu-id="17595-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="17595-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="17595-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="17595-110">S_OK</span></span>|<span data-ttu-id="17595-111">`InitializeHostOverlapped` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="17595-111">`InitializeHostOverlapped` returned successfully.</span></span>|  
|<span data-ttu-id="17595-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="17595-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="17595-113">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="17595-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="17595-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="17595-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="17595-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="17595-115">The call timed out.</span></span>|  
|<span data-ttu-id="17595-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="17595-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="17595-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="17595-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="17595-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="17595-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="17595-119">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="17595-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="17595-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="17595-120">E_FAIL</span></span>|<span data-ttu-id="17595-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="17595-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="17595-122">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="17595-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="17595-123">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="17595-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="17595-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="17595-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="17595-125">Não havia memória suficiente disponível para alocar o recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="17595-125">Not enough memory was available to allocate the requested resource.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="17595-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="17595-126">Remarks</span></span>  
 <span data-ttu-id="17595-127">As funções da plataforma Windows usam a estrutura de `OVERLAPPED` para armazenar o estado de solicitações de e/s assíncronas.</span><span class="sxs-lookup"><span data-stu-id="17595-127">The Windows Platform functions use the `OVERLAPPED` structure to store state for asynchronous I/O requests.</span></span> <span data-ttu-id="17595-128">O CLR chama o método `InitializeHostOverlapped` para dar ao host a oportunidade de acrescentar dados personalizados a uma instância de `OVERLAPPED`.</span><span class="sxs-lookup"><span data-stu-id="17595-128">The CLR calls the `InitializeHostOverlapped` method to give the host the opportunity to append custom data to an `OVERLAPPED` instance.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="17595-129">Para chegar ao início do bloco de dados personalizado, os hosts devem definir o deslocamento para o tamanho da estrutura de `OVERLAPPED` (`sizeof(OVERLAPPED)`).</span><span class="sxs-lookup"><span data-stu-id="17595-129">To get to the beginning of their custom data block, hosts must set the offset to the size of the `OVERLAPPED` structure (`sizeof(OVERLAPPED)`).</span></span>  
  
 <span data-ttu-id="17595-130">Um valor de retorno de E_OUTOFMEMORY indica que o host falhou ao inicializar seus dados personalizados.</span><span class="sxs-lookup"><span data-stu-id="17595-130">A return value of E_OUTOFMEMORY indicates that the host has failed to initialize its custom data.</span></span> <span data-ttu-id="17595-131">Nesse caso, o CLR relata um erro e falha na chamada.</span><span class="sxs-lookup"><span data-stu-id="17595-131">In this case, the CLR reports an error and fails the call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17595-132">Requisitos</span><span class="sxs-lookup"><span data-stu-id="17595-132">Requirements</span></span>  
 <span data-ttu-id="17595-133">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17595-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17595-134">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="17595-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="17595-135">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="17595-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="17595-136">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17595-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17595-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="17595-137">See also</span></span>

- [<span data-ttu-id="17595-138">Interface ICLRIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="17595-138">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="17595-139">Método GetHostOverlappedSize</span><span class="sxs-lookup"><span data-stu-id="17595-139">GetHostOverlappedSize Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-gethostoverlappedsize-method.md)
- [<span data-ttu-id="17595-140">Interface IHostIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="17595-140">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
