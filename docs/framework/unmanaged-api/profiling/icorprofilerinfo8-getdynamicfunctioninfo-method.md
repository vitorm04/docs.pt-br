---
title: ICorProfilerInfo8::GetDynamicFunctionInfo
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo8.GetDynamicFunctionInfo
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 9b5059d9e4bf9b79dc67664c7a7971041d1cf35b
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76861678"
---
# <a name="icorprofilerinfo8getdynamicfunctioninfo-method"></a>Método ICorProfilerInfo8:: GetDynamicFunctionInfo

Recupera informações sobre métodos dinâmicos.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetDynamicFunctionInfo( [in]  FunctionID              functionId,
                                [out] ModuleID                *moduleId,
                                [out] PCCOR_SIGNATURE         *ppvSig,
                                [out] ULONG                   *pbSig,
                                [in]  ULONG                   cchName,
                                [out] ULONG                   *pcchName,
                                [out] WCHAR                   wszName[]);
```

## <a name="parameters"></a>Parâmetros

- `functionId`

  \[em] a ID da função para a qual recuperar informações.

- `moduleId`

  \[em] um ponteiro para o módulo no qual a classe pai da função é definida.

- `ppvSig`

  \[out] um ponteiro para a assinatura da função.

- `pbSig`

  \[out] um ponteiro para a contagem de bytes para a assinatura de função.

- `cchName`

  \[em] o tamanho máximo da matriz de `wszName`.

- `pcchName`

  \[out] o número de caracteres na matriz `wszName`.

- `wszName`

  \[out] uma matriz de `WCHAR` que é o nome da função, se existir uma.

## <a name="remarks"></a>Comentários

Determinados métodos, como stubs IL ou LCG, não têm metadados associados que podem ser recuperados usando as APIs [IMetaDataImport](../metadata/imetadataimport-interface.md) e [IMetaDataImport2](../metadata/imetadataimport2-interface.md) . Esses métodos podem ser encontrados por infilers por meio de ponteiros de instrução ou ouvindo [ICorProfilerCallback8::D ynamicmethodjitcompilationstarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md).

Essa API pode ser usada para recuperar informações sobre métodos dinâmicos, incluindo um nome amigável, se disponível.

## <a name="requirements"></a>Requisitos do

**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).

**Cabeçalho:** CorProf. idl, CorProf. h

**Biblioteca:** CorGuids.lib

**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Veja também

- [Interface ICorProfilerInfo8](icorprofilerinfo8-interface.md)
