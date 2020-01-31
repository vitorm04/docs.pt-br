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
ms.openlocfilehash: e104f8c522af2ee4cd42332b7459f4a2fd185511
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792681"
---
# <a name="icordebugobjectvalue-interface"></a>Interface ICorDebugObjectValue

Uma subclasse de "ICorDebugValue" que representa um valor que contém um objeto.  
  
## <a name="methods"></a>{1&gt;Métodos&lt;1}  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método GetClass](icordebugobjectvalue-getclass-method.md)|Obtém um ponteiro de interface para o <xref:System.Type> de Common Language Runtime (CLR) do objeto ao qual esse `ICorDebugObjectValue` faz referência.|  
|[Método GetContext](icordebugobjectvalue-getcontext-method.md)|Não implementado.|  
|[Método GetFieldValue](icordebugobjectvalue-getfieldvalue-method.md)|Obtém um ponteiro de interface para um [ICorDebugValue](icordebugvalue-interface.md) que representa o valor do campo especificado da classe especificada.|  
|[Método GetManagedCopy](icordebugobjectvalue-getmanagedcopy-method.md)|{1&gt;{2&gt;Obsoleta. &lt;2}&lt;1} Não chame esse método.|  
|[Método GetVirtualMethod](icordebugobjectvalue-getvirtualmethod-method.md)|Não implementado.|  
|[Método IsValueClass](icordebugobjectvalue-isvalueclass-method.md)|Obtém um valor que indica se o objeto referenciado por essa `ICorDebugObjectValue` é um tipo de valor.|  
|[Método SetFromManagedCopy](icordebugobjectvalue-setfrommanagedcopy-method.md)|{1&gt;{2&gt;Obsoleta. &lt;2}&lt;1} Não chame esse método.|  
  
## <a name="remarks"></a>Comentários  
 Um `ICorDebugObjectValue` permanece válido até que o processo que está sendo depurado seja continuado.  
  
> [!NOTE]
> Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Depurando interfaces](debugging-interfaces.md)
