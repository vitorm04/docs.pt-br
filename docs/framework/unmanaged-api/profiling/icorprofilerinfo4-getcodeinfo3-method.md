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
ms.openlocfilehash: d29145a9c224a064cf9210c56c8617d99f7690ba
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443070"
---
# <a name="icorprofilerinfo4getcodeinfo3-method"></a><span data-ttu-id="74c30-102">Método ICorProfilerInfo4::GetCodeInfo3</span><span class="sxs-lookup"><span data-stu-id="74c30-102">ICorProfilerInfo4::GetCodeInfo3 Method</span></span>
<span data-ttu-id="74c30-103">Obtém as extensões do código nativo associado à versão recompilada do JIT da função especificada.</span><span class="sxs-lookup"><span data-stu-id="74c30-103">Gets the extents of native code associated with the JIT-recompiled version of the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74c30-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="74c30-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCodeInfo3(  
    [in]  FunctionID functionID,  
    [in]  ReJITID reJitId,  
    [in]  ULONG32 cCodeInfos,  
    [out] ULONG32 *pcCodeInfos,  
    [out, size_is(cCodeInfos), length_is(*pcCodeInfos)]  
    COR_PRF_CODE_INFO codeInfos[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="74c30-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="74c30-105">Parameters</span></span>  
 `functionID`  
 <span data-ttu-id="74c30-106">no A ID da função à qual o código nativo está associado.</span><span class="sxs-lookup"><span data-stu-id="74c30-106">[in] The ID of the function with which the native code is associated.</span></span>  
  
 `reJitId`  
 <span data-ttu-id="74c30-107">no A identidade da função de compilação JIT recompilada.</span><span class="sxs-lookup"><span data-stu-id="74c30-107">[in] The identity of the JIT-recompiled function.</span></span>  
  
 `cCodeInfos`  
 <span data-ttu-id="74c30-108">no O tamanho da matriz de `codeInfos`.</span><span class="sxs-lookup"><span data-stu-id="74c30-108">[in] The size of the `codeInfos` array.</span></span>  
  
 `pcCodeInfos`  
 <span data-ttu-id="74c30-109">fora Um ponteiro para o número total de estruturas de [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) disponíveis.</span><span class="sxs-lookup"><span data-stu-id="74c30-109">[out] A pointer to the total number of [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structures available.</span></span>  
  
 `codeInfos`  
 <span data-ttu-id="74c30-110">fora Um buffer fornecido pelo chamador.</span><span class="sxs-lookup"><span data-stu-id="74c30-110">[out] A caller-provided buffer.</span></span> <span data-ttu-id="74c30-111">Depois que o método retorna, ele contém uma matriz de estruturas `COR_PRF_CODE_INFO`, cada uma delas descreve um bloco de código nativo.</span><span class="sxs-lookup"><span data-stu-id="74c30-111">After the method returns, it contains an array of `COR_PRF_CODE_INFO` structures, each of which describes a block of native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="74c30-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="74c30-112">Remarks</span></span>  
 <span data-ttu-id="74c30-113">O método `GetCodeInfo3` é semelhante a [GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md), exceto pelo fato de que ele obterá a ID de compilação JIT recompilada da função que contém o endereço IP especificado.</span><span class="sxs-lookup"><span data-stu-id="74c30-113">The `GetCodeInfo3` method is similar to [GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md), except that it will get the JIT-recompiled ID of the function that contains the specified IP address.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="74c30-114">`GetCodeInfo3` pode disparar uma coleta de lixo, enquanto [GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md) não vai.</span><span class="sxs-lookup"><span data-stu-id="74c30-114">`GetCodeInfo3` can trigger a garbage collection, whereas [GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md) will not.</span></span> <span data-ttu-id="74c30-115">Para obter mais informações, consulte o [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md) HRESULT.</span><span class="sxs-lookup"><span data-stu-id="74c30-115">For more information, see the [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md) HRESULT.</span></span>  
  
 <span data-ttu-id="74c30-116">As extensões são classificadas em ordem crescente de deslocamento de Common Intermediate Language (CIL).</span><span class="sxs-lookup"><span data-stu-id="74c30-116">The extents are sorted in order of increasing Common Intermediate Language (CIL) offset.</span></span>  
  
 <span data-ttu-id="74c30-117">Depois que `GetCodeInfo3` retorna, você deve verificar se o buffer de `codeInfos` era grande o suficiente para conter todas as estruturas de [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="74c30-117">After `GetCodeInfo3` returns, you must verify that the `codeInfos` buffer was large enough to contain all the [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structures.</span></span> <span data-ttu-id="74c30-118">Para fazer isso, compare o valor de `cCodeInfos` com o valor do parâmetro `cchName`.</span><span class="sxs-lookup"><span data-stu-id="74c30-118">To do this, compare the value of `cCodeInfos` with the value of the `cchName` parameter.</span></span> <span data-ttu-id="74c30-119">Se `cCodeInfos` dividido pelo tamanho de uma estrutura de [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) for menor do que `pcCodeInfos`, aloque um buffer de `codeInfos` maior, atualize `cCodeInfos` com o tamanho novo, maior e chame `GetCodeInfo3` novamente.</span><span class="sxs-lookup"><span data-stu-id="74c30-119">If `cCodeInfos` divided by the size of a [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structure is smaller than `pcCodeInfos`, allocate a larger `codeInfos` buffer, update `cCodeInfos` with the new, larger size, and call `GetCodeInfo3` again.</span></span>  
  
 <span data-ttu-id="74c30-120">Como alternativa, você pode primeiro chamar `GetCodeInfo3` com um buffer de `codeInfos` de comprimento zero para obter o tamanho de buffer correto.</span><span class="sxs-lookup"><span data-stu-id="74c30-120">Alternatively, you can first call `GetCodeInfo3` with a zero-length `codeInfos` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="74c30-121">Em seguida, você pode definir o tamanho do buffer de `codeInfos` para o valor retornado em `pcCodeInfos`, multiplicado pelo tamanho de uma estrutura de [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) e chamar `GetCodeInfo3` novamente.</span><span class="sxs-lookup"><span data-stu-id="74c30-121">You can then set the `codeInfos` buffer size to the value returned in `pcCodeInfos`, multiplied by the size of a [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structure, and call `GetCodeInfo3` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74c30-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="74c30-122">Requirements</span></span>  
 <span data-ttu-id="74c30-123">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="74c30-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74c30-124">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="74c30-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="74c30-125">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="74c30-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="74c30-126">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74c30-126">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74c30-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="74c30-127">See also</span></span>

- [<span data-ttu-id="74c30-128">Método GetCodeInfo2</span><span class="sxs-lookup"><span data-stu-id="74c30-128">GetCodeInfo2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md)
- [<span data-ttu-id="74c30-129">Interface ICorProfilerInfo4</span><span class="sxs-lookup"><span data-stu-id="74c30-129">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [<span data-ttu-id="74c30-130">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="74c30-130">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="74c30-131">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="74c30-131">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
