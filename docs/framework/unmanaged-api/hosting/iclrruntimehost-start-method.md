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
ms.openlocfilehash: c36d1e4aea284db6111ae1b7df6a683e5d5d85c2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54561162"
---
# <a name="iclrruntimehoststart-method"></a><span data-ttu-id="c5941-102">Método ICLRRuntimeHost::Start</span><span class="sxs-lookup"><span data-stu-id="c5941-102">ICLRRuntimeHost::Start Method</span></span>
<span data-ttu-id="c5941-103">Inicializa o common language runtime (CLR) em um processo.</span><span class="sxs-lookup"><span data-stu-id="c5941-103">Initializes the common language runtime (CLR) into a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5941-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c5941-104">Syntax</span></span>  
  
```  
HRESULT Start();  
```  
  
## <a name="return-value"></a><span data-ttu-id="c5941-105">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="c5941-105">Return Value</span></span>  
  
|<span data-ttu-id="c5941-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c5941-106">HRESULT</span></span>|<span data-ttu-id="c5941-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="c5941-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c5941-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="c5941-108">S_OK</span></span>|<span data-ttu-id="c5941-109">`Start` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="c5941-109">`Start` returned successfully.</span></span>|  
|<span data-ttu-id="c5941-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c5941-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c5941-111">O CLR não tenha sido carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="c5941-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c5941-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c5941-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c5941-113">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="c5941-113">The call timed out.</span></span>|  
|<span data-ttu-id="c5941-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c5941-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c5941-115">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="c5941-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c5941-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c5941-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c5941-117">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="c5941-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c5941-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c5941-118">E_FAIL</span></span>|<span data-ttu-id="c5941-119">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="c5941-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c5941-120">Se um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="c5941-120">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c5941-121">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="c5941-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c5941-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="c5941-122">Remarks</span></span>  
 <span data-ttu-id="c5941-123">Em muitos cenários, não é necessário chamar `Start`, pois o tempo de execução será se inicialize automaticamente após a primeira solicitação para executar código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="c5941-123">In many scenarios it is not necessary to call `Start`, because the runtime will initialize itself automatically upon the first request to run managed code.</span></span> <span data-ttu-id="c5941-124">No entanto, você pode usar `Start` para especificar exatamente quando o tempo de execução deve ser inicializado.</span><span class="sxs-lookup"><span data-stu-id="c5941-124">You can, however, use `Start` to specify exactly when the runtime should be initialized.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5941-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c5941-125">Requirements</span></span>  
 <span data-ttu-id="c5941-126">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c5941-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5941-127">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c5941-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c5941-128">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="c5941-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c5941-129">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5941-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5941-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c5941-130">See also</span></span>
- <xref:System.AppDomain>
- [<span data-ttu-id="c5941-131">Interface ICLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="c5941-131">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
