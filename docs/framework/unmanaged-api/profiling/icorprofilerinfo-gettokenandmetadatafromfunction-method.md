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
ms.openlocfilehash: b608b8818890bdb27a956a90c7987cf7c421304d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67772277"
---
# <a name="icorprofilerinfogettokenandmetadatafromfunction-method"></a><span data-ttu-id="deab6-102">Método ICorProfilerInfo::GetTokenAndMetadataFromFunction</span><span class="sxs-lookup"><span data-stu-id="deab6-102">ICorProfilerInfo::GetTokenAndMetadataFromFunction Method</span></span>
<span data-ttu-id="deab6-103">Obtém o token de metadados e uma instância de interface de metadados que pode ser usada com o token para a função especificada.</span><span class="sxs-lookup"><span data-stu-id="deab6-103">Gets the metadata token and a metadata interface instance that can be used against the token for the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="deab6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="deab6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTokenAndMetaDataFromFunction(  
    [in]  FunctionID functionId,  
    [in]  REFIID     riid,  
    [out] IUnknown   **ppImport,  
    [out] mdToken    *pToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="deab6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="deab6-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="deab6-106">[in] A ID da função para o qual obter o token de metadados e a interface de metadados.</span><span class="sxs-lookup"><span data-stu-id="deab6-106">[in] The ID of the function for which to get the metadata token and metadata interface.</span></span>  
  
 `riid`  
 <span data-ttu-id="deab6-107">[in] A ID de referência da interface de metadados para obter a instância do.</span><span class="sxs-lookup"><span data-stu-id="deab6-107">[in] The reference ID of the metadata interface to get the instance of.</span></span>  
  
 `ppImport`  
 <span data-ttu-id="deab6-108">[out] Um ponteiro para o endereço da instância de interface de metadados que pode ser usado com o token para a função especificada.</span><span class="sxs-lookup"><span data-stu-id="deab6-108">[out] A pointer to the address of the metadata interface instance that can be used against the token for the specified function.</span></span>  
  
 `pToken`  
 <span data-ttu-id="deab6-109">[out] Um ponteiro para o token de metadados para a função especificada.</span><span class="sxs-lookup"><span data-stu-id="deab6-109">[out] A pointer to the metadata token for the specified function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="deab6-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="deab6-110">Requirements</span></span>  
 <span data-ttu-id="deab6-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="deab6-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="deab6-112">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="deab6-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="deab6-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="deab6-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="deab6-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="deab6-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="deab6-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="deab6-115">See also</span></span>

- [<span data-ttu-id="deab6-116">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="deab6-116">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
