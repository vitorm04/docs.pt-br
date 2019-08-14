---
title: ICorProfilerInfo9::GetCodeInfo4
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo9.GetCodeInfo4
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: e0493ed3f8796019d5715ef468c88675b9970a39
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68973836"
---
# <a name="icorprofilerinfo9getcodeinfo4-method"></a><span data-ttu-id="53981-102">Método ICorProfilerInfo9:: GetCodeInfo4</span><span class="sxs-lookup"><span data-stu-id="53981-102">ICorProfilerInfo9::GetCodeInfo4 Method</span></span>
  
 <span data-ttu-id="53981-103">Dado o endereço de início do código nativo, retorna os blocos de memória virtual que armazenam esse código.</span><span class="sxs-lookup"><span data-stu-id="53981-103">Given the native code start address, returns the blocks of virtual memory that store this code.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="53981-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="53981-104">Syntax</span></span>  
  
```cpp
HRESULT GetCodeInfo4( [in]  UINT_PTR pNativeCodeStartAddress,
                      [in]  ULONG32 cCodeInfos,
                      [out] ULONG32* pcCodeInfos,
                      [out] COR_PRF_CODE_INFO codeInfos[]);
```  
  
#### <a name="parameters"></a><span data-ttu-id="53981-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="53981-105">Parameters</span></span>  
 `pNativeCodeStartAddress`  
 <span data-ttu-id="53981-106">no Um ponteiro para o início de uma função nativa.</span><span class="sxs-lookup"><span data-stu-id="53981-106">[in] A pointer to the start of a native function.</span></span>  

 `cCodeInfos`  
 <span data-ttu-id="53981-107">no O tamanho da `codeInfos` matriz.</span><span class="sxs-lookup"><span data-stu-id="53981-107">[in] The size of the `codeInfos` array.</span></span>  
  
 `pcCodeInfos`  
 <span data-ttu-id="53981-108">fora Um ponteiro para o número total de estruturas [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) disponíveis.</span><span class="sxs-lookup"><span data-stu-id="53981-108">[out] A pointer to the total number of [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structures available.</span></span>  
  
 `codeInfos`  
 <span data-ttu-id="53981-109">fora Um buffer fornecido pelo chamador.</span><span class="sxs-lookup"><span data-stu-id="53981-109">[out] A caller-provided buffer.</span></span> <span data-ttu-id="53981-110">Depois que o método retorna, ele contém uma matriz `COR_PRF_CODE_INFO` de estruturas, cada uma delas descreve um bloco de código nativo.</span><span class="sxs-lookup"><span data-stu-id="53981-110">After the method returns, it contains an array of `COR_PRF_CODE_INFO` structures, each of which describes a block of native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="53981-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="53981-111">Remarks</span></span>  
 <span data-ttu-id="53981-112">O `GetCodeInfo4` método é semelhante a [GetCodeInfo3](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getcodeinfo3-method.md), exceto pelo fato de que ele pode pesquisar informações de código para versões nativas diferentes de um método.</span><span class="sxs-lookup"><span data-stu-id="53981-112">The `GetCodeInfo4` method is similar to [GetCodeInfo3](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getcodeinfo3-method.md), except that it can look up code information for different native versions of a method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="53981-113">`GetCodeInfo4`pode disparar uma coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="53981-113">`GetCodeInfo4` can trigger a garbage collection.</span></span>
  
 <span data-ttu-id="53981-114">As extensões são classificadas em ordem crescente de deslocamento de Common Intermediate Language (CIL).</span><span class="sxs-lookup"><span data-stu-id="53981-114">The extents are sorted in order of increasing Common Intermediate Language (CIL) offset.</span></span>  
  
 <span data-ttu-id="53981-115">Depois `GetCodeInfo4` de retornar, você deve verificar se `codeInfos` o buffer foi grande o suficiente para conter todas as estruturas [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="53981-115">After `GetCodeInfo4` returns, you must verify that the `codeInfos` buffer was large enough to contain all the [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structures.</span></span> <span data-ttu-id="53981-116">Para fazer isso, compare o valor de `cCodeInfos` com o valor `cchName` do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="53981-116">To do this, compare the value of `cCodeInfos` with the value of the `cchName` parameter.</span></span> <span data-ttu-id="53981-117">Se `cCodeInfos` dividido pelo tamanho de uma estrutura [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) for menor que `pcCodeInfos`, aloque um buffer maior `codeInfos` , atualize `cCodeInfos` com o novo tamanho, maior e chame `GetCodeInfo4` novamente.</span><span class="sxs-lookup"><span data-stu-id="53981-117">If `cCodeInfos` divided by the size of a [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structure is smaller than `pcCodeInfos`, allocate a larger `codeInfos` buffer, update `cCodeInfos` with the new, larger size, and call `GetCodeInfo4` again.</span></span>  
  
 <span data-ttu-id="53981-118">Como alternativa, você pode primeiro chamar `GetCodeInfo4` com um buffer de comprimento `codeInfos` zero para obter o tamanho de buffer correto.</span><span class="sxs-lookup"><span data-stu-id="53981-118">Alternatively, you can first call `GetCodeInfo4` with a zero-length `codeInfos` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="53981-119">Em seguida, você pode `codeInfos` definir o tamanho do buffer para o `pcCodeInfos`valor retornado em, multiplicado pelo tamanho de uma estrutura [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) e `GetCodeInfo4` chamar novamente.</span><span class="sxs-lookup"><span data-stu-id="53981-119">You can then set the `codeInfos` buffer size to the value returned in `pcCodeInfos`, multiplied by the size of a [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structure, and call `GetCodeInfo4` again.</span></span>   
  

## <a name="requirements"></a><span data-ttu-id="53981-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="53981-120">Requirements</span></span>  
 <span data-ttu-id="53981-121">**Compatíveis** Consulte [sistemas operacionais com suporte do .NET Core](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span><span class="sxs-lookup"><span data-stu-id="53981-121">**Platforms:** See [.NET Core supported operating systems](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span></span>  
  
 <span data-ttu-id="53981-122">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="53981-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="53981-123">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="53981-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="53981-124">**Versões do .net:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53981-124">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="53981-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="53981-125">See also</span></span>
- [<span data-ttu-id="53981-126">Interface ICorProfilerInfo9</span><span class="sxs-lookup"><span data-stu-id="53981-126">ICorProfilerInfo9 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/ICorProfilerInfo9-interface.md)

