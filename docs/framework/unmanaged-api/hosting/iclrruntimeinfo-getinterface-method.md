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
ms.openlocfilehash: 4924f373270a30b593e27c334d383963fc4a7cf0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="iclrruntimeinfogetinterface-method"></a><span data-ttu-id="0e99c-102">Método ICLRRuntimeInfo::GetInterface</span><span class="sxs-lookup"><span data-stu-id="0e99c-102">ICLRRuntimeInfo::GetInterface Method</span></span>
<span data-ttu-id="0e99c-103">Carrega o CLR no processo atual e retorna o tempo de execução de ponteiros de interface, como [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md), [ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md), e [IMetaDataDispenserEx](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md).</span><span class="sxs-lookup"><span data-stu-id="0e99c-103">Loads the CLR into the current process and returns runtime interface pointers, such as [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md), [ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md), and [IMetaDataDispenserEx](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md).</span></span>  
  
 <span data-ttu-id="0e99c-104">Esse método substitui todos o `CorBindTo`\* funções no [funções de hospedagem de CLR preterido](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) seção.</span><span class="sxs-lookup"><span data-stu-id="0e99c-104">This method supersedes all the `CorBindTo`\* functions in the [Deprecated CLR Hosting Functions](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e99c-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0e99c-105">Syntax</span></span>  
  
```  
HRESULT GetInterface(  
[in]  REFCLSID rclsid,  
[in]  REFIID   riid,  
[out, iid_is(riid), retval] LPVOID *ppUnk);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0e99c-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0e99c-106">Parameters</span></span>  
 `rclsid`  
 <span data-ttu-id="0e99c-107">[in] A interface CLSID para coclass.</span><span class="sxs-lookup"><span data-stu-id="0e99c-107">[in] The CLSID interface for the coclass.</span></span>  
  
 `riid`  
 <span data-ttu-id="0e99c-108">[in] O IID da solicitados `rclsid` interface.</span><span class="sxs-lookup"><span data-stu-id="0e99c-108">[in] The IID of the requested `rclsid` interface.</span></span>  
  
 `ppUnk`  
 <span data-ttu-id="0e99c-109">[out] Um ponteiro para a interface consultado.</span><span class="sxs-lookup"><span data-stu-id="0e99c-109">[out] A pointer to the queried interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0e99c-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="0e99c-110">Return Value</span></span>  
 <span data-ttu-id="0e99c-111">Este método retorna a seguintes HRESULTs específicos, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="0e99c-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="0e99c-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0e99c-112">HRESULT</span></span>|<span data-ttu-id="0e99c-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="0e99c-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0e99c-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="0e99c-114">S_OK</span></span>|<span data-ttu-id="0e99c-115">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="0e99c-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="0e99c-116">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="0e99c-116">E_POINTER</span></span>|<span data-ttu-id="0e99c-117">`ppUnk` é nulo.</span><span class="sxs-lookup"><span data-stu-id="0e99c-117">`ppUnk` is null.</span></span>|  
|<span data-ttu-id="0e99c-118">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="0e99c-118">E_OUTOFMEMORY</span></span>|<span data-ttu-id="0e99c-119">Não há memória suficiente está disponível para tratar a solicitação.</span><span class="sxs-lookup"><span data-stu-id="0e99c-119">Not enough memory is available to handle the request.</span></span>|  
|<span data-ttu-id="0e99c-120">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span><span class="sxs-lookup"><span data-stu-id="0e99c-120">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span></span>|<span data-ttu-id="0e99c-121">Um tempo de execução diferente já foi associado à política de ativação 2 de versão do CLR herdada.</span><span class="sxs-lookup"><span data-stu-id="0e99c-121">A different runtime was already bound to the legacy CLR version 2 activation policy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0e99c-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="0e99c-122">Remarks</span></span>  
 <span data-ttu-id="0e99c-123">Este método faz com que o CLR ser carregado, mas não inicializado.</span><span class="sxs-lookup"><span data-stu-id="0e99c-123">This method causes the CLR to be loaded but not initialized.</span></span>  
  
 <span data-ttu-id="0e99c-124">A tabela a seguir mostra as combinações com suporte para `rclsid` e `riid`.</span><span class="sxs-lookup"><span data-stu-id="0e99c-124">The following table shows the supported combinations for `rclsid` and `riid`.</span></span>  
  
|`rclsid`|`riid`|  
|--------------|------------|  
|<span data-ttu-id="0e99c-125">CLSID_CorMetaDataDispenser</span><span class="sxs-lookup"><span data-stu-id="0e99c-125">CLSID_CorMetaDataDispenser</span></span>|<span data-ttu-id="0e99c-126">IID_IMetaDataDispenser, IID_IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="0e99c-126">IID_IMetaDataDispenser, IID_IMetaDataDispenserEx</span></span>|  
|<span data-ttu-id="0e99c-127">CLSID_CorMetaDataDispenserRuntime</span><span class="sxs-lookup"><span data-stu-id="0e99c-127">CLSID_CorMetaDataDispenserRuntime</span></span>|<span data-ttu-id="0e99c-128">IID_IMetaDataDispenser, IID_IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="0e99c-128">IID_IMetaDataDispenser, IID_IMetaDataDispenserEx</span></span>|  
|<span data-ttu-id="0e99c-129">CLSID_CorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="0e99c-129">CLSID_CorRuntimeHost</span></span>|<span data-ttu-id="0e99c-130">IID_ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="0e99c-130">IID_ICorRuntimeHost</span></span>|  
|<span data-ttu-id="0e99c-131">CLSID_CLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="0e99c-131">CLSID_CLRRuntimeHost</span></span>|<span data-ttu-id="0e99c-132">IID_ICLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="0e99c-132">IID_ICLRRuntimeHost</span></span>|  
|<span data-ttu-id="0e99c-133">CLSID_TypeNameFactory</span><span class="sxs-lookup"><span data-stu-id="0e99c-133">CLSID_TypeNameFactory</span></span>|<span data-ttu-id="0e99c-134">IID_ITypeNameFactory</span><span class="sxs-lookup"><span data-stu-id="0e99c-134">IID_ITypeNameFactory</span></span>|  
|<span data-ttu-id="0e99c-135">CLSID_CLRDebuggingLegacy</span><span class="sxs-lookup"><span data-stu-id="0e99c-135">CLSID_CLRDebuggingLegacy</span></span>|<span data-ttu-id="0e99c-136">IID_ICorDebug</span><span class="sxs-lookup"><span data-stu-id="0e99c-136">IID_ICorDebug</span></span>|  
|||  
|<span data-ttu-id="0e99c-137">CLSID_CLRStrongName</span><span class="sxs-lookup"><span data-stu-id="0e99c-137">CLSID_CLRStrongName</span></span>|<span data-ttu-id="0e99c-138">IID_ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="0e99c-138">IID_ICLRStrongName</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0e99c-139">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0e99c-139">Requirements</span></span>  
 <span data-ttu-id="0e99c-140">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0e99c-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e99c-141">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="0e99c-141">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="0e99c-142">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="0e99c-142">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0e99c-143">**Versões do .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e99c-143">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e99c-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0e99c-144">See Also</span></span>  
 [<span data-ttu-id="0e99c-145">Interface ICLRRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="0e99c-145">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [<span data-ttu-id="0e99c-146">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="0e99c-146">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="0e99c-147">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="0e99c-147">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
