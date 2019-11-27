---
title: Método ICorProfilerCallback::JITCompilationStarted
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITCompilationStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITCompilationStarted
helpviewer_keywords:
- JITCompilationStarted method [.NET Framework profiling]
- ICorProfilerCallback::JITCompilationStarted method [.NET Framework profiling]
ms.assetid: 31782b36-d311-4518-8f45-25f65385af5b
topic_type:
- apiref
ms.openlocfilehash: 96ab77a36c0a0bddda0fca342433666dd19082d3
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74426187"
---
# <a name="icorprofilercallbackjitcompilationstarted-method"></a>Método ICorProfilerCallback::JITCompilationStarted
Notifica o criador de perfil de que o compilador JIT (just-in-time) começou a compilar uma função.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT JITCompilationStarted(  
    [in] FunctionID functionId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `functionId`  
 no A ID da função para a qual a compilação está sendo iniciada.  
  
 `fIsSafeToBlock`  
 no Um valor que indica ao criador de perfil se o bloqueio afetará a operação do tempo de execução. O valor será `true` se o bloqueio puder fazer com que o tempo de execução aguarde até que o thread de chamada retorne deste retorno de chamada; caso contrário, `false`.  
  
 Embora um valor de `true` não danifique o tempo de execução, ele pode distorcer os resultados de criação de perfil.  
  
## <a name="remarks"></a>Comentários  
 É possível receber mais de um par de chamadas `JITCompilationStarted` e [ICorProfilerCallback:: JITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md) para cada função devido à maneira como o tempo de execução manipula construtores de classe. Por exemplo, o tempo de execução inicia o método A de compilação JIT a, mas o construtor de classe para a classe B precisa ser executado. Portanto, o tempo de execução JIT compila o construtor para a classe B e o executa. Enquanto o Construtor está em execução, ele faz uma chamada para o método A, o que faz com que o método A seja compilado em JIT novamente. Nesse cenário, a primeira compilação JIT do método A é interrompida. No entanto, ambas as tentativas de compilação JIT do método A são relatadas com eventos de compilação JIT. Se o criador de perfil substituir o código MSIL (Microsoft Intermediate Language) para o método A chamando o método [ICorProfilerInfo:: SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) , ele deverá fazer isso para ambos os eventos `JITCompilationStarted`, mas poderá usar o mesmo bloco MSIL para ambos.  
  
 Os profileres devem dar suporte à sequência de retornos de chamada JIT nos casos em que dois threads estão realizando retornos de chamada simultaneamente. Por exemplo, thread A chama `JITCompilationStarted`. No entanto, antes do thread A chamar `JITCompilationFinished`, thread B chama [ICorProfilerCallback:: ExceptionSearchFunctionEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md) com a ID da função do retorno de chamada `JITCompilationStarted` do thread A. Pode parecer que a ID da função ainda não deve ser válida porque uma chamada para `JITCompilationFinished` ainda não tinha sido recebida pelo criador de perfil. No entanto, em um caso como este, a ID da função é válida.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [Método JITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)
