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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fba81500749a16a59405edaaa2ee1d12d86229f2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerinfo4getiltonativemapping2-method"></a>Método ICorProfilerInfo4::GetILToNativeMapping2
Obtém um mapa do Microsoft intermediate language (MSIL) desloca para deslocamentos nativo para o código contido na versão recompilada JIT da função especificada.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetILToNativeMapping(  
    [in] FunctionID functionId,  
    [in] ReJITID reJitId,  
    [in] ULONG32 cMap,  
    [out] ULONG32 *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `functionId`  
 [in] A ID da função que contém o código.  
  
 `pReJitId`  
 [in] A identidade da função recompilado JIT. A identidade deve ser zero no [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)].  
  
 `cMap`  
 [in] O tamanho máximo da `map` matriz.  
  
 `pcMap`  
 [out] O número total de estruturas COR_DEBUG_IL_TO_NATIVE_MAP disponíveis.  
  
 `map`  
 [out] Uma matriz de `COR_DEBUG_IL_TO_NATIVE_MAP` estruturas, cada uma delas Especifica os deslocamentos. Após o `GetILToNativeMapping2` método retorna, `map` conterá alguns ou todos os `COR_DEBUG_IL_TO_NATIVE_MAP` estruturas.  
  
## <a name="remarks"></a>Comentários  
 `GetILToNativeMapping2` é semelhante do [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md) método, exceto que permitirá que o criador de perfil especificar a ID da função recompilada em futuras versões.  
  
> [!NOTE]
>  O [Icorprofilerfunctioncontrol](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setilinstrumentedcodemap-method.md) método não está implementado no [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], portanto, funções que tenham sido recompilado JIT não podem ter um mapeamento de IL nativa que difere do originalmente função compilada. Como tal, `GetILToNativeMapping2` não pode ser chamado com uma ID diferente de zero recompilado JIT no [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)].  
  
 O `GetILToNativeMapping2` método retorna uma matriz de `COR_DEBUG_IL_TO_NATIVE_MAP` estruturas. Para transmitir que determinados intervalos de instruções nativo correspondem às regiões especiais de código (por exemplo, o prólogo), uma entrada na matriz pode ter seu `ilOffset` campo definido como um valor de [CorDebugIlToNativeMappingTypes](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md) enumeração.  
  
 Depois de `GetILToNativeMapping2` retorna, você deve verificar se o `map` buffer era grande o suficiente para conter todos o `COR_DEBUG_IL_TO_NATIVE_MAP` estruturas. Para fazer isso, comparar o valor de `cMap` com o valor de `pcMap` parâmetro. Se o `pcMap` valor, quando ele é multiplicado pelo tamanho de um `COR_DEBUG_IL_TO_NATIVE_MAP` estrutura, é maior do que `cMap`, alocar uma maior `map` buffer, atualize `cMap` com o novo tamanho maior e chame `GetILToNativeMapping2` novamente.  
  
 Como alternativa, você pode primeiro chamar `GetILToNativeMapping2` com um comprimento zero `map` buffer para obter o tamanho do buffer correto. Você pode definir o tamanho do buffer para o valor retornado em `pcMap` e chame `GetILToNativeMapping2` novamente.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Método GetILToNativeMapping](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md)  
 [Interface ICorProfilerInfo4](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 [Interfaces de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Criação de perfil](../../../../docs/framework/unmanaged-api/profiling/index.md)
