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
ms.openlocfilehash: b9185600d9d8b2a33830d86642727ac54b87a9cf
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73099652"
---
# <a name="clr_debugging_process_flags-enumeration"></a>Enumeração CLR_DEBUGGING_PROCESS_FLAGS
Fornece valores que são usados pelo método [ICLRDebugging:: OpenVirtualProcess](iclrdebugging-openvirtualprocess-method.md) .  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
typedef enum CLR_DEBUGGING_PROCESS_FLAGS  
{  
   CLR_DEBUGGING_MANAGED_EVENT_PENDING = 1,  
   CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH = 2  
}  CLR_DEBUGGING_PROCESS_FLAGS;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`CLR_DEBUGGING_MANAGED_EVENT_PENDING`|Esse tempo de execução tem um evento de depurador gerenciado que não é de atualização a ser enviado. Consulte a seção comentários para a distinção entre eventos de atualização e não-atualização.|  
|`CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH`|O evento gerenciado que está pendente é uma solicitação de <xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType>.|  
  
## <a name="remarks"></a>Comentários  
 Eventos de atualização incluem notificações de processo, domínio de aplicativo, assembly, módulo e criação de threads que trazem o depurador para o estado atual depois que ele é anexado a um processo. Eventos que não são de atualização, que são indicados pelo sinalizador `CLR_DEBUGGING_MANAGED_EVENT_PENDING`, incluem todos os outros eventos do depurador, como exceções e notificações do MDA (Assistente de depuração gerenciada).  
  
 O sinalizador `CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH` permite que o tempo de execução Diferencie entre uma exceção de término e uma solicitação para anexar um depurador gerenciado que pode ser cancelado.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** MetaHost. idl, MetaHost. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Declarando enumerações](debugging-enumerations.md)
- [Depuração](index.md)
