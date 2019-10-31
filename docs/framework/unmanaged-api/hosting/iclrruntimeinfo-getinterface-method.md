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
ms.openlocfilehash: 295deeec2e8eb42ccaa4d0cfb8b08b32438d047c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120248"
---
# <a name="iclrruntimeinfogetinterface-method"></a><span data-ttu-id="236b9-102">Método ICLRRuntimeInfo::GetInterface</span><span class="sxs-lookup"><span data-stu-id="236b9-102">ICLRRuntimeInfo::GetInterface Method</span></span>
<span data-ttu-id="236b9-103">Carrega o CLR no processo atual e retorna ponteiros de interface de tempo de execução, como [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md), [ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)e [IMetaDataDispenserEx](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md).</span><span class="sxs-lookup"><span data-stu-id="236b9-103">Loads the CLR into the current process and returns runtime interface pointers, such as [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md), [ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md), and [IMetaDataDispenserEx](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md).</span></span>  
  
 <span data-ttu-id="236b9-104">Esse método substitui todas as funções `CorBindTo`\* na seção [funções de Hospedagem de CLR preteridas](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) .</span><span class="sxs-lookup"><span data-stu-id="236b9-104">This method supersedes all the `CorBindTo`\* functions in the [Deprecated CLR Hosting Functions](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="236b9-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="236b9-105">Syntax</span></span>  
  
```cpp  
HRESULT GetInterface(  
[in]  REFCLSID rclsid,  
[in]  REFIID   riid,  
[out, iid_is(riid), retval] LPVOID *ppUnk);  
```  
  
## <a name="parameters"></a><span data-ttu-id="236b9-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="236b9-106">Parameters</span></span>  
 `rclsid`  
 <span data-ttu-id="236b9-107">no A interface CLSID para a coclass.</span><span class="sxs-lookup"><span data-stu-id="236b9-107">[in] The CLSID interface for the coclass.</span></span>  
  
 `riid`  
 <span data-ttu-id="236b9-108">no O IID da interface de `rclsid` solicitada.</span><span class="sxs-lookup"><span data-stu-id="236b9-108">[in] The IID of the requested `rclsid` interface.</span></span>  
  
 `ppUnk`  
 <span data-ttu-id="236b9-109">fora Um ponteiro para a interface consultada.</span><span class="sxs-lookup"><span data-stu-id="236b9-109">[out] A pointer to the queried interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="236b9-110">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="236b9-110">Return Value</span></span>  
 <span data-ttu-id="236b9-111">Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.</span><span class="sxs-lookup"><span data-stu-id="236b9-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="236b9-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="236b9-112">HRESULT</span></span>|<span data-ttu-id="236b9-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="236b9-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="236b9-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="236b9-114">S_OK</span></span>|<span data-ttu-id="236b9-115">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="236b9-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="236b9-116">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="236b9-116">E_POINTER</span></span>|<span data-ttu-id="236b9-117">`ppUnk` é nulo.</span><span class="sxs-lookup"><span data-stu-id="236b9-117">`ppUnk` is null.</span></span>|  
|<span data-ttu-id="236b9-118">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="236b9-118">E_OUTOFMEMORY</span></span>|<span data-ttu-id="236b9-119">Não há memória suficiente disponível para lidar com a solicitação.</span><span class="sxs-lookup"><span data-stu-id="236b9-119">Not enough memory is available to handle the request.</span></span>|  
|<span data-ttu-id="236b9-120">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span><span class="sxs-lookup"><span data-stu-id="236b9-120">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span></span>|<span data-ttu-id="236b9-121">Um tempo de execução diferente já estava associado à política de ativação do CLR versão 2 herdada.</span><span class="sxs-lookup"><span data-stu-id="236b9-121">A different runtime was already bound to the legacy CLR version 2 activation policy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="236b9-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="236b9-122">Remarks</span></span>  
 <span data-ttu-id="236b9-123">Esse método faz com que o CLR seja carregado, mas não inicializado.</span><span class="sxs-lookup"><span data-stu-id="236b9-123">This method causes the CLR to be loaded but not initialized.</span></span>  
  
 <span data-ttu-id="236b9-124">A tabela a seguir mostra as combinações com suporte para `rclsid` e `riid`.</span><span class="sxs-lookup"><span data-stu-id="236b9-124">The following table shows the supported combinations for `rclsid` and `riid`.</span></span>  
  
|`rclsid`|`riid`|  
|--------------|------------|  
|<span data-ttu-id="236b9-125">CLSID_CorMetaDataDispenser</span><span class="sxs-lookup"><span data-stu-id="236b9-125">CLSID_CorMetaDataDispenser</span></span>|<span data-ttu-id="236b9-126">IID_IMetaDataDispenser, IID_IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="236b9-126">IID_IMetaDataDispenser, IID_IMetaDataDispenserEx</span></span>|  
|<span data-ttu-id="236b9-127">CLSID_CorMetaDataDispenserRuntime</span><span class="sxs-lookup"><span data-stu-id="236b9-127">CLSID_CorMetaDataDispenserRuntime</span></span>|<span data-ttu-id="236b9-128">IID_IMetaDataDispenser, IID_IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="236b9-128">IID_IMetaDataDispenser, IID_IMetaDataDispenserEx</span></span>|  
|<span data-ttu-id="236b9-129">CLSID_CorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="236b9-129">CLSID_CorRuntimeHost</span></span>|<span data-ttu-id="236b9-130">IID_ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="236b9-130">IID_ICorRuntimeHost</span></span>|  
|<span data-ttu-id="236b9-131">CLSID_CLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="236b9-131">CLSID_CLRRuntimeHost</span></span>|<span data-ttu-id="236b9-132">IID_ICLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="236b9-132">IID_ICLRRuntimeHost</span></span>|  
|<span data-ttu-id="236b9-133">CLSID_TypeNameFactory</span><span class="sxs-lookup"><span data-stu-id="236b9-133">CLSID_TypeNameFactory</span></span>|<span data-ttu-id="236b9-134">IID_ITypeNameFactory</span><span class="sxs-lookup"><span data-stu-id="236b9-134">IID_ITypeNameFactory</span></span>|  
|<span data-ttu-id="236b9-135">CLSID_CLRDebuggingLegacy</span><span class="sxs-lookup"><span data-stu-id="236b9-135">CLSID_CLRDebuggingLegacy</span></span>|<span data-ttu-id="236b9-136">IID_ICorDebug</span><span class="sxs-lookup"><span data-stu-id="236b9-136">IID_ICorDebug</span></span>|  
|||  
|<span data-ttu-id="236b9-137">CLSID_CLRStrongName</span><span class="sxs-lookup"><span data-stu-id="236b9-137">CLSID_CLRStrongName</span></span>|<span data-ttu-id="236b9-138">IID_ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="236b9-138">IID_ICLRStrongName</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="236b9-139">Requisitos</span><span class="sxs-lookup"><span data-stu-id="236b9-139">Requirements</span></span>  
 <span data-ttu-id="236b9-140">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="236b9-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="236b9-141">**Cabeçalho:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="236b9-141">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="236b9-142">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="236b9-142">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="236b9-143">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="236b9-143">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="236b9-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="236b9-144">See also</span></span>

- [<span data-ttu-id="236b9-145">Interface ICLRRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="236b9-145">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="236b9-146">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="236b9-146">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="236b9-147">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="236b9-147">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
