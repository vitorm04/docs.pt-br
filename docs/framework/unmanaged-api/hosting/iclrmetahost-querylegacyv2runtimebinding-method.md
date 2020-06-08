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
ms.openlocfilehash: b270a6691d4e4ee4a5d0b42f424694eb7993e4e7
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504141"
---
# <a name="iclrmetahostquerylegacyv2runtimebinding-method"></a><span data-ttu-id="c94d8-102">Método ICLRMetaHost::QueryLegacyV2RuntimeBinding</span><span class="sxs-lookup"><span data-stu-id="c94d8-102">ICLRMetaHost::QueryLegacyV2RuntimeBinding Method</span></span>
<span data-ttu-id="c94d8-103">Retorna uma interface que representa um tempo de execução ao qual a política de ativação herdada foi associada, por exemplo, usando o `useLegacyV2RuntimeActivationPolicy` atributo na entrada do arquivo de configuração do [ \<startup> elemento](../../configure-apps/file-schema/startup/startup-element.md) , usando o uso direto das APIs de ativação herdadas ou chamando o método [ICLRRuntimeInfo:: BindAsLegacyV2Runtime](iclrruntimeinfo-bindaslegacyv2runtime-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c94d8-103">Returns an interface that represents a runtime to which legacy activation policy has been bound, for example, by using the `useLegacyV2RuntimeActivationPolicy` attribute on the [\<startup> element](../../configure-apps/file-schema/startup/startup-element.md) configuration file entry, by direct use of the legacy activation APIs, or by calling the [ICLRRuntimeInfo::BindAsLegacyV2Runtime](iclrruntimeinfo-bindaslegacyv2runtime-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c94d8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c94d8-104">Syntax</span></span>  
  
```cpp  
HRESULT QueryLegacyV2RuntimeBinding (  
    [in] REFIID riid,  
    [out, iid_is(riid), retval] LPVOID *ppUnk);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c94d8-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c94d8-105">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="c94d8-106">no Obrigatório. no momento, o único valor válido para esse parâmetro é `IID_ICLRRuntimeInfo` .</span><span class="sxs-lookup"><span data-stu-id="c94d8-106">[in] Required.Currently the only valid value for this parameter is `IID_ICLRRuntimeInfo`.</span></span>  
  
 `ppUnk`  
 <span data-ttu-id="c94d8-107">fora Necessário.</span><span class="sxs-lookup"><span data-stu-id="c94d8-107">[out] Required.</span></span> <span data-ttu-id="c94d8-108">Quando esse método retorna, contém um ponteiro para a interface [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) que representa um tempo de execução que foi associado à política de ativação herdada.</span><span class="sxs-lookup"><span data-stu-id="c94d8-108">When this method returns, contains a pointer to the [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface that represents a runtime that has been bound to legacy activation policy.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c94d8-109">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="c94d8-109">Return Value</span></span>  
 <span data-ttu-id="c94d8-110">Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.</span><span class="sxs-lookup"><span data-stu-id="c94d8-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="c94d8-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c94d8-111">HRESULT</span></span>|<span data-ttu-id="c94d8-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="c94d8-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c94d8-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="c94d8-113">S_OK</span></span>|<span data-ttu-id="c94d8-114">O método foi concluído com êxito e retornou um tempo de execução que foi associado à política de ativação herdada.</span><span class="sxs-lookup"><span data-stu-id="c94d8-114">The method completed successfully and returned a runtime that was bound to legacy activation policy.</span></span>|  
|<span data-ttu-id="c94d8-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="c94d8-115">S_FALSE</span></span>|<span data-ttu-id="c94d8-116">O método foi concluído com êxito, mas um tempo de execução herdado ainda não foi associado.</span><span class="sxs-lookup"><span data-stu-id="c94d8-116">The method completed successfully, but a legacy runtime has not yet been bound.</span></span>|  
|<span data-ttu-id="c94d8-117">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="c94d8-117">E_NOINTERFACE</span></span>|<span data-ttu-id="c94d8-118">O método encontrou um tempo de execução que foi associado à política de ativação herdada, mas `riid` não tem suporte nesse tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="c94d8-118">The method found a runtime that was bound to legacy activation policy, but `riid` is not supported by that runtime.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c94d8-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="c94d8-119">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c94d8-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c94d8-120">Requirements</span></span>  
 <span data-ttu-id="c94d8-121">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c94d8-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c94d8-122">**Cabeçalho:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="c94d8-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="c94d8-123">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c94d8-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c94d8-124">**.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c94d8-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c94d8-125">Confira também</span><span class="sxs-lookup"><span data-stu-id="c94d8-125">See also</span></span>

- [<span data-ttu-id="c94d8-126">Interface ICLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="c94d8-126">ICLRMetaHost Interface</span></span>](iclrmetahost-interface.md)
- [<span data-ttu-id="c94d8-127">Hosting</span><span class="sxs-lookup"><span data-stu-id="c94d8-127">Hosting</span></span>](index.md)
