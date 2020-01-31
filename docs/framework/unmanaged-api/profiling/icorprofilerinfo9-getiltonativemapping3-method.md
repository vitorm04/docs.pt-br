---
title: ICorProfilerInfo9::GetILToNativeMapping3
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo9.GetILToNativeMapping3
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 5c49d75432980d2f3af77ee040bc6eb20886b027
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76861665"
---
# <a name="icorprofilerinfo9getiltonativemapping3-method"></a><span data-ttu-id="889fb-102">Método ICorProfilerInfo9:: GetILToNativeMapping3</span><span class="sxs-lookup"><span data-stu-id="889fb-102">ICorProfilerInfo9::GetILToNativeMapping3 Method</span></span>

<span data-ttu-id="889fb-103">Dado o endereço de início do código nativo, retorna as informações de mapeamento nativo para IL para essa versão JIT do código.</span><span class="sxs-lookup"><span data-stu-id="889fb-103">Given the native code start address, returns the native to IL mapping information for this jitted version of the code.</span></span>

## <a name="syntax"></a><span data-ttu-id="889fb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="889fb-104">Syntax</span></span>

```cpp
HRESULT GetILToNativeMapping3( [in]  UINT_PTR pNativeCodeStartAddress,
                               [in]  ULONG32 cMap,
                               [out] ULONG32 *pcMap,
                               [out] COR_DEBUG_IL_TO_NATIVE_MAP map[]);
```

## <a name="parameters"></a><span data-ttu-id="889fb-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="889fb-105">Parameters</span></span>

- `pNativeCodeStartAddress`

  <span data-ttu-id="889fb-106">\[em] um ponteiro para o início de uma função nativa.</span><span class="sxs-lookup"><span data-stu-id="889fb-106">\[in] A pointer to the start of a native function.</span></span>

- `cMap`

  <span data-ttu-id="889fb-107">\[em] o tamanho máximo da matriz de `map`.</span><span class="sxs-lookup"><span data-stu-id="889fb-107">\[in] The maximum size of the `map` array.</span></span>

- `pcMap`

  <span data-ttu-id="889fb-108">\[out] o número total de estruturas de COR_DEBUG_IL_TO_NATIVE_MAP disponíveis.</span><span class="sxs-lookup"><span data-stu-id="889fb-108">\[out] The total number of available COR_DEBUG_IL_TO_NATIVE_MAP structures.</span></span>

- `map`

  <span data-ttu-id="889fb-109">\[out] uma matriz de estruturas de [COR_DEBUG_IL_TO_NATIVE_MAP](../debugging/cor-debug-il-to-native-map-structure.md) , cada uma delas especifica os deslocamentos.</span><span class="sxs-lookup"><span data-stu-id="889fb-109">\[out] An array of [COR_DEBUG_IL_TO_NATIVE_MAP](../debugging/cor-debug-il-to-native-map-structure.md) structures, each of which specifies the offsets.</span></span> <span data-ttu-id="889fb-110">Depois que o método `GetILToNativeMapping3` retornar, `map` conterá algumas ou todas as estruturas de `COR_DEBUG_IL_TO_NATIVE_MAP`.</span><span class="sxs-lookup"><span data-stu-id="889fb-110">After the `GetILToNativeMapping3` method returns, `map` will contain some or all of the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span>

## <a name="remarks"></a><span data-ttu-id="889fb-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="889fb-111">Remarks</span></span>

<span data-ttu-id="889fb-112">Quando a compilação em camadas está habilitada, um método pode ter mais de um corpo de código nativo.</span><span class="sxs-lookup"><span data-stu-id="889fb-112">When tiered compilation is enabled, a method may have more than one native code body.</span></span> <span data-ttu-id="889fb-113">[ICorProfilerInfo9:: GetNativeCodeStartAddresses](icorprofilerinfo9-getnativecodestartaddresses-method.md) retornará os endereços iniciais para todos os corpos de código nativos.</span><span class="sxs-lookup"><span data-stu-id="889fb-113">[ICorProfilerInfo9::GetNativeCodeStartAddresses](icorprofilerinfo9-getnativecodestartaddresses-method.md) will return the start addresses for all of the native code bodies.</span></span>

## <a name="requirements"></a><span data-ttu-id="889fb-114">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="889fb-114">Requirements</span></span>

<span data-ttu-id="889fb-115">**Plataformas:** Consulte [sistemas operacionais com suporte do .NET Core](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="889fb-115">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span></span>

<span data-ttu-id="889fb-116">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="889fb-116">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="889fb-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="889fb-117">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="889fb-118">**Versões do .NET Framework:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="889fb-118">**.NET Framework Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="889fb-119">Veja também</span><span class="sxs-lookup"><span data-stu-id="889fb-119">See also</span></span>

- [<span data-ttu-id="889fb-120">Interface ICorProfilerInfo9</span><span class="sxs-lookup"><span data-stu-id="889fb-120">ICorProfilerInfo9 Interface</span></span>](icorprofilerinfo9-interface.md)
