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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2b116a1f422daa20a2b51f0a5fc12d6065c2a01e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779810"
---
# <a name="iclrmetahostenumerateinstalledruntimes-method"></a><span data-ttu-id="c8c0e-102">Método ICLRMetaHost::EnumerateInstalledRuntimes</span><span class="sxs-lookup"><span data-stu-id="c8c0e-102">ICLRMetaHost::EnumerateInstalledRuntimes Method</span></span>
<span data-ttu-id="c8c0e-103">Retorna uma enumeração que contém um válido [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface para cada versão do common language runtime (CLR) que é instalado em um computador.</span><span class="sxs-lookup"><span data-stu-id="c8c0e-103">Returns an enumeration that contains a valid [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface for each version of the common language runtime (CLR) that is installed on a computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8c0e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c8c0e-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateInstalledRuntimes (  
    [out, retval] IEnumUnknown **ppEnumerator);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c8c0e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c8c0e-105">Parameters</span></span>  
 `ppEnumerator`  
 <span data-ttu-id="c8c0e-106">[out] Uma enumeração de [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfaces correspondente a cada versão do CLR que está instalado no computador.</span><span class="sxs-lookup"><span data-stu-id="c8c0e-106">[out] An enumeration of [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfaces corresponding to each version of the CLR that is installed on the computer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c8c0e-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="c8c0e-107">Return Value</span></span>  
 <span data-ttu-id="c8c0e-108">Esse método retorna os HRESULTs específicos a seguir, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="c8c0e-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="c8c0e-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c8c0e-109">HRESULT</span></span>|<span data-ttu-id="c8c0e-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="c8c0e-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c8c0e-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="c8c0e-111">S_OK</span></span>|<span data-ttu-id="c8c0e-112">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="c8c0e-112">The method completed successfully.</span></span>|  
|<span data-ttu-id="c8c0e-113">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="c8c0e-113">E_POINTER</span></span>|<span data-ttu-id="c8c0e-114">`ppEnumerator` é nulo.</span><span class="sxs-lookup"><span data-stu-id="c8c0e-114">`ppEnumerator` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c8c0e-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c8c0e-115">Requirements</span></span>  
 <span data-ttu-id="c8c0e-116">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c8c0e-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8c0e-117">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="c8c0e-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="c8c0e-118">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="c8c0e-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c8c0e-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8c0e-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8c0e-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c8c0e-120">See also</span></span>

- [<span data-ttu-id="c8c0e-121">Interface ICLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="c8c0e-121">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [<span data-ttu-id="c8c0e-122">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="c8c0e-122">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
