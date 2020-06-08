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
ms.openlocfilehash: 7b09bb9c3abcb23997bfd412c3ea939404e583c1
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504167"
---
# <a name="iclrmetahostenumerateloadedruntimes-method"></a><span data-ttu-id="03404-102">Método ICLRMetaHost::EnumerateLoadedRuntimes</span><span class="sxs-lookup"><span data-stu-id="03404-102">ICLRMetaHost::EnumerateLoadedRuntimes Method</span></span>
<span data-ttu-id="03404-103">Retorna uma enumeração que inclui um ponteiro de interface [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) válido para cada versão do Common Language Runtime (CLR) que é carregado em um determinado processo.</span><span class="sxs-lookup"><span data-stu-id="03404-103">Returns an enumeration that includes a valid [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface pointer for each version of the common language runtime (CLR) that is loaded in a given process.</span></span> <span data-ttu-id="03404-104">Esse método substitui a função [GetVersionFromProcess](getversionfromprocess-function.md) .</span><span class="sxs-lookup"><span data-stu-id="03404-104">This method supersedes the [GetVersionFromProcess](getversionfromprocess-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03404-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="03404-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateLoadedRuntimes (  
    [in] HANDLE hndProcess,  
    [out, retval] IEnumUnknown **ppEnumerator  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="03404-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="03404-106">Parameters</span></span>  
 `hndProcess`  
 <span data-ttu-id="03404-107">no O identificador do processo para inspecionar os tempos de execução carregados.</span><span class="sxs-lookup"><span data-stu-id="03404-107">[in] The handle of the process to inspect for loaded runtimes.</span></span>  
  
 `ppEnumerator`  
 <span data-ttu-id="03404-108">fora Uma <xref:Microsoft.VisualStudio.OLE.Interop.IEnumUnknown> enumeração de interfaces [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) correspondentes a cada CLR que é carregado pelo processo.</span><span class="sxs-lookup"><span data-stu-id="03404-108">[out] An <xref:Microsoft.VisualStudio.OLE.Interop.IEnumUnknown> enumeration of [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interfaces corresponding to each CLR that is loaded by the process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="03404-109">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="03404-109">Return Value</span></span>  
 <span data-ttu-id="03404-110">Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.</span><span class="sxs-lookup"><span data-stu-id="03404-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="03404-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="03404-111">HRESULT</span></span>|<span data-ttu-id="03404-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="03404-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="03404-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="03404-113">S_OK</span></span>|<span data-ttu-id="03404-114">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="03404-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="03404-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="03404-115">E_POINTER</span></span>|<span data-ttu-id="03404-116">`ppEnumerator` é nulo.</span><span class="sxs-lookup"><span data-stu-id="03404-116">`ppEnumerator` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="03404-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="03404-117">Remarks</span></span>  
 <span data-ttu-id="03404-118">Esse método lista todos os tempos de execução carregados, mesmo que eles tenham sido carregados com funções preteridas, como [CorBindToRuntime](corbindtoruntime-function.md).</span><span class="sxs-lookup"><span data-stu-id="03404-118">This method is lists all loaded runtimes, even if they were loaded with deprecated functions such as [CorBindToRuntime](corbindtoruntime-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03404-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="03404-119">Requirements</span></span>  
 <span data-ttu-id="03404-120">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="03404-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03404-121">**Cabeçalho:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="03404-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="03404-122">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="03404-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="03404-123">**.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03404-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03404-124">Confira também</span><span class="sxs-lookup"><span data-stu-id="03404-124">See also</span></span>

- [<span data-ttu-id="03404-125">Interface ICLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="03404-125">ICLRMetaHost Interface</span></span>](iclrmetahost-interface.md)
- [<span data-ttu-id="03404-126">Hosting</span><span class="sxs-lookup"><span data-stu-id="03404-126">Hosting</span></span>](index.md)
