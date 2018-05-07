---
title: Interface ICorPublishEnum
ms.date: 03/30/2017
api_name:
- ICorPublishEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishEnum
helpviewer_keywords:
- ICorPublishEnum interface [.NET Framework debugging]
ms.assetid: 76a136b5-e444-417a-8ade-f1596d597dc7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b3536184fa7798ac8eabe851221ec692c126460b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icorpublishenum-interface"></a>Interface ICorPublishEnum
Serve como a interface base abstrata para os enumeradores que são usados na publicação de informações sobre domínios de aplicativos e processos.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método Clone](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-clone-method.md)|Cria uma cópia deste objeto `ICorPublishEnum`.|  
|[Método GetCount](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-getcount-method.md)|Obtém o número de itens na enumeração.|  
|[Método Reset](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-reset-method.md)|Move o cursor de para o início da enumeração.|  
|[Método Skip](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-skip-method.md)|Move o cursor para a frente na enumeração pelo número especificado de itens.|  
  
## <a name="remarks"></a>Comentários  
 Os seguintes enumeradores derivam `ICorPublishEnum`:  
  
-   [ICorPublishAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)  
  
-   [ICorPublishProcessEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorPub.idl, CorPub.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Coclass CorpubPublish](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)  
 [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
