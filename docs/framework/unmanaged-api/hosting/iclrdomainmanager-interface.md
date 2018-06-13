---
title: Interface ICLRDomainManager
ms.date: 03/30/2017
api_name:
- ICLRDomainManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDomainManager
helpviewer_keywords:
- ICLRDomainManager interface [.NET Framework hosting]
ms.assetid: f08b2390-d872-4521-a815-e9c237c4c45d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c3b8dd67cb7dff4bec5bab192a08461ef13fcbd9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436352"
---
# <a name="iclrdomainmanager-interface"></a>Interface ICLRDomainManager
Permite que o host especificar o Gerenciador de domínio de aplicativo que será usado para inicializar o domínio de aplicativo padrão e para especificar propriedades de inicialização.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método SetAppDomainManagerType](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md)|Especifica o tipo derivado de <xref:System.AppDomainManager?displayProperty=nameWithType> classe do Gerenciador de domínio de aplicativo que será usado para inicializar o domínio de aplicativo padrão.|  
|[Método SetPropertiesForDefaultAppDomain](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setpropertiesfordefaultappdomain-method.md)|Define as propriedades que serão usadas para inicializar o domínio de aplicativo padrão.|  
  
## <a name="remarks"></a>Comentários  
 Para obter uma instância desta interface, chame o [Iclrcontrol](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) método com o tipo de Gerenciador IID `IID_ICLRDomainManager`.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MetaHost.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Hospedagem de Interfaces](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [Hospedagem](../../../../docs/framework/unmanaged-api/hosting/index.md)
