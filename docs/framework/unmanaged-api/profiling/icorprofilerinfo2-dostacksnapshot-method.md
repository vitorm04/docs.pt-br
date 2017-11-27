---
title: "Método ICorProfilerInfo2::DoStackSnapshot"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.DoStackSnapshot
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::DoStackSnapshot
helpviewer_keywords:
- ICorProfilerInfo2::DoStackSnapshot method [.NET Framework profiling]
- DoStackSnapshot method [.NET Framework profiling]
ms.assetid: 287b11e9-7c52-4a13-ba97-751203fa97f4
topic_type: apiref
caps.latest.revision: "25"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6a210fc0c1984ee9bc77114ba30c3287ae43b169
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo2dostacksnapshot-method"></a>Método ICorProfilerInfo2::DoStackSnapshot
Explica os quadros gerenciados na pilha do thread especificado e envia informações para o criador de perfil por meio de um retorno de chamada.  
  
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
  
#### <a name="parameters"></a>Parâmetros  
 `thread`  
 [in] A ID do thread de destino.  
  
 Passando null no `thread` gera um instantâneo do thread atual. Se um `ThreadID` de um thread diferente for passado, o common language runtime (CLR) suspende esse thread, executa o instantâneo e continua.  
  
 `callback`  
 [in] Um ponteiro para a implementação de [StackSnapshotCallback](../../../../docs/framework/unmanaged-api/profiling/stacksnapshotcallback-function.md) método, que é chamado pelo CLR para fornecer o criador de perfil com informações sobre cada quadro gerenciado e cada execução de quadros não gerenciados.  
  
 O `StackSnapshotCallback` método é implementado pelo gerador de criador de perfil.  
  
 `infoFlags`  
 [in] Um valor de [COR_PRF_SNAPSHOT_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-snapshot-info-enumeration.md) enumeração, que especifica a quantidade de dados a serem passados para cada quadro por `StackSnapshotCallback`.  
  
 `clientData`  
 [in] Um ponteiro para os dados do cliente, que são passados diretamente para o `StackSnapshotCallback` função de retorno de chamada.  
  
 `context`  
 [in] Um ponteiro para um Win32 `CONTEXT` estrutura, que é usada para propagar a movimentação da pilha. O Win32 `CONTEXT` estrutura contém valores dos registros de CPU e representa o estado da CPU em um momento específico.  
  
 A semente ajuda CLR determinar onde começar a movimentação da pilha, se a parte superior da pilha de código não gerenciado auxiliar; Caso contrário, a semente é ignorada. Uma semente deve ser fornecida para um exame assíncrona. Se você estiver fazendo uma movimentação assíncrona, nenhuma semente é necessário.  
  
 O `context` parâmetro é válido somente se o sinalizador COR_PRF_SNAPSHOT_CONTEXT foi passado a `infoFlags` parâmetro.  
  
 `contextSize`  
 [in] O tamanho do `CONTEXT` estrutura, que é referenciada pelo `context` parâmetro.  
  
## <a name="remarks"></a>Comentários  
 Passar nulo para `thread` gera um instantâneo do thread atual. Instantâneos podem ser criados de outros threads somente se o thread de destino está suspensa no momento.  
  
 Quando deseja que o criador de perfil percorrer a pilha, ele chama `DoStackSnapshot`. Antes do CLR retorna daquela chamada, ele chama o `StackSnapshotCallback` várias vezes, uma vez para cada gerenciados quadro (ou execução de quadros não gerenciados) na pilha. Quando são encontrados quadros não gerenciados, você mesmo deve orientá-lo.  
  
 A ordem na qual a pilha está sendo movimentada é o inverso de como os quadros foram inseridos na pilha: folha (enviado pelo último) primeiro, principal (primeira enviado) quadro última.  
  
 Para obter mais informações sobre como programar o criador de perfil para movimentar pilhas gerenciadas, consulte [movimentação de pilhas do criador de perfil do .NET Framework 2.0: Noções básicas e além](http://go.microsoft.com/fwlink/?LinkId=73638).  
  
 Um exame da pilha pode ser síncronas ou assíncronas, conforme explicado nas seções a seguir.  
  
## <a name="synchronous-stack-walk"></a>Movimentação de pilha síncrona  
 Um exame da pilha síncronas envolve a movimentação de pilha do thread atual em resposta a um retorno de chamada. Ele não requer a propagação ou suspender.  
  
 Fazer um síncrono chamar quando, em resposta ao chamar um o criador de perfil CLR [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) (ou [ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)) métodos, chame `DoStackSnapshot` para percorrer a pilha da thread atual. Isso é útil quando você deseja ver a pilha de aparência em uma notificação, como [: ObjectAllocated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md). Você acabou de chamar `DoStackSnapshot` no seu `ICorProfilerCallback` método, passando null no `context` e `thread` parâmetros.  
  
## <a name="asynchronous-stack-walk"></a>Movimentação de pilha assíncrona  
 Um exame da pilha assíncrona envolve a movimentação de pilha de um thread diferente ou movimentação de pilha do thread atual, não em resposta a um retorno de chamada, mas por captura o ponteiro de instrução do thread atual. Um exame assíncrona requer uma semente, se a parte superior da pilha de código não gerenciado que não faz parte de uma plataforma de invocação (PInvoke) ou chamada de COM, mas o código auxiliar no próprio CLR. Por exemplo, o código que faz just-in-time (JIT) compilar ou coleta de lixo é código auxiliar.  
  
 Obter uma semente suspendendo diretamente o thread de destino e percorrer sua pilha por conta própria, até encontrar o primeiro quadro gerenciado. Depois que o thread de destino está suspenso, obter o contexto de registro atual do thread de destino. Em seguida, determine se o contexto de registro aponta para código não gerenciado chamando [GetFunctionFromIP](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctionfromip-method.md) — se ela retorna um `FunctionID` é igual a zero, o quadro de código não gerenciado. Agora, movimentar a pilha até atingir o primeiro quadro gerenciado e, em seguida, calcular o contexto de semente com base no contexto do registro para o quadro.  
  
 Chamar `DoStackSnapshot` com o contexto de semente para começar a movimentação da pilha assíncrona. Se você não fornecer uma semente, `DoStackSnapshot` pode ignorar quadros gerenciados na parte superior da pilha e, consequentemente, você terá um exame da pilha incompleta. Se você fornecer uma semente, ela deve apontar para o gerador de imagem nativa ou compilação JIT (Ngen.exe)-gerado código; Caso contrário, `DoStackSnapshot` retorna o código de falha, CORPROF_E_STACKSNAPSHOT_UNMANAGED_CTX.  
  
 Movimentações de pilha assíncronas facilmente podem causar deadlocks ou violações de acesso, a menos que você siga estas diretrizes:  
  
-   Quando você suspende diretamente threads, lembre-se de que apenas um thread que nunca executou código gerenciado pode suspender outro thread.  
  
-   Sempre bloquear seu [: ThreadDestroyed](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threaddestroyed-method.md) retorno de chamada até que essa movimentação de pilha seja concluída.  
  
-   Não manter um bloqueio enquanto o criador de perfil chama uma função CLR que podem disparar uma coleta de lixo. Ou seja, não manter um bloqueio se o thread que pode fazer uma chamada que dispara uma coleta de lixo.  
  
 Também há um risco de deadlock se você chamar `DoStackSnapshot` por um thread que criou o criador de perfil para que você pode percorrer a pilha de um segmento separado de destino. Na primeira vez que o thread que você criou insere certos `ICorProfilerInfo*` métodos (incluindo `DoStackSnapshot`), o CLR irá realizar inicialização por thread, CLR específicas nesse segmento. Se o criador de perfil suspendeu o thread de destino cuja pilha que você está tentando percorrer e se esse thread de destino aconteceu possua um bloqueio necessárias para executar essa inicialização por thread, ocorrerá um deadlock. Para evitar esse deadlock, fazer uma chamada inicial em `DoStackSnapshot` partir do thread criado pelo criador de perfil para percorrer um separado thread de destino, mas não suspender o thread de destino pela primeira vez. Essa chamada inicial garante que a inicialização por thread poderá ser concluído sem bloqueio. Se `DoStackSnapshot` for bem-sucedida e relatórios de pelo menos um quadro, após esse ponto, é seguro para esse thread criado pelo criador de perfil suspender qualquer thread de destino e a chamada `DoStackSnapshot` para percorrer a pilha do thread de destino.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [Interface ICorProfilerInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
