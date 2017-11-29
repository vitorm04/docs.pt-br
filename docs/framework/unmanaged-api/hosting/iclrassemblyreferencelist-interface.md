---
title: Interface ICLRAssemblyReferenceList
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRAssemblyReferenceList
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRAssemblyReferenceList
helpviewer_keywords: ICLRAssemblyReferenceList interface [.NET Framework hosting]
ms.assetid: 5f890fdf-d22a-429e-a35f-135273d1a636
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4249616ca46fe5ef09dce4a3e245794a103298c1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrassemblyreferencelist-interface"></a>Interface ICLRAssemblyReferenceList
Gerencia uma lista de assemblies que são carregados pelo common language runtime (CLR) e não pelo host.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método IsAssemblyReferenceInList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-isassemblyreferenceinlist-method.md)|Obtém um valor que indica se o ponteiro fornecido faz referência a um assembly na lista.|  
|[Método IsStringAssemblyReferenceInList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-isstringassemblyreferenceinlist-method.md)|Obtém um valor que indica se o nome fornecido corresponde ao nome de um assembly na lista.|  
  
## <a name="remarks"></a>Comentários  
 Chamar o [: Getclrassemblyreferencelist](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md) método para obter um ponteiro para uma instância de `ICLRAssemblyReferenceList`.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICLRAssemblyIdentityManager](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [Interface IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)  
 [Interfaces de hospedagem](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
