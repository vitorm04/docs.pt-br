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
ms.openlocfilehash: 9e8e4c7e6c367970100c98dc3dc8237b25f99221
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69665609"
---
# <a name="icorprofilerinfo9getiltonativemapping3-method"></a><span data-ttu-id="0ecba-102">Método ICorProfilerInfo9:: GetILToNativeMapping3</span><span class="sxs-lookup"><span data-stu-id="0ecba-102">ICorProfilerInfo9::GetILToNativeMapping3 Method</span></span>

<span data-ttu-id="0ecba-103">Dado o endereço de início do código nativo, retorna as informações de mapeamento nativo para IL para essa versão JIT do código.</span><span class="sxs-lookup"><span data-stu-id="0ecba-103">Given the native code start address, returns the native to IL mapping information for this jitted version of the code.</span></span>

## <a name="syntax"></a><span data-ttu-id="0ecba-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0ecba-104">Syntax</span></span>

```cpp
HRESULT GetILToNativeMapping3( [in]  UINT_PTR pNativeCodeStartAddress,
                               [in]  ULONG32 cMap,
                               [out] ULONG32 *pcMap,
                               [out] COR_DEBUG_IL_TO_NATIVE_MAP map[]);
```

#### <a name="parameters"></a><span data-ttu-id="0ecba-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ecba-105">Parameters</span></span>

`pNativeCodeStartAddress` \
<span data-ttu-id="0ecba-106">no Um ponteiro para o início de uma função nativa.</span><span class="sxs-lookup"><span data-stu-id="0ecba-106">[in] A pointer to the start of a native function.</span></span>

`cMap` \
<span data-ttu-id="0ecba-107">no O tamanho máximo da `map` matriz.</span><span class="sxs-lookup"><span data-stu-id="0ecba-107">[in] The maximum size of the `map` array.</span></span>

`pcMap` \
<span data-ttu-id="0ecba-108">fora O número total de estruturas COR_DEBUG_IL_TO_NATIVE_MAP disponíveis.</span><span class="sxs-lookup"><span data-stu-id="0ecba-108">[out] The total number of available COR_DEBUG_IL_TO_NATIVE_MAP structures.</span></span>

`map` \
<span data-ttu-id="0ecba-109">fora Uma matriz de estruturas [COR_DEBUG_IL_TO_NATIVE_MAP](../debugging/cor-debug-il-to-native-map-structure.md) , cada uma delas especifica os deslocamentos.</span><span class="sxs-lookup"><span data-stu-id="0ecba-109">[out] An array of [COR_DEBUG_IL_TO_NATIVE_MAP](../debugging/cor-debug-il-to-native-map-structure.md) structures, each of which specifies the offsets.</span></span> <span data-ttu-id="0ecba-110">Depois que `GetILToNativeMapping3` o método retornar `map` , conterá `COR_DEBUG_IL_TO_NATIVE_MAP` algumas ou todas as estruturas.</span><span class="sxs-lookup"><span data-stu-id="0ecba-110">After the `GetILToNativeMapping3` method returns, `map` will contain some or all of the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span>

## <a name="remarks"></a><span data-ttu-id="0ecba-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="0ecba-111">Remarks</span></span>

<span data-ttu-id="0ecba-112">Quando a compilação em camadas está habilitada, um método pode ter mais de um corpo de código nativo.</span><span class="sxs-lookup"><span data-stu-id="0ecba-112">When tiered compilation is enabled, a method may have more than one native code body.</span></span> <span data-ttu-id="0ecba-113">[ICorProfilerInfo9:: GetNativeCodeStartAddresses](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-getnativecodestartaddresses-method.md) retornará os endereços iniciais para todos os corpos de código nativos.</span><span class="sxs-lookup"><span data-stu-id="0ecba-113">[ICorProfilerInfo9::GetNativeCodeStartAddresses](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-getnativecodestartaddresses-method.md) will return the start addresses for all of the native code bodies.</span></span>

## <a name="requirements"></a><span data-ttu-id="0ecba-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0ecba-114">Requirements</span></span>

<span data-ttu-id="0ecba-115">**Compatíveis** Consulte [sistemas operacionais com suporte do .NET Core](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span><span class="sxs-lookup"><span data-stu-id="0ecba-115">**Platforms:** See [.NET Core supported operating systems](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span></span>

<span data-ttu-id="0ecba-116">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0ecba-116">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="0ecba-117">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0ecba-117">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="0ecba-118">**Versões do .NET Framework:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ecba-118">**.NET Framework Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="0ecba-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ecba-119">See also</span></span>

- [<span data-ttu-id="0ecba-120">Interface ICorProfilerInfo9</span><span class="sxs-lookup"><span data-stu-id="0ecba-120">ICorProfilerInfo9 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-interface.md)
