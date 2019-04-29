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
ms.openlocfilehash: 2f229e421cc69f2ff45110233c4c6c36d7a1fc4c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61771755"
---
# <a name="iclrruntimeinfogetinterface-method"></a><span data-ttu-id="d6101-102">Método ICLRRuntimeInfo::GetInterface</span><span class="sxs-lookup"><span data-stu-id="d6101-102">ICLRRuntimeInfo::GetInterface Method</span></span>
<span data-ttu-id="d6101-103">Carrega o CLR no processo atual e retorna o tempo de execução de ponteiros de interface, tais como [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md), [ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md), e [IMetaDataDispenserEx](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md).</span><span class="sxs-lookup"><span data-stu-id="d6101-103">Loads the CLR into the current process and returns runtime interface pointers, such as [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md), [ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md), and [IMetaDataDispenserEx](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md).</span></span>  
  
 <span data-ttu-id="d6101-104">Esse método substitui todos o `CorBindTo`\* funções na [funções de hospedagem de CLR preterido](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) seção.</span><span class="sxs-lookup"><span data-stu-id="d6101-104">This method supersedes all the `CorBindTo`\* functions in the [Deprecated CLR Hosting Functions](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6101-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d6101-105">Syntax</span></span>  
  
```  
HRESULT GetInterface(  
[in]  REFCLSID rclsid,  
[in]  REFIID   riid,  
[out, iid_is(riid), retval] LPVOID *ppUnk);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d6101-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d6101-106">Parameters</span></span>  
 `rclsid`  
 <span data-ttu-id="d6101-107">[in] A interface do CLSID para coclass.</span><span class="sxs-lookup"><span data-stu-id="d6101-107">[in] The CLSID interface for the coclass.</span></span>  
  
 `riid`  
 <span data-ttu-id="d6101-108">[in] O IID da solicitada `rclsid` interface.</span><span class="sxs-lookup"><span data-stu-id="d6101-108">[in] The IID of the requested `rclsid` interface.</span></span>  
  
 `ppUnk`  
 <span data-ttu-id="d6101-109">[out] Um ponteiro para a interface consultado.</span><span class="sxs-lookup"><span data-stu-id="d6101-109">[out] A pointer to the queried interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d6101-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="d6101-110">Return Value</span></span>  
 <span data-ttu-id="d6101-111">Esse método retorna os HRESULTs específicos a seguir, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="d6101-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="d6101-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d6101-112">HRESULT</span></span>|<span data-ttu-id="d6101-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="d6101-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d6101-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="d6101-114">S_OK</span></span>|<span data-ttu-id="d6101-115">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="d6101-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="d6101-116">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="d6101-116">E_POINTER</span></span>|<span data-ttu-id="d6101-117">`ppUnk` é nulo.</span><span class="sxs-lookup"><span data-stu-id="d6101-117">`ppUnk` is null.</span></span>|  
|<span data-ttu-id="d6101-118">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="d6101-118">E_OUTOFMEMORY</span></span>|<span data-ttu-id="d6101-119">Não há memória suficiente está disponível para tratar a solicitação.</span><span class="sxs-lookup"><span data-stu-id="d6101-119">Not enough memory is available to handle the request.</span></span>|  
|<span data-ttu-id="d6101-120">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span><span class="sxs-lookup"><span data-stu-id="d6101-120">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span></span>|<span data-ttu-id="d6101-121">Um tempo de execução diferente já foi associado à política de 2 de ativação de versão do CLR herdada.</span><span class="sxs-lookup"><span data-stu-id="d6101-121">A different runtime was already bound to the legacy CLR version 2 activation policy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d6101-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="d6101-122">Remarks</span></span>  
 <span data-ttu-id="d6101-123">Esse método faz com que o CLR a ser carregado, mas não inicializado.</span><span class="sxs-lookup"><span data-stu-id="d6101-123">This method causes the CLR to be loaded but not initialized.</span></span>  
  
 <span data-ttu-id="d6101-124">A tabela a seguir mostra as combinações com suporte para `rclsid` e `riid`.</span><span class="sxs-lookup"><span data-stu-id="d6101-124">The following table shows the supported combinations for `rclsid` and `riid`.</span></span>  
  
|`rclsid`|`riid`|  
|--------------|------------|  
|<span data-ttu-id="d6101-125">CLSID_CorMetaDataDispenser</span><span class="sxs-lookup"><span data-stu-id="d6101-125">CLSID_CorMetaDataDispenser</span></span>|<span data-ttu-id="d6101-126">IID_IMetaDataDispenser, IID_IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="d6101-126">IID_IMetaDataDispenser, IID_IMetaDataDispenserEx</span></span>|  
|<span data-ttu-id="d6101-127">CLSID_CorMetaDataDispenserRuntime</span><span class="sxs-lookup"><span data-stu-id="d6101-127">CLSID_CorMetaDataDispenserRuntime</span></span>|<span data-ttu-id="d6101-128">IID_IMetaDataDispenser, IID_IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="d6101-128">IID_IMetaDataDispenser, IID_IMetaDataDispenserEx</span></span>|  
|<span data-ttu-id="d6101-129">CLSID_CorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="d6101-129">CLSID_CorRuntimeHost</span></span>|<span data-ttu-id="d6101-130">IID_ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="d6101-130">IID_ICorRuntimeHost</span></span>|  
|<span data-ttu-id="d6101-131">CLSID_CLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="d6101-131">CLSID_CLRRuntimeHost</span></span>|<span data-ttu-id="d6101-132">IID_ICLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="d6101-132">IID_ICLRRuntimeHost</span></span>|  
|<span data-ttu-id="d6101-133">CLSID_TypeNameFactory</span><span class="sxs-lookup"><span data-stu-id="d6101-133">CLSID_TypeNameFactory</span></span>|<span data-ttu-id="d6101-134">IID_ITypeNameFactory</span><span class="sxs-lookup"><span data-stu-id="d6101-134">IID_ITypeNameFactory</span></span>|  
|<span data-ttu-id="d6101-135">CLSID_CLRDebuggingLegacy</span><span class="sxs-lookup"><span data-stu-id="d6101-135">CLSID_CLRDebuggingLegacy</span></span>|<span data-ttu-id="d6101-136">IID_ICorDebug</span><span class="sxs-lookup"><span data-stu-id="d6101-136">IID_ICorDebug</span></span>|  
|||  
|<span data-ttu-id="d6101-137">CLSID_CLRStrongName</span><span class="sxs-lookup"><span data-stu-id="d6101-137">CLSID_CLRStrongName</span></span>|<span data-ttu-id="d6101-138">IID_ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="d6101-138">IID_ICLRStrongName</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d6101-139">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d6101-139">Requirements</span></span>  
 <span data-ttu-id="d6101-140">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6101-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6101-141">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="d6101-141">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="d6101-142">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="d6101-142">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d6101-143">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6101-143">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6101-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d6101-144">See also</span></span>

- [<span data-ttu-id="d6101-145">Interface ICLRRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="d6101-145">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="d6101-146">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="d6101-146">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="d6101-147">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="d6101-147">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
