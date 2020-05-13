---
title: Interface ICorDebugMDA
ms.date: 03/30/2017
api_name:
- ICorDebugMDA
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA
helpviewer_keywords:
- ICorDebugMDA interface [.NET Framework debugging]
ms.assetid: 8ecbb854-295c-4dd4-b9fc-01ebeac46e06
topic_type:
- apiref
ms.openlocfilehash: d711f36b4e2071dac9458a023e1d3cf4743e77b3
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212627"
---
# <a name="icordebugmda-interface"></a>Interface ICorDebugMDA
Representa uma mensagem do assistente de depuração gerenciado (MDA).  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método GetDescription](icordebugmda-getdescription-method.md)|Obtém uma cadeia de caracteres que contém uma descrição deste MDA.|  
|[Método GetFlags](icordebugmda-getflags-method.md)|Obtém os sinalizadores associados a este MDA.|  
|[Método GetName](icordebugmda-getname-method.md)|Obtém uma cadeia de caracteres que contém o nome deste MDA.|  
|[Método GetOSThreadId](icordebugmda-getosthreadid-method.md)|Obtém o identificador de thread do sistema operacional no qual este MDA está sendo executado.|  
|[Método GetXML](icordebugmda-getxml-method.md)|Obtém o fluxo XML completo associado a este MDA.|  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
> Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Depurando interfaces](debugging-interfaces.md)
- [Diagnosticando erros com assistentes para depuração gerenciada](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
