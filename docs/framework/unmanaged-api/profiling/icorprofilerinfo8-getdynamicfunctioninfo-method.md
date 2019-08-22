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
ms.openlocfilehash: d59de04e6af6cfec473899e0a3edadcb3257d385
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69665688"
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

#### <a name="parameters"></a>Parâmetros

`functionId` \
no A ID da função para a qual recuperar informações.

`moduleId` \
no Um ponteiro para o módulo no qual a classe pai da função é definida.

`ppvSig` \
fora Um ponteiro para a assinatura da função.

`pbSig` \
fora Um ponteiro para a contagem de bytes para a assinatura de função.

`cchName` \
no O tamanho máximo da `wszName` matriz.

`pcchName` \
fora O número de caracteres na `wszName` matriz.

`wszName` \
fora Uma matriz `WCHAR` que é o nome da função, se existir uma.

## <a name="remarks"></a>Comentários

Determinados métodos, como stubs IL ou LCG, não têm metadados associados que podem ser recuperados usando as APIs [IMetaDataImport](../metadata/imetadataimport-interface.md) e [IMetaDataImport2](../metadata/imetadataimport2-interface.md) . Esses métodos podem ser encontrados por infilers por meio de ponteiros de instrução ou ouvindo [ICorProfilerCallback8::D ynamicmethodjitcompilationstarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md).

Essa API pode ser usada para recuperar informações sobre métodos dinâmicos, incluindo um nome amigável, se disponível.

## <a name="requirements"></a>Requisitos

**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).

**Cabeçalho:** CorProf.idl, CorProf.h

**Biblioteca** CorGuids.lib

**.NET Framework versões:** [! INCLUIR[net_current_v472plus](../../../../includes/net-current-v472plus.md)

## <a name="see-also"></a>Consulte também

- [Interface ICorProfilerInfo8](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-interface.md)
