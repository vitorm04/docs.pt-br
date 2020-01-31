---
title: Método ICorProfilerInfo::GetILToNativeMapping
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetILToNativeMapping
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetILToNativeMapping
helpviewer_keywords:
- GetILToNativeMapping method, ICorProfilerInfo interface [.NET Framework profiling]
- ICorProfilerInfo::GetILToNativeMapping method [.NET Framework profiling]
ms.assetid: 6a5431ef-22fb-4e53-bac5-703986297eb1
topic_type:
- apiref
ms.openlocfilehash: f9abb3ae9cd3f9c70485e584399a6ed32b32a572
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76870593"
---
# <a name="icorprofilerinfogetiltonativemapping-method"></a>Método ICorProfilerInfo::GetILToNativeMapping
Obtém um mapa de deslocamentos de MSIL (Microsoft Intermediate Language) para deslocamentos nativos do código contido na função especificada.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetILToNativeMapping(  
    [in] FunctionID functionId,  
    [in] ULONG32 cMap,  
    [out] ULONG32 *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `functionId`  
 no A ID da função que contém o código.  
  
 `cMap`  
 no O tamanho máximo da matriz de `map`.  
  
 `pcMap`  
 fora O número total de estruturas de COR_DEBUG_IL_TO_NATIVE_MAP disponíveis.  
  
 `map`  
 fora Uma matriz de estruturas `COR_DEBUG_IL_TO_NATIVE_MAP`, cada uma delas especifica os deslocamentos. Depois que o método `GetILToNativeMapping` retornar, `map` conterá algumas ou todas as estruturas de `COR_DEBUG_IL_TO_NATIVE_MAP`.  
  
## <a name="remarks"></a>Comentários  
 O método `GetILToNativeMapping` retorna uma matriz de estruturas de `COR_DEBUG_IL_TO_NATIVE_MAP`. Para transmitir que determinados intervalos de instruções nativas correspondem a regiões especiais de código (por exemplo, o prólogo), uma entrada na matriz pode ter seu campo `ilOffset` definido como um valor da enumeração [CorDebugIlToNativeMappingTypes](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md) .  
  
 Depois que `GetILToNativeMapping` retorna, você deve verificar se o buffer de `map` era grande o suficiente para conter todas as estruturas de `COR_DEBUG_IL_TO_NATIVE_MAP`. Para fazer isso, compare o valor de `cMap` com o valor do parâmetro `pcMap`. Se o valor de `pcMap`, quando for multiplicado pelo tamanho de uma estrutura de `COR_DEBUG_IL_TO_NATIVE_MAP`, for maior que `cMap`, aloque um buffer de `map` maior, atualize `cMap` com o tamanho novo, maior e chame `GetILToNativeMapping` novamente.  
  
 Como alternativa, você pode primeiro chamar `GetILToNativeMapping` com um buffer de `map` de comprimento zero para obter o tamanho de buffer correto. Em seguida, você pode definir o tamanho do buffer para o valor retornado em `pcMap` e chamar `GetILToNativeMapping` novamente.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorProfilerInfo](icorprofilerinfo-interface.md)
- [Método GetILToNativeMapping2](icorprofilerinfo4-getiltonativemapping2-method.md)
- [Interfaces de criação de perfil](profiling-interfaces.md)
- [Criação de perfil](index.md)
