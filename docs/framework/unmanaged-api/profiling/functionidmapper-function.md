---
title: "Função FunctionIDMapper"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: FunctionIDMapper
api_location: mscorwks.dll
api_type: COM
f1_keywords: FunctionIDMapper
helpviewer_keywords: FunctionIDMapper function [.NET Framework profiling]
ms.assetid: b8205b60-1893-4303-8cff-7ac5a00892aa
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 629bcd5085169fcb136884c53434c29d385642cd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="functionidmapper-function"></a>Função FunctionIDMapper
Notifica o criador de perfil que o identificador especificado de uma função pode ser mapeado novamente para uma ID alternativa a ser usado no [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md), e [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) retornos de chamada para essa função. `FunctionIDMapper`também permite que o criador de perfil indicar se deseja receber retornos de chamada para essa função.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
UINT_PTR __stdcall FunctionIDMapper (  
    [in]  FunctionID  funcId,   
    [out] BOOL       *pbHookFunction  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `funcId`  
 [in] O identificador de função a ser remapeados.  
  
 `pbHookFunction`  
 [out] Um ponteiro para um valor que define o criador de perfil para `true` se deseja receber `FunctionEnter2`, `FunctionLeave2`, e `FunctionTailcall2` retornos de chamada; caso contrário, ele define esse valor como `false`.  
  
## <a name="return-value"></a>Valor de retorno  
 O criador de perfil retorna um valor que usa o mecanismo de execução como um identificador de função alternativos. O valor de retorno não pode ser nulo, a menos que `false` é retornado no `pbHookFunction`. Caso contrário, um valor de retorno nulo produzirá resultados imprevisíveis, incluindo possivelmente interromper o processo.  
  
## <a name="remarks"></a>Comentários  
 O `FunctionIDMapper` função é um retorno de chamada. Ele é implementado pelo criador de perfil para remapear uma ID de função para outro identificador que é mais útil para o criador de perfil. O `FunctionIDMapper` retorna a ID alternativa a ser usado para qualquer função fornecida. O mecanismo de execução, em seguida, leva em conta a solicitação do criador de perfil, passando essa ID alternativo, além da ID de função tradicional, volta para o criador de perfil no `clientData` parâmetro o `FunctionEnter2`, `FunctionLeave2`, e `FunctionTailcall2` ganchos para identificar a função para a qual o gancho está sendo chamado.  
  
 Você pode usar o [: Setfunctionidmapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md) método para especificar a implementação de `FunctionIDMapper` função. Você pode chamar o `ICorProfilerInfo::SetFunctionIDMapper` método apenas uma vez e é recomendável que você faça isso no [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) retorno de chamada.  
  
 Por padrão, supõe-se que um criador de perfil que define o sinalizador COR_PRF_MONITOR_ENTERLEAVE usando [: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md), e que define ganchos via [Setenterleavefunctionhooks](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md) ou [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md), deve receber o `FunctionEnter2`, `FunctionLeave2`, e `FunctionTailcall2` retornos de chamada para cada função. No entanto, os criadores de perfil podem implementar `FunctionIDMapper` evitar seletivamente a receber esses retornos de chamada para determinadas funções definindo `pbHookFunction` para `false`.  
  
 Criadores de perfil devem ser tolerante a falhas de casos em que vários threads de um aplicativo de perfil estão chamando a método/função mesmo simultaneamente. Nesses casos, o criador de perfil pode receber vários `FunctionIDMapper` retornos de chamada para o mesmo `FunctionID`. O criador de perfil deve ser determinada retornar os mesmos valores desse retorno de chamada quando ele for chamado várias vezes com o mesmo `FunctionID`.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Método SetFunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)  
 [Função FunctionIDMapper2](../../../../docs/framework/unmanaged-api/profiling/functionidmapper2-function.md)  
 [Função FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)  
 [Função FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)  
 [Função FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)  
 [Funções estáticas globais de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
