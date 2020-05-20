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
ms.openlocfilehash: c99607bfe5fda01eb1abfd7771cb3907ddabeec5
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703780"
---
# <a name="iclrmetahostenumerateinstalledruntimes-method"></a><span data-ttu-id="9bc20-102">Método ICLRMetaHost::EnumerateInstalledRuntimes</span><span class="sxs-lookup"><span data-stu-id="9bc20-102">ICLRMetaHost::EnumerateInstalledRuntimes Method</span></span>
<span data-ttu-id="9bc20-103">Retorna uma enumeração que contém uma interface [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) válida para cada versão do Common Language Runtime (CLR) que está instalado em um computador.</span><span class="sxs-lookup"><span data-stu-id="9bc20-103">Returns an enumeration that contains a valid [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface for each version of the common language runtime (CLR) that is installed on a computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9bc20-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9bc20-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateInstalledRuntimes (  
    [out, retval] IEnumUnknown **ppEnumerator);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9bc20-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9bc20-105">Parameters</span></span>  
 `ppEnumerator`  
 <span data-ttu-id="9bc20-106">fora Uma enumeração de interfaces [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) correspondentes a cada versão do CLR instalada no computador.</span><span class="sxs-lookup"><span data-stu-id="9bc20-106">[out] An enumeration of [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interfaces corresponding to each version of the CLR that is installed on the computer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9bc20-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="9bc20-107">Return Value</span></span>  
 <span data-ttu-id="9bc20-108">Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.</span><span class="sxs-lookup"><span data-stu-id="9bc20-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="9bc20-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9bc20-109">HRESULT</span></span>|<span data-ttu-id="9bc20-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="9bc20-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9bc20-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="9bc20-111">S_OK</span></span>|<span data-ttu-id="9bc20-112">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="9bc20-112">The method completed successfully.</span></span>|  
|<span data-ttu-id="9bc20-113">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="9bc20-113">E_POINTER</span></span>|<span data-ttu-id="9bc20-114">`ppEnumerator` é nulo.</span><span class="sxs-lookup"><span data-stu-id="9bc20-114">`ppEnumerator` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9bc20-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9bc20-115">Requirements</span></span>  
 <span data-ttu-id="9bc20-116">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9bc20-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9bc20-117">**Cabeçalho:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="9bc20-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="9bc20-118">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9bc20-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9bc20-119">**.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9bc20-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bc20-120">Veja também</span><span class="sxs-lookup"><span data-stu-id="9bc20-120">See also</span></span>

- [<span data-ttu-id="9bc20-121">Interface ICLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="9bc20-121">ICLRMetaHost Interface</span></span>](iclrmetahost-interface.md)
- [<span data-ttu-id="9bc20-122">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="9bc20-122">Hosting</span></span>](index.md)
