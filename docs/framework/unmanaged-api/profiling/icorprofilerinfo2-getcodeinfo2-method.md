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
ms.openlocfilehash: 04ce9ebded4be7ac3b20a4ceb78dd02294bbff4a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502884"
---
# <a name="icorprofilerinfo2getcodeinfo2-method"></a><span data-ttu-id="11fd6-102">Método ICorProfilerInfo2::GetCodeInfo2</span><span class="sxs-lookup"><span data-stu-id="11fd6-102">ICorProfilerInfo2::GetCodeInfo2 Method</span></span>
<span data-ttu-id="11fd6-103">Obtém as extensões do código nativo associado ao especificado `FunctionID` .</span><span class="sxs-lookup"><span data-stu-id="11fd6-103">Gets the extents of native code associated with the specified `FunctionID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11fd6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="11fd6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCodeInfo2(  
    [in]  FunctionID functionID,  
    [in]  ULONG32 cCodeInfos,  
    [out] ULONG32 *pcCodeInfos,  
    [out, size_is(cCodeInfos), length_is(*pcCodeInfos)]  
    COR_PRF_CODE_INFO codeInfos[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="11fd6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="11fd6-105">Parameters</span></span>  
 `functionID`  
 <span data-ttu-id="11fd6-106">no A ID da função à qual o código nativo está associado.</span><span class="sxs-lookup"><span data-stu-id="11fd6-106">[in] The ID of the function with which the native code is associated.</span></span>  
  
 `cCodeInfos`  
 <span data-ttu-id="11fd6-107">no O tamanho da `codeInfos` matriz.</span><span class="sxs-lookup"><span data-stu-id="11fd6-107">[in] The size of the `codeInfos` array.</span></span>  
  
 `pcCodeInfos`  
 <span data-ttu-id="11fd6-108">fora Um ponteiro para o número total de estruturas de [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) disponíveis.</span><span class="sxs-lookup"><span data-stu-id="11fd6-108">[out] A pointer to the total number of [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structures available.</span></span>  
  
 `codeInfos`  
 <span data-ttu-id="11fd6-109">fora Um buffer fornecido pelo chamador.</span><span class="sxs-lookup"><span data-stu-id="11fd6-109">[out] A caller-provided buffer.</span></span> <span data-ttu-id="11fd6-110">Depois que o método retorna, ele contém uma matriz de `COR_PRF_CODE_INFO` estruturas, cada uma delas descreve um bloco de código nativo.</span><span class="sxs-lookup"><span data-stu-id="11fd6-110">After the method returns, it contains an array of `COR_PRF_CODE_INFO` structures, each of which describes a block of native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="11fd6-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="11fd6-111">Remarks</span></span>  
 <span data-ttu-id="11fd6-112">As extensões são classificadas em ordem de aumento do deslocamento da MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="11fd6-112">The extents are sorted in order of increasing Microsoft intermediate language (MSIL) offset.</span></span>  
  
 <span data-ttu-id="11fd6-113">Depois de `GetCodeInfo2` retornar, você deve verificar se o `codeInfos` buffer foi grande o suficiente para conter todas as `COR_PRF_CODE_INFO` estruturas.</span><span class="sxs-lookup"><span data-stu-id="11fd6-113">After `GetCodeInfo2` returns, you must verify that the `codeInfos` buffer was large enough to contain all the `COR_PRF_CODE_INFO` structures.</span></span> <span data-ttu-id="11fd6-114">Para fazer isso, compare o valor de `cCodeInfos` com o valor do `cchName` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="11fd6-114">To do this, compare the value of `cCodeInfos` with the value of the `cchName` parameter.</span></span> <span data-ttu-id="11fd6-115">Se `cCodeInfos` dividido pelo tamanho de uma `COR_PRF_CODE_INFO` estrutura for menor que `pcCodeInfos` , aloque um buffer maior `codeInfos` , atualize `cCodeInfos` com o tamanho novo, maior e chame `GetCodeInfo2` novamente.</span><span class="sxs-lookup"><span data-stu-id="11fd6-115">If `cCodeInfos` divided by the size of a `COR_PRF_CODE_INFO` structure is smaller than `pcCodeInfos`, allocate a larger `codeInfos` buffer, update `cCodeInfos` with the new, larger size, and call `GetCodeInfo2` again.</span></span>  
  
 <span data-ttu-id="11fd6-116">Como alternativa, você pode primeiro chamar `GetCodeInfo2` com um buffer de comprimento zero `codeInfos` para obter o tamanho de buffer correto.</span><span class="sxs-lookup"><span data-stu-id="11fd6-116">Alternatively, you can first call `GetCodeInfo2` with a zero-length `codeInfos` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="11fd6-117">Em seguida, você pode definir o `codeInfos` tamanho do buffer para o valor retornado em `pcCodeInfos` , multiplicado pelo tamanho de uma `COR_PRF_CODE_INFO` estrutura e chamar `GetCodeInfo2` novamente.</span><span class="sxs-lookup"><span data-stu-id="11fd6-117">You can then set the `codeInfos` buffer size to the value returned in `pcCodeInfos`, multiplied by the size of a `COR_PRF_CODE_INFO` structure, and call `GetCodeInfo2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11fd6-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="11fd6-118">Requirements</span></span>  
 <span data-ttu-id="11fd6-119">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="11fd6-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11fd6-120">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="11fd6-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="11fd6-121">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="11fd6-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="11fd6-122">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11fd6-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11fd6-123">Confira também</span><span class="sxs-lookup"><span data-stu-id="11fd6-123">See also</span></span>

- [<span data-ttu-id="11fd6-124">Método GetCodeInfo3</span><span class="sxs-lookup"><span data-stu-id="11fd6-124">GetCodeInfo3 Method</span></span>](icorprofilerinfo4-getcodeinfo3-method.md)
- [<span data-ttu-id="11fd6-125">Interface ICorProfilerInfo2</span><span class="sxs-lookup"><span data-stu-id="11fd6-125">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
- [<span data-ttu-id="11fd6-126">Criação de perfil de interfaces</span><span class="sxs-lookup"><span data-stu-id="11fd6-126">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="11fd6-127">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="11fd6-127">Profiling</span></span>](index.md)
