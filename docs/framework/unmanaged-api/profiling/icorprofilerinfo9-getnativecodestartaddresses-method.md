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
ms.openlocfilehash: ca1643dfa980fa647164accf6432082428124acb
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90541233"
---
# <a name="icorprofilerinfo9getnativecodestartaddresses-method"></a>Método ICorProfilerInfo9:: GetNativeCodeStartAddresses

Dada uma FunctionID e rejitId, enumera o endereço inicial do código de início de todas as versões com compilação JIT desse código que existem atualmente.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetNativeCodeStartAddresses( [in]  FunctionID functionID,
                                     [in]  ReJITID reJitId,
                                     [in]  ULONG32 cCodeStartAddresses,
                                     [out] ULONG32 *pcCodeStartAddresses,
                                     [out] UINT_PTR codeStartAddresses[]);
```

## <a name="parameters"></a>Parâmetros

- `functionId`

  \[in] a ID da função cujos endereços de início de código nativo devem ser retornados.

- `reJitId`

  \[in] a identidade da função de compilação JIT recompilada.

- `cCodeStartAddresses`

  \[in] o tamanho máximo da `codeStartAddresses` matriz.

- `pcCodeStartAddresses`

  \[out] o número de endereços disponíveis.

- `codeStartAddresses`

  \[out] uma matriz de `UINT_PTR` , cada uma delas é o endereço inicial de um corpo nativo para a função especificada.

## <a name="remarks"></a>Comentários

Quando a compilação em camadas está habilitada, uma função pode ter mais de um corpo de código nativo.

## <a name="requirements"></a>Requisitos

**Plataformas:** Consulte [sistemas operacionais com suporte do .NET Core](../../../core/install/windows.md?pivots=os-windows).

**Cabeçalho:** CorProf. idl, CorProf. h

**Biblioteca:** CorGuids.lib

**Versões do .net:**[!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]

## <a name="see-also"></a>Confira também

- [Interface ICorProfilerInfo9](icorprofilerinfo9-interface.md)
