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
ms.openlocfilehash: 54e522aaaf23ae81b96b6be7168a9a13f28a16d2
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496125"
---
# <a name="icorprofilerinfo4getcodeinfo3-method"></a><span data-ttu-id="545e7-102">Método ICorProfilerInfo4::GetCodeInfo3</span><span class="sxs-lookup"><span data-stu-id="545e7-102">ICorProfilerInfo4::GetCodeInfo3 Method</span></span>
<span data-ttu-id="545e7-103">Obtém as extensões do código nativo associado à versão recompilada do JIT da função especificada.</span><span class="sxs-lookup"><span data-stu-id="545e7-103">Gets the extents of native code associated with the JIT-recompiled version of the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="545e7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="545e7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCodeInfo3(  
    [in]  FunctionID functionID,  
    [in]  ReJITID reJitId,  
    [in]  ULONG32 cCodeInfos,  
    [out] ULONG32 *pcCodeInfos,  
    [out, size_is(cCodeInfos), length_is(*pcCodeInfos)]  
    COR_PRF_CODE_INFO codeInfos[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="545e7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="545e7-105">Parameters</span></span>  
 `functionID`  
 <span data-ttu-id="545e7-106">no A ID da função à qual o código nativo está associado.</span><span class="sxs-lookup"><span data-stu-id="545e7-106">[in] The ID of the function with which the native code is associated.</span></span>  
  
 `reJitId`  
 <span data-ttu-id="545e7-107">no A identidade da função de compilação JIT recompilada.</span><span class="sxs-lookup"><span data-stu-id="545e7-107">[in] The identity of the JIT-recompiled function.</span></span>  
  
 `cCodeInfos`  
 <span data-ttu-id="545e7-108">no O tamanho da `codeInfos` matriz.</span><span class="sxs-lookup"><span data-stu-id="545e7-108">[in] The size of the `codeInfos` array.</span></span>  
  
 `pcCodeInfos`  
 <span data-ttu-id="545e7-109">fora Um ponteiro para o número total de estruturas de [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) disponíveis.</span><span class="sxs-lookup"><span data-stu-id="545e7-109">[out] A pointer to the total number of [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structures available.</span></span>  
  
 `codeInfos`  
 <span data-ttu-id="545e7-110">fora Um buffer fornecido pelo chamador.</span><span class="sxs-lookup"><span data-stu-id="545e7-110">[out] A caller-provided buffer.</span></span> <span data-ttu-id="545e7-111">Depois que o método retorna, ele contém uma matriz de `COR_PRF_CODE_INFO` estruturas, cada uma delas descreve um bloco de código nativo.</span><span class="sxs-lookup"><span data-stu-id="545e7-111">After the method returns, it contains an array of `COR_PRF_CODE_INFO` structures, each of which describes a block of native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="545e7-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="545e7-112">Remarks</span></span>  
 <span data-ttu-id="545e7-113">O `GetCodeInfo3` método é semelhante a [GetCodeInfo2](icorprofilerinfo2-getcodeinfo2-method.md), exceto pelo fato de que ele receberá a ID de compilação JIT recompilada da função que contém o endereço IP especificado.</span><span class="sxs-lookup"><span data-stu-id="545e7-113">The `GetCodeInfo3` method is similar to [GetCodeInfo2](icorprofilerinfo2-getcodeinfo2-method.md), except that it will get the JIT-recompiled ID of the function that contains the specified IP address.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="545e7-114">`GetCodeInfo3`pode disparar uma coleta de lixo, enquanto [GetCodeInfo2](icorprofilerinfo2-getcodeinfo2-method.md) não vai.</span><span class="sxs-lookup"><span data-stu-id="545e7-114">`GetCodeInfo3` can trigger a garbage collection, whereas [GetCodeInfo2](icorprofilerinfo2-getcodeinfo2-method.md) will not.</span></span> <span data-ttu-id="545e7-115">Para obter mais informações, consulte o [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](corprof-e-unsupported-call-sequence-hresult.md) HRESULT.</span><span class="sxs-lookup"><span data-stu-id="545e7-115">For more information, see the [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](corprof-e-unsupported-call-sequence-hresult.md) HRESULT.</span></span>  
  
 <span data-ttu-id="545e7-116">As extensões são classificadas em ordem crescente de deslocamento de Common Intermediate Language (CIL).</span><span class="sxs-lookup"><span data-stu-id="545e7-116">The extents are sorted in order of increasing Common Intermediate Language (CIL) offset.</span></span>  
  
 <span data-ttu-id="545e7-117">Depois de `GetCodeInfo3` retornar, você deve verificar se o `codeInfos` buffer foi grande o suficiente para conter todas as estruturas de [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="545e7-117">After `GetCodeInfo3` returns, you must verify that the `codeInfos` buffer was large enough to contain all the [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structures.</span></span> <span data-ttu-id="545e7-118">Para fazer isso, compare o valor de `cCodeInfos` com o valor do `cchName` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="545e7-118">To do this, compare the value of `cCodeInfos` with the value of the `cchName` parameter.</span></span> <span data-ttu-id="545e7-119">Se `cCodeInfos` dividido pelo tamanho de uma estrutura de [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) for menor que `pcCodeInfos` , aloque um `codeInfos` buffer maior, atualize `cCodeInfos` com o tamanho novo, maior e chame `GetCodeInfo3` novamente.</span><span class="sxs-lookup"><span data-stu-id="545e7-119">If `cCodeInfos` divided by the size of a [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structure is smaller than `pcCodeInfos`, allocate a larger `codeInfos` buffer, update `cCodeInfos` with the new, larger size, and call `GetCodeInfo3` again.</span></span>  
  
 <span data-ttu-id="545e7-120">Como alternativa, você pode primeiro chamar `GetCodeInfo3` com um buffer de comprimento zero `codeInfos` para obter o tamanho de buffer correto.</span><span class="sxs-lookup"><span data-stu-id="545e7-120">Alternatively, you can first call `GetCodeInfo3` with a zero-length `codeInfos` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="545e7-121">Em seguida, você pode definir o `codeInfos` tamanho do buffer para o valor retornado em `pcCodeInfos` , multiplicado pelo tamanho de uma estrutura de [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) e chamar `GetCodeInfo3` novamente.</span><span class="sxs-lookup"><span data-stu-id="545e7-121">You can then set the `codeInfos` buffer size to the value returned in `pcCodeInfos`, multiplied by the size of a [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structure, and call `GetCodeInfo3` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="545e7-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="545e7-122">Requirements</span></span>  
 <span data-ttu-id="545e7-123">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="545e7-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="545e7-124">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="545e7-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="545e7-125">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="545e7-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="545e7-126">**.NET Framework versões:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="545e7-126">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="545e7-127">Confira também</span><span class="sxs-lookup"><span data-stu-id="545e7-127">See also</span></span>

- [<span data-ttu-id="545e7-128">Método GetCodeInfo2</span><span class="sxs-lookup"><span data-stu-id="545e7-128">GetCodeInfo2 Method</span></span>](icorprofilerinfo2-getcodeinfo2-method.md)
- [<span data-ttu-id="545e7-129">Interface ICorProfilerInfo4</span><span class="sxs-lookup"><span data-stu-id="545e7-129">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
- [<span data-ttu-id="545e7-130">Criação de perfil de interfaces</span><span class="sxs-lookup"><span data-stu-id="545e7-130">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="545e7-131">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="545e7-131">Profiling</span></span>](index.md)
