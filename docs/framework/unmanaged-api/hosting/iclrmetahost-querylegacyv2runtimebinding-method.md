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
ms.openlocfilehash: 90474a61b16d65565889bd69ef75616804d8bc60
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140886"
---
# <a name="iclrmetahostquerylegacyv2runtimebinding-method"></a><span data-ttu-id="a8842-102">Método ICLRMetaHost::QueryLegacyV2RuntimeBinding</span><span class="sxs-lookup"><span data-stu-id="a8842-102">ICLRMetaHost::QueryLegacyV2RuntimeBinding Method</span></span>
<span data-ttu-id="a8842-103">Retorna uma interface que representa um tempo de execução ao qual a política de ativação herdada foi associada, por exemplo, usando o atributo `useLegacyV2RuntimeActivationPolicy` na entrada do arquivo de configuração do [elemento de > de inicialização de\<](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) , por meio do uso direto das APIs de ativação herdadas ou chamando o método [ICLRRuntimeInfo:: BindAsLegacyV2Runtime](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-bindaslegacyv2runtime-method.md) .</span><span class="sxs-lookup"><span data-stu-id="a8842-103">Returns an interface that represents a runtime to which legacy activation policy has been bound, for example, by using the `useLegacyV2RuntimeActivationPolicy` attribute on the [\<startup> element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) configuration file entry, by direct use of the legacy activation APIs, or by calling the [ICLRRuntimeInfo::BindAsLegacyV2Runtime](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-bindaslegacyv2runtime-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8842-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a8842-104">Syntax</span></span>  
  
```cpp  
HRESULT QueryLegacyV2RuntimeBinding (  
    [in] REFIID riid,  
    [out, iid_is(riid), retval] LPVOID *ppUnk);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a8842-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a8842-105">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="a8842-106">no Necessário. no momento, o único valor válido para esse parâmetro é `IID_ICLRRuntimeInfo`.</span><span class="sxs-lookup"><span data-stu-id="a8842-106">[in] Required.Currently the only valid value for this parameter is `IID_ICLRRuntimeInfo`.</span></span>  
  
 `ppUnk`  
 <span data-ttu-id="a8842-107">fora Necessário.</span><span class="sxs-lookup"><span data-stu-id="a8842-107">[out] Required.</span></span> <span data-ttu-id="a8842-108">Quando esse método retorna, contém um ponteiro para a interface [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) que representa um tempo de execução que foi associado à política de ativação herdada.</span><span class="sxs-lookup"><span data-stu-id="a8842-108">When this method returns, contains a pointer to the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface that represents a runtime that has been bound to legacy activation policy.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a8842-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="a8842-109">Return Value</span></span>  
 <span data-ttu-id="a8842-110">Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.</span><span class="sxs-lookup"><span data-stu-id="a8842-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="a8842-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a8842-111">HRESULT</span></span>|<span data-ttu-id="a8842-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="a8842-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a8842-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="a8842-113">S_OK</span></span>|<span data-ttu-id="a8842-114">O método foi concluído com êxito e retornou um tempo de execução que foi associado à política de ativação herdada.</span><span class="sxs-lookup"><span data-stu-id="a8842-114">The method completed successfully and returned a runtime that was bound to legacy activation policy.</span></span>|  
|<span data-ttu-id="a8842-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="a8842-115">S_FALSE</span></span>|<span data-ttu-id="a8842-116">O método foi concluído com êxito, mas um tempo de execução herdado ainda não foi associado.</span><span class="sxs-lookup"><span data-stu-id="a8842-116">The method completed successfully, but a legacy runtime has not yet been bound.</span></span>|  
|<span data-ttu-id="a8842-117">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="a8842-117">E_NOINTERFACE</span></span>|<span data-ttu-id="a8842-118">O método encontrou um tempo de execução que foi associado à política de ativação herdada, mas não há suporte para `riid` nesse tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="a8842-118">The method found a runtime that was bound to legacy activation policy, but `riid` is not supported by that runtime.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a8842-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="a8842-119">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8842-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a8842-120">Requirements</span></span>  
 <span data-ttu-id="a8842-121">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a8842-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8842-122">**Cabeçalho:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="a8842-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="a8842-123">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a8842-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a8842-124">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8842-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8842-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a8842-125">See also</span></span>

- [<span data-ttu-id="a8842-126">Interface ICLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="a8842-126">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [<span data-ttu-id="a8842-127">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="a8842-127">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
