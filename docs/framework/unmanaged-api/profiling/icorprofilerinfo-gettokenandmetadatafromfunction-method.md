---
title: Método ICorProfilerInfo::GetTokenAndMetadataFromFunction
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetTokenAndMetadataFromFunction
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetTokenAndMetadataFromFunction
helpviewer_keywords:
- ICorProfilerInfo::GetTokenAndMetadataFromFunction method [.NET Framework profiling]
- GetTokenAndMetadataFromFunction method [.NET Framework profiling]
ms.assetid: e525aa16-c923-4b16-833b-36f1f0dd70fc
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9bcf8919037d5b79f3819fffec02708886064b40
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33453197"
---
# <a name="icorprofilerinfogettokenandmetadatafromfunction-method"></a><span data-ttu-id="a4f73-102">Método ICorProfilerInfo::GetTokenAndMetadataFromFunction</span><span class="sxs-lookup"><span data-stu-id="a4f73-102">ICorProfilerInfo::GetTokenAndMetadataFromFunction Method</span></span>
<span data-ttu-id="a4f73-103">Obtém o token de metadados e uma instância da interface de metadados que pode ser usada em relação ao token para a função especificada.</span><span class="sxs-lookup"><span data-stu-id="a4f73-103">Gets the metadata token and a metadata interface instance that can be used against the token for the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4f73-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a4f73-104">Syntax</span></span>  
  
```  
HRESULT GetTokenAndMetaDataFromFunction(  
    [in]  FunctionID functionId,  
    [in]  REFIID     riid,  
    [out] IUnknown   **ppImport,  
    [out] mdToken    *pToken);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a4f73-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a4f73-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="a4f73-106">[in] A ID da função para a qual obter o token de metadados e a interface de metadados.</span><span class="sxs-lookup"><span data-stu-id="a4f73-106">[in] The ID of the function for which to get the metadata token and metadata interface.</span></span>  
  
 `riid`  
 <span data-ttu-id="a4f73-107">[in] A ID de referência da interface de metadados para obter a instância do.</span><span class="sxs-lookup"><span data-stu-id="a4f73-107">[in] The reference ID of the metadata interface to get the instance of.</span></span>  
  
 `ppImport`  
 <span data-ttu-id="a4f73-108">[out] Um ponteiro para o endereço da instância de interface de metadados que pode ser usado em relação ao token para a função especificada.</span><span class="sxs-lookup"><span data-stu-id="a4f73-108">[out] A pointer to the address of the metadata interface instance that can be used against the token for the specified function.</span></span>  
  
 `pToken`  
 <span data-ttu-id="a4f73-109">[out] Um ponteiro para o token de metadados para a função especificada.</span><span class="sxs-lookup"><span data-stu-id="a4f73-109">[out] A pointer to the metadata token for the specified function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4f73-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a4f73-110">Requirements</span></span>  
 <span data-ttu-id="a4f73-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a4f73-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4f73-112">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a4f73-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a4f73-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a4f73-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a4f73-114">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a4f73-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4f73-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a4f73-115">See Also</span></span>  
 [<span data-ttu-id="a4f73-116">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="a4f73-116">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
