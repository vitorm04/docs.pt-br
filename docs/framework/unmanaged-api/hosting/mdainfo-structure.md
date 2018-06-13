---
title: Estrutura MDAInfo
ms.date: 03/30/2017
api_name:
- MDAInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- MDAInfo
helpviewer_keywords:
- MDAInfo structure [.NET Framework hosting]
ms.assetid: fb8c14f7-d461-43d1-8b47-adb6723b9b93
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5164e85ecc97de99dcc493c2ba5efa8fc3468471
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33443174"
---
# <a name="mdainfo-structure"></a>Estrutura MDAInfo
Fornece detalhes sobre o `Event_MDAFired` evento que dispara a criação de um Assistente de depuração gerenciado (MDA).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef struct _MDAInfo {  
    LPCWSTR  lpMDACaption;  
    LPCWSTR  lpMDAMessage  
} MDAInfo;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`lpMDACaption`|O título do MDA atual. O título descreve o tipo de falha que disparou o `Event_MDAFired` evento.|  
|`lpMDAMessage`|A mensagem de saída fornecida pelo MDA atual.|  
  
## <a name="remarks"></a>Comentários  
 Assistentes de depuração gerenciados (MDAs) estiver depurando os recursos que funcionam em conjunto com o common language runtime (CLR) para executar tarefas como identificar condições inválidas no mecanismo de execução de tempo de execução ou despejar informações adicionais sobre o estado das mecanismo. MDAs geram mensagens XML sobre eventos que são difíceis de interceptação. Eles são especialmente úteis para depurar transições entre código gerenciado e não gerenciado.  
  
 O tempo de execução executa as seguintes etapas quando um evento que aciona a criação de um MDA é acionado:  
  
-   Se o host não tiver registrado um [IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) instância chamando [Iclroneventmanager](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) para ser notificado sobre uma `Event_MDAFired` evento, o tempo de execução continua com o seu padrão, o comportamento não hospedado.  
  
-   Se o host tiver registrado um manipulador para esse evento, o tempo de execução verifica se um depurador é anexado ao processo. Se for, o tempo de execução invade o depurador. Quando o depurador continua, ele chama o host. Se nenhum depurador estiver anexado, o tempo de execução chama `IActionOnCLREvent::OnEvent` e passa um ponteiro para um `MDAInfo` a instância como o `data` parâmetro.  
  
 O host pode optar por ativar MDAs e ser notificado quando um MDA é ativado. Esse host uma oportunidade para substituir o comportamento padrão e para anular o thread gerenciado que gerou o evento, para impedir que ele corrompendo o estado do processo. Para obter mais informações sobre MDAs, consulte [diagnosticando erros com assistentes de depuração gerenciada](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.idl  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Estruturas de hospedagem](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)  
 [Diagnosticando erros com Assistentes de Depuração Gerenciados](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
