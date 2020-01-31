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
ms.openlocfilehash: e69b32430651edd0222db874e2659bd959f89549
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788704"
---
# <a name="icordebugeval2-interface"></a>Interface ICorDebugEval2

Estende "ICorDebugEval" para fornecer suporte para tipos genéricos.  
  
## <a name="methods"></a>{1&gt;Métodos&lt;1}  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método CallParameterizedFunction](icordebugeval2-callparameterizedfunction-method.md)|Define uma chamada para o "ICorDebugFunction" especificado, que pode ser aninhado dentro de um tipo cujo construtor usa parâmetros de tipo ou pode usar parâmetros de tipo.|  
|[Método CreateValueForType](icordebugeval2-createvaluefortype-method.md)|Obtém um ponteiro para um novo "ICorDebugValue" do tipo especificado, com um valor inicial de NULL ou zero.|  
|[Método NewParameterizedArray](icordebugeval2-newparameterizedarray-method.md)|Aloca uma nova matriz do tipo e das dimensões do elemento especificado.|  
|[Método NewParameterizedObject](icordebugeval2-newparameterizedobject-method.md)|Cria uma instância de um novo objeto de tipo com parâmetros e chama o método de construtor do objeto.|  
|[Método NewParameterizedObjectNoConstructor](icordebugeval2-newparameterizedobjectnoconstructor-method.md)|Cria uma instância de um novo objeto de tipo com parâmetros da classe especificada sem tentar chamar um método de Construtor|  
|[Método NewStringWithLength](icordebugeval2-newstringwithlength-method.md)|Cria uma nova cadeia de caracteres do comprimento especificado com o conteúdo especificado.|  
|[Método RudeAbort](icordebugeval2-rudeabort-method.md)|Anula a computação que esse `ICorDebugEval2` está executando no momento.|  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
> Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Depurando interfaces](debugging-interfaces.md)
