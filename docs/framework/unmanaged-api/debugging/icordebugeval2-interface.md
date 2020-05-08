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
ms.openlocfilehash: b597d95b5b25e5ebf04fac48e4f3fda312a9594c
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976116"
---
# <a name="icordebugeval2-interface"></a>Interface ICorDebugEval2

Estende "ICorDebugEval" para fornecer suporte para tipos genéricos.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método CallParameterizedFunction](icordebugeval2-callparameterizedfunction-method.md)|Define uma chamada para o "ICorDebugFunction" especificado, que pode ser aninhado dentro de um tipo cujo construtor usa parâmetros de tipo ou pode usar parâmetros de tipo.|  
|[Método CreateValueForType](icordebugeval2-createvaluefortype-method.md)|Obtém um ponteiro para um novo "ICorDebugValue" do tipo especificado, com um valor inicial de NULL ou zero.|  
|[Método NewParameterizedArray](icordebugeval2-newparameterizedarray-method.md)|Aloca uma nova matriz do tipo e das dimensões do elemento especificado.|  
|[Método NewParameterizedObject](icordebugeval2-newparameterizedobject-method.md)|Cria uma instância de um novo objeto de tipo com parâmetros e chama o método de construtor do objeto.|  
|[Método NewParameterizedObjectNoConstructor](icordebugeval2-newparameterizedobjectnoconstructor-method.md)|Cria uma instância de um novo objeto de tipo com parâmetros da classe especificada sem tentar chamar um método de Construtor|  
|[Método NewStringWithLength](icordebugeval2-newstringwithlength-method.md)|Cria uma nova cadeia de caracteres do comprimento especificado com o conteúdo especificado.|  
|[Método RudeAbort](icordebugeval2-rudeabort-method.md)|Anula a computação que `ICorDebugEval2` está executando no momento.|  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
> Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Depurando interfaces](debugging-interfaces.md)
