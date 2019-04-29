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
ms.openlocfilehash: 3be6f2b9454ed2f74d2cc6792cd9aaa2c25215db
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61765200"
---
# <a name="mdainfo-structure"></a>Estrutura MDAInfo
Fornece detalhes sobre o `Event_MDAFired` evento, que dispara a criação de um Assistente para depuração gerenciada (MDA).  
  
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
|`lpMDACaption`|O título do MDA atual. O título descreve o tipo de falha que disparou o `Event_MDAFired` eventos.|  
|`lpMDAMessage`|A mensagem de saída fornecida pelo MDA atual.|  
  
## <a name="remarks"></a>Comentários  
 Assistentes de depuração gerenciados (MDAs) são recursos de depuração que trabalham em conjunto com o common language runtime (CLR) para executar tarefas como identificar condições inválidas no mecanismo de execução de tempo de execução ou despejar informações adicionais sobre o estado das mecanismo. Os MDAs geram mensagens XML sobre eventos que seriam difíceis de interceptar. Eles são especialmente úteis para transições entre código gerenciado e de depuração.  
  
 O tempo de execução realiza as seguintes etapas quando um evento que dispara a criação de um MDA é disparado:  
  
- Se o host não tiver registrado um [IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) instância chamando [iclroneventmanager:: Registeractiononevent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) para ser notificado sobre um `Event_MDAFired` evento, o tempo de execução continua com sua padrão, o comportamento não hospedados.  
  
- Se o host tiver registrado um manipulador para este evento, o tempo de execução verifica se um depurador está anexado ao processo. Se for, o tempo de execução invade o depurador. Quando o depurador continua, ele chama o host. Se nenhum depurador estiver anexado, o tempo de execução chama `IActionOnCLREvent::OnEvent` e passa um ponteiro para um `MDAInfo` a instância como o `data` parâmetro.  
  
 O host pode escolher ativar MDAs e ser notificado quando um MDA é ativado. Isso o host uma oportunidade para substituir o comportamento padrão e anular o thread gerenciado que gerou o evento, para impedir que ele se corromper o estado do processo. Para obter mais informações sobre como usar os MDAs, consulte [diagnosticando erros com assistentes para depuração gerenciada](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.idl  
  
 **Biblioteca:** Incluído como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Estruturas de hospedagem](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [Diagnosticando erros com Assistentes de Depuração Gerenciados](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
