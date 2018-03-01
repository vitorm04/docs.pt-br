---
title: "Método ICLRMetaHost::EnumerateInstalledRuntimes"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 41e9b9de120154fe90eb3e73ada2ced4fa3e4544
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrmetahostenumerateinstalledruntimes-method"></a><span data-ttu-id="6f2d1-102">Método ICLRMetaHost::EnumerateInstalledRuntimes</span><span class="sxs-lookup"><span data-stu-id="6f2d1-102">ICLRMetaHost::EnumerateInstalledRuntimes Method</span></span>
<span data-ttu-id="6f2d1-103">Retorna uma enumeração que contém um válido [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface para cada versão do common language runtime (CLR) que é instalado em um computador.</span><span class="sxs-lookup"><span data-stu-id="6f2d1-103">Returns an enumeration that contains a valid [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface for each version of the common language runtime (CLR) that is installed on a computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f2d1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6f2d1-104">Syntax</span></span>  
  
```  
HRESULT EnumerateInstalledRuntimes (  
    [out, retval] IEnumUnknown **ppEnumerator);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6f2d1-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6f2d1-105">Parameters</span></span>  
 `ppEnumerator`  
 <span data-ttu-id="6f2d1-106">[out] Uma enumeração de [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfaces correspondente a cada versão do CLR que está instalado no computador.</span><span class="sxs-lookup"><span data-stu-id="6f2d1-106">[out] An enumeration of [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfaces corresponding to each version of the CLR that is installed on the computer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6f2d1-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="6f2d1-107">Return Value</span></span>  
 <span data-ttu-id="6f2d1-108">Este método retorna a seguintes HRESULTs específicos, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="6f2d1-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="6f2d1-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6f2d1-109">HRESULT</span></span>|<span data-ttu-id="6f2d1-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="6f2d1-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6f2d1-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="6f2d1-111">S_OK</span></span>|<span data-ttu-id="6f2d1-112">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="6f2d1-112">The method completed successfully.</span></span>|  
|<span data-ttu-id="6f2d1-113">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="6f2d1-113">E_POINTER</span></span>|<span data-ttu-id="6f2d1-114">`ppEnumerator` é nulo.</span><span class="sxs-lookup"><span data-stu-id="6f2d1-114">`ppEnumerator` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6f2d1-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6f2d1-115">Requirements</span></span>  
 <span data-ttu-id="6f2d1-116">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6f2d1-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f2d1-117">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="6f2d1-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="6f2d1-118">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="6f2d1-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6f2d1-119">**Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f2d1-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f2d1-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6f2d1-120">See Also</span></span>  
 [<span data-ttu-id="6f2d1-121">Interface ICLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="6f2d1-121">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 [<span data-ttu-id="6f2d1-122">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="6f2d1-122">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
