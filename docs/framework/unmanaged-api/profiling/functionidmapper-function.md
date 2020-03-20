---
title: Função FunctionIDMapper
ms.date: 03/30/2017
api_name:
- FunctionIDMapper
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionIDMapper
helpviewer_keywords:
- FunctionIDMapper function [.NET Framework profiling]
ms.assetid: b8205b60-1893-4303-8cff-7ac5a00892aa
topic_type:
- apiref
ms.openlocfilehash: 0cf2014d7007593c51868eff0b488fdab136e362
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175168"
---
# <a name="functionidmapper-function"></a>Função FunctionIDMapper
Notifica o profiler de que o identificador dado de uma função pode ser remapped para um ID alternativo a ser usado nos [retornos de functionEnter2,](functionenter2-function.md) [FunctionLeave2](functionleave2-function.md)e [FunctionTailcall2](functiontailcall2-function.md) para essa função. `FunctionIDMapper`também permite que o profiler indique se ele quer receber retornos para essa função.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
UINT_PTR __stdcall FunctionIDMapper (  
    [in]  FunctionID  funcId,
    [out] BOOL       *pbHookFunction  
);  
```  
  
## <a name="parameters"></a>parâmetros

- `funcId`

  \[em] O identificador de função a ser remapeado.

- `pbHookFunction`

  \[fora] Um ponteiro para um valor `true` que o profiler `FunctionLeave2`define `FunctionTailcall2` para se ele quiser receber `FunctionEnter2`, e retornos de chamada; caso contrário, ele define `false`esse valor para .

## <a name="return-value"></a>Valor retornado  
 O profiler retorna um valor que o mecanismo de execução usa como um identificador de função alternativa. O valor de devolução não pode ser nulo a menos que `false` seja devolvido em `pbHookFunction`. Caso contrário, um valor de retorno nulo produzirá resultados imprevisíveis, incluindo possivelmente interromper o processo.  
  
## <a name="remarks"></a>Comentários  
 A `FunctionIDMapper` função é um retorno de chamada. Ele é implementado pelo profiler para remapear um ID de função para algum outro identificador que seja mais útil para o profiler. O `FunctionIDMapper` retorno do ID alternativo a ser usado para qualquer função. O motor de execução então honra o pedido do profiler, passando este ID alternativo, além `clientData` do ID `FunctionEnter2` `FunctionLeave2`de `FunctionTailcall2` função tradicional, de volta ao profiler no parâmetro do , e ganchos, para identificar a função para a qual o gancho está sendo chamado.  
  
 Você pode usar o método [ICorProfilerInfo::SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md) `FunctionIDMapper` para especificar a implementação da função. Você pode `ICorProfilerInfo::SetFunctionIDMapper` chamar o método apenas uma vez, e recomendamos que você o faça no [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) callback.  
  
 Por padrão, supõe-se que um profiler que define o COR_PRF_MONITOR_ENTERLEAVE flag usando [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md), e que define ganchos via [ICorProfilerInfo::SetEnterLeaveFunctionHooks](icorprofilerinfo-setenterleavefunctionhooks-method.md) `FunctionLeave2`ou `FunctionTailcall2` [ICorProfilerInfo2:SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md), deve receber os `FunctionEnter2`, e retornos de chamadas para cada função. No entanto, os `FunctionIDMapper` profilers podem implementar para evitar seletivamente `pbHookFunction` `false`receber esses retornos de chamadas para determinadas funções, configurando para .  
  
 Os profilers devem ser tolerantes aos casos em que vários segmentos de um aplicativo perfilado estão chamando o mesmo método/função simultaneamente. Nesses casos, o profiler `FunctionIDMapper` pode receber vários `FunctionID`retornos de chamada para o mesmo . O profiler deve ter certeza de retornar os mesmos valores a `FunctionID`partir deste retorno de chamada quando for chamado várias vezes com o mesmo .  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Método SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md)
- [Função FunctionIDMapper2](functionidmapper2-function.md)
- [Função FunctionEnter2](functionenter2-function.md)
- [Função FunctionLeave2](functionleave2-function.md)
- [Função FunctionTailcall2](functiontailcall2-function.md)
- [Criando perfil de funções estáticas globais](profiling-global-static-functions.md)
