---
title: Método ICLRRuntimeHost::Stop
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.Stop
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::Stop
helpviewer_keywords:
- ICLRRuntimeHost::Stop method [.NET Framework hosting]
- Stop method, ICLRRuntimeHost interface [.NET Framework hosting]
ms.assetid: b8fd7daf-8f8d-4ad7-92ae-019db244cec1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 97a0e6cbbd8972f58f9eedcfeb8aff1f93694064
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67765661"
---
# <a name="iclrruntimehoststop-method"></a><span data-ttu-id="1721c-102">Método ICLRRuntimeHost::Stop</span><span class="sxs-lookup"><span data-stu-id="1721c-102">ICLRRuntimeHost::Stop Method</span></span>
<span data-ttu-id="1721c-103">Interrompe a execução de código, o common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="1721c-103">Stops the execution of code by the common language runtime (CLR).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1721c-104">Esse método não liberar recursos para o host, descarregar domínios de aplicativo ou destruir threads.</span><span class="sxs-lookup"><span data-stu-id="1721c-104">This method does not release resources to the host, unload application domains, or destroy threads.</span></span> <span data-ttu-id="1721c-105">Você deve encerrar o processo para liberar esses recursos.</span><span class="sxs-lookup"><span data-stu-id="1721c-105">You must terminate the process to release these resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1721c-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1721c-106">Syntax</span></span>  
  
```cpp  
HRESULT Stop();  
```  
  
## <a name="return-value"></a><span data-ttu-id="1721c-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="1721c-107">Return Value</span></span>  
  
|<span data-ttu-id="1721c-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1721c-108">HRESULT</span></span>|<span data-ttu-id="1721c-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="1721c-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1721c-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="1721c-110">S_OK</span></span>|<span data-ttu-id="1721c-111">`Stop` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="1721c-111">`Stop` returned successfully.</span></span>|  
|<span data-ttu-id="1721c-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1721c-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1721c-113">O CLR não tenha sido carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="1721c-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1721c-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1721c-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1721c-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="1721c-115">The call timed out.</span></span>|  
|<span data-ttu-id="1721c-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1721c-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1721c-117">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="1721c-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1721c-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1721c-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1721c-119">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="1721c-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1721c-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1721c-120">E_FAIL</span></span>|<span data-ttu-id="1721c-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="1721c-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1721c-122">Se um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="1721c-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1721c-123">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="1721c-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1721c-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1721c-124">Requirements</span></span>  
 <span data-ttu-id="1721c-125">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1721c-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1721c-126">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1721c-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1721c-127">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="1721c-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1721c-128">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1721c-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1721c-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1721c-129">See also</span></span>

- [<span data-ttu-id="1721c-130">Interface ICLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="1721c-130">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
