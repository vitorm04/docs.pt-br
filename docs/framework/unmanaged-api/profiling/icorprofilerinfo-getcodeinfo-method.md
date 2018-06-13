---
title: Método ICorProfilerInfo::GetCodeInfo
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetCodeInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetCodeInfo
helpviewer_keywords:
- GetCodeInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetCodeInfo method [.NET Framework profiling]
ms.assetid: 90140b0f-a926-4a7e-b6fa-23e05f703cce
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 21dc937bef2bbe197a5dc4af72ff50dff64dbbbd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33454137"
---
# <a name="icorprofilerinfogetcodeinfo-method"></a><span data-ttu-id="0dfa9-102">Método ICorProfilerInfo::GetCodeInfo</span><span class="sxs-lookup"><span data-stu-id="0dfa9-102">ICorProfilerInfo::GetCodeInfo Method</span></span>
<span data-ttu-id="0dfa9-103">Obtém a extensão do código nativo associado com a ID de função especificada.</span><span class="sxs-lookup"><span data-stu-id="0dfa9-103">Gets the extent of native code associated with the specified function ID.</span></span>  
  
 <span data-ttu-id="0dfa9-104">Esse método é obsoleto.</span><span class="sxs-lookup"><span data-stu-id="0dfa9-104">This method is obsolete.</span></span> <span data-ttu-id="0dfa9-105">Use o [ICorProfilerInfo2::GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md) método em vez disso.</span><span class="sxs-lookup"><span data-stu-id="0dfa9-105">Use the [ICorProfilerInfo2::GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0dfa9-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0dfa9-106">Syntax</span></span>  
  
```  
HRESULT GetCodeInfo(  
    [in]  FunctionID functionId,  
    [out] LPCBYTE    *pStart,  
    [out] ULONG      *pcSize);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0dfa9-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0dfa9-107">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="0dfa9-108">[in] A ID da função à qual o código nativo está associado.</span><span class="sxs-lookup"><span data-stu-id="0dfa9-108">[in] The ID of the function with which the native code is associated.</span></span>  
  
 `pStart`  
 <span data-ttu-id="0dfa9-109">[out] Um ponteiro para uma matriz de bytes que compõem o código nativo da função.</span><span class="sxs-lookup"><span data-stu-id="0dfa9-109">[out] A pointer to an array of bytes that compose the native code of the function.</span></span>  
  
 `pcSize`  
 <span data-ttu-id="0dfa9-110">[out] Um ponteiro para um inteiro que especifica o tamanho, em bytes, do código nativo.</span><span class="sxs-lookup"><span data-stu-id="0dfa9-110">[out] A pointer to an integer that specifies the size, in bytes, of the native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0dfa9-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="0dfa9-111">Remarks</span></span>  
 <span data-ttu-id="0dfa9-112">Para otimizar o desempenho, o tempo de execução do .NET Framework versão 2.0 divide o código nativo, pré-compilados de uma função em várias regiões.</span><span class="sxs-lookup"><span data-stu-id="0dfa9-112">To optimize performance, the runtime in the .NET Framework version 2.0 splits the precompiled, native code of a function into multiple regions.</span></span> <span data-ttu-id="0dfa9-113">Consequentemente, o `GetCodeInfo` método está obsoleto no .NET Framework 2.0 porque não é possível lidar com a extensão do código nativo da função.</span><span class="sxs-lookup"><span data-stu-id="0dfa9-113">Consequently, the `GetCodeInfo` method is obsolete in the .NET Framework 2.0 because it is unable to handle the extent of a function's native code.</span></span> <span data-ttu-id="0dfa9-114">Criadores de perfil devem alternar para o mais geral `ICorProfilerInfo2::GetCodeInfo2` método em vez disso.</span><span class="sxs-lookup"><span data-stu-id="0dfa9-114">Profilers should switch to using the more general `ICorProfilerInfo2::GetCodeInfo2` method instead.</span></span>  
  
 <span data-ttu-id="0dfa9-115">Essa função usa buffers alocada pelo chamador.</span><span class="sxs-lookup"><span data-stu-id="0dfa9-115">This function uses caller-allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0dfa9-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0dfa9-116">Requirements</span></span>  
 <span data-ttu-id="0dfa9-117">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0dfa9-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0dfa9-118">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0dfa9-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0dfa9-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0dfa9-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0dfa9-120">**Versões do .NET framework:** 1.0</span><span class="sxs-lookup"><span data-stu-id="0dfa9-120">**.NET Framework Versions:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0dfa9-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0dfa9-121">See Also</span></span>  
 [<span data-ttu-id="0dfa9-122">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="0dfa9-122">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="0dfa9-123">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="0dfa9-123">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="0dfa9-124">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="0dfa9-124">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
