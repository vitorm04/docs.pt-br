---
title: Enumeração CLR_DEBUGGING_PROCESS_FLAGS
ms.date: 03/30/2017
api_name:
- CLR_DEBUGGING_PROCESS_FLAGS
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CLR_DEBUGGING_PROCESS_FLAG
helpviewer_keywords:
- CLR_DEBUGGING_PROCESS_FLAGS enumeration [.NET Framework debugging]
ms.assetid: 85b85fde-1f87-490b-ba8d-d604670959c3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dff6b245c80050a5e85561b8bba6aa9ba8199ba8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33407060"
---
# <a name="clrdebuggingprocessflags-enumeration"></a>Enumeração CLR_DEBUGGING_PROCESS_FLAGS
Fornece valores que são usados pelo [Iclrdebugging](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) método.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef enum CLR_DEBUGGING_PROCESS_FLAGS  
{  
   CLR_DEBUGGING_MANAGED_EVENT_PENDING = 1,  
   CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH = 2  
}  CLR_DEBUGGING_PROCESS_FLAGS;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`CLR_DEBUGGING_MANAGED_EVENT_PENDING`|Esse tempo de execução tem um evento de depurador gerenciado não captura-o para enviar. Consulte a seção comentários para a distinção entre os eventos de recuperação do atraso e não o catch.|  
|`CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH`|O evento gerenciado está pendente é um <xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> solicitação.|  
  
## <a name="remarks"></a>Comentários  
 Ajuste de eventos incluem o processo, domínio de aplicativo, assembly, módulo e notificações de criação de thread que trazem o depurador até o estado atual depois que ele foi anexado a um processo. Eventos não-catch-up, que são indicados pelo `CLR_DEBUGGING_MANAGED_EVENT_PENDING` sinalizador, incluir todos os outros eventos do depurador, como exceções e gerenciados depuração notificações de assistente (MDA).  
  
 O `CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH` sinalizador permite que o tempo de execução diferenciar uma exceção de terminação e uma solicitação para anexar um depurador gerenciado que pode ser cancelado.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Metahost.idl, Metahost.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Declarando enumerações](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
 [Depuração](../../../../docs/framework/unmanaged-api/debugging/index.md)
