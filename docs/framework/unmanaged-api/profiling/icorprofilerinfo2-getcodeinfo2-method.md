---
title: Método ICorProfilerInfo2::GetCodeInfo2
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetCodeInfo2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetCodeInfo2
helpviewer_keywords:
- ICorProfilerInfo2::GetCodeInfo2 method [.NET Framework profiling]
- GetCodeInfo2 method [.NET Framework profiling]
ms.assetid: 532da6ee-7f0a-401b-a61e-fc47ec235d2e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1acdc5d094fe93118e6cc62774f1cbf47a357dfc
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67751811"
---
# <a name="icorprofilerinfo2getcodeinfo2-method"></a><span data-ttu-id="9d661-102">Método ICorProfilerInfo2::GetCodeInfo2</span><span class="sxs-lookup"><span data-stu-id="9d661-102">ICorProfilerInfo2::GetCodeInfo2 Method</span></span>
<span data-ttu-id="9d661-103">Obtém as extensões de código nativo associado especificado `FunctionID`.</span><span class="sxs-lookup"><span data-stu-id="9d661-103">Gets the extents of native code associated with the specified `FunctionID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d661-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9d661-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCodeInfo2(  
    [in]  FunctionID functionID,  
    [in]  ULONG32 cCodeInfos,  
    [out] ULONG32 *pcCodeInfos,  
    [out, size_is(cCodeInfos), length_is(*pcCodeInfos)]  
    COR_PRF_CODE_INFO codeInfos[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9d661-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9d661-105">Parameters</span></span>  
 `functionID`  
 <span data-ttu-id="9d661-106">[in] A ID da função à qual o código nativo está associado.</span><span class="sxs-lookup"><span data-stu-id="9d661-106">[in] The ID of the function with which the native code is associated.</span></span>  
  
 `cCodeInfos`  
 <span data-ttu-id="9d661-107">[in] O tamanho do `codeInfos` matriz.</span><span class="sxs-lookup"><span data-stu-id="9d661-107">[in] The size of the `codeInfos` array.</span></span>  
  
 `pcCodeInfos`  
 <span data-ttu-id="9d661-108">[out] Um ponteiro para o número total de [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) estruturas disponíveis.</span><span class="sxs-lookup"><span data-stu-id="9d661-108">[out] A pointer to the total number of [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structures available.</span></span>  
  
 `codeInfos`  
 <span data-ttu-id="9d661-109">[out] Um buffer fornecido pelo chamador.</span><span class="sxs-lookup"><span data-stu-id="9d661-109">[out] A caller-provided buffer.</span></span> <span data-ttu-id="9d661-110">Depois que o método retorna, ele contém uma matriz de `COR_PRF_CODE_INFO` estruturas, cada um deles descreve um bloco de código nativo.</span><span class="sxs-lookup"><span data-stu-id="9d661-110">After the method returns, it contains an array of `COR_PRF_CODE_INFO` structures, each of which describes a block of native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9d661-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="9d661-111">Remarks</span></span>  
 <span data-ttu-id="9d661-112">As extensões são classificadas em ordem crescente deslocamento do Microsoft intermediate language (MSIL).</span><span class="sxs-lookup"><span data-stu-id="9d661-112">The extents are sorted in order of increasing Microsoft intermediate language (MSIL) offset.</span></span>  
  
 <span data-ttu-id="9d661-113">Após `GetCodeInfo2` é retornado, você deve verificar se o `codeInfos` buffer era grande o suficiente para conter todos o `COR_PRF_CODE_INFO` estruturas.</span><span class="sxs-lookup"><span data-stu-id="9d661-113">After `GetCodeInfo2` returns, you must verify that the `codeInfos` buffer was large enough to contain all the `COR_PRF_CODE_INFO` structures.</span></span> <span data-ttu-id="9d661-114">Para fazer isso, comparar o valor de `cCodeInfos` com o valor da `cchName` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="9d661-114">To do this, compare the value of `cCodeInfos` with the value of the `cchName` parameter.</span></span> <span data-ttu-id="9d661-115">Se `cCodeInfos` dividida pelo tamanho de um `COR_PRF_CODE_INFO` estrutura é menor que `pcCodeInfos`, alocar uma maior `codeInfos` buffer, atualize `cCodeInfos` com o novo e maior tamanho e a chamada `GetCodeInfo2` novamente.</span><span class="sxs-lookup"><span data-stu-id="9d661-115">If `cCodeInfos` divided by the size of a `COR_PRF_CODE_INFO` structure is smaller than `pcCodeInfos`, allocate a larger `codeInfos` buffer, update `cCodeInfos` with the new, larger size, and call `GetCodeInfo2` again.</span></span>  
  
 <span data-ttu-id="9d661-116">Como alternativa, você pode primeiro chamar `GetCodeInfo2` com um comprimento de zero `codeInfos` buffer para obter o tamanho do buffer correto.</span><span class="sxs-lookup"><span data-stu-id="9d661-116">Alternatively, you can first call `GetCodeInfo2` with a zero-length `codeInfos` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="9d661-117">Em seguida, você pode definir a `codeInfos` buffers de tamanho para o valor retornado na `pcCodeInfos`, multiplicado pelo tamanho de um `COR_PRF_CODE_INFO` estrutura e chame `GetCodeInfo2` novamente.</span><span class="sxs-lookup"><span data-stu-id="9d661-117">You can then set the `codeInfos` buffer size to the value returned in `pcCodeInfos`, multiplied by the size of a `COR_PRF_CODE_INFO` structure, and call `GetCodeInfo2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d661-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9d661-118">Requirements</span></span>  
 <span data-ttu-id="9d661-119">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d661-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d661-120">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9d661-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9d661-121">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9d661-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9d661-122">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d661-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d661-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9d661-123">See also</span></span>

- [<span data-ttu-id="9d661-124">Método GetCodeInfo3</span><span class="sxs-lookup"><span data-stu-id="9d661-124">GetCodeInfo3 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getcodeinfo3-method.md)
- [<span data-ttu-id="9d661-125">Interface ICorProfilerInfo2</span><span class="sxs-lookup"><span data-stu-id="9d661-125">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
- [<span data-ttu-id="9d661-126">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="9d661-126">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="9d661-127">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="9d661-127">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
