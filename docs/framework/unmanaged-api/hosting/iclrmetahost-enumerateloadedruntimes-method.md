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
ms.openlocfilehash: f89307ad7ed41f872ad66a99be03663ac1f30f13
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140976"
---
# <a name="iclrmetahostenumerateloadedruntimes-method"></a><span data-ttu-id="beb67-102">Método ICLRMetaHost::EnumerateLoadedRuntimes</span><span class="sxs-lookup"><span data-stu-id="beb67-102">ICLRMetaHost::EnumerateLoadedRuntimes Method</span></span>
<span data-ttu-id="beb67-103">Retorna uma enumeração que inclui um ponteiro de interface [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) válido para cada versão do Common Language Runtime (CLR) que é carregado em um determinado processo.</span><span class="sxs-lookup"><span data-stu-id="beb67-103">Returns an enumeration that includes a valid [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface pointer for each version of the common language runtime (CLR) that is loaded in a given process.</span></span> <span data-ttu-id="beb67-104">Esse método substitui a função [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) .</span><span class="sxs-lookup"><span data-stu-id="beb67-104">This method supersedes the [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="beb67-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="beb67-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateLoadedRuntimes (  
    [in] HANDLE hndProcess,  
    [out, retval] IEnumUnknown **ppEnumerator  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="beb67-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="beb67-106">Parameters</span></span>  
 `hndProcess`  
 <span data-ttu-id="beb67-107">no O identificador do processo para inspecionar os tempos de execução carregados.</span><span class="sxs-lookup"><span data-stu-id="beb67-107">[in] The handle of the process to inspect for loaded runtimes.</span></span>  
  
 `ppEnumerator`  
 <span data-ttu-id="beb67-108">fora Uma <xref:Microsoft.VisualStudio.OLE.Interop.IEnumUnknown> enumeração de interfaces [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) correspondentes a cada CLR que é carregado pelo processo.</span><span class="sxs-lookup"><span data-stu-id="beb67-108">[out] An <xref:Microsoft.VisualStudio.OLE.Interop.IEnumUnknown> enumeration of [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfaces corresponding to each CLR that is loaded by the process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="beb67-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="beb67-109">Return Value</span></span>  
 <span data-ttu-id="beb67-110">Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.</span><span class="sxs-lookup"><span data-stu-id="beb67-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="beb67-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="beb67-111">HRESULT</span></span>|<span data-ttu-id="beb67-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="beb67-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="beb67-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="beb67-113">S_OK</span></span>|<span data-ttu-id="beb67-114">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="beb67-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="beb67-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="beb67-115">E_POINTER</span></span>|<span data-ttu-id="beb67-116">`ppEnumerator` é nulo.</span><span class="sxs-lookup"><span data-stu-id="beb67-116">`ppEnumerator` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="beb67-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="beb67-117">Remarks</span></span>  
 <span data-ttu-id="beb67-118">Esse método lista todos os tempos de execução carregados, mesmo que eles tenham sido carregados com funções preteridas, como [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md).</span><span class="sxs-lookup"><span data-stu-id="beb67-118">This method is lists all loaded runtimes, even if they were loaded with deprecated functions such as [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="beb67-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="beb67-119">Requirements</span></span>  
 <span data-ttu-id="beb67-120">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="beb67-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="beb67-121">**Cabeçalho:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="beb67-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="beb67-122">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="beb67-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="beb67-123">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="beb67-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="beb67-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="beb67-124">See also</span></span>

- [<span data-ttu-id="beb67-125">Interface ICLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="beb67-125">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [<span data-ttu-id="beb67-126">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="beb67-126">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
