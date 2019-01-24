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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0f21e25c077ae6ca837a41d3e2227d12dd517d95
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54555499"
---
# <a name="ihostiocompletionmanagergethostoverlappedsize-method"></a><span data-ttu-id="818c3-102">Método IHostIoCompletionManager::GetHostOverlappedSize</span><span class="sxs-lookup"><span data-stu-id="818c3-102">IHostIoCompletionManager::GetHostOverlappedSize Method</span></span>
<span data-ttu-id="818c3-103">Obtém o tamanho de qualquer host pretende anexar às solicitações de e/s de dados personalizados.</span><span class="sxs-lookup"><span data-stu-id="818c3-103">Gets the size of any custom data the host intends to append to I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="818c3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="818c3-104">Syntax</span></span>  
  
```  
HRESULT GetHostOverlappedSize (  
    [out] DWORD *pcbSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="818c3-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="818c3-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="818c3-106">[out] Um ponteiro para o número de bytes que o common language runtime (CLR) deve alocar além do tamanho do Win32 `OVERLAPPED` objeto.</span><span class="sxs-lookup"><span data-stu-id="818c3-106">[out] A pointer to the number of bytes that the common language runtime (CLR) should allocate in addition to the size of the Win32 `OVERLAPPED` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="818c3-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="818c3-107">Return Value</span></span>  
  
|<span data-ttu-id="818c3-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="818c3-108">HRESULT</span></span>|<span data-ttu-id="818c3-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="818c3-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="818c3-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="818c3-110">S_OK</span></span>|<span data-ttu-id="818c3-111">`GetHostOverlappedSize` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="818c3-111">`GetHostOverlappedSize` returned successfully.</span></span>|  
|<span data-ttu-id="818c3-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="818c3-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="818c3-113">O CLR não tenha sido carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="818c3-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="818c3-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="818c3-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="818c3-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="818c3-115">The call timed out.</span></span>|  
|<span data-ttu-id="818c3-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="818c3-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="818c3-117">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="818c3-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="818c3-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="818c3-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="818c3-119">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="818c3-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="818c3-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="818c3-120">E_FAIL</span></span>|<span data-ttu-id="818c3-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="818c3-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="818c3-122">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="818c3-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="818c3-123">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="818c3-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="818c3-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="818c3-124">Remarks</span></span>  
 <span data-ttu-id="818c3-125">Todas as chamadas de e/s assíncronas para APIs da plataforma Windows levar Win32 `OVERLAPPED` objeto, que fornece informações como a posição do ponteiro de arquivo.</span><span class="sxs-lookup"><span data-stu-id="818c3-125">All asynchronous I/O calls to Windows Platform APIs take a Win32 `OVERLAPPED` object, which provides information such as the file pointer position.</span></span> <span data-ttu-id="818c3-126">Para manter o estado, os aplicativos que fazem chamadas de e/s assíncronas normalmente adicionam dados personalizados para a estrutura.</span><span class="sxs-lookup"><span data-stu-id="818c3-126">To maintain state, applications that make asynchronous I/O calls typically add custom data to the structure.</span></span> <span data-ttu-id="818c3-127">`GetHostOverlappedSize` e [ihostiocompletionmanager:: Initializehostoverlapped](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-initializehostoverlapped-method.md) oferecem uma oportunidade para o host incluir esses dados personalizados.</span><span class="sxs-lookup"><span data-stu-id="818c3-127">`GetHostOverlappedSize` and [IHostIoCompletionManager::InitializeHostOverlapped](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-initializehostoverlapped-method.md) provide an opportunity for the host to include such custom data.</span></span>  
  
 <span data-ttu-id="818c3-128">O CLR chama o `GetHostOverlappedSize` método para determinar o tamanho dos dados personalizados que o host deve ser acrescentado ao `OVERLAPPED` objeto.</span><span class="sxs-lookup"><span data-stu-id="818c3-128">The CLR calls the `GetHostOverlappedSize` method to determine the size of the custom data that the host intends to append to the `OVERLAPPED` object.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="818c3-129">`GetHostOverlappedSize` é chamado apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="818c3-129">`GetHostOverlappedSize` is called only once.</span></span> <span data-ttu-id="818c3-130">Dados personalizados do host devem ser o mesmo tamanho para cada solicitação de e/s.</span><span class="sxs-lookup"><span data-stu-id="818c3-130">The host's custom data must be the same size for every I/O request.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="818c3-131">O tamanho do `OVERLAPPED` próprio objeto não está incluído no valor do `pcbSize`.</span><span class="sxs-lookup"><span data-stu-id="818c3-131">The size of the `OVERLAPPED` object itself is not included in the value of `pcbSize`.</span></span>  
  
 <span data-ttu-id="818c3-132">Para obter mais informações sobre o `OVERLAPPED` estrutura, consulte a documentação da plataforma Windows.</span><span class="sxs-lookup"><span data-stu-id="818c3-132">For more information about the `OVERLAPPED` structure, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="818c3-133">Requisitos</span><span class="sxs-lookup"><span data-stu-id="818c3-133">Requirements</span></span>  
 <span data-ttu-id="818c3-134">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="818c3-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="818c3-135">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="818c3-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="818c3-136">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="818c3-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="818c3-137">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="818c3-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="818c3-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="818c3-138">See also</span></span>
- <xref:System.Threading.NativeOverlapped>
- [<span data-ttu-id="818c3-139">Interface ICLRIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="818c3-139">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="818c3-140">Interface IHostIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="818c3-140">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
