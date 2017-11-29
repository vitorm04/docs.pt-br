---
title: "Método ICLRMetaHost::EnumerateLoadedRuntimes"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRMetaHost.EnumerateLoadedRuntimes
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRMetaHost::EnumerateLoadedRuntimes
helpviewer_keywords:
- EnumerateLoadedRuntimes method [.NET Framework hosting]
- ICLRMetaHost::EnumerateLoadedRuntimes method [.NET Framework hosting]
ms.assetid: 22fc0a3f-dce4-4766-9a3c-9fab15f4b4ca
topic_type: apiref
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e0724bf44eaf82b39262876ea4a44509b6c7d576
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrmetahostenumerateloadedruntimes-method"></a><span data-ttu-id="382d6-102">Método ICLRMetaHost::EnumerateLoadedRuntimes</span><span class="sxs-lookup"><span data-stu-id="382d6-102">ICLRMetaHost::EnumerateLoadedRuntimes Method</span></span>
<span data-ttu-id="382d6-103">Retorna uma enumeração que inclui uma opção válida [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) ponteiro de interface para cada versão do common language runtime (CLR) que é carregado em um determinado processo.</span><span class="sxs-lookup"><span data-stu-id="382d6-103">Returns an enumeration that includes a valid [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface pointer for each version of the common language runtime (CLR) that is loaded in a given process.</span></span> <span data-ttu-id="382d6-104">Esse método substitui o [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) função.</span><span class="sxs-lookup"><span data-stu-id="382d6-104">This method supersedes the [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="382d6-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="382d6-105">Syntax</span></span>  
  
```  
HRESULT EnumerateLoadedRuntimes (  
    [in] HANDLE hndProcess,  
    [out, retval] IEnumUnknown **ppEnumerator  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="382d6-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="382d6-106">Parameters</span></span>  
 `hndProcess`  
 <span data-ttu-id="382d6-107">[in] O identificador do processo para inspecionar os tempos de execução carregados.</span><span class="sxs-lookup"><span data-stu-id="382d6-107">[in] The handle of the process to inspect for loaded runtimes.</span></span>  
  
 `ppEnumerator`  
 <span data-ttu-id="382d6-108">[out] Um <!--zz <xref:Microsoft.VisualStudio.OLE.Interop.IEnumUnknown>--> `Microsoft.VisualStudio.OLE.Interop.IEnumUnknown` enumeração de [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfaces correspondente a cada CLR que é carregado pelo processo.</span><span class="sxs-lookup"><span data-stu-id="382d6-108">[out] An <!--zz <xref:Microsoft.VisualStudio.OLE.Interop.IEnumUnknown>--> `Microsoft.VisualStudio.OLE.Interop.IEnumUnknown` enumeration of [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfaces corresponding to each CLR that is loaded by the process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="382d6-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="382d6-109">Return Value</span></span>  
 <span data-ttu-id="382d6-110">Este método retorna a seguintes HRESULTs específicos, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="382d6-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="382d6-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="382d6-111">HRESULT</span></span>|<span data-ttu-id="382d6-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="382d6-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="382d6-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="382d6-113">S_OK</span></span>|<span data-ttu-id="382d6-114">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="382d6-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="382d6-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="382d6-115">E_POINTER</span></span>|<span data-ttu-id="382d6-116">`ppEnumerator` é nulo.</span><span class="sxs-lookup"><span data-stu-id="382d6-116">`ppEnumerator` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="382d6-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="382d6-117">Remarks</span></span>  
 <span data-ttu-id="382d6-118">Esse método é carregado lista todos os tempos de execução, mesmo se eles foram carregados com funções preteridas como [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md).</span><span class="sxs-lookup"><span data-stu-id="382d6-118">This method is lists all loaded runtimes, even if they were loaded with deprecated functions such as [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="382d6-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="382d6-119">Requirements</span></span>  
 <span data-ttu-id="382d6-120">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="382d6-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="382d6-121">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="382d6-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="382d6-122">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="382d6-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="382d6-123">**Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="382d6-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="382d6-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="382d6-124">See Also</span></span>  
 [<span data-ttu-id="382d6-125">Interface ICLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="382d6-125">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 [<span data-ttu-id="382d6-126">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="382d6-126">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
