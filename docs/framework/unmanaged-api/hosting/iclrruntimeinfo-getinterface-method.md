---
title: Método ICLRRuntimeInfo::GetInterface
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.GetInterface
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::GetInterface
helpviewer_keywords:
- GetInterface method [.NET Framework hosting]
- ICLRRuntimeInfo::GetInterface method [.NET Framework hosting]
ms.assetid: cc7b0e5b-48c3-4509-8ebb-611ddb1f7ec2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4244ef04d6789b7c17ccc8330cb0c26a6c9f3866
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67765551"
---
# <a name="iclrruntimeinfogetinterface-method"></a><span data-ttu-id="db031-102">Método ICLRRuntimeInfo::GetInterface</span><span class="sxs-lookup"><span data-stu-id="db031-102">ICLRRuntimeInfo::GetInterface Method</span></span>
<span data-ttu-id="db031-103">Carrega o CLR no processo atual e retorna o tempo de execução de ponteiros de interface, tais como [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md), [ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md), e [IMetaDataDispenserEx](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md).</span><span class="sxs-lookup"><span data-stu-id="db031-103">Loads the CLR into the current process and returns runtime interface pointers, such as [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md), [ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md), and [IMetaDataDispenserEx](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md).</span></span>  
  
 <span data-ttu-id="db031-104">Esse método substitui todos o `CorBindTo`\* funções na [funções de hospedagem de CLR preterido](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) seção.</span><span class="sxs-lookup"><span data-stu-id="db031-104">This method supersedes all the `CorBindTo`\* functions in the [Deprecated CLR Hosting Functions](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db031-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="db031-105">Syntax</span></span>  
  
```cpp  
HRESULT GetInterface(  
[in]  REFCLSID rclsid,  
[in]  REFIID   riid,  
[out, iid_is(riid), retval] LPVOID *ppUnk);  
```  
  
## <a name="parameters"></a><span data-ttu-id="db031-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="db031-106">Parameters</span></span>  
 `rclsid`  
 <span data-ttu-id="db031-107">[in] A interface do CLSID para coclass.</span><span class="sxs-lookup"><span data-stu-id="db031-107">[in] The CLSID interface for the coclass.</span></span>  
  
 `riid`  
 <span data-ttu-id="db031-108">[in] O IID da solicitada `rclsid` interface.</span><span class="sxs-lookup"><span data-stu-id="db031-108">[in] The IID of the requested `rclsid` interface.</span></span>  
  
 `ppUnk`  
 <span data-ttu-id="db031-109">[out] Um ponteiro para a interface consultado.</span><span class="sxs-lookup"><span data-stu-id="db031-109">[out] A pointer to the queried interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="db031-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="db031-110">Return Value</span></span>  
 <span data-ttu-id="db031-111">Esse método retorna os HRESULTs específicos a seguir, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="db031-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="db031-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="db031-112">HRESULT</span></span>|<span data-ttu-id="db031-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="db031-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="db031-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="db031-114">S_OK</span></span>|<span data-ttu-id="db031-115">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="db031-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="db031-116">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="db031-116">E_POINTER</span></span>|<span data-ttu-id="db031-117">`ppUnk` é nulo.</span><span class="sxs-lookup"><span data-stu-id="db031-117">`ppUnk` is null.</span></span>|  
|<span data-ttu-id="db031-118">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="db031-118">E_OUTOFMEMORY</span></span>|<span data-ttu-id="db031-119">Não há memória suficiente está disponível para tratar a solicitação.</span><span class="sxs-lookup"><span data-stu-id="db031-119">Not enough memory is available to handle the request.</span></span>|  
|<span data-ttu-id="db031-120">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span><span class="sxs-lookup"><span data-stu-id="db031-120">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span></span>|<span data-ttu-id="db031-121">Um tempo de execução diferente já foi associado à política de 2 de ativação de versão do CLR herdada.</span><span class="sxs-lookup"><span data-stu-id="db031-121">A different runtime was already bound to the legacy CLR version 2 activation policy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="db031-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="db031-122">Remarks</span></span>  
 <span data-ttu-id="db031-123">Esse método faz com que o CLR a ser carregado, mas não inicializado.</span><span class="sxs-lookup"><span data-stu-id="db031-123">This method causes the CLR to be loaded but not initialized.</span></span>  
  
 <span data-ttu-id="db031-124">A tabela a seguir mostra as combinações com suporte para `rclsid` e `riid`.</span><span class="sxs-lookup"><span data-stu-id="db031-124">The following table shows the supported combinations for `rclsid` and `riid`.</span></span>  
  
|`rclsid`|`riid`|  
|--------------|------------|  
|<span data-ttu-id="db031-125">CLSID_CorMetaDataDispenser</span><span class="sxs-lookup"><span data-stu-id="db031-125">CLSID_CorMetaDataDispenser</span></span>|<span data-ttu-id="db031-126">IID_IMetaDataDispenser, IID_IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="db031-126">IID_IMetaDataDispenser, IID_IMetaDataDispenserEx</span></span>|  
|<span data-ttu-id="db031-127">CLSID_CorMetaDataDispenserRuntime</span><span class="sxs-lookup"><span data-stu-id="db031-127">CLSID_CorMetaDataDispenserRuntime</span></span>|<span data-ttu-id="db031-128">IID_IMetaDataDispenser, IID_IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="db031-128">IID_IMetaDataDispenser, IID_IMetaDataDispenserEx</span></span>|  
|<span data-ttu-id="db031-129">CLSID_CorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="db031-129">CLSID_CorRuntimeHost</span></span>|<span data-ttu-id="db031-130">IID_ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="db031-130">IID_ICorRuntimeHost</span></span>|  
|<span data-ttu-id="db031-131">CLSID_CLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="db031-131">CLSID_CLRRuntimeHost</span></span>|<span data-ttu-id="db031-132">IID_ICLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="db031-132">IID_ICLRRuntimeHost</span></span>|  
|<span data-ttu-id="db031-133">CLSID_TypeNameFactory</span><span class="sxs-lookup"><span data-stu-id="db031-133">CLSID_TypeNameFactory</span></span>|<span data-ttu-id="db031-134">IID_ITypeNameFactory</span><span class="sxs-lookup"><span data-stu-id="db031-134">IID_ITypeNameFactory</span></span>|  
|<span data-ttu-id="db031-135">CLSID_CLRDebuggingLegacy</span><span class="sxs-lookup"><span data-stu-id="db031-135">CLSID_CLRDebuggingLegacy</span></span>|<span data-ttu-id="db031-136">IID_ICorDebug</span><span class="sxs-lookup"><span data-stu-id="db031-136">IID_ICorDebug</span></span>|  
|||  
|<span data-ttu-id="db031-137">CLSID_CLRStrongName</span><span class="sxs-lookup"><span data-stu-id="db031-137">CLSID_CLRStrongName</span></span>|<span data-ttu-id="db031-138">IID_ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="db031-138">IID_ICLRStrongName</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="db031-139">Requisitos</span><span class="sxs-lookup"><span data-stu-id="db031-139">Requirements</span></span>  
 <span data-ttu-id="db031-140">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db031-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db031-141">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="db031-141">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="db031-142">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="db031-142">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="db031-143">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db031-143">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db031-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="db031-144">See also</span></span>

- [<span data-ttu-id="db031-145">Interface ICLRRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="db031-145">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="db031-146">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="db031-146">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="db031-147">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="db031-147">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
