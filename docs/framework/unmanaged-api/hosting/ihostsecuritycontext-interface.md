---
title: Interface IHostSecurityContext
ms.date: 03/30/2017
api_name:
- IHostSecurityContext
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityContext
helpviewer_keywords:
- IHostSecurityContext interface [.NET Framework hosting]
ms.assetid: 88e2eac0-8ccb-404f-abbc-287d55159842
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9d71b7e1265110a70329377ce8ab7430e1943c49
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59124015"
---
# <a name="ihostsecuritycontext-interface"></a>Interface IHostSecurityContext
Permite que o common language runtime (CLR) para manter informações de contexto de segurança implementadas pelo host.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método Capture](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-capture-method.md)|Obtém um clone do `IHostSecurityContext` instância retornada de uma chamada para [ihostsecuritymanager:: Getsecuritycontext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md).|  
  
## <a name="remarks"></a>Comentários  
 Um host pode controlar todo o acesso de código para tokens de thread pelo código do usuário e o CLR. Ele também pode garantir que a segurança completa informações de contexto são passadas entre os pontos de código com acesso de código restrito ou operações assíncronas. `IHostSecurityContext` encapsula a essas informações de contexto de segurança, que é opacas para o tempo de execução. O tempo de execução captura essas informações usando `Capture`, e a move entre despacho de item de trabalho de pool de threads, execução do finalizador e construtores de classe e de módulo.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** Incluído como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICLRHostProtectionManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)
- [Interface IHostSecurityManager](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
- [Hospedagem de Interfaces](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
