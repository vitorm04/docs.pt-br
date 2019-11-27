---
title: Método ICorProfilerInfo::SetILInstrumentedCodeMap
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetILInstrumentedCodeMap
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetILInstrumentedCodeMap
helpviewer_keywords:
- ICorProfilerInfo::SetILInstrumentedCodeMap method [.NET Framework profiling]
- SetILInstrumentedCodeMap method [.NET Framework profiling]
ms.assetid: bce1dcf8-b4ec-4e73-a917-f2df1ad49c8a
topic_type:
- apiref
ms.openlocfilehash: 32e63a6d2b6f739025d4c5558c16fe2d74fde73c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449872"
---
# <a name="icorprofilerinfosetilinstrumentedcodemap-method"></a>Método ICorProfilerInfo::SetILInstrumentedCodeMap

Define um mapa de código para a função especificada usando as entradas de mapa da MSIL (Microsoft Intermediate Language) especificadas.

> [!NOTE]
> No .NET Framework versão 2,0, a chamada de `SetILInstrumentedCodeMap` em um `FunctionID` que representa uma função genérica em um domínio de aplicativo específico afetará todas as instâncias dessa função no domínio do aplicativo.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT SetILInstrumentedCodeMap(
    [in]  FunctionID functionId,
    [in]  BOOL       fStartJit,
    [in]  ULONG      cILMapEntries,
    [in, size_is(cILMapEntries)] COR_IL_MAP rgILMapEntries[]);
```

## <a name="parameters"></a>Parâmetros

`functionId`\
no A ID da função para a qual definir o mapa de código.

`fStartJit`\
no Um valor booliano que indica se a chamada para o método `SetILInstrumentedCodeMap` é a primeira para um `FunctionID`específico. Defina `fStartJit` como `true` na primeira chamada para `SetILInstrumentedCodeMap` para um determinado `FunctionID`e para `false` daí em diante.

`cILMapEntries`\
no O número de elementos na matriz de `cILMapEntries`.

`rgILMapEntries`\
no Uma matriz de estruturas COR_IL_MAP, cada uma delas especifica um deslocamento MSIL.

## <a name="remarks"></a>Comentários

Um criador de perfil geralmente insere instruções no código-fonte de um método para instrumentar esse método (por exemplo, para notificar quando uma determinada linha de origem for atingida). `SetILInstrumentedCodeMap` permite que um criador de perfil Mapeie as instruções originais do MSIL para seus novos locais. Um criador de perfil pode usar o método [ICorProfilerInfo:: GetILToNativeMapping](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md) para obter o deslocamento de MSIL original para um determinado deslocamento nativo.

O depurador assumirá que cada deslocamento antigo se refere a um deslocamento MSIL dentro do código MSIL original e não modificado, e que cada deslocamento novo se refere ao deslocamento MSIL dentro do novo código instrumentado. O mapa deve ser classificado em ordem crescente. Para que a depuração funcione corretamente, siga estas diretrizes:

- Não reordene o código MSIL instrumentado.

- Não remova o código MSIL original.

- Inclua entradas para todos os pontos de sequência do arquivo de banco de dados do programa (PDB) no mapa. O mapa não interpola as entradas ausentes. Portanto, considerando o seguinte mapa:

  (0 antigo, 0 novo)

  (5 antigos, 10 novos)

  (9 antigos, 20 novos)

  - Um deslocamento antigo de 0, 1, 2, 3 ou 4 será mapeado para o novo deslocamento 0.

  - Um deslocamento antigo de 5, 6, 7 ou 8 será mapeado para o novo deslocamento 10.

  - Um deslocamento antigo de 9 ou superior será mapeado para o novo deslocamento 20.

  - Um novo deslocamento de 0, 1, 2, 3, 4, 5, 6, 7, 8 ou 9 será mapeado para o deslocamento antigo 0.

  - Um novo deslocamento de 10, 11, 12, 13, 14, 15, 16, 17, 18 ou 19 será mapeado para o deslocamento antigo 5.

  - Um novo deslocamento de 20 ou mais será mapeado para o deslocamento antigo 9.

No .NET Framework 3,5 e versões anteriores, você aloca a matriz de `rgILMapEntries` chamando o método [CoTaskMemAlloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemalloc) . Como o tempo de execução se apropria dessa memória, o criador de perfil não deve tentar liberá-la.

## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}

**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).

**Cabeçalho:** CorProf. idl, CorProf. h

**Biblioteca:** CorGuids.lib

**Versões do .NET Framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]

## <a name="see-also"></a>Consulte também

- [Interface ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
