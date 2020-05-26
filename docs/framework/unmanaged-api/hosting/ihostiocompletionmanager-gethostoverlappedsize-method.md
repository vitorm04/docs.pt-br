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
ms.openlocfilehash: a97009a4ebc834d867dddcc350033c550364ea42
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804746"
---
# <a name="ihostiocompletionmanagergethostoverlappedsize-method"></a><span data-ttu-id="34451-102">Método IHostIoCompletionManager::GetHostOverlappedSize</span><span class="sxs-lookup"><span data-stu-id="34451-102">IHostIoCompletionManager::GetHostOverlappedSize Method</span></span>
<span data-ttu-id="34451-103">Obtém o tamanho de qualquer dado personalizado que o host pretende acrescentar às solicitações de e/s.</span><span class="sxs-lookup"><span data-stu-id="34451-103">Gets the size of any custom data the host intends to append to I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34451-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="34451-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHostOverlappedSize (  
    [out] DWORD *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="34451-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="34451-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="34451-106">fora Um ponteiro para o número de bytes que o Common Language Runtime (CLR) deve alocar além do tamanho do objeto do Win32 `OVERLAPPED` .</span><span class="sxs-lookup"><span data-stu-id="34451-106">[out] A pointer to the number of bytes that the common language runtime (CLR) should allocate in addition to the size of the Win32 `OVERLAPPED` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="34451-107">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="34451-107">Return Value</span></span>  
  
|<span data-ttu-id="34451-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="34451-108">HRESULT</span></span>|<span data-ttu-id="34451-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="34451-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="34451-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="34451-110">S_OK</span></span>|<span data-ttu-id="34451-111">`GetHostOverlappedSize`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="34451-111">`GetHostOverlappedSize` returned successfully.</span></span>|  
|<span data-ttu-id="34451-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="34451-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="34451-113">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="34451-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="34451-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="34451-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="34451-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="34451-115">The call timed out.</span></span>|  
|<span data-ttu-id="34451-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="34451-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="34451-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="34451-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="34451-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="34451-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="34451-119">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="34451-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="34451-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="34451-120">E_FAIL</span></span>|<span data-ttu-id="34451-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="34451-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="34451-122">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="34451-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="34451-123">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="34451-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="34451-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="34451-124">Remarks</span></span>  
 <span data-ttu-id="34451-125">Todas as chamadas de e/s assíncronas para APIs da plataforma Windows usam um `OVERLAPPED` objeto Win32, que fornece informações como a posição do ponteiro do arquivo.</span><span class="sxs-lookup"><span data-stu-id="34451-125">All asynchronous I/O calls to Windows Platform APIs take a Win32 `OVERLAPPED` object, which provides information such as the file pointer position.</span></span> <span data-ttu-id="34451-126">Para manter o estado, os aplicativos que fazem chamadas de e/s assíncronas normalmente adicionam dados personalizados à estrutura.</span><span class="sxs-lookup"><span data-stu-id="34451-126">To maintain state, applications that make asynchronous I/O calls typically add custom data to the structure.</span></span> <span data-ttu-id="34451-127">`GetHostOverlappedSize`e [IHostIoCompletionManager:: InitializeHostOverlapped](ihostiocompletionmanager-initializehostoverlapped-method.md) fornecem uma oportunidade para o host incluir esses dados personalizados.</span><span class="sxs-lookup"><span data-stu-id="34451-127">`GetHostOverlappedSize` and [IHostIoCompletionManager::InitializeHostOverlapped](ihostiocompletionmanager-initializehostoverlapped-method.md) provide an opportunity for the host to include such custom data.</span></span>  
  
 <span data-ttu-id="34451-128">O CLR chama o `GetHostOverlappedSize` método para determinar o tamanho dos dados personalizados que o host pretende acrescentar ao `OVERLAPPED` objeto.</span><span class="sxs-lookup"><span data-stu-id="34451-128">The CLR calls the `GetHostOverlappedSize` method to determine the size of the custom data that the host intends to append to the `OVERLAPPED` object.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="34451-129">`GetHostOverlappedSize`é chamado apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="34451-129">`GetHostOverlappedSize` is called only once.</span></span> <span data-ttu-id="34451-130">Os dados personalizados do host devem ter o mesmo tamanho para cada solicitação de e/s.</span><span class="sxs-lookup"><span data-stu-id="34451-130">The host's custom data must be the same size for every I/O request.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="34451-131">O tamanho do `OVERLAPPED` objeto em si não é incluído no valor de `pcbSize` .</span><span class="sxs-lookup"><span data-stu-id="34451-131">The size of the `OVERLAPPED` object itself is not included in the value of `pcbSize`.</span></span>  
  
 <span data-ttu-id="34451-132">Para obter mais informações sobre a `OVERLAPPED` estrutura, consulte a documentação da plataforma Windows.</span><span class="sxs-lookup"><span data-stu-id="34451-132">For more information about the `OVERLAPPED` structure, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="34451-133">Requisitos</span><span class="sxs-lookup"><span data-stu-id="34451-133">Requirements</span></span>  
 <span data-ttu-id="34451-134">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="34451-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34451-135">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="34451-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="34451-136">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="34451-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="34451-137">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34451-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34451-138">Confira também</span><span class="sxs-lookup"><span data-stu-id="34451-138">See also</span></span>

- <xref:System.Threading.NativeOverlapped>
- [<span data-ttu-id="34451-139">Interface ICLRIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="34451-139">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="34451-140">Interface IHostIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="34451-140">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
