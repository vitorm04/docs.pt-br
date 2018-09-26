---
title: Método ICLRMetaHost::EnumerateLoadedRuntimes
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.EnumerateLoadedRuntimes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::EnumerateLoadedRuntimes
helpviewer_keywords:
- EnumerateLoadedRuntimes method [.NET Framework hosting]
- ICLRMetaHost::EnumerateLoadedRuntimes method [.NET Framework hosting]
ms.assetid: 22fc0a3f-dce4-4766-9a3c-9fab15f4b4ca
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: db10b5c67a098cc34292a2680bd832f9cef2861b
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47204990"
---
# <a name="iclrmetahostenumerateloadedruntimes-method"></a><span data-ttu-id="fd885-102">Método ICLRMetaHost::EnumerateLoadedRuntimes</span><span class="sxs-lookup"><span data-stu-id="fd885-102">ICLRMetaHost::EnumerateLoadedRuntimes Method</span></span>
<span data-ttu-id="fd885-103">Retorna uma enumeração que inclui um válido [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) ponteiro de interface para cada versão do common language runtime (CLR) que é carregado em um determinado processo.</span><span class="sxs-lookup"><span data-stu-id="fd885-103">Returns an enumeration that includes a valid [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface pointer for each version of the common language runtime (CLR) that is loaded in a given process.</span></span> <span data-ttu-id="fd885-104">Esse método substitui o [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) função.</span><span class="sxs-lookup"><span data-stu-id="fd885-104">This method supersedes the [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd885-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fd885-105">Syntax</span></span>  
  
```  
HRESULT EnumerateLoadedRuntimes (  
    [in] HANDLE hndProcess,  
    [out, retval] IEnumUnknown **ppEnumerator  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fd885-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="fd885-106">Parameters</span></span>  
 `hndProcess`  
 <span data-ttu-id="fd885-107">[in] O identificador do processo a ser inspecionado para tempos de execução carregados.</span><span class="sxs-lookup"><span data-stu-id="fd885-107">[in] The handle of the process to inspect for loaded runtimes.</span></span>  
  
 `ppEnumerator`  
 <span data-ttu-id="fd885-108">[out] Uma <xref:Microsoft.VisualStudio.OLE.Interop.IEnumUnknown> enumeração dos [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfaces correspondente a cada CLR que é carregado pelo processo.</span><span class="sxs-lookup"><span data-stu-id="fd885-108">[out] An <xref:Microsoft.VisualStudio.OLE.Interop.IEnumUnknown> enumeration of [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfaces corresponding to each CLR that is loaded by the process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fd885-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="fd885-109">Return Value</span></span>  
 <span data-ttu-id="fd885-110">Esse método retorna os HRESULTs específicos a seguir, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="fd885-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="fd885-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fd885-111">HRESULT</span></span>|<span data-ttu-id="fd885-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="fd885-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fd885-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="fd885-113">S_OK</span></span>|<span data-ttu-id="fd885-114">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="fd885-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="fd885-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="fd885-115">E_POINTER</span></span>|<span data-ttu-id="fd885-116">`ppEnumerator` é nulo.</span><span class="sxs-lookup"><span data-stu-id="fd885-116">`ppEnumerator` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fd885-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="fd885-117">Remarks</span></span>  
 <span data-ttu-id="fd885-118">Esse método é carregado lista todos os tempos de execução, mesmo que eles tenham sido carregados, como com funções preteridas [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md).</span><span class="sxs-lookup"><span data-stu-id="fd885-118">This method is lists all loaded runtimes, even if they were loaded with deprecated functions such as [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd885-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fd885-119">Requirements</span></span>  
 <span data-ttu-id="fd885-120">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fd885-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd885-121">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="fd885-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="fd885-122">**Biblioteca:** incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="fd885-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fd885-123">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd885-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd885-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fd885-124">See Also</span></span>  
 [<span data-ttu-id="fd885-125">Interface ICLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="fd885-125">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 [<span data-ttu-id="fd885-126">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="fd885-126">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
