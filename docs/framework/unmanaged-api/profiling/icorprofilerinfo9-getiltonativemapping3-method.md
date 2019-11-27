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
ms.openlocfilehash: 1a5a259e6604d906e55166b3fcb770bc37d346c5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444727"
---
# <a name="icorprofilerinfo9getiltonativemapping3-method"></a>Método ICorProfilerInfo9:: GetILToNativeMapping3

Dado o endereço de início do código nativo, retorna as informações de mapeamento nativo para IL para essa versão JIT do código.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetILToNativeMapping3( [in]  UINT_PTR pNativeCodeStartAddress,
                               [in]  ULONG32 cMap,
                               [out] ULONG32 *pcMap,
                               [out] COR_DEBUG_IL_TO_NATIVE_MAP map[]);
```

#### <a name="parameters"></a>Parâmetros

`pNativeCodeStartAddress` \
no Um ponteiro para o início de uma função nativa.

`cMap` \
no O tamanho máximo da matriz de `map`.

`pcMap` \
fora O número total de estruturas de COR_DEBUG_IL_TO_NATIVE_MAP disponíveis.

`map` \
fora Uma matriz de estruturas [COR_DEBUG_IL_TO_NATIVE_MAP](../debugging/cor-debug-il-to-native-map-structure.md) , cada uma delas especifica os deslocamentos. Depois que o método `GetILToNativeMapping3` retornar, `map` conterá algumas ou todas as estruturas de `COR_DEBUG_IL_TO_NATIVE_MAP`.

## <a name="remarks"></a>Comentários

Quando a compilação em camadas está habilitada, um método pode ter mais de um corpo de código nativo. [ICorProfilerInfo9:: GetNativeCodeStartAddresses](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-getnativecodestartaddresses-method.md) retornará os endereços iniciais para todos os corpos de código nativos.

## <a name="requirements"></a>Requisitos

**Plataformas:** Consulte [sistemas operacionais com suporte do .NET Core](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).

**Cabeçalho:** CorProf. idl, CorProf. h

**Biblioteca:** CorGuids.lib

**Versões do .NET Framework:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]

## <a name="see-also"></a>Consulte também

- [Interface ICorProfilerInfo9](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-interface.md)
