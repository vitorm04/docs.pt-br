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
ms.openlocfilehash: 7e6d3f4a1c77e8b5070086e871d4d08fcf138f6f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54696913"
---
# <a name="iclrerrorreportingmanagerbegincustomdump-method"></a><span data-ttu-id="41bf1-102">Método ICLRErrorReportingManager::BeginCustomDump</span><span class="sxs-lookup"><span data-stu-id="41bf1-102">ICLRErrorReportingManager::BeginCustomDump Method</span></span>
<span data-ttu-id="41bf1-103">Especifica a configuração de despejos de heap personalizado para o relatório de erros.</span><span class="sxs-lookup"><span data-stu-id="41bf1-103">Specifies the configuration of custom heap dumps for error reporting.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41bf1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="41bf1-104">Syntax</span></span>  
  
```  
HRESULT BeginCustomDump (  
    [in] ECustomDumpFlavor dwFlavor,  
    [in] DWORD dwNumItems,  
    [in, size_is(dwNumItems), length_is(dwNumItems)] CustomDumpItem items[],  
    DWORD dwReserved  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="41bf1-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="41bf1-105">Parameters</span></span>  
 `dwFlavor`  
 <span data-ttu-id="41bf1-106">[in] Um [ECustomDumpFlavor](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpflavor-enumeration.md) valor que indica o tipo de despejo de pilha no qual criar o despejo de heap personalizado.</span><span class="sxs-lookup"><span data-stu-id="41bf1-106">[in] A [ECustomDumpFlavor](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpflavor-enumeration.md) value that indicates the kind of heap dump upon which to build the custom heap dump.</span></span>  
  
 `dwNumItems`  
 <span data-ttu-id="41bf1-107">[in] O comprimento do `items` matriz.</span><span class="sxs-lookup"><span data-stu-id="41bf1-107">[in] The length of the `items` array.</span></span> <span data-ttu-id="41bf1-108">Se `dwFlavor` não é DUMP_FLAVOR_Mini, `dwNumItems` deve ser zero.</span><span class="sxs-lookup"><span data-stu-id="41bf1-108">If `dwFlavor` is not DUMP_FLAVOR_Mini, `dwNumItems` should be zero.</span></span>  
  
 `items`  
 <span data-ttu-id="41bf1-109">[in] Uma matriz de [CustomDumpItem](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md) instâncias, especificando os itens a serem adicionados ao miniarquivo de despejo.</span><span class="sxs-lookup"><span data-stu-id="41bf1-109">[in] An array of [CustomDumpItem](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md) instances, specifying the items to add to the mini-dump.</span></span> <span data-ttu-id="41bf1-110">Se `dwFlavor` não é DUMP_FLAVOR_Mini, `items` deve ser nulo.</span><span class="sxs-lookup"><span data-stu-id="41bf1-110">If `dwFlavor` is not DUMP_FLAVOR_Mini, `items` should be null.</span></span>  
  
 `dwReserved`  
 <span data-ttu-id="41bf1-111">[in] Reservado para uso futuro.</span><span class="sxs-lookup"><span data-stu-id="41bf1-111">[in] Reserved for future use.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="41bf1-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="41bf1-112">Return Value</span></span>  
  
|<span data-ttu-id="41bf1-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="41bf1-113">HRESULT</span></span>|<span data-ttu-id="41bf1-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="41bf1-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="41bf1-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="41bf1-115">S_OK</span></span>|<span data-ttu-id="41bf1-116">O método é retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="41bf1-116">The method returned successfully.</span></span>|  
|<span data-ttu-id="41bf1-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="41bf1-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="41bf1-118">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="41bf1-118">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="41bf1-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="41bf1-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="41bf1-120">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="41bf1-120">The call timed out.</span></span>|  
|<span data-ttu-id="41bf1-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="41bf1-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="41bf1-122">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="41bf1-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="41bf1-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="41bf1-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="41bf1-124">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="41bf1-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="41bf1-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="41bf1-125">E_FAIL</span></span>|<span data-ttu-id="41bf1-126">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="41bf1-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="41bf1-127">Depois que um método retorna E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="41bf1-127">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="41bf1-128">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="41bf1-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="41bf1-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="41bf1-129">Remarks</span></span>  
 <span data-ttu-id="41bf1-130">O `BeginCustomDump` método define a configuração de despejo de heap personalizado.</span><span class="sxs-lookup"><span data-stu-id="41bf1-130">The `BeginCustomDump` method sets custom heap dump configuration.</span></span> <span data-ttu-id="41bf1-131">O [EndCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-endcustomdump-method.md) método limpa a configuração de despejo de heap personalizado e libera qualquer estado associado.</span><span class="sxs-lookup"><span data-stu-id="41bf1-131">The [EndCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-endcustomdump-method.md) method clears the custom heap dump configuration and frees any associated state.</span></span> <span data-ttu-id="41bf1-132">Ele deve ser chamado depois que o despejo de heap personalizado for concluído.</span><span class="sxs-lookup"><span data-stu-id="41bf1-132">It should be called after the custom heap dump is complete.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="41bf1-133">Falha ao chamar `EndCustomDump` faz com que a memória de vazar.</span><span class="sxs-lookup"><span data-stu-id="41bf1-133">Failure to call `EndCustomDump` causes memory to leak.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41bf1-134">Requisitos</span><span class="sxs-lookup"><span data-stu-id="41bf1-134">Requirements</span></span>  
 <span data-ttu-id="41bf1-135">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="41bf1-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41bf1-136">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="41bf1-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="41bf1-137">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="41bf1-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="41bf1-138">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41bf1-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41bf1-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="41bf1-139">See also</span></span>
- [<span data-ttu-id="41bf1-140">Estrutura CustomDumpItem</span><span class="sxs-lookup"><span data-stu-id="41bf1-140">CustomDumpItem Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md)
- [<span data-ttu-id="41bf1-141">Enumeração ECustomDumpFlavor</span><span class="sxs-lookup"><span data-stu-id="41bf1-141">ECustomDumpFlavor Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpflavor-enumeration.md)
- [<span data-ttu-id="41bf1-142">Interface ICLRErrorReportingManager</span><span class="sxs-lookup"><span data-stu-id="41bf1-142">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
