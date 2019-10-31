---
title: Método IHostIoCompletionManager::GetHostOverlappedSize
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.GetHostOverlappedSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::GetHostOverlappedSize
helpviewer_keywords:
- IHostIoCompletionManager::GetHostOverlappedSize method [.NET Framework hosting]
- GetHostOverlappedSize method [.NET Framework hosting]
ms.assetid: 2902578b-d5e2-4f8d-a103-0c7b6dceda9e
topic_type:
- apiref
ms.openlocfilehash: 3c662021894acbb8eb448fa2166498254158caa4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133861"
---
# <a name="ihostiocompletionmanagergethostoverlappedsize-method"></a><span data-ttu-id="37fba-102">Método IHostIoCompletionManager::GetHostOverlappedSize</span><span class="sxs-lookup"><span data-stu-id="37fba-102">IHostIoCompletionManager::GetHostOverlappedSize Method</span></span>
<span data-ttu-id="37fba-103">Obtém o tamanho de qualquer dado personalizado que o host pretende acrescentar às solicitações de e/s.</span><span class="sxs-lookup"><span data-stu-id="37fba-103">Gets the size of any custom data the host intends to append to I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37fba-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="37fba-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHostOverlappedSize (  
    [out] DWORD *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="37fba-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="37fba-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="37fba-106">fora Um ponteiro para o número de bytes que o Common Language Runtime (CLR) deve alocar, além do tamanho do objeto de `OVERLAPPED` do Win32.</span><span class="sxs-lookup"><span data-stu-id="37fba-106">[out] A pointer to the number of bytes that the common language runtime (CLR) should allocate in addition to the size of the Win32 `OVERLAPPED` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="37fba-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="37fba-107">Return Value</span></span>  
  
|<span data-ttu-id="37fba-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="37fba-108">HRESULT</span></span>|<span data-ttu-id="37fba-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="37fba-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="37fba-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="37fba-110">S_OK</span></span>|<span data-ttu-id="37fba-111">`GetHostOverlappedSize` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="37fba-111">`GetHostOverlappedSize` returned successfully.</span></span>|  
|<span data-ttu-id="37fba-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="37fba-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="37fba-113">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="37fba-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="37fba-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="37fba-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="37fba-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="37fba-115">The call timed out.</span></span>|  
|<span data-ttu-id="37fba-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="37fba-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="37fba-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="37fba-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="37fba-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="37fba-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="37fba-119">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="37fba-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="37fba-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="37fba-120">E_FAIL</span></span>|<span data-ttu-id="37fba-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="37fba-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="37fba-122">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="37fba-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="37fba-123">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="37fba-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="37fba-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="37fba-124">Remarks</span></span>  
 <span data-ttu-id="37fba-125">Todas as chamadas de e/s assíncronas para APIs da plataforma Windows usam um objeto de `OVERLAPPED` do Win32, que fornece informações como a posição do ponteiro do arquivo.</span><span class="sxs-lookup"><span data-stu-id="37fba-125">All asynchronous I/O calls to Windows Platform APIs take a Win32 `OVERLAPPED` object, which provides information such as the file pointer position.</span></span> <span data-ttu-id="37fba-126">Para manter o estado, os aplicativos que fazem chamadas de e/s assíncronas normalmente adicionam dados personalizados à estrutura.</span><span class="sxs-lookup"><span data-stu-id="37fba-126">To maintain state, applications that make asynchronous I/O calls typically add custom data to the structure.</span></span> <span data-ttu-id="37fba-127">`GetHostOverlappedSize` e [IHostIoCompletionManager:: InitializeHostOverlapped](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-initializehostoverlapped-method.md) fornecem uma oportunidade para o host incluir esses dados personalizados.</span><span class="sxs-lookup"><span data-stu-id="37fba-127">`GetHostOverlappedSize` and [IHostIoCompletionManager::InitializeHostOverlapped](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-initializehostoverlapped-method.md) provide an opportunity for the host to include such custom data.</span></span>  
  
 <span data-ttu-id="37fba-128">O CLR chama o método `GetHostOverlappedSize` para determinar o tamanho dos dados personalizados que o host pretende acrescentar ao objeto `OVERLAPPED`.</span><span class="sxs-lookup"><span data-stu-id="37fba-128">The CLR calls the `GetHostOverlappedSize` method to determine the size of the custom data that the host intends to append to the `OVERLAPPED` object.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="37fba-129">`GetHostOverlappedSize` é chamado apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="37fba-129">`GetHostOverlappedSize` is called only once.</span></span> <span data-ttu-id="37fba-130">Os dados personalizados do host devem ter o mesmo tamanho para cada solicitação de e/s.</span><span class="sxs-lookup"><span data-stu-id="37fba-130">The host's custom data must be the same size for every I/O request.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="37fba-131">O tamanho do objeto `OVERLAPPED` em si não é incluído no valor de `pcbSize`.</span><span class="sxs-lookup"><span data-stu-id="37fba-131">The size of the `OVERLAPPED` object itself is not included in the value of `pcbSize`.</span></span>  
  
 <span data-ttu-id="37fba-132">Para obter mais informações sobre a estrutura de `OVERLAPPED`, consulte a documentação da plataforma Windows.</span><span class="sxs-lookup"><span data-stu-id="37fba-132">For more information about the `OVERLAPPED` structure, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37fba-133">Requisitos</span><span class="sxs-lookup"><span data-stu-id="37fba-133">Requirements</span></span>  
 <span data-ttu-id="37fba-134">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="37fba-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37fba-135">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="37fba-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="37fba-136">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="37fba-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="37fba-137">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37fba-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37fba-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="37fba-138">See also</span></span>

- <xref:System.Threading.NativeOverlapped>
- [<span data-ttu-id="37fba-139">Interface ICLRIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="37fba-139">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="37fba-140">Interface IHostIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="37fba-140">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
