---
title: Coclass CorRuntimeHost
ms.date: 03/30/2017
api_name:
- CorRuntimeHost Coclass
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorRuntimeHost
helpviewer_keywords:
- CoRuntimeHost coclass [.NET Framework hosting]
ms.assetid: 5833740b-7d67-44b4-865c-b5bf45e291e3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7c81a39acee31986421c810e2814a4f7e6c4d970
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54597522"
---
# <a name="corruntimehost-coclass"></a>Coclass CorRuntimeHost
Fornece interfaces para gerenciar aplicativos que estão sendo executados pelo common language runtime.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
coclass CorRuntimeHost {  
    [default] interface ICorRuntimeHost;  
    interface IGCHost;  
    interface ICorConfiguration;  
    interface IValidator;  
    interface IDebuggerInfo;  
};  
```  
  
## <a name="interfaces"></a>Interfaces  
  
|Interface|Descrição|  
|---------------|-----------------|  
|[Interface ICorConfiguration](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)|Fornece métodos para configurar o common language runtime (CLR).|  
|[Interface ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)|Fornece métodos que permitem que o host iniciar e parar o common language runtime explicitamente, para criar e configurar domínios do aplicativo, para acessar o domínio padrão e para enumerar todos os domínios em execução no processo.|  
|[Interface IDebuggerInfo](../../../../docs/framework/unmanaged-api/hosting/idebuggerinfo-interface.md)|Fornece métodos para obter informações sobre o estado dos serviços de depuração.|  
|[Interface IGCHost](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)|Fornece métodos para obter informações sobre o sistema de coleta de lixo e para controlar alguns aspectos da coleta de lixo.|  
|"IValidator"|Fornece métodos para validação de imagens executáveis portáteis e relatórios detalhados de erros de validação.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.idl  
  
 **Biblioteca:** Incluído como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Coclasses de hospedagem](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)
