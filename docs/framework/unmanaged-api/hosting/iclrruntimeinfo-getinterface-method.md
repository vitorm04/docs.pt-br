---
title: "Método ICLRRuntimeInfo::GetInterface"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3c5150a10a813da85fc035c7bfa43a7647fac308
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrruntimeinfogetinterface-method"></a><span data-ttu-id="77557-102">Método ICLRRuntimeInfo::GetInterface</span><span class="sxs-lookup"><span data-stu-id="77557-102">ICLRRuntimeInfo::GetInterface Method</span></span>
<span data-ttu-id="77557-103">Carrega o CLR no processo atual e retorna o tempo de execução de ponteiros de interface, como [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md), [ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md), e [IMetaDataDispenserEx](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md).</span><span class="sxs-lookup"><span data-stu-id="77557-103">Loads the CLR into the current process and returns runtime interface pointers, such as [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md), [ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md), and [IMetaDataDispenserEx](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md).</span></span>  
  
 <span data-ttu-id="77557-104">Esse método substitui todos o `CorBindTo`\* funções no [funções de hospedagem de CLR preterido](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) seção.</span><span class="sxs-lookup"><span data-stu-id="77557-104">This method supersedes all the `CorBindTo`\* functions in the [Deprecated CLR Hosting Functions](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77557-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="77557-105">Syntax</span></span>  
  
```  
HRESULT GetInterface(  
[in]  REFCLSID rclsid,  
[in]  REFIID   riid,  
[out, iid_is(riid), retval] LPVOID *ppUnk);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="77557-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="77557-106">Parameters</span></span>  
 `rclsid`  
 <span data-ttu-id="77557-107">[in] A interface CLSID para coclass.</span><span class="sxs-lookup"><span data-stu-id="77557-107">[in] The CLSID interface for the coclass.</span></span>  
  
 `riid`  
 <span data-ttu-id="77557-108">[in] O IID da solicitados `rclsid` interface.</span><span class="sxs-lookup"><span data-stu-id="77557-108">[in] The IID of the requested `rclsid` interface.</span></span>  
  
 `ppUnk`  
 <span data-ttu-id="77557-109">[out] Um ponteiro para a interface consultado.</span><span class="sxs-lookup"><span data-stu-id="77557-109">[out] A pointer to the queried interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="77557-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="77557-110">Return Value</span></span>  
 <span data-ttu-id="77557-111">Este método retorna a seguintes HRESULTs específicos, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="77557-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="77557-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="77557-112">HRESULT</span></span>|<span data-ttu-id="77557-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="77557-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="77557-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="77557-114">S_OK</span></span>|<span data-ttu-id="77557-115">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="77557-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="77557-116">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="77557-116">E_POINTER</span></span>|<span data-ttu-id="77557-117">`ppUnk` é nulo.</span><span class="sxs-lookup"><span data-stu-id="77557-117">`ppUnk` is null.</span></span>|  
|<span data-ttu-id="77557-118">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="77557-118">E_OUTOFMEMORY</span></span>|<span data-ttu-id="77557-119">Não há memória suficiente está disponível para tratar a solicitação.</span><span class="sxs-lookup"><span data-stu-id="77557-119">Not enough memory is available to handle the request.</span></span>|  
|<span data-ttu-id="77557-120">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span><span class="sxs-lookup"><span data-stu-id="77557-120">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span></span>|<span data-ttu-id="77557-121">Um tempo de execução diferente já foi associado à política de ativação 2 de versão do CLR herdada.</span><span class="sxs-lookup"><span data-stu-id="77557-121">A different runtime was already bound to the legacy CLR version 2 activation policy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="77557-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="77557-122">Remarks</span></span>  
 <span data-ttu-id="77557-123">Este método faz com que o CLR ser carregado, mas não inicializado.</span><span class="sxs-lookup"><span data-stu-id="77557-123">This method causes the CLR to be loaded but not initialized.</span></span>  
  
 <span data-ttu-id="77557-124">A tabela a seguir mostra as combinações com suporte para `rclsid` e `riid`.</span><span class="sxs-lookup"><span data-stu-id="77557-124">The following table shows the supported combinations for `rclsid` and `riid`.</span></span>  
  
|`rclsid`|`riid`|  
|--------------|------------|  
|<span data-ttu-id="77557-125">CLSID_CorMetaDataDispenser</span><span class="sxs-lookup"><span data-stu-id="77557-125">CLSID_CorMetaDataDispenser</span></span>|<span data-ttu-id="77557-126">IID_IMetaDataDispenser, IID_IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="77557-126">IID_IMetaDataDispenser, IID_IMetaDataDispenserEx</span></span>|  
|<span data-ttu-id="77557-127">CLSID_CorMetaDataDispenserRuntime</span><span class="sxs-lookup"><span data-stu-id="77557-127">CLSID_CorMetaDataDispenserRuntime</span></span>|<span data-ttu-id="77557-128">IID_IMetaDataDispenser, IID_IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="77557-128">IID_IMetaDataDispenser, IID_IMetaDataDispenserEx</span></span>|  
|<span data-ttu-id="77557-129">CLSID_CorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="77557-129">CLSID_CorRuntimeHost</span></span>|<span data-ttu-id="77557-130">IID_ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="77557-130">IID_ICorRuntimeHost</span></span>|  
|<span data-ttu-id="77557-131">CLSID_CLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="77557-131">CLSID_CLRRuntimeHost</span></span>|<span data-ttu-id="77557-132">IID_ICLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="77557-132">IID_ICLRRuntimeHost</span></span>|  
|<span data-ttu-id="77557-133">CLSID_TypeNameFactory</span><span class="sxs-lookup"><span data-stu-id="77557-133">CLSID_TypeNameFactory</span></span>|<span data-ttu-id="77557-134">IID_ITypeNameFactory</span><span class="sxs-lookup"><span data-stu-id="77557-134">IID_ITypeNameFactory</span></span>|  
|<span data-ttu-id="77557-135">CLSID_CLRDebuggingLegacy</span><span class="sxs-lookup"><span data-stu-id="77557-135">CLSID_CLRDebuggingLegacy</span></span>|<span data-ttu-id="77557-136">IID_ICorDebug</span><span class="sxs-lookup"><span data-stu-id="77557-136">IID_ICorDebug</span></span>|  
|||  
|<span data-ttu-id="77557-137">CLSID_CLRStrongName</span><span class="sxs-lookup"><span data-stu-id="77557-137">CLSID_CLRStrongName</span></span>|<span data-ttu-id="77557-138">IID_ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="77557-138">IID_ICLRStrongName</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="77557-139">Requisitos</span><span class="sxs-lookup"><span data-stu-id="77557-139">Requirements</span></span>  
 <span data-ttu-id="77557-140">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77557-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77557-141">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="77557-141">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="77557-142">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="77557-142">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="77557-143">**Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77557-143">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77557-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="77557-144">See Also</span></span>  
 [<span data-ttu-id="77557-145">Interface ICLRRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="77557-145">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [<span data-ttu-id="77557-146">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="77557-146">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="77557-147">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="77557-147">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
