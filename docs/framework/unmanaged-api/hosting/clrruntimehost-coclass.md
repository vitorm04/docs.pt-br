---
title: Coclass CLRRuntimeHost
ms.date: 03/30/2017
api_name:
- CLRRuntimeHost Coclass
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CLRRuntimeHost
helpviewer_keywords:
- CLRRuntimeHost coclass [.NET Framework hosting]
ms.assetid: 2ac9cbf5-8a2d-4e4f-8831-0dad8ef0a897
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8bae2d134c412023d0f126453b5285662d994c78
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59207754"
---
# <a name="clrruntimehost-coclass"></a>Coclass CLRRuntimeHost
Fornece interfaces para gerenciar a execução de código em tempo de execução.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
coclass CLRRuntimeHost {  
    [default] interface  ICLRRuntimeHost;  
    interface            ICLRValidator;  
};  
```  
  
## <a name="interfaces"></a>Interfaces  
  
|Interface|Descrição|  
|---------------|-----------------|  
|[Interface ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)|Fornece métodos para controlar a execução de aplicativos em tempo de execução.|  
|[Interface ICLRValidator](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)|Fornece métodos para a validação de imagens executáveis portáteis e relatórios detalhados de erros de validação.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.idl  
  
 **Biblioteca:** Incluído como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Hospedando coclasses](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)
