---
title: Método ICorProfilerInfo2::DoStackSnapshot
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.DoStackSnapshot
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::DoStackSnapshot
helpviewer_keywords:
- ICorProfilerInfo2::DoStackSnapshot method [.NET Framework profiling]
- DoStackSnapshot method [.NET Framework profiling]
ms.assetid: 287b11e9-7c52-4a13-ba97-751203fa97f4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 12ef215253ca02048a5a3fc2c7c682823233929f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59108076"
---
# <a name="icorprofilerinfo2dostacksnapshot-method"></a>Método ICorProfilerInfo2::DoStackSnapshot
Orienta os quadros gerenciados na pilha para o thread especificado e envia informações para o criador de perfil por meio de um retorno de chamada.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT DoStackSnapshot(  
    [in] ThreadID thread,  
    [in] StackSnapshotCallback *callback,  
    [in] ULONG32 infoFlags,  
    [in] void *clientData,  
    [in, size_is(contextSize), length_is(contextSize)] BYTE context[],  
    [in] ULONG32 contextSize);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `thread`  
 [in] A ID do thread de destino.  
  
 Passando null no `thread` gera um instantâneo do thread atual. Se um `ThreadID` de um thread diferente for passado, o common language runtime (CLR) suspende o thread em questão, executa o instantâneo e será retomada.  
  
 `callback`  
 [in] Um ponteiro para a implementação de [StackSnapshotCallback](../../../../docs/framework/unmanaged-api/profiling/stacksnapshotcallback-function.md) método, que é chamado pelo CLR para fornecer o criador de perfil com informações sobre cada quadro gerenciado e cada execução de quadros não gerenciados.  
  
 O `StackSnapshotCallback` método é implementado pelo gerador de criador de perfil.  
  
 `infoFlags`  
 [in] Um valor igual a [COR_PRF_SNAPSHOT_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-snapshot-info-enumeration.md) enumeração que especifica a quantidade de dados a serem passados de volta para cada quadro por `StackSnapshotCallback`.  
  
 `clientData`  
 [in] Um ponteiro para os dados de cliente, que são passados diretamente para o `StackSnapshotCallback` função de retorno de chamada.  
  
 `context`  
 [in] Um ponteiro para um Win32 `CONTEXT` estrutura, que é usada para propagar a movimentação da pilha. O Win32 `CONTEXT` estrutura contém valores dos registros de CPU e representa o estado da CPU em um momento específico no tempo.  
  
 A propagação ajuda a CLR determinar onde começar a movimentação da pilha, se a parte superior da pilha for código não gerenciado auxiliar; Caso contrário, a semente é ignorada. Uma semente deve ser fornecida para um exame de assíncrono. Se você estiver fazendo uma movimentação assíncrona, nenhuma semente é necessário.  
  
 O `context` parâmetro é válido somente se o sinalizador COR_PRF_SNAPSHOT_CONTEXT foi passado a `infoFlags` parâmetro.  
  
 `contextSize`  
 [in] O tamanho do `CONTEXT` estrutura, que é referenciada pelo `context` parâmetro.  
  
## <a name="remarks"></a>Comentários  
 Passar nulo para `thread` gera um instantâneo do thread atual. Instantâneos podem ser criados de outros threads somente se o thread de destino está suspenso no momento.  
  
 Quando o criador de perfil deseja movimentar a pilha, ele chama `DoStackSnapshot`. Antes do CLR retorna daquela chamada, ele chama sua `StackSnapshotCallback` várias vezes, uma vez para cada uma gerenciada quadro (ou execução de quadros não gerenciados) na pilha. Quando são encontrados quadros não gerenciados, você deve movimentá-los por conta própria.  
  
 A ordem em que a pilha é movimentada é o inverso de como os quadros foram colocados na pilha: folha (enviado pelo último) quadro principal, primeiro quadro (enviado primeiro) pela última vez.  
  
 Para obter mais informações sobre como programar o criador de perfil para movimentar pilhas gerenciadas, consulte [movimentação de pilhas do Profiler no .NET Framework 2.0: Noções básicas e além](https://go.microsoft.com/fwlink/?LinkId=73638).  
  
 Um exame da pilha pode ser síncrono ou assíncrono, conforme explicado nas seções a seguir.  
  
## <a name="synchronous-stack-walk"></a>Movimentação de pilha síncronas  
 Uma movimentação de pilha síncronas envolve a movimentação de pilha do thread atual em resposta a um retorno de chamada. Ele não requer a propagação ou a suspensão.  
  
 Você tornar um síncrono chamar e quando, em resposta ao chamar um dos seu gerador de perfil CLR [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) (ou [ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)) métodos, chame `DoStackSnapshot` para movimentar a pilha das thread atual. Isso é útil quando você deseja ver a pilha de aparência em uma notificação, como [ICorProfilerCallback:: ObjectAllocated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md). Basta chamar `DoStackSnapshot` no seu `ICorProfilerCallback` método, passando nulo na `context` e `thread` parâmetros.  
  
## <a name="asynchronous-stack-walk"></a>Movimentação de pilha assíncrona  
 Uma movimentação de pilha assíncrona envolve a movimentar a pilha de um thread diferente, ou a movimentação de pilha do thread atual, não em resposta a um retorno de chamada, mas por sequestro de ponteiro de instrução do thread atual. Um exame de assíncrono exige uma semente, se a parte superior da pilha for código não gerenciado que não faz parte de uma plataforma de invocação (PInvoke) ou a chamada de COM, mas o código auxiliar no próprio CLR. Por exemplo, o código que faz o just-in-time (JIT) compilar ou coleta de lixo é o código auxiliar.  
  
 Obter uma semente suspendendo diretamente o thread-alvo e movimentar sua pilha por conta própria, até encontrar o primeiro quadro gerenciado. Depois que o thread-alvo é suspenso, obtenha o contexto de registro atual do thread de destino. Em seguida, determine se o contexto de registro aponta para código não gerenciado, chamando [ICorProfilerInfo:: GetFunctionFromIP](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctionfromip-method.md) — se ela retorna um `FunctionID` igual a zero, o quadro é o código não gerenciado. Agora, movimentar a pilha até atingir o primeiro quadro gerenciado e, em seguida, calcular o contexto de semente com base no contexto do registro para o quadro.  
  
 Chamar `DoStackSnapshot` com o contexto de sua semente para começar a movimentação de pilha assíncrona. Se você não fornecer uma semente, `DoStackSnapshot` podem ignorar quadros gerenciados na parte superior da pilha e, consequentemente, lhe dará uma movimentação de pilha incompleta. Se você fornecer uma semente, ela deve apontar para o gerador de imagem nativa ou compilado por JIT (Ngen.exe)-gerado código; Caso contrário, `DoStackSnapshot` retorna o código de falha, CORPROF_E_STACKSNAPSHOT_UNMANAGED_CTX.  
  
 Movimentações de pilha assíncronas podem facilmente causar deadlocks ou violações, de acesso, a menos que você siga estas diretrizes:  
  
-   Quando você suspende diretamente threads, lembre-se de que apenas um thread que nunca executa código gerenciado pode suspender outro thread.  
  
-   Sempre bloquear sua [ICorProfilerCallback:: ThreadDestroyed](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threaddestroyed-method.md) retorno de chamada até que a movimentação da pilha do thread for concluída.  
  
-   Não segure um bloqueio enquanto seu gerador de perfil chama uma função CLR que pode disparar uma coleta de lixo. Ou seja, não segure um bloqueio se o thread proprietário pode fazer uma chamada que dispara uma coleta de lixo.  
  
 Também há um risco de deadlock se você chamar `DoStackSnapshot` de um thread que seu gerador de perfil foi criado para que você pode movimentar a pilha de um thread de destino separado. Na primeira vez que o thread que você criou entra em determinados `ICorProfilerInfo*` métodos (incluindo `DoStackSnapshot`), o CLR realizará a inicialização por thread, CLR específico nesse thread. Se seu gerador de perfil suspendeu cuja pilha está tentando movimentar o thread-alvo, e se esse thread-alvo aconteceu possua um bloqueio necessário para realizar essa inicialização por thread, ocorrerá um deadlock. Para evitar esse deadlock, faça uma chamada inicial em `DoStackSnapshot` de seu thread criado pelo criador de perfil para movimentar um separado thread de destino, mas não suspender o thread de destino primeiro. Essa chamada inicial garante que a inicialização por thread pode ser concluída sem deadlock. Se `DoStackSnapshot` for bem-sucedida e relata a pelo menos um quadro, após esse ponto, será seguro para que esse thread criado pelo criador de perfil de suspender qualquer thread-alvo e chamada `DoStackSnapshot` para movimentar a pilha do thread-alvo.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [Interface ICorProfilerInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
