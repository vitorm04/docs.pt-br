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
ms.openlocfilehash: 312db617f185467eda7a9ffa0e8db919e2e94566
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54702633"
---
# <a name="iclrmetahostenumerateinstalledruntimes-method"></a><span data-ttu-id="a6c23-102">Método ICLRMetaHost::EnumerateInstalledRuntimes</span><span class="sxs-lookup"><span data-stu-id="a6c23-102">ICLRMetaHost::EnumerateInstalledRuntimes Method</span></span>
<span data-ttu-id="a6c23-103">Retorna uma enumeração que contém um válido [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface para cada versão do common language runtime (CLR) que é instalado em um computador.</span><span class="sxs-lookup"><span data-stu-id="a6c23-103">Returns an enumeration that contains a valid [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface for each version of the common language runtime (CLR) that is installed on a computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6c23-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a6c23-104">Syntax</span></span>  
  
```  
HRESULT EnumerateInstalledRuntimes (  
    [out, retval] IEnumUnknown **ppEnumerator);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a6c23-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a6c23-105">Parameters</span></span>  
 `ppEnumerator`  
 <span data-ttu-id="a6c23-106">[out] Uma enumeração de [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfaces correspondente a cada versão do CLR que está instalado no computador.</span><span class="sxs-lookup"><span data-stu-id="a6c23-106">[out] An enumeration of [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfaces corresponding to each version of the CLR that is installed on the computer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a6c23-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="a6c23-107">Return Value</span></span>  
 <span data-ttu-id="a6c23-108">Esse método retorna os HRESULTs específicos a seguir, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="a6c23-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="a6c23-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a6c23-109">HRESULT</span></span>|<span data-ttu-id="a6c23-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="a6c23-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a6c23-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="a6c23-111">S_OK</span></span>|<span data-ttu-id="a6c23-112">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="a6c23-112">The method completed successfully.</span></span>|  
|<span data-ttu-id="a6c23-113">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="a6c23-113">E_POINTER</span></span>|<span data-ttu-id="a6c23-114">`ppEnumerator` é nulo.</span><span class="sxs-lookup"><span data-stu-id="a6c23-114">`ppEnumerator` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a6c23-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a6c23-115">Requirements</span></span>  
 <span data-ttu-id="a6c23-116">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a6c23-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6c23-117">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="a6c23-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="a6c23-118">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="a6c23-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a6c23-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6c23-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6c23-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a6c23-120">See also</span></span>
- [<span data-ttu-id="a6c23-121">Interface ICLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="a6c23-121">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [<span data-ttu-id="a6c23-122">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="a6c23-122">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
