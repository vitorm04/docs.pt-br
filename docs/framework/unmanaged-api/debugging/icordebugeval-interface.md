---
title: ICorDebugEval Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 77e97e31a20c392eebae1b373bb1af53f87c23e9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugeval-interface1"></a>ICorDebugEval Interface1
Fornece métodos para permitir que o depurador execute um código no contexto do código que está sendo depurado.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método Abort](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-abort-method.md)|Anula a computação isso `ICorDebugEval` objeto está executando no momento.|  
|[Método CallFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-callfunction-method.md)|Configura uma chamada para a função especificada. (Obsoleto no .NET Framework versão 2.0; use [Icordebugeval2](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-callparameterizedfunction-method.md) em vez disso.)|  
|[Método CreateValue](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-createvalue-method.md)|Obtém um ponteiro de interface para um objeto de "ICorDebugValue" do tipo especificado, com um valor inicial de zero ou nulo. (Obsoleto no .NET Framework 2.0; use [Icordebugeval2](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md) em vez disso.)|  
|[Método GetResult](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-getresult-method.md)|Obtém um ponteiro de interface para um `ICorDebugValue` que contém os resultados da avaliação.|  
|[Método GetThread](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-getthread-method.md)|Obtém um ponteiro de interface para o "ICorDebugThread" onde esta avaliação está em execução ou será executado.|  
|[Método IsActive](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-isactive-method.md)|Obtém um valor que indica se este `ICorDebugEval` objeto está em execução atualmente.|  
|[Método NewArray](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-newarray-method.md)|Aloca uma nova matriz do tipo de elemento especificado e dimensões. (Obsoleto no .NET Framework 2.0; use [Icordebugeval2](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedarray-method.md) em vez disso.)|  
|[Método NewObject](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-newobject-method.md)|Aloca uma nova instância de objeto e chama o método de construtor especificado. (Obsoleto no .NET Framework 2.0; use [Icordebugeval2](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md) em vez disso.)|  
|[Método NewObjectNoConstructor](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-newobjectnoconstructor-method.md)|Aloca uma nova instância de objeto do tipo especificado, sem tentar chamar um método de construtor. (Obsoleto no .NET Framework 2.0; use [Icordebugeval2](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobjectnoconstructor-method.md) em vez disso.)|  
|[Método NewString](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-newstring-method.md)|Aloca um novo objeto de cadeia de caracteres com o conteúdo especificado.|  
  
## <a name="remarks"></a>Comentários  
 Um `ICorDebugEval` objeto é criado no contexto de um segmento específico que é usado para executar as avaliações. Todos os objetos e os tipos usados em uma determinada avaliação devem residir no mesmo domínio de aplicativo. Domínio de aplicativo não precisa ser o mesmo que o domínio de aplicativo atual do thread. Avaliações podem ser aninhadas.  
  
 Operações de avaliação não concluída até que as chamadas do depurador [Icordebugcontroller](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)e, em seguida, recebe um [: Evalcomplete](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-evalcomplete-method.md) retorno de chamada. Se você precisar usar a funcionalidade de avaliação sem permitir que outros threads executar, suspender os threads usando [: Setallthreadsdebugstate](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md) ou [Icordebugcontroller](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md)antes de chamar [Icordebugcontroller](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md).  
  
 Código do usuário está em execução quando a avaliação está em andamento, os eventos de depuração podem ocorrer, incluindo cargas de classe e os pontos de interrupção. O depurador irá receber retornos de chamada, normalmente, esses eventos. O estado de avaliação será visto como parte de inspeção do estado normal do programa. A cadeia da pilha será um `CHAIN_FUNC_EVAL` cadeia (consulte a enumeração de "CorDebugStepReason" e o [: Getreason](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getreason-method.md) método). A API do depurador completo continuará a operar normalmente.  
  
 Se ocorrer uma situação de loop infinita ou bloqueada, o código do usuário nunca pode ser concluída. Nesse caso, você deve chamar [Icordebugeval](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-abort-method.md) antes de continuar o programa.  
  
> [!NOTE]
>  Esta interface não dá suporte a que está sendo chamado remotamente, entre computadores ou entre processos.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
    
    
    
 [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
