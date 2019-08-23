---
title: Método ICLRErrorReportingManager::EndCustomDump
ms.date: 03/30/2017
api_name:
- ICLRErrorReportingManager.EndCustomDump
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRErrorReportingManager::EndCustomDump
helpviewer_keywords:
- ICLRErrorReportingManager::EndCustomDump method [.NET Framework hosting]
- EndCustomDump method [.NET Framework hosting]
ms.assetid: 88a5da04-8729-4108-82c4-af206a7d483e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a262ab26c9bbb93e42a11217fbeea6b3c55c7eb9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966259"
---
# <a name="iclrerrorreportingmanagerendcustomdump-method"></a><span data-ttu-id="4bdc0-102">Método ICLRErrorReportingManager::EndCustomDump</span><span class="sxs-lookup"><span data-stu-id="4bdc0-102">ICLRErrorReportingManager::EndCustomDump Method</span></span>
<span data-ttu-id="4bdc0-103">Remove a configuração de despejo de pilha personalizada que foi especificada em uma chamada anterior para o método [ICLRErrorReportingManager:: BeginCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) .</span><span class="sxs-lookup"><span data-stu-id="4bdc0-103">Removes the custom stack dump configuration that was specified in an earlier call to the [ICLRErrorReportingManager::BeginCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4bdc0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4bdc0-104">Syntax</span></span>  
  
```cpp  
HRESULT EndCustomDump ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="4bdc0-105">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="4bdc0-105">Return Value</span></span>  
  
|<span data-ttu-id="4bdc0-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4bdc0-106">HRESULT</span></span>|<span data-ttu-id="4bdc0-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="4bdc0-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4bdc0-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="4bdc0-108">S_OK</span></span>|<span data-ttu-id="4bdc0-109">`EndCustomDump`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="4bdc0-109">`EndCustomDump` returned successfully.</span></span>|  
|<span data-ttu-id="4bdc0-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4bdc0-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4bdc0-111">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="4bdc0-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4bdc0-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4bdc0-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4bdc0-113">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="4bdc0-113">The call timed out.</span></span>|  
|<span data-ttu-id="4bdc0-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4bdc0-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4bdc0-115">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="4bdc0-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4bdc0-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4bdc0-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4bdc0-117">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="4bdc0-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4bdc0-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4bdc0-118">E_FAIL</span></span>|<span data-ttu-id="4bdc0-119">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="4bdc0-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4bdc0-120">Depois que um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="4bdc0-120">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4bdc0-121">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="4bdc0-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4bdc0-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="4bdc0-122">Remarks</span></span>  
 <span data-ttu-id="4bdc0-123">O `EndCustomDump` método limpa a configuração de despejo de pilha personalizada definida por uma chamada anterior para `BeginCustomDump` o método e libera qualquer estado associado.</span><span class="sxs-lookup"><span data-stu-id="4bdc0-123">The `EndCustomDump` method clears the custom stack dump configuration set by an earlier call to the `BeginCustomDump` method and frees any associated state.</span></span> <span data-ttu-id="4bdc0-124">Ele deve ser chamado após a conclusão do despejo de pilha personalizado.</span><span class="sxs-lookup"><span data-stu-id="4bdc0-124">It should be called after the custom stack dump is complete.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="4bdc0-125">Falha ao chamar `EndCustomDump` faz com que a memória seja vazada.</span><span class="sxs-lookup"><span data-stu-id="4bdc0-125">Failure to call `EndCustomDump` causes memory to leak.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4bdc0-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4bdc0-126">Requirements</span></span>  
 <span data-ttu-id="4bdc0-127">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4bdc0-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4bdc0-128">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4bdc0-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4bdc0-129">**Biblioteca** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4bdc0-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4bdc0-130">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4bdc0-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bdc0-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4bdc0-131">See also</span></span>

- [<span data-ttu-id="4bdc0-132">Estrutura CustomDumpItem</span><span class="sxs-lookup"><span data-stu-id="4bdc0-132">CustomDumpItem Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md)
- [<span data-ttu-id="4bdc0-133">Enumeração ECustomDumpFlavor</span><span class="sxs-lookup"><span data-stu-id="4bdc0-133">ECustomDumpFlavor Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpflavor-enumeration.md)
- [<span data-ttu-id="4bdc0-134">Interface ICLRErrorReportingManager</span><span class="sxs-lookup"><span data-stu-id="4bdc0-134">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
