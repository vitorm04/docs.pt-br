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
ms.openlocfilehash: b625b2962c829e7c0692a61d8f5561818f7ebf1e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62000513"
---
# <a name="icorprofilerinfo4getiltonativemapping2-method"></a>Método ICorProfilerInfo4::GetILToNativeMapping2
Obtém um mapa da Microsoft intermediate language (MSIL) deslocamentos para deslocamentos nativos para o código contido na versão recompilado por JIT da função especificada.  
  
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
  
## <a name="parameters"></a>Parâmetros  
 `functionId`  
 [in] A ID da função que contém o código.  
  
 `pReJitId`  
 [in] A identidade da função recompilado por JIT. A identidade deve ser zero no [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)].  
  
 `cMap`  
 [in] O tamanho máximo da `map` matriz.  
  
 `pcMap`  
 [out] O número total de estruturas COR_DEBUG_IL_TO_NATIVE_MAP disponíveis.  
  
 `map`  
 [out] Uma matriz de `COR_DEBUG_IL_TO_NATIVE_MAP` estruturas, cada um deles especifica os deslocamentos. Após o `GetILToNativeMapping2` método retorna, `map` irá conter algumas ou todas as `COR_DEBUG_IL_TO_NATIVE_MAP` estruturas.  
  
## <a name="remarks"></a>Comentários  
 `GetILToNativeMapping2` é semelhante para o [ICorProfilerInfo:: Getiltonativemapping](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md) método, exceto que ele permitirá que o criador de perfil especificar a ID da função recompilada em futuras versões.  
  
> [!NOTE]
>  O [icorprofilerfunctioncontrol:: Setilinstrumentedcodemap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setilinstrumentedcodemap-method.md) método não está implementado de [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], portanto, as funções que tenham sido recompilado por JIT não podem ter um mapeamento de IL para nativo que é diferente do originalmente função compilada. Como tal, `GetILToNativeMapping2` não pode ser chamado com uma ID diferente de zero recompilado por JIT no [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)].  
  
 O `GetILToNativeMapping2` método retorna uma matriz de `COR_DEBUG_IL_TO_NATIVE_MAP` estruturas. Para transmitir que determinados intervalos de instruções nativas correspondem a regiões especiais do código (por exemplo, o prólogo), uma entrada na matriz pode ter sua `ilOffset` campo definido como um valor de [CorDebugIlToNativeMappingTypes](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md) enumeração.  
  
 Após `GetILToNativeMapping2` é retornado, você deve verificar se o `map` buffer era grande o suficiente para conter todos o `COR_DEBUG_IL_TO_NATIVE_MAP` estruturas. Para fazer isso, comparar o valor de `cMap` com o valor da `pcMap` parâmetro. Se o `pcMap` valor, quando ele é multiplicado pelo tamanho de um `COR_DEBUG_IL_TO_NATIVE_MAP` estrutura, é maior que `cMap`, alocar uma maior `map` do buffer, atualize `cMap` com o novo e maior tamanho e a chamada `GetILToNativeMapping2` novamente.  
  
 Como alternativa, você pode primeiro chamar `GetILToNativeMapping2` com um comprimento de zero `map` buffer para obter o tamanho do buffer correto. Em seguida, você pode definir o tamanho do buffer para o valor retornado em `pcMap` e chamar `GetILToNativeMapping2` novamente.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Método GetILToNativeMapping](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md)
- [Interface ICorProfilerInfo4](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [Interfaces de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Criação de perfil](../../../../docs/framework/unmanaged-api/profiling/index.md)
