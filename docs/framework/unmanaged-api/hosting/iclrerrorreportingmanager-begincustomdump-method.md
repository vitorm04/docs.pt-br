---
title: Método ICLRErrorReportingManager::BeginCustomDump
ms.date: 03/30/2017
api_name:
- ICLRErrorReportingManager.BeginCustomDump
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRErrorReportingManager::BeginCustomDump
helpviewer_keywords:
- ICLRErrorReportingManager::BeginCustomDump method [.NET Framework hosting]
- BeginCustomDump method
ms.assetid: 93424a87-ba13-4fa1-b4dc-69d44437b7ae
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b5d58a90901b7d7cb80ea7f25401b857b4d4875e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33434506"
---
# <a name="iclrerrorreportingmanagerbegincustomdump-method"></a><span data-ttu-id="e0ece-102">Método ICLRErrorReportingManager::BeginCustomDump</span><span class="sxs-lookup"><span data-stu-id="e0ece-102">ICLRErrorReportingManager::BeginCustomDump Method</span></span>
<span data-ttu-id="e0ece-103">Especifica a configuração de despejos de pilha personalizado para o relatório de erros.</span><span class="sxs-lookup"><span data-stu-id="e0ece-103">Specifies the configuration of custom heap dumps for error reporting.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0ece-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e0ece-104">Syntax</span></span>  
  
```  
HRESULT BeginCustomDump (  
    [in] ECustomDumpFlavor dwFlavor,  
    [in] DWORD dwNumItems,  
    [in, size_is(dwNumItems), length_is(dwNumItems)] CustomDumpItem items[],  
    DWORD dwReserved  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e0ece-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e0ece-105">Parameters</span></span>  
 `dwFlavor`  
 <span data-ttu-id="e0ece-106">[in] Um [ECustomDumpFlavor](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpflavor-enumeration.md) valor que indica o tipo de despejo de pilha no qual criar o despejo de pilha personalizado.</span><span class="sxs-lookup"><span data-stu-id="e0ece-106">[in] A [ECustomDumpFlavor](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpflavor-enumeration.md) value that indicates the kind of heap dump upon which to build the custom heap dump.</span></span>  
  
 `dwNumItems`  
 <span data-ttu-id="e0ece-107">[in] O comprimento do `items` matriz.</span><span class="sxs-lookup"><span data-stu-id="e0ece-107">[in] The length of the `items` array.</span></span> <span data-ttu-id="e0ece-108">Se `dwFlavor` não é DUMP_FLAVOR_Mini, `dwNumItems` deve ser zero.</span><span class="sxs-lookup"><span data-stu-id="e0ece-108">If `dwFlavor` is not DUMP_FLAVOR_Mini, `dwNumItems` should be zero.</span></span>  
  
 `items`  
 <span data-ttu-id="e0ece-109">[in] Uma matriz de [CustomDumpItem](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md) instâncias, especificando os itens a serem adicionados para o minidespejo.</span><span class="sxs-lookup"><span data-stu-id="e0ece-109">[in] An array of [CustomDumpItem](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md) instances, specifying the items to add to the mini-dump.</span></span> <span data-ttu-id="e0ece-110">Se `dwFlavor` não é DUMP_FLAVOR_Mini, `items` deve ser nulo.</span><span class="sxs-lookup"><span data-stu-id="e0ece-110">If `dwFlavor` is not DUMP_FLAVOR_Mini, `items` should be null.</span></span>  
  
 `dwReserved`  
 <span data-ttu-id="e0ece-111">[in] Reservado para uso futuro.</span><span class="sxs-lookup"><span data-stu-id="e0ece-111">[in] Reserved for future use.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e0ece-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="e0ece-112">Return Value</span></span>  
  
|<span data-ttu-id="e0ece-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e0ece-113">HRESULT</span></span>|<span data-ttu-id="e0ece-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="e0ece-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e0ece-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="e0ece-115">S_OK</span></span>|<span data-ttu-id="e0ece-116">O método é retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="e0ece-116">The method returned successfully.</span></span>|  
|<span data-ttu-id="e0ece-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e0ece-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e0ece-118">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="e0ece-118">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e0ece-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e0ece-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e0ece-120">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="e0ece-120">The call timed out.</span></span>|  
|<span data-ttu-id="e0ece-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e0ece-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e0ece-122">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="e0ece-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e0ece-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e0ece-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e0ece-124">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="e0ece-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e0ece-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e0ece-125">E_FAIL</span></span>|<span data-ttu-id="e0ece-126">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="e0ece-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e0ece-127">Depois que um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="e0ece-127">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e0ece-128">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e0ece-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e0ece-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="e0ece-129">Remarks</span></span>  
 <span data-ttu-id="e0ece-130">O `BeginCustomDump` método define a configuração de despejo de pilha personalizado.</span><span class="sxs-lookup"><span data-stu-id="e0ece-130">The `BeginCustomDump` method sets custom heap dump configuration.</span></span> <span data-ttu-id="e0ece-131">O [EndCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-endcustomdump-method.md) método limpa a configuração de despejo de pilha personalizado e libera qualquer estado associado.</span><span class="sxs-lookup"><span data-stu-id="e0ece-131">The [EndCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-endcustomdump-method.md) method clears the custom heap dump configuration and frees any associated state.</span></span> <span data-ttu-id="e0ece-132">Ele deve ser chamado depois que o despejo de pilha personalizado for concluído.</span><span class="sxs-lookup"><span data-stu-id="e0ece-132">It should be called after the custom heap dump is complete.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e0ece-133">Falha ao chamar `EndCustomDump` faz com que a memória vazem.</span><span class="sxs-lookup"><span data-stu-id="e0ece-133">Failure to call `EndCustomDump` causes memory to leak.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0ece-134">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e0ece-134">Requirements</span></span>  
 <span data-ttu-id="e0ece-135">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e0ece-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0ece-136">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e0ece-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e0ece-137">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="e0ece-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e0ece-138">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0ece-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0ece-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e0ece-139">See Also</span></span>  
 [<span data-ttu-id="e0ece-140">Estrutura CustomDumpItem</span><span class="sxs-lookup"><span data-stu-id="e0ece-140">CustomDumpItem Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md)  
 [<span data-ttu-id="e0ece-141">Enumeração ECustomDumpFlavor</span><span class="sxs-lookup"><span data-stu-id="e0ece-141">ECustomDumpFlavor Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpflavor-enumeration.md)  
 [<span data-ttu-id="e0ece-142">Interface ICLRErrorReportingManager</span><span class="sxs-lookup"><span data-stu-id="e0ece-142">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
