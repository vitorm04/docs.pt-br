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
ms.openlocfilehash: b9b9b8a728932caa085bba1665dc97faf02be8fe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33431374"
---
# <a name="corruntimehost-coclass"></a>Coclass CorRuntimeHost
Fornece interfaces de gerenciamento de aplicativos que estão sendo executados pelo common language runtime.  
  
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
|[Interface ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)|Fornece métodos que permitem que o host iniciar e parar o common language runtime explicitamente, para criar e configurar domínios de aplicativo, para acessar o domínio padrão e para enumerar todos os domínios em execução no processo.|  
|[Interface IDebuggerInfo](../../../../docs/framework/unmanaged-api/hosting/idebuggerinfo-interface.md)|Fornece métodos para obter informações sobre o estado dos serviços de depuração.|  
|[Interface IGCHost](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)|Fornece métodos para obter informações sobre o sistema de coleta de lixo e para controlar alguns aspectos da coleta de lixo.|  
|"IValidator"|Fornece métodos para validação de imagens executáveis portáteis e os relatórios detalhados de erros de validação.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.idl  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Coclasses de hospedagem](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)
