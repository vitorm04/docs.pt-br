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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 550b39445dfe4d97e712e9a4c73aa0f497b3fce5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420960"
---
# <a name="icordebugmda-interface"></a>Interface ICorDebugMDA
Representa uma mensagem do assistente de depuração gerenciado (MDA).  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método GetDescription](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getdescription-method.md)|Obtém uma cadeia de caracteres que contém uma descrição do que esse MDA.|  
|[Método GetFlags](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getflags-method.md)|Obtém os sinalizadores associados a esse MDA.|  
|[Método GetName](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getname-method.md)|Obtém uma cadeia de caracteres que contém o nome desse MDA.|  
|[Método GetOSThreadId](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getosthreadid-method.md)|Obtém o identificador de thread do sistema operacional em que esse MDA está em execução.|  
|[Método GetXML](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getxml-method.md)|Obtém o fluxo XML completo associado a esse MDA.|  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
>  Esta interface não dá suporte a que está sendo chamado remotamente, entre computadores ou entre processos.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Diagnosticando erros com Assistentes de Depuração Gerenciados](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
