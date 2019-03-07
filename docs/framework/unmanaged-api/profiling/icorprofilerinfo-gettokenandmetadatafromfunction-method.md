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
ms.openlocfilehash: fb81972a7f52889d10a59cd5cd9ea0e8e1e3e571
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57492875"
---
# <a name="icorprofilerinfogettokenandmetadatafromfunction-method"></a><span data-ttu-id="3acbe-102">Método ICorProfilerInfo::GetTokenAndMetadataFromFunction</span><span class="sxs-lookup"><span data-stu-id="3acbe-102">ICorProfilerInfo::GetTokenAndMetadataFromFunction Method</span></span>
<span data-ttu-id="3acbe-103">Obtém o token de metadados e uma instância de interface de metadados que pode ser usada com o token para a função especificada.</span><span class="sxs-lookup"><span data-stu-id="3acbe-103">Gets the metadata token and a metadata interface instance that can be used against the token for the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3acbe-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3acbe-104">Syntax</span></span>  
  
```  
HRESULT GetTokenAndMetaDataFromFunction(  
    [in]  FunctionID functionId,  
    [in]  REFIID     riid,  
    [out] IUnknown   **ppImport,  
    [out] mdToken    *pToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3acbe-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3acbe-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="3acbe-106">[in] A ID da função para o qual obter o token de metadados e a interface de metadados.</span><span class="sxs-lookup"><span data-stu-id="3acbe-106">[in] The ID of the function for which to get the metadata token and metadata interface.</span></span>  
  
 `riid`  
 <span data-ttu-id="3acbe-107">[in] A ID de referência da interface de metadados para obter a instância do.</span><span class="sxs-lookup"><span data-stu-id="3acbe-107">[in] The reference ID of the metadata interface to get the instance of.</span></span>  
  
 `ppImport`  
 <span data-ttu-id="3acbe-108">[out] Um ponteiro para o endereço da instância de interface de metadados que pode ser usado com o token para a função especificada.</span><span class="sxs-lookup"><span data-stu-id="3acbe-108">[out] A pointer to the address of the metadata interface instance that can be used against the token for the specified function.</span></span>  
  
 `pToken`  
 <span data-ttu-id="3acbe-109">[out] Um ponteiro para o token de metadados para a função especificada.</span><span class="sxs-lookup"><span data-stu-id="3acbe-109">[out] A pointer to the metadata token for the specified function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3acbe-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3acbe-110">Requirements</span></span>  
 <span data-ttu-id="3acbe-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3acbe-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3acbe-112">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3acbe-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3acbe-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3acbe-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3acbe-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3acbe-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3acbe-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3acbe-115">See also</span></span>
- [<span data-ttu-id="3acbe-116">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="3acbe-116">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
