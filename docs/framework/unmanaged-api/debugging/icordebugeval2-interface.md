---
title: Interface ICorDebugEval2
ms.date: 03/30/2017
api_name:
- ICorDebugEval2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2
helpviewer_keywords:
- ICorDebugEval2 interface [.NET Framework debugging]
ms.assetid: fce34531-2687-406d-9131-d6ad94f2ce0e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d4315c9f5296e8c3ffc9d8241b929c71c2448db6
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965854"
---
# <a name="icordebugeval2-interface"></a>Interface ICorDebugEval2

Estende o "ICorDebugEval" para fornecer suporte para tipos genéricos.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método CallParameterizedFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-callparameterizedfunction-method.md)|Define uma chamada para o especificado "ICorDebugFunction", que pode ser aninhada dentro de um tipo cujo construtor usa parâmetros de tipo, ou pode se pegar parâmetros de tipo.|  
|[Método CreateValueForType](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md)|Obtém um ponteiro para um novo "ICorDebugValue" do tipo especificado, com um valor inicial de valor nulo ou zero.|  
|[Método NewParameterizedArray](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedarray-method.md)|Aloca uma nova matriz do tipo de elemento especificado e dimensões.|  
|[Método NewParameterizedObject](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md)|Cria uma instância de um novo objeto de tipo parametrizado e chama o método de construtor do objeto.|  
|[Método NewParameterizedObjectNoConstructor](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobjectnoconstructor-method.md)|Cria uma instância de um novo objeto de tipo parametrizado da classe especificada sem tentar chamar um método de construtor|  
|[Método NewStringWithLength](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newstringwithlength-method.md)|Cria uma nova cadeia de caracteres de comprimento especificado com o conteúdo especificado.|  
|[Método RudeAbort](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-rudeabort-method.md)|Anula o cálculo que este `ICorDebugEval2` está executando no momento.|  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
>  Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
