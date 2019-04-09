---
title: Método ICLRRuntimeHost::Start
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.Start
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::Start
helpviewer_keywords:
- ICLRRuntimeHost::Start method [.NET Framework hosting]
- Start method, ICLRRuntimeHost interface [.NET Framework hosting]
ms.assetid: c0a6dce5-0a8d-42e8-808b-6ca14df9d289
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 608612f6a0f4395092e33ce75fdbd249f19ae4f4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59172608"
---
# <a name="iclrruntimehoststart-method"></a><span data-ttu-id="5d827-102">Método ICLRRuntimeHost::Start</span><span class="sxs-lookup"><span data-stu-id="5d827-102">ICLRRuntimeHost::Start Method</span></span>
<span data-ttu-id="5d827-103">Inicializa o common language runtime (CLR) em um processo.</span><span class="sxs-lookup"><span data-stu-id="5d827-103">Initializes the common language runtime (CLR) into a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d827-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5d827-104">Syntax</span></span>  
  
```  
HRESULT Start();  
```  
  
## <a name="return-value"></a><span data-ttu-id="5d827-105">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="5d827-105">Return Value</span></span>  
  
|<span data-ttu-id="5d827-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5d827-106">HRESULT</span></span>|<span data-ttu-id="5d827-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="5d827-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5d827-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="5d827-108">S_OK</span></span>|`Start` <span data-ttu-id="5d827-109">retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="5d827-109">returned successfully.</span></span>|  
|<span data-ttu-id="5d827-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5d827-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5d827-111">O CLR não tenha sido carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="5d827-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5d827-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5d827-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5d827-113">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="5d827-113">The call timed out.</span></span>|  
|<span data-ttu-id="5d827-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5d827-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5d827-115">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="5d827-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5d827-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5d827-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5d827-117">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="5d827-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5d827-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5d827-118">E_FAIL</span></span>|<span data-ttu-id="5d827-119">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="5d827-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5d827-120">Se um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="5d827-120">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5d827-121">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="5d827-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5d827-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="5d827-122">Remarks</span></span>  
 <span data-ttu-id="5d827-123">Em muitos cenários, não é necessário chamar `Start`, pois o tempo de execução será se inicialize automaticamente após a primeira solicitação para executar código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="5d827-123">In many scenarios it is not necessary to call `Start`, because the runtime will initialize itself automatically upon the first request to run managed code.</span></span> <span data-ttu-id="5d827-124">No entanto, você pode usar `Start` para especificar exatamente quando o tempo de execução deve ser inicializado.</span><span class="sxs-lookup"><span data-stu-id="5d827-124">You can, however, use `Start` to specify exactly when the runtime should be initialized.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d827-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5d827-125">Requirements</span></span>  
 <span data-ttu-id="5d827-126">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5d827-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d827-127">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5d827-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5d827-128">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="5d827-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="5d827-129">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="5d827-129">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5d827-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5d827-130">See also</span></span>

- <xref:System.AppDomain>
- [<span data-ttu-id="5d827-131">Interface ICLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="5d827-131">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
