---
title: "Método ICorProfilerCallback::JITCompilationStarted"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.JITCompilationStarted
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::JITCompilationStarted
helpviewer_keywords:
- JITCompilationStarted method [.NET Framework profiling]
- ICorProfilerCallback::JITCompilationStarted method [.NET Framework profiling]
ms.assetid: 31782b36-d311-4518-8f45-25f65385af5b
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 12a25f452ccb121ef7ebcae05048eb7116b4ac48
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackjitcompilationstarted-method"></a>Método ICorProfilerCallback::JITCompilationStarted
Notifica o criador de perfil que o compilador just-in-time (JIT) foi iniciado compilar uma função.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT JITCompilationStarted(  
    [in] FunctionID functionId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `functionId`  
 [in] A ID da função para a qual a compilação está iniciando.  
  
 `fIsSafeToBlock`  
 [in] Um valor que indica o criador de perfil se bloqueio afetará a operação do tempo de execução. O valor é `true` se o bloqueio pode fazer com que o tempo de execução aguardar o thread de chamada de retorno de chamada de retorno; caso contrário, `false`.  
  
 Embora um valor de `true` não prejudicarão o tempo de execução, ele pode afetar os resultados da criação de perfil.  
  
## <a name="remarks"></a>Comentários  
 É possível receber mais de um par de `JITCompilationStarted` e [Jitcompilationfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md) chama para cada função devido a maneira como o tempo de execução construtores de classe de identificadores. Por exemplo, o tempo de execução começa a um método de compilação JIT, mas o construtor de classe para classe B deve ser executado. Portanto, é o tempo de execução JIT compila o construtor de classe B e o executa. Durante a execução, o construtor faz uma chamada ao método A, que faz com que o método A ser compilado por JIT novamente. Nesse cenário, a primeira compilação JIT do método A é interrompida. No entanto, ambas as tentativas de um método de compilação JIT são relatadas com eventos de compilação JIT. Se for o criador de perfil para substituir o código do Microsoft intermediate language (MSIL) para o método um chamando o [: Setilfunctionbody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) método, ele deve fazer isso para ambas `JITCompilationStarted` eventos, mas ele pode usar o mesmo bloco MSIL para ambos.  
  
 Criadores de perfil devem dar suporte a sequência de retornos de chamada JIT em casos onde dois threads simultaneamente fazem retornos de chamada. Por exemplo, um thread de chamadas `JITCompilationStarted`. No entanto, antes de chamadas do thread A `JITCompilationFinished`, chamadas de thread B [: Exceptionsearchfunctionenter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md) com a ID de função de thread do `JITCompilationStarted` retorno de chamada. Pode parecer que a ID de função não deve ainda ser válida porque uma chamada para `JITCompilationFinished` ainda não foi recebido pelo criador de perfil. No entanto, em casos como esse, a ID de função é válida.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [Método JITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)
