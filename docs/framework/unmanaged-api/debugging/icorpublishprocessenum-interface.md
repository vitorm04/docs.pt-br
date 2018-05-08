---
title: Interface ICorPublishProcessEnum
ms.date: 03/30/2017
api_name:
- ICorPublishProcessEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcessEnum
helpviewer_keywords:
- ICorPublishProcessEnum interface [.NET Framework debugging]
ms.assetid: aac8fcf9-ac09-437c-bd5c-2fda14ae1007
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dd71a2bd4a52da8fa77592363e2eb7c8f5101fd3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icorpublishprocessenum-interface"></a>Interface ICorPublishProcessEnum
Uma subclasse do [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) interface que fornece métodos para atravessar uma coleção de [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) objetos.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método Next](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-next-method.md)|Obtém o número especificado de `ICorPublishProcess` instâncias da coleção, começando na posição atual.|  
  
## <a name="remarks"></a>Comentários  
 O `ICorPublishProcessEnum` interface implementa os métodos da interface abstrata, [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md).  
  
 Um `ICorPublishProcessEnum` instância é criada pelo [Icorpublish](../../../../docs/framework/unmanaged-api/debugging/icorpublish-enumprocesses-method.md) método. A passagem do conjunto de `ICorPublishProcess` objetos é com base nos critérios de filtro fornecidos no momento em que o `ICorPublishProcessEnum` instância foi criada.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorPub.idl, CorPub.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Coclass CorpubPublish](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
