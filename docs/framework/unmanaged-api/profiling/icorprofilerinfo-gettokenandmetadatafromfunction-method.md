---
title: "Método ICorProfilerInfo::GetTokenAndMetadataFromFunction"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetTokenAndMetadataFromFunction
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetTokenAndMetadataFromFunction
helpviewer_keywords:
- ICorProfilerInfo::GetTokenAndMetadataFromFunction method [.NET Framework profiling]
- GetTokenAndMetadataFromFunction method [.NET Framework profiling]
ms.assetid: e525aa16-c923-4b16-833b-36f1f0dd70fc
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 585b28161814045777cf2294f78bafc3229bfae9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfogettokenandmetadatafromfunction-method"></a><span data-ttu-id="c7144-102">Método ICorProfilerInfo::GetTokenAndMetadataFromFunction</span><span class="sxs-lookup"><span data-stu-id="c7144-102">ICorProfilerInfo::GetTokenAndMetadataFromFunction Method</span></span>
<span data-ttu-id="c7144-103">Obtém o token de metadados e uma instância da interface de metadados que pode ser usada em relação ao token para a função especificada.</span><span class="sxs-lookup"><span data-stu-id="c7144-103">Gets the metadata token and a metadata interface instance that can be used against the token for the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7144-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c7144-104">Syntax</span></span>  
  
```  
HRESULT GetTokenAndMetaDataFromFunction(  
    [in]  FunctionID functionId,  
    [in]  REFIID     riid,  
    [out] IUnknown   **ppImport,  
    [out] mdToken    *pToken);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c7144-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c7144-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="c7144-106">[in] A ID da função para a qual obter o token de metadados e a interface de metadados.</span><span class="sxs-lookup"><span data-stu-id="c7144-106">[in] The ID of the function for which to get the metadata token and metadata interface.</span></span>  
  
 `riid`  
 <span data-ttu-id="c7144-107">[in] A ID de referência da interface de metadados para obter a instância do.</span><span class="sxs-lookup"><span data-stu-id="c7144-107">[in] The reference ID of the metadata interface to get the instance of.</span></span>  
  
 `ppImport`  
 <span data-ttu-id="c7144-108">[out] Um ponteiro para o endereço da instância de interface de metadados que pode ser usado em relação ao token para a função especificada.</span><span class="sxs-lookup"><span data-stu-id="c7144-108">[out] A pointer to the address of the metadata interface instance that can be used against the token for the specified function.</span></span>  
  
 `pToken`  
 <span data-ttu-id="c7144-109">[out] Um ponteiro para o token de metadados para a função especificada.</span><span class="sxs-lookup"><span data-stu-id="c7144-109">[out] A pointer to the metadata token for the specified function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7144-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c7144-110">Requirements</span></span>  
 <span data-ttu-id="c7144-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7144-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7144-112">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c7144-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c7144-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c7144-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c7144-114">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7144-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7144-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c7144-115">See Also</span></span>  
 [<span data-ttu-id="c7144-116">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="c7144-116">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
