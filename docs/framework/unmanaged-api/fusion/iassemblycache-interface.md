---
title: Interface IAssemblyCache
ms.date: 03/30/2017
api_name:
- IAssemblyCache
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCache
helpviewer_keywords:
- IAssemblyCache interface [.NET Framework fusion]
ms.assetid: 71ea170f-872d-4fc5-81b6-27da1dec9b19
topic_type:
- apiref
ms.openlocfilehash: 5ed0075da1429c70900750f3f28e8ce36a41fb28
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134534"
---
# <a name="iassemblycache-interface"></a>Interface IAssemblyCache
Representa o cache de assembly global para uso pela tecnologia Fusion.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método CreateAssemblyCacheItem](iassemblycache-createassemblycacheitem-method.md)|Obtém uma referência a um novo [IAssemblyCacheItem](iassemblycacheitem-interface.md).|  
|[Método CreateAssemblyScavenger](iassemblycache-createassemblyscavenger-method.md)|Reservado para uso interno pela tecnologia Fusion.|  
|[Método InstallAssembly](iassemblycache-installassembly-method.md)|Instala o assembly especificado no cache de assembly global.|  
|[Método QueryAssemblyInfo](iassemblycache-queryassemblyinfo-method.md)|Obtém os dados solicitados sobre o assembly especificado.|  
|[Método UninstallAssembly](iassemblycache-uninstallassembly-method.md)|Desinstala o assembly especificado do cache de assembly global.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** Fusion. h  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interfaces de fusão](fusion-interfaces.md)
- [Cache de assembly global](../../app-domains/gac.md)
