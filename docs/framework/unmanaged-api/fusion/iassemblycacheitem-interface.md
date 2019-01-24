---
title: Interface IAssemblyCacheItem
ms.date: 03/30/2017
api_name:
- IAssemblyCacheItem
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCacheItem
helpviewer_keywords:
- IAssemblyCacheItem interface [.NET Framework fusion]
ms.assetid: ccc9387a-9f44-4f4f-bf8f-0ea6d2afa21b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d89a531ad09e6865bd9c7dad00c1d8c1840fab8f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54662160"
---
# <a name="iassemblycacheitem-interface"></a>Interface IAssemblyCacheItem
Representa um único assembly no cache de assembly global.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método AbortItem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-abortitem-method.md)|Permite que o assembly no cache de assembly global executar operações de limpeza antes do lançamento.|  
|[Método Commit](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-commit-method.md)|Confirma a referência de assembly em cache na memória.|  
|[Método CreateStream](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-createstream-method.md)|Cria um fluxo com o nome especificado e o formato.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Fusion.h  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Interfaces de fusão](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
- [Cache de assembly global](../../../../docs/framework/app-domains/gac.md)
- [Interface IAssemblyCache](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)
