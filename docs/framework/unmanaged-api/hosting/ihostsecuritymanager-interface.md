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
ms.openlocfilehash: 13f60730fedef4876f81f078f811104777050175
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33440249"
---
# <a name="ihostsecuritymanager-interface"></a>Interface IHostSecurityManager
Fornece métodos que permitem o acesso e controle sobre o contexto de segurança do thread em execução no momento.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método GetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md)|Obtém a solicitação [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) do host.|  
|[Método ImpersonateLoggedOnUser](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-impersonateloggedonuser-method.md)|Solicitações que código ser executado usando as credenciais da identidade do usuário atual.|  
|[Método OpenThreadToken](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-openthreadtoken-method.md)|Abre o token de acesso discricionário associado ao segmento atual.|  
|[Método RevertToSelf](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-reverttoself-method.md)|Finaliza a representação da identidade do usuário atual e retorna o token de thread original.|  
|[Método SetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setsecuritycontext-method.md)|Define o contexto de segurança para o thread em execução no momento.|  
|[Método SetThreadToken](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setthreadtoken-method.md)|Define um identificador para o thread em execução no momento.|  
  
## <a name="remarks"></a>Comentários  
 Um host pode controlar o acesso de código todos os tokens de thread, o common language runtime (CLR) e o código do usuário. Ele também pode assegurar que a segurança completa informações de contexto são passadas pela operações assíncronas ou pontos de código com acesso restrito de código. `IHostSecurityContext` encapsula essas informações de contexto de segurança, que é opacas para o CLR.  
  
 O CLR trata o contexto do thread gerenciado internamente. Ele consulta o específicos de processo `IHostSecurityManager` nas seguintes situações:  
  
-   No thread do finalizador, durante a execução do finalizador.  
  
-   Durante a execução de construtor de classe e o módulo.  
  
-   Em pontos assíncronos no thread de trabalho, em chamadas para o [Ihostthreadpoolmanager](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md) método.  
  
-   Serviço de portas de conclusão de e/s.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 [Hospedagem de Interfaces](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
