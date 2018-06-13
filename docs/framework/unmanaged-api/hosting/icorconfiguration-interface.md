---
title: Interface ICorConfiguration
ms.date: 03/30/2017
api_name:
- ICorConfiguration
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorConfiguration
helpviewer_keywords:
- ICorConfiguration interface [.NET Framework hosting]
ms.assetid: aaf96116-372b-4538-afb1-9e0fcdac1f98
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 63699f0af69b3a7623c5e9da156c2ff8ae83ccfc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33437501"
---
# <a name="icorconfiguration-interface"></a>Interface ICorConfiguration
Fornece métodos para configurar o common language runtime (CLR).  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método AddDebuggerSpecialThread](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-adddebuggerspecialthread-method.md)|Para os serviços de depuração, indica que um determinado thread deve ter permissão para continuar em execução enquanto o depurador tem um aplicativo interrompido durante a cenários de depuração gerenciados ou não gerenciados.|  
|[Método SetDebuggerThreadControl](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setdebuggerthreadcontrol-method.md)|Define a interface de retorno de chamada que os serviços de depuração chamará como threads do CLR são bloqueados e desbloqueados para depuração.|  
|[Método SetGCHostControl](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setgchostcontrol-method.md)|Define a interface de retorno de chamada a ser usado pelo coletor de lixo para solicitar o host para alterar os limites de memória virtual.|  
|[Método SetGCThreadControl](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setgcthreadcontrol-method.md)|Define a interface de retorno de chamada para o agendamento de threads para tarefas de tempo de execução não seriam bloqueadas caso contrário, uma coleta de lixo.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Hospedagem de Interfaces](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [Coclass CorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
