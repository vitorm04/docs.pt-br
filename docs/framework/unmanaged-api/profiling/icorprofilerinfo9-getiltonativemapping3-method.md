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
ms.openlocfilehash: 14391a0fe046b44aedca1da2bc42c7d962e1a5e7
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90541272"
---
# <a name="icorprofilerinfo9getiltonativemapping3-method"></a><span data-ttu-id="34655-102">Método ICorProfilerInfo9:: GetILToNativeMapping3</span><span class="sxs-lookup"><span data-stu-id="34655-102">ICorProfilerInfo9::GetILToNativeMapping3 Method</span></span>

<span data-ttu-id="34655-103">Dado o endereço de início do código nativo, retorna as informações de mapeamento nativo para IL para essa versão JIT do código.</span><span class="sxs-lookup"><span data-stu-id="34655-103">Given the native code start address, returns the native to IL mapping information for this jitted version of the code.</span></span>

## <a name="syntax"></a><span data-ttu-id="34655-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="34655-104">Syntax</span></span>

```cpp
HRESULT GetILToNativeMapping3( [in]  UINT_PTR pNativeCodeStartAddress,
                               [in]  ULONG32 cMap,
                               [out] ULONG32 *pcMap,
                               [out] COR_DEBUG_IL_TO_NATIVE_MAP map[]);
```

## <a name="parameters"></a><span data-ttu-id="34655-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="34655-105">Parameters</span></span>

- `pNativeCodeStartAddress`

  <span data-ttu-id="34655-106">\[in] um ponteiro para o início de uma função nativa.</span><span class="sxs-lookup"><span data-stu-id="34655-106">\[in] A pointer to the start of a native function.</span></span>

- `cMap`

  <span data-ttu-id="34655-107">\[in] o tamanho máximo da `map` matriz.</span><span class="sxs-lookup"><span data-stu-id="34655-107">\[in] The maximum size of the `map` array.</span></span>

- `pcMap`

  <span data-ttu-id="34655-108">\[out] o número total de estruturas de COR_DEBUG_IL_TO_NATIVE_MAP disponíveis.</span><span class="sxs-lookup"><span data-stu-id="34655-108">\[out] The total number of available COR_DEBUG_IL_TO_NATIVE_MAP structures.</span></span>

- `map`

  <span data-ttu-id="34655-109">\[out] uma matriz de estruturas [COR_DEBUG_IL_TO_NATIVE_MAP](../debugging/cor-debug-il-to-native-map-structure.md) , cada uma delas especifica os deslocamentos.</span><span class="sxs-lookup"><span data-stu-id="34655-109">\[out] An array of [COR_DEBUG_IL_TO_NATIVE_MAP](../debugging/cor-debug-il-to-native-map-structure.md) structures, each of which specifies the offsets.</span></span> <span data-ttu-id="34655-110">Depois que o `GetILToNativeMapping3` método retornar, `map` conterá algumas ou todas as `COR_DEBUG_IL_TO_NATIVE_MAP` estruturas.</span><span class="sxs-lookup"><span data-stu-id="34655-110">After the `GetILToNativeMapping3` method returns, `map` will contain some or all of the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span>

## <a name="remarks"></a><span data-ttu-id="34655-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="34655-111">Remarks</span></span>

<span data-ttu-id="34655-112">Quando a compilação em camadas está habilitada, um método pode ter mais de um corpo de código nativo.</span><span class="sxs-lookup"><span data-stu-id="34655-112">When tiered compilation is enabled, a method may have more than one native code body.</span></span> <span data-ttu-id="34655-113">[ICorProfilerInfo9:: GetNativeCodeStartAddresses](icorprofilerinfo9-getnativecodestartaddresses-method.md) retornará os endereços iniciais para todos os corpos de código nativos.</span><span class="sxs-lookup"><span data-stu-id="34655-113">[ICorProfilerInfo9::GetNativeCodeStartAddresses](icorprofilerinfo9-getnativecodestartaddresses-method.md) will return the start addresses for all of the native code bodies.</span></span>

## <a name="requirements"></a><span data-ttu-id="34655-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="34655-114">Requirements</span></span>

<span data-ttu-id="34655-115">**Plataformas:** Consulte [sistemas operacionais com suporte do .NET Core](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="34655-115">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>

<span data-ttu-id="34655-116">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="34655-116">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="34655-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="34655-117">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="34655-118">**.NET Framework versões:**[!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34655-118">**.NET Framework Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="34655-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="34655-119">See also</span></span>

- [<span data-ttu-id="34655-120">Interface ICorProfilerInfo9</span><span class="sxs-lookup"><span data-stu-id="34655-120">ICorProfilerInfo9 Interface</span></span>](icorprofilerinfo9-interface.md)
