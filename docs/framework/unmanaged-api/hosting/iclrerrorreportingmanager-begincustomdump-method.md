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
ms.openlocfilehash: 4c83ffaf920abe005ba987e0a744e13aa0d3c016
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615664"
---
# <a name="iclrerrorreportingmanagerbegincustomdump-method"></a><span data-ttu-id="43ac7-102">Método ICLRErrorReportingManager::BeginCustomDump</span><span class="sxs-lookup"><span data-stu-id="43ac7-102">ICLRErrorReportingManager::BeginCustomDump Method</span></span>
<span data-ttu-id="43ac7-103">Especifica a configuração de despejos de heap personalizados para o relatório de erros.</span><span class="sxs-lookup"><span data-stu-id="43ac7-103">Specifies the configuration of custom heap dumps for error reporting.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43ac7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="43ac7-104">Syntax</span></span>  
  
```cpp  
HRESULT BeginCustomDump (  
    [in] ECustomDumpFlavor dwFlavor,  
    [in] DWORD dwNumItems,  
    [in, size_is(dwNumItems), length_is(dwNumItems)] CustomDumpItem items[],  
    DWORD dwReserved  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="43ac7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="43ac7-105">Parameters</span></span>  
 `dwFlavor`  
 <span data-ttu-id="43ac7-106">no Um valor [ECustomDumpFlavor](ecustomdumpflavor-enumeration.md) que indica o tipo de despejo de heap no qual Compilar o despejo de heap personalizado.</span><span class="sxs-lookup"><span data-stu-id="43ac7-106">[in] A [ECustomDumpFlavor](ecustomdumpflavor-enumeration.md) value that indicates the kind of heap dump upon which to build the custom heap dump.</span></span>  
  
 `dwNumItems`  
 <span data-ttu-id="43ac7-107">no O comprimento da `items` matriz.</span><span class="sxs-lookup"><span data-stu-id="43ac7-107">[in] The length of the `items` array.</span></span> <span data-ttu-id="43ac7-108">Se `dwFlavor` não for DUMP_FLAVOR_Mini, `dwNumItems` deverá ser zero.</span><span class="sxs-lookup"><span data-stu-id="43ac7-108">If `dwFlavor` is not DUMP_FLAVOR_Mini, `dwNumItems` should be zero.</span></span>  
  
 `items`  
 <span data-ttu-id="43ac7-109">no Uma matriz de instâncias de [CustomDumpItem](customdumpitem-structure.md) , especificando os itens a serem adicionados ao mini-despejo.</span><span class="sxs-lookup"><span data-stu-id="43ac7-109">[in] An array of [CustomDumpItem](customdumpitem-structure.md) instances, specifying the items to add to the mini-dump.</span></span> <span data-ttu-id="43ac7-110">Se `dwFlavor` não for DUMP_FLAVOR_Mini, `items` deverá ser NULL.</span><span class="sxs-lookup"><span data-stu-id="43ac7-110">If `dwFlavor` is not DUMP_FLAVOR_Mini, `items` should be null.</span></span>  
  
 `dwReserved`  
 <span data-ttu-id="43ac7-111">no Reservado para uso futuro.</span><span class="sxs-lookup"><span data-stu-id="43ac7-111">[in] Reserved for future use.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="43ac7-112">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="43ac7-112">Return Value</span></span>  
  
|<span data-ttu-id="43ac7-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="43ac7-113">HRESULT</span></span>|<span data-ttu-id="43ac7-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="43ac7-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="43ac7-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="43ac7-115">S_OK</span></span>|<span data-ttu-id="43ac7-116">O método foi retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="43ac7-116">The method returned successfully.</span></span>|  
|<span data-ttu-id="43ac7-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="43ac7-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="43ac7-118">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="43ac7-118">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="43ac7-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="43ac7-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="43ac7-120">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="43ac7-120">The call timed out.</span></span>|  
|<span data-ttu-id="43ac7-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="43ac7-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="43ac7-122">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="43ac7-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="43ac7-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="43ac7-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="43ac7-124">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="43ac7-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="43ac7-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="43ac7-125">E_FAIL</span></span>|<span data-ttu-id="43ac7-126">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="43ac7-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="43ac7-127">Depois que um método retorna E_FAIL, o CLR não pode mais ser usado no processo.</span><span class="sxs-lookup"><span data-stu-id="43ac7-127">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="43ac7-128">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="43ac7-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="43ac7-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="43ac7-129">Remarks</span></span>  
 <span data-ttu-id="43ac7-130">O `BeginCustomDump` método define a configuração de despejo de heap personalizado.</span><span class="sxs-lookup"><span data-stu-id="43ac7-130">The `BeginCustomDump` method sets custom heap dump configuration.</span></span> <span data-ttu-id="43ac7-131">O método [EndCustomDump](iclrerrorreportingmanager-endcustomdump-method.md) limpa a configuração de despejo de heap personalizada e libera qualquer estado associado.</span><span class="sxs-lookup"><span data-stu-id="43ac7-131">The [EndCustomDump](iclrerrorreportingmanager-endcustomdump-method.md) method clears the custom heap dump configuration and frees any associated state.</span></span> <span data-ttu-id="43ac7-132">Ele deve ser chamado após a conclusão do despejo de heap personalizado.</span><span class="sxs-lookup"><span data-stu-id="43ac7-132">It should be called after the custom heap dump is complete.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="43ac7-133">Falha ao chamar `EndCustomDump` faz com que a memória seja vazada.</span><span class="sxs-lookup"><span data-stu-id="43ac7-133">Failure to call `EndCustomDump` causes memory to leak.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="43ac7-134">Requisitos</span><span class="sxs-lookup"><span data-stu-id="43ac7-134">Requirements</span></span>  
 <span data-ttu-id="43ac7-135">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="43ac7-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43ac7-136">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="43ac7-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="43ac7-137">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="43ac7-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="43ac7-138">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="43ac7-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43ac7-139">Veja também</span><span class="sxs-lookup"><span data-stu-id="43ac7-139">See also</span></span>

- [<span data-ttu-id="43ac7-140">Estrutura CustomDumpItem</span><span class="sxs-lookup"><span data-stu-id="43ac7-140">CustomDumpItem Structure</span></span>](customdumpitem-structure.md)
- [<span data-ttu-id="43ac7-141">Enumeração ECustomDumpFlavor</span><span class="sxs-lookup"><span data-stu-id="43ac7-141">ECustomDumpFlavor Enumeration</span></span>](ecustomdumpflavor-enumeration.md)
- [<span data-ttu-id="43ac7-142">Interface ICLRErrorReportingManager</span><span class="sxs-lookup"><span data-stu-id="43ac7-142">ICLRErrorReportingManager Interface</span></span>](iclrerrorreportingmanager-interface.md)
