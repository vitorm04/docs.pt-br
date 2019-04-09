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
ms.openlocfilehash: f5e14749c3596ad22a435a11f75c928110c434de
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59196600"
---
# <a name="iclrerrorreportingmanagerendcustomdump-method"></a><span data-ttu-id="8e627-102">Método ICLRErrorReportingManager::EndCustomDump</span><span class="sxs-lookup"><span data-stu-id="8e627-102">ICLRErrorReportingManager::EndCustomDump Method</span></span>
<span data-ttu-id="8e627-103">Remove a configuração de despejo de pilha personalizado que foi especificada em uma chamada anterior para o [ICLRErrorReportingManager:: Begincustomdump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="8e627-103">Removes the custom stack dump configuration that was specified in an earlier call to the [ICLRErrorReportingManager::BeginCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e627-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8e627-104">Syntax</span></span>  
  
```  
HRESULT EndCustomDump ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="8e627-105">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="8e627-105">Return Value</span></span>  
  
|<span data-ttu-id="8e627-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8e627-106">HRESULT</span></span>|<span data-ttu-id="8e627-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="8e627-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8e627-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="8e627-108">S_OK</span></span>|`EndCustomDump` <span data-ttu-id="8e627-109">retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="8e627-109">returned successfully.</span></span>|  
|<span data-ttu-id="8e627-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8e627-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8e627-111">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="8e627-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8e627-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8e627-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8e627-113">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="8e627-113">The call timed out.</span></span>|  
|<span data-ttu-id="8e627-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8e627-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8e627-115">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="8e627-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8e627-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8e627-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8e627-117">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="8e627-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8e627-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8e627-118">E_FAIL</span></span>|<span data-ttu-id="8e627-119">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="8e627-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8e627-120">Depois que um método retorna E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="8e627-120">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8e627-121">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="8e627-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8e627-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="8e627-122">Remarks</span></span>  
 <span data-ttu-id="8e627-123">O `EndCustomDump` método limpa a configuração de despejo de pilha personalizado definida por uma chamada anterior para o `BeginCustomDump` método e libera qualquer estado associado.</span><span class="sxs-lookup"><span data-stu-id="8e627-123">The `EndCustomDump` method clears the custom stack dump configuration set by an earlier call to the `BeginCustomDump` method and frees any associated state.</span></span> <span data-ttu-id="8e627-124">Ele deve ser chamado após a conclusão do despejo da pilha personalizado.</span><span class="sxs-lookup"><span data-stu-id="8e627-124">It should be called after the custom stack dump is complete.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="8e627-125">Falha ao chamar `EndCustomDump` faz com que a memória de vazar.</span><span class="sxs-lookup"><span data-stu-id="8e627-125">Failure to call `EndCustomDump` causes memory to leak.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e627-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8e627-126">Requirements</span></span>  
 <span data-ttu-id="8e627-127">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8e627-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8e627-128">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8e627-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8e627-129">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="8e627-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="8e627-130">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="8e627-130">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8e627-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8e627-131">See also</span></span>

- [<span data-ttu-id="8e627-132">Estrutura CustomDumpItem</span><span class="sxs-lookup"><span data-stu-id="8e627-132">CustomDumpItem Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md)
- [<span data-ttu-id="8e627-133">Enumeração ECustomDumpFlavor</span><span class="sxs-lookup"><span data-stu-id="8e627-133">ECustomDumpFlavor Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpflavor-enumeration.md)
- [<span data-ttu-id="8e627-134">Interface ICLRErrorReportingManager</span><span class="sxs-lookup"><span data-stu-id="8e627-134">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
