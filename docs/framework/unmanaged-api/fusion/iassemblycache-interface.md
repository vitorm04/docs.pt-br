---
title: Interface IAssemblyCache
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IAssemblyCache
api_location: fusion.dll
api_type: COM
f1_keywords: IAssemblyCache
helpviewer_keywords: IAssemblyCache interface [.NET Framework fusion]
ms.assetid: 71ea170f-872d-4fc5-81b6-27da1dec9b19
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6244e6c3b0cc88c50cda050a480f5af5b3996b47
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="iassemblycache-interface"></a>Interface IAssemblyCache
Representa o cache de assembly global para uso pela tecnologia de fusão.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método CreateAssemblyCacheItem](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-createassemblycacheitem-method.md)|Obtém uma referência a um novo [IAssemblyCacheItem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md).|  
|[Método CreateAssemblyScavenger](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-createassemblyscavenger-method.md)|Reservado para uso interno pela tecnologia de fusão.|  
|[Método InstallAssembly](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-installassembly-method.md)|Instala o assembly especificado no cache de assembly global.|  
|[Método QueryAssemblyInfo](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-queryassemblyinfo-method.md)|Obtém os dados solicitados sobre o assembly especificado.|  
|[Método UninstallAssembly](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-uninstallassembly-method.md)|Desinstala o assembly especificado do cache de assembly global.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Fusion.h  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de fusão](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [Cache de assembly global](../../../../docs/framework/app-domains/gac.md)
