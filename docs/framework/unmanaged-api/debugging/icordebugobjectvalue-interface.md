---
title: Interface ICorDebugObjectValue
ms.date: 03/30/2017
api_name:
- ICorDebugObjectValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectValue
helpviewer_keywords:
- ICorDebugObjectValue interface [.NET Framework debugging]
ms.assetid: 937de6a0-6fbf-4ddc-80ea-a6217b73e62b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d0ac91681313b60ebfcaf725dcc2e0d6547e3c1b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59222608"
---
# <a name="icordebugobjectvalue-interface"></a>Interface ICorDebugObjectValue

Uma subclasse de "ICorDebugValue" que representa um valor que contém um objeto.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md)|Obtém um ponteiro de interface para o common language runtime (CLR) <xref:System.Type> do objeto que este `ICorDebugObjectValue` referências.|  
|[Método GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getcontext-method.md)|Não implementado.|  
|[Método GetFieldValue](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getfieldvalue-method.md)|Obtém um ponteiro de interface para um [ICorDebugValue](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-interface.md) que representa o valor do campo especificado da classe especificada.|  
|[Método GetManagedCopy](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getmanagedcopy-method.md)|Obsoleto. Não chame este método.|  
|[Método GetVirtualMethod](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getvirtualmethod-method.md)|Não implementado.|  
|[Método IsValueClass](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-isvalueclass-method.md)|Obtém um valor que indica se o objeto referenciado por este `ICorDebugObjectValue` é um tipo de valor.|  
|[Método SetFromManagedCopy](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-setfrommanagedcopy-method.md)|Obsoleto. Não chame este método.|  
  
## <a name="remarks"></a>Comentários  
 Um `ICorDebugObjectValue` permanece válido até que o processo que está sendo depurado é continuado.  
  
> [!NOTE]
>  Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
