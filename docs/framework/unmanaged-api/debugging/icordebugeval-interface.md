---
title: Interface ICorDebugEval
ms.date: 03/30/2017
api_name:
- ICorDebugEval
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval
helpviewer_keywords:
- ICorDebugEval interface [.NET Framework debugging]
ms.assetid: 3a5c9815-832d-47e1-b7f7-bbba135d7cf1
topic_type:
- apiref
ms.openlocfilehash: c9e2dc95bf78d95e5d608a8ce6e9462345c20a07
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788739"
---
# <a name="icordebugeval-interface"></a>Interface ICorDebugEval

Fornece métodos para permitir que o depurador execute um código no contexto do código que está sendo depurado.  
  
## <a name="methods"></a>{1&gt;Métodos&lt;1}  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método Abort](icordebugeval-abort-method.md)|Anula a computação que este `ICorDebugEval` objeto está executando no momento.|  
|[Método CallFunction](icordebugeval-callfunction-method.md)|Define uma chamada para a função especificada. (Obsoleto na versão de .NET Framework 2,0; use [ICorDebugEval2:: CallParameterizedFunction](icordebugeval2-callparameterizedfunction-method.md) em vez disso.)|  
|[Método CreateValue](icordebugeval-createvalue-method.md)|Obtém um ponteiro de interface para um objeto "ICorDebugValue" do tipo especificado, com um valor inicial de zero ou NULL. (Obsoleto no .NET Framework 2,0; use [ICorDebugEval2:: CreateValueForType](icordebugeval2-createvaluefortype-method.md) em vez disso.)|  
|[Método GetResult](icordebugeval-getresult-method.md)|Obtém um ponteiro de interface para um `ICorDebugValue` que contém os resultados da avaliação.|  
|[Método GetThread](icordebugeval-getthread-method.md)|Obtém um ponteiro de interface para o "ICorDebugThread" no qual essa avaliação está sendo executada ou será executada.|  
|[Método IsActive](icordebugeval-isactive-method.md)|Obtém um valor que indica se este objeto de `ICorDebugEval` está em execução no momento.|  
|[Método NewArray](icordebugeval-newarray-method.md)|Aloca uma nova matriz do tipo e das dimensões do elemento especificado. (Obsoleto no .NET Framework 2,0; use [ICorDebugEval2:: NewParameterizedArray](icordebugeval2-newparameterizedarray-method.md) em vez disso.)|  
|[Método NewObject](icordebugeval-newobject-method.md)|Aloca uma nova instância de objeto e chama o método de Construtor especificado. (Obsoleto no .NET Framework 2,0; use [ICorDebugEval2:: NewParameterizedObject](icordebugeval2-newparameterizedobject-method.md) em vez disso.)|  
|[Método NewObjectNoConstructor](icordebugeval-newobjectnoconstructor-method.md)|Aloca uma nova instância de objeto do tipo especificado, sem tentar chamar um método de construtor. (Obsoleto no .NET Framework 2,0; use [ICorDebugEval2:: NewParameterizedObjectNoConstructor](icordebugeval2-newparameterizedobjectnoconstructor-method.md) em vez disso.)|  
|[Método NewString](icordebugeval-newstring-method.md)|Aloca um novo objeto de cadeia de caracteres com o conteúdo especificado.|  
  
## <a name="remarks"></a>Comentários  
 Um objeto `ICorDebugEval` é criado no contexto de um thread específico que é usado para executar as avaliações. Todos os objetos e tipos usados em uma determinada avaliação devem residir no mesmo domínio de aplicativo. Esse domínio de aplicativo não precisa ser o mesmo que o domínio de aplicativo atual do thread. As avaliações podem ser aninhadas.  
  
 As operações da avaliação não são concluídas até que o depurador chame [ICorDebugController:: Continue](icordebugcontroller-continue-method.md)e receba um retorno de chamada [ICorDebugManagedCallback:: EvalComplete](icordebugmanagedcallback-evalcomplete-method.md) . Se você precisar usar a funcionalidade de avaliação sem permitir que outros threads sejam executados, suspenda os threads usando [ICorDebugController:: SetAllThreadsDebugState](icordebugcontroller-setallthreadsdebugstate-method.md) ou [ICorDebugController:: Stop](icordebugcontroller-stop-method.md) antes de chamar [ICorDebugController:: Continue](icordebugcontroller-continue-method.md).  
  
 Como o código do usuário está em execução quando a avaliação está em andamento, qualquer evento de depuração pode ocorrer, incluindo cargas de classe e pontos de interrupção. O depurador receberá retornos de chamada, como de costume, para esses eventos. O estado da avaliação será visto como parte da inspeção do estado normal do programa. A cadeia de pilha será uma cadeia de `CHAIN_FUNC_EVAL` (consulte a enumeração "CorDebugStepReason" e o método [ICorDebugChain:: GetReason](icordebugchain-getreason-method.md) ). A API do depurador completo continuará a funcionar normalmente.  
  
 Se ocorrer uma situação de loop infinita ou deadlock, o código do usuário poderá nunca ser concluído. Nesse caso, você deve chamar [ICorDebugEval:: Abort](icordebugeval-abort-method.md) antes de retomar o programa.  
  
> [!NOTE]
> Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Depurando interfaces](debugging-interfaces.md)
