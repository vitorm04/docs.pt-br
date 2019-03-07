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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5eb881c8f024373fbff1dad17cd883ab6cafa2a0
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466625"
---
# <a name="icorprofilercallbackjitcompilationstarted-method"></a>Método ICorProfilerCallback::JITCompilationStarted
Notifica o criador de perfil que o compilador just-in-time (JIT) começou a compilar uma função.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT JITCompilationStarted(  
    [in] FunctionID functionId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `functionId`  
 [in] A ID da função para o qual a compilação está sendo iniciada.  
  
 `fIsSafeToBlock`  
 [in] Um valor que indica o criador de perfil, se o bloqueio afetará a operação de tempo de execução. O valor será `true` se o bloqueio pode fazer com que o tempo de execução aguardar o thread de chamada de retorno desse retorno de chamada; caso contrário, `false`.  
  
 Embora um valor de `true` não danificará o tempo de execução, ele pode afetar os resultados de criação de perfil.  
  
## <a name="remarks"></a>Comentários  
 É possível receber mais de um par de `JITCompilationStarted` e [ICorProfilerCallback:: Jitcompilationfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md) chama para cada função devido à maneira o tempo de execução lida com construtores de classe. Por exemplo, o tempo de execução começa a um método de compilação JIT, mas o construtor de classe para classe B precisa ser executado. Portanto, é o tempo de execução JIT compila o construtor da classe B e executa-o. Enquanto o construtor é executado, ele faz uma chamada ao método A, que faz com que o método A ser compilado por JIT novamente. Nesse cenário, a primeira compilação JIT do método um é interrompida. No entanto, ambas as tentativas de um método de compilação JIT são relatadas com eventos de compilação JIT. Se o criador de perfil vai substituir o código do Microsoft intermediate language (MSIL) para o método um chamando o [ICorProfilerInfo:: Setilfunctionbody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) método, ele deve fazer isso para ambas `JITCompilationStarted` eventos, mas ele pode usar o mesmo bloco MSIL para ambos.  
  
 Os criadores de perfis devem dar suporte a sequência de retornos de chamada do JIT em casos em que dois threads simultaneamente fazendo retornos de chamada. Por exemplo, o thread A chama `JITCompilationStarted`. No entanto, antes de chamadas do thread A `JITCompilationFinished`, o thread B chama [ICorProfilerCallback:: Exceptionsearchfunctionenter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md) com a ID de função do thread do `JITCompilationStarted` retorno de chamada. Pode parecer que a ID de função não deve ainda ser válida porque uma chamada para `JITCompilationFinished` ainda não foi recebido pelo criador de perfil. No entanto, em casos como esse, a ID de função é válida.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Interface ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [Método JITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)
