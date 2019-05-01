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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 745917af176de47999737c87833c23df9c75ea7b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61995945"
---
# <a name="icordebugeval-interface"></a>Interface ICorDebugEval

Fornece métodos para permitir que o depurador execute um código no contexto do código que está sendo depurado.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método Abort](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-abort-method.md)|Anula a computação isso `ICorDebugEval` objeto está executando no momento.|  
|[Método CallFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-callfunction-method.md)|Define uma chamada para a função especificada. (Obsoleto no .NET Framework versão 2.0; use [ICorDebugEval2::CallParameterizedFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-callparameterizedfunction-method.md) em vez disso.)|  
|[Método CreateValue](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-createvalue-method.md)|Obtém um ponteiro de interface para um objeto de "ICorDebugValue" do tipo especificado, com um valor inicial de zero ou nulo. (Obsoleto no .NET Framework 2.0; use [ICorDebugEval2::CreateValueForType](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md) em vez disso.)|  
|[Método GetResult](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-getresult-method.md)|Obtém um ponteiro de interface para um `ICorDebugValue` que contém os resultados da avaliação.|  
|[Método GetThread](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-getthread-method.md)|Obtém um ponteiro de interface para o "ICorDebugThread" onde essa avaliação está em execução ou será executado.|  
|[Método IsActive](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-isactive-method.md)|Obtém um valor que indica se este `ICorDebugEval` objeto está em execução atualmente.|  
|[Método NewArray](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-newarray-method.md)|Aloca uma nova matriz do tipo de elemento especificado e dimensões. (Obsoleto no .NET Framework 2.0; use [ICorDebugEval2::NewParameterizedArray](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedarray-method.md) em vez disso.)|  
|[Método NewObject](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-newobject-method.md)|Aloca uma nova instância de objeto e chama o método de construtor especificado. (Obsoleto no .NET Framework 2.0; use [ICorDebugEval2::NewParameterizedObject](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md) em vez disso.)|  
|[Método NewObjectNoConstructor](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-newobjectnoconstructor-method.md)|Aloca uma nova instância de objeto do tipo especificado, sem tentar chamar um método de construtor. (Obsoleto no .NET Framework 2.0; use [ICorDebugEval2::NewParameterizedObjectNoConstructor](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobjectnoconstructor-method.md) em vez disso.)|  
|[Método NewString](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-newstring-method.md)|Aloca um novo objeto de cadeia de caracteres com o conteúdo especificado.|  
  
## <a name="remarks"></a>Comentários  
 Um `ICorDebugEval` objeto é criado no contexto de um thread específico que é usado para executar as avaliações. Todos os objetos e tipos usados em uma determinada avaliação devem residir no mesmo domínio de aplicativo. Domínio de aplicativo não precisa ser o mesmo domínio do aplicativo atual do thread. Avaliações podem ser aninhadas.  
  
 Operações da avaliação não concluir até que as chamadas do depurador [icordebugcontroller:: continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)e, em seguida, recebe um [icordebugmanagedcallback:: Evalcomplete](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-evalcomplete-method.md) retorno de chamada. Se você precisar usar a funcionalidade de avaliação sem permitir que outros threads executar, suspender os threads, usando uma [icordebugcontroller:: Setallthreadsdebugstate](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md) ou [icordebugcontroller:: Stop](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md)antes de chamar [icordebugcontroller:: continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md).  
  
 Porque o código do usuário está em execução quando a avaliação está em andamento, pode ocorrer nenhum evento de depuração, incluindo cargas de classe e os pontos de interrupção. O depurador irá receber retornos de chamada, normalmente, esses eventos. O estado da avaliação será visto como parte da inspeção do estado normal do programa. A cadeia de pilha será um `CHAIN_FUNC_EVAL` cadeia (consulte a enumeração de "CorDebugStepReason" e o [icordebugchain:: Getreason](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getreason-method.md) método). A API do depurador completo continuará a operar normalmente.  
  
 Se surgir uma situação de loop infinita ou com deadlock, o código do usuário nunca pode ser concluída. Nesse caso, você deve chamar [icordebugeval:: Abort](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-abort-method.md) antes de retomar o programa.  
  
> [!NOTE]
>  Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
