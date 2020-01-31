---
title: ICorProfilerInfo9::GetNativeCodeStartAddresses
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo9.GetNativeCodeStartAddresses
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 8412020fb98fde245b873a2f0c6a355f6436f712
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868272"
---
# <a name="icorprofilerinfo9getnativecodestartaddresses-method"></a><span data-ttu-id="52e6b-102">Método ICorProfilerInfo9:: GetNativeCodeStartAddresses</span><span class="sxs-lookup"><span data-stu-id="52e6b-102">ICorProfilerInfo9::GetNativeCodeStartAddresses Method</span></span>

<span data-ttu-id="52e6b-103">Dada uma FunctionID e rejitId, enumera o endereço inicial do código de início de todas as versões com compilação JIT desse código que existem atualmente.</span><span class="sxs-lookup"><span data-stu-id="52e6b-103">Given a functionId and rejitId, enumerates the native code start address of all jitted versions of this code that currently exist.</span></span>

## <a name="syntax"></a><span data-ttu-id="52e6b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="52e6b-104">Syntax</span></span>

```cpp
HRESULT GetNativeCodeStartAddresses( [in]  FunctionID functionID,
                                     [in]  ReJITID reJitId,
                                     [in]  ULONG32 cCodeStartAddresses,
                                     [out] ULONG32 *pcCodeStartAddresses,
                                     [out] UINT_PTR codeStartAddresses[]);
```

## <a name="parameters"></a><span data-ttu-id="52e6b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="52e6b-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="52e6b-106">\[em] a ID da função cujos endereços de início de código nativo devem ser retornados.</span><span class="sxs-lookup"><span data-stu-id="52e6b-106">\[in] The ID of the function whose native code start addresses should be returned.</span></span>

- `reJitId`

  <span data-ttu-id="52e6b-107">\[em] a identidade da função de compilação JIT recompilada.</span><span class="sxs-lookup"><span data-stu-id="52e6b-107">\[in] The identity of the JIT-recompiled function.</span></span>

- `cCodeStartAddresses`

  <span data-ttu-id="52e6b-108">\[em] o tamanho máximo da matriz de `codeStartAddresses`.</span><span class="sxs-lookup"><span data-stu-id="52e6b-108">\[in] The maximum size of the `codeStartAddresses` array.</span></span>

- `pcCodeStartAddresses`

  <span data-ttu-id="52e6b-109">\[out] o número de endereços disponíveis.</span><span class="sxs-lookup"><span data-stu-id="52e6b-109">\[out] The number of available addresses.</span></span>

- `codeStartAddresses`

  <span data-ttu-id="52e6b-110">\[out] uma matriz de `UINT_PTR`, cada uma delas é o endereço inicial de um corpo nativo para a função especificada.</span><span class="sxs-lookup"><span data-stu-id="52e6b-110">\[out] An array of `UINT_PTR`, each one of which is the start address for a native body for the specified function.</span></span>

## <a name="remarks"></a><span data-ttu-id="52e6b-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="52e6b-111">Remarks</span></span>

<span data-ttu-id="52e6b-112">Quando a compilação em camadas está habilitada, uma função pode ter mais de um corpo de código nativo.</span><span class="sxs-lookup"><span data-stu-id="52e6b-112">When tiered compilation is enabled, a function may have more than one native code body.</span></span>

## <a name="requirements"></a><span data-ttu-id="52e6b-113">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="52e6b-113">Requirements</span></span>

<span data-ttu-id="52e6b-114">**Plataformas:** Consulte [sistemas operacionais com suporte do .NET Core](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="52e6b-114">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span></span>

<span data-ttu-id="52e6b-115">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="52e6b-115">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="52e6b-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="52e6b-116">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="52e6b-117">**Versões do .net:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52e6b-117">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="52e6b-118">Veja também</span><span class="sxs-lookup"><span data-stu-id="52e6b-118">See also</span></span>

- [<span data-ttu-id="52e6b-119">Interface ICorProfilerInfo9</span><span class="sxs-lookup"><span data-stu-id="52e6b-119">ICorProfilerInfo9 Interface</span></span>](icorprofilerinfo9-interface.md)
