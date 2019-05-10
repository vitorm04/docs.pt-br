---
title: Interface IHostSecurityManager
ms.date: 03/30/2017
api_name:
- IHostSecurityManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager
helpviewer_keywords:
- IHostSecurityManager interface [.NET Framework hosting]
ms.assetid: c3be2cbd-2d93-438b-9888-9a0251b63c03
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a2c71f32dfd190e188bb28aad5d51c72160eb4bc
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64603217"
---
# <a name="ihostsecuritymanager-interface"></a>Interface IHostSecurityManager
Fornece métodos que permitem acesso e controle sobre o contexto de segurança do thread em execução no momento.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método GetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md)|Obtém o solicitada [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) do host.|  
|[Método ImpersonateLoggedOnUser](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-impersonateloggedonuser-method.md)|As solicitações que o código ser executado usando as credenciais da identidade do usuário atual.|  
|[Método OpenThreadToken](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-openthreadtoken-method.md)|Abre o token de acesso discricionário associado ao thread atual.|  
|[Método RevertToSelf](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-reverttoself-method.md)|Finaliza a representação da identidade do usuário atual e retorna o token do thread original.|  
|[Método SetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setsecuritycontext-method.md)|Define o contexto de segurança para o thread em execução no momento.|  
|[Método SetThreadToken](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setthreadtoken-method.md)|Define um identificador para o thread em execução no momento.|  
  
## <a name="remarks"></a>Comentários  
 Um host pode controlar todo o acesso de código para tokens de thread, o common language runtime (CLR) e o código do usuário. Ele também pode garantir que a segurança completa informações de contexto são passadas entre os pontos de código com acesso de código restrito ou operações assíncronas. `IHostSecurityContext` encapsula a essas informações de contexto de segurança, que é opacas para o CLR.  
  
 O CLR trata o contexto de thread gerenciado internamente. Ele consulta o processo específico `IHostSecurityManager` nas seguintes situações:  
  
- No thread do finalizador, durante a execução do finalizador.  
  
- Durante a execução de construtor de classe e módulo.  
  
- Em pontos assíncronos no thread de trabalho, em chamadas para o [ihostthreadpoolmanager:: QueueUserWorkItem](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md) método.  
  
- Na manutenção das portas de conclusão de e/s.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** Incluído como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [Hospedagem de Interfaces](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
