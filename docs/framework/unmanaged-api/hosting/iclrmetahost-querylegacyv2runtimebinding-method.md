---
title: Método ICLRMetaHost::QueryLegacyV2RuntimeBinding
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.RequestRuntimeLoadedNotification
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::QueryLegacyV2RuntimeBinding
helpviewer_keywords:
- QueryLegacyV2RuntimeBinding method [.NET Framework hosting]
- ICLRMetaHost::QueryLegacyV2RuntimeBinding method [.NET Framework hosting]
ms.assetid: 9929817e-acc9-40b7-960c-598664e04b60
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0252f27f30c3ce8abe349a2ddc45b20692fbb5ea
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61993181"
---
# <a name="iclrmetahostquerylegacyv2runtimebinding-method"></a><span data-ttu-id="b39e2-102">Método ICLRMetaHost::QueryLegacyV2RuntimeBinding</span><span class="sxs-lookup"><span data-stu-id="b39e2-102">ICLRMetaHost::QueryLegacyV2RuntimeBinding Method</span></span>
<span data-ttu-id="b39e2-103">Retorna uma interface que representa um tempo de execução para o qual política de ativação herdados foi associada, por exemplo, usando o `useLegacyV2RuntimeActivationPolicy` atributo o [ \<inicialização > elemento](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) entrada do arquivo de configuração, pelo uso direto de APIs de ativação herdadas, ou chamando o [ICLRRuntimeInfo::BindAsLegacyV2Runtime](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-bindaslegacyv2runtime-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="b39e2-103">Returns an interface that represents a runtime to which legacy activation policy has been bound, for example, by using the `useLegacyV2RuntimeActivationPolicy` attribute on the [\<startup> element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) configuration file entry, by direct use of the legacy activation APIs, or by calling the [ICLRRuntimeInfo::BindAsLegacyV2Runtime](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-bindaslegacyv2runtime-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b39e2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b39e2-104">Syntax</span></span>  
  
```  
HRESULT QueryLegacyV2RuntimeBinding (  
    [in] REFIID riid,  
    [out, iid_is(riid), retval] LPVOID *ppUnk);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b39e2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b39e2-105">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="b39e2-106">[in] Required.Currently é o único valor válido para esse parâmetro `IID_ICLRRuntimeInfo`.</span><span class="sxs-lookup"><span data-stu-id="b39e2-106">[in] Required.Currently the only valid value for this parameter is `IID_ICLRRuntimeInfo`.</span></span>  
  
 `ppUnk`  
 <span data-ttu-id="b39e2-107">[out] Necessário.</span><span class="sxs-lookup"><span data-stu-id="b39e2-107">[out] Required.</span></span> <span data-ttu-id="b39e2-108">Quando este método retorna, contém um ponteiro para o [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface que representa um tempo de execução que foi associado à política de ativação herdados.</span><span class="sxs-lookup"><span data-stu-id="b39e2-108">When this method returns, contains a pointer to the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface that represents a runtime that has been bound to legacy activation policy.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b39e2-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="b39e2-109">Return Value</span></span>  
 <span data-ttu-id="b39e2-110">Esse método retorna os HRESULTs específicos a seguir, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="b39e2-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="b39e2-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b39e2-111">HRESULT</span></span>|<span data-ttu-id="b39e2-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="b39e2-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b39e2-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="b39e2-113">S_OK</span></span>|<span data-ttu-id="b39e2-114">O método foi concluída com êxito e retornou um tempo de execução que foi associado à política de ativação herdados.</span><span class="sxs-lookup"><span data-stu-id="b39e2-114">The method completed successfully and returned a runtime that was bound to legacy activation policy.</span></span>|  
|<span data-ttu-id="b39e2-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="b39e2-115">S_FALSE</span></span>|<span data-ttu-id="b39e2-116">O método foi concluída com êxito, mas um tempo de execução herdado não ainda foi associado.</span><span class="sxs-lookup"><span data-stu-id="b39e2-116">The method completed successfully, but a legacy runtime has not yet been bound.</span></span>|  
|<span data-ttu-id="b39e2-117">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="b39e2-117">E_NOINTERFACE</span></span>|<span data-ttu-id="b39e2-118">O método encontrado um tempo de execução que estava associado à política de ativação herdados, mas `riid` não é compatível com esse tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="b39e2-118">The method found a runtime that was bound to legacy activation policy, but `riid` is not supported by that runtime.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b39e2-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="b39e2-119">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b39e2-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b39e2-120">Requirements</span></span>  
 <span data-ttu-id="b39e2-121">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b39e2-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b39e2-122">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="b39e2-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="b39e2-123">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="b39e2-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b39e2-124">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b39e2-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b39e2-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b39e2-125">See also</span></span>

- [<span data-ttu-id="b39e2-126">Interface ICLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="b39e2-126">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [<span data-ttu-id="b39e2-127">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="b39e2-127">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
