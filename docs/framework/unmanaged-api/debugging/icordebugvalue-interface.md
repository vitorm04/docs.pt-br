---
title: Interface ICorDebugValue
ms.date: 03/30/2017
api_name:
- ICorDebugValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue
helpviewer_keywords:
- ICorDebugValue interface [.NET Framework debugging]
ms.assetid: b2f7007f-c446-4b18-aed1-a25cff8aee31
topic_type:
- apiref
ms.openlocfilehash: e1044386bd6251132703c4e98a0cf2ed267d34e0
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791145"
---
# <a name="icordebugvalue-interface"></a>Interface ICorDebugValue
Representa um valor no processo que está sendo depurado. O valor pode ser um valor de leitura ou de gravação.  
  
## <a name="methods"></a>{1&gt;Métodos&lt;1}  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método CreateBreakpoint](icordebugvalue-createbreakpoint-method.md)|Este método não está implementado no momento.|  
|[Método GetAddress](icordebugvalue-getaddress-method.md)|Obtém o endereço deste `ICorDebugValue` objeto, que está no processo de depuração.|  
|[Método GetSize](icordebugvalue-getsize-method.md)|Obtém o tamanho, em bytes, deste `ICorDebugValue` objeto.|  
|[Método GetType](icordebugvalue-gettype-method.md)|Obtém o tipo primitivo deste `ICorDebugValue` objeto.|  
  
## <a name="remarks"></a>Comentários  
 Em geral, a propriedade de um objeto de valor é passada quando é retornada. O destinatário é responsável por remover uma referência do objeto quando ele é concluído com o objeto.  
  
 Dependendo de onde o valor foi recuperado, o valor pode não permanecer válido depois que o processo for retomado. Portanto, em geral, o valor não deve ser mantido em uma chamada do método [ICorDebugController:: Continue](icordebugcontroller-continue-method.md) .  
  
> [!NOTE]
> Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorDebugValue3](icordebugvalue3-interface.md)
- [Depurando interfaces](debugging-interfaces.md)
