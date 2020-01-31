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
# <a name="icorprofilerinfo9getiltonativemapping3-method"></a>Método ICorProfilerInfo9:: GetILToNativeMapping3

Dado o endereço de início do código nativo, retorna as informações de mapeamento nativo para IL para essa versão JIT do código.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetILToNativeMapping3( [in]  UINT_PTR pNativeCodeStartAddress,
                               [in]  ULONG32 cMap,
                               [out] ULONG32 *pcMap,
                               [out] COR_DEBUG_IL_TO_NATIVE_MAP map[]);
```

## <a name="parameters"></a>Parâmetros

- `pNativeCodeStartAddress`

  \[em] um ponteiro para o início de uma função nativa.

- `cMap`

  \[em] o tamanho máximo da matriz de `map`.

- `pcMap`

  \[out] o número total de estruturas de COR_DEBUG_IL_TO_NATIVE_MAP disponíveis.

- `map`

  \[out] uma matriz de estruturas de [COR_DEBUG_IL_TO_NATIVE_MAP](../debugging/cor-debug-il-to-native-map-structure.md) , cada uma delas especifica os deslocamentos. Depois que o método `GetILToNativeMapping3` retornar, `map` conterá algumas ou todas as estruturas de `COR_DEBUG_IL_TO_NATIVE_MAP`.

## <a name="remarks"></a>Comentários

Quando a compilação em camadas está habilitada, um método pode ter mais de um corpo de código nativo. [ICorProfilerInfo9:: GetNativeCodeStartAddresses](icorprofilerinfo9-getnativecodestartaddresses-method.md) retornará os endereços iniciais para todos os corpos de código nativos.

## <a name="requirements"></a>Requisitos do

**Plataformas:** Consulte [sistemas operacionais com suporte do .NET Core](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).

**Cabeçalho:** CorProf. idl, CorProf. h

**Biblioteca:** CorGuids.lib

**Versões do .NET Framework:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]

## <a name="see-also"></a>Veja também

- [Interface ICorProfilerInfo9](icorprofilerinfo9-interface.md)
