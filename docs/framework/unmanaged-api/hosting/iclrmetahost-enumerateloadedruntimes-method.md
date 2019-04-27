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
ms.openlocfilehash: b0e1213128f5728f17225fbf6906d877dc64e86d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61919289"
---
# <a name="iclrmetahostenumerateloadedruntimes-method"></a><span data-ttu-id="444e2-102">Método ICLRMetaHost::EnumerateLoadedRuntimes</span><span class="sxs-lookup"><span data-stu-id="444e2-102">ICLRMetaHost::EnumerateLoadedRuntimes Method</span></span>
<span data-ttu-id="444e2-103">Retorna uma enumeração que inclui um válido [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) ponteiro de interface para cada versão do common language runtime (CLR) que é carregado em um determinado processo.</span><span class="sxs-lookup"><span data-stu-id="444e2-103">Returns an enumeration that includes a valid [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface pointer for each version of the common language runtime (CLR) that is loaded in a given process.</span></span> <span data-ttu-id="444e2-104">Esse método substitui o [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) função.</span><span class="sxs-lookup"><span data-stu-id="444e2-104">This method supersedes the [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="444e2-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="444e2-105">Syntax</span></span>  
  
```  
HRESULT EnumerateLoadedRuntimes (  
    [in] HANDLE hndProcess,  
    [out, retval] IEnumUnknown **ppEnumerator  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="444e2-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="444e2-106">Parameters</span></span>  
 `hndProcess`  
 <span data-ttu-id="444e2-107">[in] O identificador do processo a ser inspecionado para tempos de execução carregados.</span><span class="sxs-lookup"><span data-stu-id="444e2-107">[in] The handle of the process to inspect for loaded runtimes.</span></span>  
  
 `ppEnumerator`  
 <span data-ttu-id="444e2-108">[out] Uma <xref:Microsoft.VisualStudio.OLE.Interop.IEnumUnknown> enumeração dos [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfaces correspondente a cada CLR que é carregado pelo processo.</span><span class="sxs-lookup"><span data-stu-id="444e2-108">[out] An <xref:Microsoft.VisualStudio.OLE.Interop.IEnumUnknown> enumeration of [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfaces corresponding to each CLR that is loaded by the process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="444e2-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="444e2-109">Return Value</span></span>  
 <span data-ttu-id="444e2-110">Esse método retorna os HRESULTs específicos a seguir, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="444e2-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="444e2-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="444e2-111">HRESULT</span></span>|<span data-ttu-id="444e2-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="444e2-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="444e2-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="444e2-113">S_OK</span></span>|<span data-ttu-id="444e2-114">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="444e2-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="444e2-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="444e2-115">E_POINTER</span></span>|<span data-ttu-id="444e2-116">`ppEnumerator` é nulo.</span><span class="sxs-lookup"><span data-stu-id="444e2-116">`ppEnumerator` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="444e2-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="444e2-117">Remarks</span></span>  
 <span data-ttu-id="444e2-118">Esse método é carregado lista todos os tempos de execução, mesmo que eles tenham sido carregados, como com funções preteridas [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md).</span><span class="sxs-lookup"><span data-stu-id="444e2-118">This method is lists all loaded runtimes, even if they were loaded with deprecated functions such as [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="444e2-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="444e2-119">Requirements</span></span>  
 <span data-ttu-id="444e2-120">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="444e2-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="444e2-121">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="444e2-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="444e2-122">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="444e2-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="444e2-123">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="444e2-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="444e2-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="444e2-124">See also</span></span>

- [<span data-ttu-id="444e2-125">Interface ICLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="444e2-125">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [<span data-ttu-id="444e2-126">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="444e2-126">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
