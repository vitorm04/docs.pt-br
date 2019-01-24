---
title: ICorDebugValue Interface1
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 41afc2e4305034340ad408e52ce08372bf8962dd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54507441"
---
# <a name="icordebugvalue-interface1"></a>ICorDebugValue Interface1
Representa um valor no processo sendo depurado. O valor pode ser uma leitura ou um valor de gravação.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método CreateBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-createbreakpoint-method.md)|Esse método não está implementado atualmente.|  
|[Método GetAddress](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getaddress-method.md)|Obtém o endereço desse `ICorDebugValue` objeto, que está no processo que está sendo depurado.|  
|[Método GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md)|Obtém o tamanho, em bytes, isso `ICorDebugValue` objeto.|  
|[Método GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md)|Obtém o tipo primitivo deste `ICorDebugValue` objeto.|  
  
## <a name="remarks"></a>Comentários  
 Em geral, a propriedade de um objeto de valor é passada quando ele é retornado. O destinatário é responsável por remover uma referência do objeto quando ele for concluído com o objeto.  
  
 Dependendo de onde o valor foi recuperado do, o valor não permanecer válido depois que o processo é retomado. Portanto, em geral, o valor não deve ser mantido em uma chamada do [icordebugcontroller:: continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) método.  
  
> [!NOTE]
>  Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também




- [Interface ICorDebugValue3](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)
- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
