---
title: Método ICLRMetaHost::EnumerateInstalledRuntimes
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.EnumerateInstalledRuntimes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::EnumerateInstalledRuntimes
helpviewer_keywords:
- ICLRMetaHost::EnumerateInstalledRuntimes method [.NET Framework hosting]
- EnumerateInstalledRuntimes method [.NET Framework hosting]
ms.assetid: 9e359384-0d3d-451c-807e-5d7fcebf2be7
topic_type:
- apiref
ms.openlocfilehash: 9415d5189edb901822abad9269e0150e7601a963
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140960"
---
# <a name="iclrmetahostenumerateinstalledruntimes-method"></a><span data-ttu-id="c0ca5-102">Método ICLRMetaHost::EnumerateInstalledRuntimes</span><span class="sxs-lookup"><span data-stu-id="c0ca5-102">ICLRMetaHost::EnumerateInstalledRuntimes Method</span></span>
<span data-ttu-id="c0ca5-103">Retorna uma enumeração que contém uma interface [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) válida para cada versão do Common Language Runtime (CLR) que está instalado em um computador.</span><span class="sxs-lookup"><span data-stu-id="c0ca5-103">Returns an enumeration that contains a valid [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface for each version of the common language runtime (CLR) that is installed on a computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0ca5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c0ca5-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateInstalledRuntimes (  
    [out, retval] IEnumUnknown **ppEnumerator);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c0ca5-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c0ca5-105">Parameters</span></span>  
 `ppEnumerator`  
 <span data-ttu-id="c0ca5-106">fora Uma enumeração de interfaces [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) correspondentes a cada versão do CLR instalada no computador.</span><span class="sxs-lookup"><span data-stu-id="c0ca5-106">[out] An enumeration of [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfaces corresponding to each version of the CLR that is installed on the computer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c0ca5-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="c0ca5-107">Return Value</span></span>  
 <span data-ttu-id="c0ca5-108">Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.</span><span class="sxs-lookup"><span data-stu-id="c0ca5-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="c0ca5-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c0ca5-109">HRESULT</span></span>|<span data-ttu-id="c0ca5-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="c0ca5-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c0ca5-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="c0ca5-111">S_OK</span></span>|<span data-ttu-id="c0ca5-112">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="c0ca5-112">The method completed successfully.</span></span>|  
|<span data-ttu-id="c0ca5-113">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="c0ca5-113">E_POINTER</span></span>|<span data-ttu-id="c0ca5-114">`ppEnumerator` é nulo.</span><span class="sxs-lookup"><span data-stu-id="c0ca5-114">`ppEnumerator` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c0ca5-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c0ca5-115">Requirements</span></span>  
 <span data-ttu-id="c0ca5-116">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c0ca5-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0ca5-117">**Cabeçalho:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="c0ca5-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="c0ca5-118">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c0ca5-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c0ca5-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0ca5-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0ca5-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c0ca5-120">See also</span></span>

- [<span data-ttu-id="c0ca5-121">Interface ICLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="c0ca5-121">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [<span data-ttu-id="c0ca5-122">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="c0ca5-122">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
