---
title: Método ICorProfilerInfo4::GetCodeInfo3
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetCodeInfo3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetCodeInfo3
helpviewer_keywords:
- GetCodeInfo3 method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::GetCodeInfo3 method [.NET Framework profiling]
ms.assetid: bb8c105e-4d9a-4684-8c05-ed6909cc1b8c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cb067d16ef7f8177f979a083707f8c6ef36750c0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59145802"
---
# <a name="icorprofilerinfo4getcodeinfo3-method"></a><span data-ttu-id="ecb7a-102">Método ICorProfilerInfo4::GetCodeInfo3</span><span class="sxs-lookup"><span data-stu-id="ecb7a-102">ICorProfilerInfo4::GetCodeInfo3 Method</span></span>
<span data-ttu-id="ecb7a-103">Obtém as extensões de código nativo associado com a versão recompilado por JIT da função especificada.</span><span class="sxs-lookup"><span data-stu-id="ecb7a-103">Gets the extents of native code associated with the JIT-recompiled version of the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ecb7a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ecb7a-104">Syntax</span></span>  
  
```  
HRESULT GetCodeInfo3(  
    [in]  FunctionID functionID,  
    [in]  ReJITID reJitId,  
    [in]  ULONG32 cCodeInfos,  
    [out] ULONG32 *pcCodeInfos,  
    [out, size_is(cCodeInfos), length_is(*pcCodeInfos)]  
    COR_PRF_CODE_INFO codeInfos[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ecb7a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ecb7a-105">Parameters</span></span>  
 `functionID`  
 <span data-ttu-id="ecb7a-106">[in] A ID da função à qual o código nativo está associado.</span><span class="sxs-lookup"><span data-stu-id="ecb7a-106">[in] The ID of the function with which the native code is associated.</span></span>  
  
 `reJitId`  
 <span data-ttu-id="ecb7a-107">[in] A identidade da função recompilado por JIT.</span><span class="sxs-lookup"><span data-stu-id="ecb7a-107">[in] The identity of the JIT-recompiled function.</span></span>  
  
 `cCodeInfos`  
 <span data-ttu-id="ecb7a-108">[in] O tamanho do `codeInfos` matriz.</span><span class="sxs-lookup"><span data-stu-id="ecb7a-108">[in] The size of the `codeInfos` array.</span></span>  
  
 `pcCodeInfos`  
 <span data-ttu-id="ecb7a-109">[out] Um ponteiro para o número total de [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) estruturas disponíveis.</span><span class="sxs-lookup"><span data-stu-id="ecb7a-109">[out] A pointer to the total number of [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structures available.</span></span>  
  
 `codeInfos`  
 <span data-ttu-id="ecb7a-110">[out] Um buffer fornecido pelo chamador.</span><span class="sxs-lookup"><span data-stu-id="ecb7a-110">[out] A caller-provided buffer.</span></span> <span data-ttu-id="ecb7a-111">Depois que o método retorna, ele contém uma matriz de `COR_PRF_CODE_INFO` estruturas, cada um deles descreve um bloco de código nativo.</span><span class="sxs-lookup"><span data-stu-id="ecb7a-111">After the method returns, it contains an array of `COR_PRF_CODE_INFO` structures, each of which describes a block of native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ecb7a-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="ecb7a-112">Remarks</span></span>  
 <span data-ttu-id="ecb7a-113">O `GetCodeInfo3` método é semelhante ao [GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md), exceto que ele obterá a ID da função que contém o endereço IP especificado recompilado por JIT.</span><span class="sxs-lookup"><span data-stu-id="ecb7a-113">The `GetCodeInfo3` method is similar to [GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md), except that it will get the JIT-recompiled ID of the function that contains the specified IP address.</span></span>  
  
> [!NOTE]
>  `GetCodeInfo3` <span data-ttu-id="ecb7a-114">pode disparar uma coleta de lixo, enquanto [GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md) será não.</span><span class="sxs-lookup"><span data-stu-id="ecb7a-114">can trigger a garbage collection, whereas [GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md) will not.</span></span> <span data-ttu-id="ecb7a-115">Para obter mais informações, consulte o [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md) HRESULT.</span><span class="sxs-lookup"><span data-stu-id="ecb7a-115">For more information, see the [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md) HRESULT.</span></span>  
  
 <span data-ttu-id="ecb7a-116">As extensões são classificadas em ordem crescente de deslocamento de idioma intermediário comum (CIL).</span><span class="sxs-lookup"><span data-stu-id="ecb7a-116">The extents are sorted in order of increasing Common Intermediate Language (CIL) offset.</span></span>  
  
 <span data-ttu-id="ecb7a-117">Após `GetCodeInfo3` é retornado, você deve verificar se o `codeInfos` buffer era grande o suficiente para conter todos os as [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) estruturas.</span><span class="sxs-lookup"><span data-stu-id="ecb7a-117">After `GetCodeInfo3` returns, you must verify that the `codeInfos` buffer was large enough to contain all the [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structures.</span></span> <span data-ttu-id="ecb7a-118">Para fazer isso, comparar o valor de `cCodeInfos` com o valor da `cchName` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="ecb7a-118">To do this, compare the value of `cCodeInfos` with the value of the `cchName` parameter.</span></span> <span data-ttu-id="ecb7a-119">Se `cCodeInfos` dividida pelo tamanho de um [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) estrutura é menor que `pcCodeInfos`, alocar uma maior `codeInfos` do buffer, atualize `cCodeInfos` com o novo e maior tamanho e a chamada `GetCodeInfo3` novamente.</span><span class="sxs-lookup"><span data-stu-id="ecb7a-119">If `cCodeInfos` divided by the size of a [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structure is smaller than `pcCodeInfos`, allocate a larger `codeInfos` buffer, update `cCodeInfos` with the new, larger size, and call `GetCodeInfo3` again.</span></span>  
  
 <span data-ttu-id="ecb7a-120">Como alternativa, você pode primeiro chamar `GetCodeInfo3` com um comprimento de zero `codeInfos` buffer para obter o tamanho do buffer correto.</span><span class="sxs-lookup"><span data-stu-id="ecb7a-120">Alternatively, you can first call `GetCodeInfo3` with a zero-length `codeInfos` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="ecb7a-121">Em seguida, você pode definir a `codeInfos` buffers de tamanho para o valor retornado na `pcCodeInfos`, multiplicado pelo tamanho de um [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) estrutura e chame `GetCodeInfo3` novamente.</span><span class="sxs-lookup"><span data-stu-id="ecb7a-121">You can then set the `codeInfos` buffer size to the value returned in `pcCodeInfos`, multiplied by the size of a [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structure, and call `GetCodeInfo3` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ecb7a-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ecb7a-122">Requirements</span></span>  
 <span data-ttu-id="ecb7a-123">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ecb7a-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ecb7a-124">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ecb7a-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ecb7a-125">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ecb7a-125">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="ecb7a-126">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="ecb7a-126">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ecb7a-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ecb7a-127">See also</span></span>

- [<span data-ttu-id="ecb7a-128">Método GetCodeInfo2</span><span class="sxs-lookup"><span data-stu-id="ecb7a-128">GetCodeInfo2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md)
- [<span data-ttu-id="ecb7a-129">Interface ICorProfilerInfo4</span><span class="sxs-lookup"><span data-stu-id="ecb7a-129">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [<span data-ttu-id="ecb7a-130">Criação de perfil de interfaces</span><span class="sxs-lookup"><span data-stu-id="ecb7a-130">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="ecb7a-131">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="ecb7a-131">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
