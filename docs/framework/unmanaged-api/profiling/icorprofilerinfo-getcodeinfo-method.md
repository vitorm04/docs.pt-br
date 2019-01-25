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
ms.openlocfilehash: 5004de587f715a2f3958c36999e432d7d6e9f2fd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54632654"
---
# <a name="icorprofilerinfogetcodeinfo-method"></a><span data-ttu-id="5d44b-102">Método ICorProfilerInfo::GetCodeInfo</span><span class="sxs-lookup"><span data-stu-id="5d44b-102">ICorProfilerInfo::GetCodeInfo Method</span></span>
<span data-ttu-id="5d44b-103">Obtém a extensão do código nativo associado com a ID da função especificada.</span><span class="sxs-lookup"><span data-stu-id="5d44b-103">Gets the extent of native code associated with the specified function ID.</span></span>  
  
 <span data-ttu-id="5d44b-104">Esse método é obsoleto.</span><span class="sxs-lookup"><span data-stu-id="5d44b-104">This method is obsolete.</span></span> <span data-ttu-id="5d44b-105">Use o [ICorProfilerInfo2::GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md) método em vez disso.</span><span class="sxs-lookup"><span data-stu-id="5d44b-105">Use the [ICorProfilerInfo2::GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d44b-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5d44b-106">Syntax</span></span>  
  
```  
HRESULT GetCodeInfo(  
    [in]  FunctionID functionId,  
    [out] LPCBYTE    *pStart,  
    [out] ULONG      *pcSize);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5d44b-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5d44b-107">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="5d44b-108">[in] A ID da função à qual o código nativo está associado.</span><span class="sxs-lookup"><span data-stu-id="5d44b-108">[in] The ID of the function with which the native code is associated.</span></span>  
  
 `pStart`  
 <span data-ttu-id="5d44b-109">[out] Um ponteiro para uma matriz de bytes que compõem o código nativo da função.</span><span class="sxs-lookup"><span data-stu-id="5d44b-109">[out] A pointer to an array of bytes that compose the native code of the function.</span></span>  
  
 `pcSize`  
 <span data-ttu-id="5d44b-110">[out] Um ponteiro para um inteiro que especifica o tamanho, em bytes, do código nativo.</span><span class="sxs-lookup"><span data-stu-id="5d44b-110">[out] A pointer to an integer that specifies the size, in bytes, of the native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5d44b-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="5d44b-111">Remarks</span></span>  
 <span data-ttu-id="5d44b-112">Para otimizar o desempenho, o tempo de execução no .NET Framework versão 2.0 divide o código nativo pré-compilado de uma função em várias regiões.</span><span class="sxs-lookup"><span data-stu-id="5d44b-112">To optimize performance, the runtime in the .NET Framework version 2.0 splits the precompiled, native code of a function into multiple regions.</span></span> <span data-ttu-id="5d44b-113">Consequentemente, o `GetCodeInfo` método está obsoleto no .NET Framework 2.0, porque não é possível lidar com a extensão do código nativo da função.</span><span class="sxs-lookup"><span data-stu-id="5d44b-113">Consequently, the `GetCodeInfo` method is obsolete in the .NET Framework 2.0 because it is unable to handle the extent of a function's native code.</span></span> <span data-ttu-id="5d44b-114">Os criadores de perfis devem passar a usar o mais geral `ICorProfilerInfo2::GetCodeInfo2` método em vez disso.</span><span class="sxs-lookup"><span data-stu-id="5d44b-114">Profilers should switch to using the more general `ICorProfilerInfo2::GetCodeInfo2` method instead.</span></span>  
  
 <span data-ttu-id="5d44b-115">Essa função usa buffers alocados pelo chamador.</span><span class="sxs-lookup"><span data-stu-id="5d44b-115">This function uses caller-allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d44b-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5d44b-116">Requirements</span></span>  
 <span data-ttu-id="5d44b-117">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5d44b-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d44b-118">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5d44b-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5d44b-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5d44b-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5d44b-120">**Versões do .NET framework:** 1.0</span><span class="sxs-lookup"><span data-stu-id="5d44b-120">**.NET Framework Versions:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d44b-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5d44b-121">See also</span></span>
- [<span data-ttu-id="5d44b-122">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="5d44b-122">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="5d44b-123">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="5d44b-123">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="5d44b-124">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="5d44b-124">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
