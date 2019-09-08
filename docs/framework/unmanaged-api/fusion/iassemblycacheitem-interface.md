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
ms.openlocfilehash: 193604068e379d62107b25f2bc348cd7c8bc6e98
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796711"
---
# <a name="iassemblycacheitem-interface"></a>Interface IAssemblyCacheItem
Representa um único assembly no cache de assembly global.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método AbortItem](iassemblycacheitem-abortitem-method.md)|Permite que o assembly no cache de assembly global execute operações de limpeza antes que ele seja liberado.|  
|[Método Commit](iassemblycacheitem-commit-method.md)|Confirma a referência de assembly armazenada em cache para a memória.|  
|[Método CreateStream](iassemblycacheitem-createstream-method.md)|Cria um fluxo com o nome e o formato especificados.|  
  
## <a name="requirements"></a>Requisitos  
 **Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** Fusion. h  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interfaces de fusão](fusion-interfaces.md)
- [Cache de assembly global](../../app-domains/gac.md)
- [Interface IAssemblyCache](iassemblycache-interface.md)
