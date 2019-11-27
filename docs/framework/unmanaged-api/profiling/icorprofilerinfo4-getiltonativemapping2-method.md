---
title: Método ICorProfilerInfo4::GetILToNativeMapping2
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetILToNativeMapping2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetILToNativeMapping2
helpviewer_keywords:
- ICorProfilerInfo4::GetILToNativeMapping2 method [.NET Framework profiling]
- GetILToNativeMapping2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 756c1c25-08a7-4060-9798-dbeaa2f3bee5
topic_type:
- apiref
ms.openlocfilehash: dfce86e95ba41a65e72524546072244a47f8360c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74442927"
---
# <a name="icorprofilerinfo4getiltonativemapping2-method"></a>Método ICorProfilerInfo4::GetILToNativeMapping2
Obtém um mapa de deslocamentos de MSIL (Microsoft Intermediate Language) para deslocamentos nativos do código contido na versão recompilada do JIT da função especificada.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetILToNativeMapping(  
    [in] FunctionID functionId,  
    [in] ReJITID reJitId,  
    [in] ULONG32 cMap,  
    [out] ULONG32 *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `functionId`  
 no A ID da função que contém o código.  
  
 `pReJitId`  
 no A identidade da função de compilação JIT recompilada. A identidade deve ser zero no .NET Framework 4,5.  
  
 `cMap`  
 no O tamanho máximo da matriz de `map`.  
  
 `pcMap`  
 fora O número total de estruturas de COR_DEBUG_IL_TO_NATIVE_MAP disponíveis.  
  
 `map`  
 fora Uma matriz de estruturas `COR_DEBUG_IL_TO_NATIVE_MAP`, cada uma delas especifica os deslocamentos. Depois que o método `GetILToNativeMapping2` retornar, `map` conterá algumas ou todas as estruturas de `COR_DEBUG_IL_TO_NATIVE_MAP`.  
  
## <a name="remarks"></a>Comentários  
 `GetILToNativeMapping2` é semelhante ao método [ICorProfilerInfo:: GetILToNativeMapping](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md) , exceto pelo fato de que ele permitirá que o criador de perfil ESPECIFIQUE a ID da função recompilada em versões futuras.  
  
> [!NOTE]
> O método [ICorProfilerFunctionControl:: SetILInstrumentedCodeMap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setilinstrumentedcodemap-method.md) não está implementado no .NET Framework 4,5, portanto, as funções que foram recompiladas por JIT não podem ter um mapeamento de Il para nativo diferente da função compilada originalmente. Dessa forma, `GetILToNativeMapping2` não pode ser chamado com uma ID de compilação JIT diferente de zero no .NET Framework 4,5.  
  
 O método `GetILToNativeMapping2` retorna uma matriz de estruturas de `COR_DEBUG_IL_TO_NATIVE_MAP`. Para transmitir que determinados intervalos de instruções nativas correspondem a regiões especiais de código (por exemplo, o prólogo), uma entrada na matriz pode ter seu campo `ilOffset` definido como um valor da enumeração [CorDebugIlToNativeMappingTypes](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md) .  
  
 Depois que `GetILToNativeMapping2` retorna, você deve verificar se o buffer de `map` era grande o suficiente para conter todas as estruturas de `COR_DEBUG_IL_TO_NATIVE_MAP`. Para fazer isso, compare o valor de `cMap` com o valor do parâmetro `pcMap`. Se o valor de `pcMap`, quando for multiplicado pelo tamanho de uma estrutura de `COR_DEBUG_IL_TO_NATIVE_MAP`, for maior que `cMap`, aloque um buffer de `map` maior, atualize `cMap` com o tamanho novo, maior e chame `GetILToNativeMapping2` novamente.  
  
 Como alternativa, você pode primeiro chamar `GetILToNativeMapping2` com um buffer de `map` de comprimento zero para obter o tamanho de buffer correto. Em seguida, você pode definir o tamanho do buffer para o valor retornado em `pcMap` e chamar `GetILToNativeMapping2` novamente.  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Método GetILToNativeMapping](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md)
- [Interface ICorProfilerInfo4](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [Interfaces de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Criação de perfil](../../../../docs/framework/unmanaged-api/profiling/index.md)
