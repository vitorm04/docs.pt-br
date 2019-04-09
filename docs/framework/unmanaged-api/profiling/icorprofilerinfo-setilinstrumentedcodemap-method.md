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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3a574a04e5746a8b2c9c32160e82aa503b392729
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59154187"
---
# <a name="icorprofilerinfosetilinstrumentedcodemap-method"></a>Método ICorProfilerInfo::SetILInstrumentedCodeMap
Define um mapa de código para a função especificada usando as entradas de mapa especificadas Microsoft intermediate language (MSIL).  
  
> [!NOTE]
>  No .NET Framework versão 2.0, chamando `SetILInstrumentedCodeMap` em um `FunctionID` que representa um genérico de função em um domínio de aplicativo específico afetará todas as instâncias dessa função no domínio do aplicativo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT SetILInstrumentedCodeMap(  
    [in]  FunctionID functionId,  
    [in]  BOOL       fStartJit,  
    [in]  ULONG      cILMapEntries,  
    [in, size_is(cILMapEntries)] COR_IL_MAP rgILMapEntries[]);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `functionId`  
 [in] A ID da função para o qual definir o mapa de código.  
  
 `fStartJit`  
 [in] Um valor booliano que indica se a chamada para o `SetILInstrumentedCodeMap` método é o primeiro para um determinado `FunctionID`. Definir `fStartJit` à `true` na primeira chamada para `SetILInstrumentedCodeMap` para um determinado `FunctionID`e, ao `false` daí em diante.  
  
 `cILMapEntries`  
 [in] O número de elementos no `cILMapEntries` matriz.  
  
 `rgILMapEntries`  
 [in] Uma matriz de estruturas COR_IL_MAP, cada um deles especifica um deslocamento do MSIL.  
  
## <a name="remarks"></a>Comentários  
 Um criador de perfil geralmente insere instruções dentro do código-fonte de um método para instrumentar o método (por exemplo, para notificar quando uma linha de origem especificado for atingida). `SetILInstrumentedCodeMap` permite que um criador de perfil mapear as instruções MSIL originais para seus novos locais. Um criador de perfil pode usar o [ICorProfilerInfo:: Getiltonativemapping](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md) método para obter o deslocamento do MSIL original para um determinado deslocamento nativo.  
  
 O depurador assumirá que cada deslocamento antigo se refere a um deslocamento dentro do código MSIL original, sem modificações de MSIL, e cada novo deslocamento refere-se para o deslocamento do MSIL dentro do código novo, instrumentado. O mapa deve ser classificado em ordem crescente. Para depuração funcione corretamente, siga estas diretrizes:  
  
-   Não reorganize o código instrumentado de MSIL.  
  
-   Não remova o código MSIL original.  
  
-   Inclua entradas para todos os pontos de sequência do arquivo de banco de dados (PDB) de programa no mapa. O mapa não interpola entradas ausentes. Então, como o mapa a seguir:  
  
     (0 antigo, 0 novos)  
  
     (5 antigo, 10 novos)  
  
     (9 antigo, 20 novas)  
  
    -   Um deslocamento antigo de 0, 1, 2, 3 ou 4 será mapeado para o novo deslocamento 0.  
  
    -   Um deslocamento antigo de 5, 6, 7 ou 8 será mapeado para o novo deslocamento de 10.  
  
    -   Um deslocamento antigo de 9 ou superior será mapeado para o novo deslocamento 20.  
  
    -   Um novo deslocamento de 0, 1, 2, 3, 4, 5, 6, 7, 8 ou 9 será mapeado para o deslocamento antigo 0.  
  
    -   Um novo deslocamento de 10, 11, 12, 13, 14, 15, 16, 17, 18 ou 19 será mapeado para o deslocamento antigo 5.  
  
    -   Um novo deslocamento de 20 ou superior será mapeado para o deslocamento antigo 9.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
