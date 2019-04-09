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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d7bbf0e03fc69332f77f3ac34a399a96f638da3f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59206714"
---
# <a name="icorprofilerinfogetiltonativemapping-method"></a>Método ICorProfilerInfo::GetILToNativeMapping
Obtém um mapa da Microsoft intermediate language (MSIL) deslocamentos para deslocamentos nativos para o código contido na função especificada.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetILToNativeMapping(  
    [in] FunctionID functionId,  
    [in] ULONG32 cMap,  
    [out] ULONG32 *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `functionId`  
 [in] A ID da função que contém o código.  
  
 `cMap`  
 [in] O tamanho máximo da `map` matriz.  
  
 `pcMap`  
 [out] O número total de estruturas COR_DEBUG_IL_TO_NATIVE_MAP disponíveis.  
  
 `map`  
 [out] Uma matriz de `COR_DEBUG_IL_TO_NATIVE_MAP` estruturas, cada um deles especifica os deslocamentos. Após o `GetILToNativeMapping` método retorna, `map` irá conter algumas ou todas as `COR_DEBUG_IL_TO_NATIVE_MAP` estruturas.  
  
## <a name="remarks"></a>Comentários  
 O `GetILToNativeMapping` método retorna uma matriz de `COR_DEBUG_IL_TO_NATIVE_MAP` estruturas. Para transmitir que determinados intervalos de instruções nativas correspondem a regiões especiais do código (por exemplo, o prólogo), uma entrada na matriz pode ter sua `ilOffset` campo definido como um valor de [CorDebugIlToNativeMappingTypes](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md) enumeração.  
  
 Após `GetILToNativeMapping` é retornado, você deve verificar se o `map` buffer era grande o suficiente para conter todos o `COR_DEBUG_IL_TO_NATIVE_MAP` estruturas. Para fazer isso, comparar o valor de `cMap` com o valor da `pcMap` parâmetro. Se o `pcMap` valor, quando ele é multiplicado pelo tamanho de um `COR_DEBUG_IL_TO_NATIVE_MAP` estrutura, é maior que `cMap`, alocar uma maior `map` do buffer, atualize `cMap` com o novo e maior tamanho e a chamada `GetILToNativeMapping` novamente.  
  
 Como alternativa, você pode primeiro chamar `GetILToNativeMapping` com um comprimento de zero `map` buffer para obter o tamanho do buffer correto. Em seguida, você pode definir o tamanho do buffer para o valor retornado em `pcMap` e chamar `GetILToNativeMapping` novamente.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [Método GetILToNativeMapping2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getiltonativemapping2-method.md)
- [Criação de perfil de interfaces](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Criação de perfil](../../../../docs/framework/unmanaged-api/profiling/index.md)
