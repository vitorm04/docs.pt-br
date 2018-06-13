---
title: Interface ICorPublishAppDomainEnum
ms.date: 03/30/2017
api_name:
- ICorPublishAppDomainEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishAppDomainEnum
helpviewer_keywords:
- ICorPublishAppDomainEnum interface [.NET Framework debugging]
ms.assetid: bb798c56-042e-475d-a245-b6fac36d0c07
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 610f62274aea88c1d5f9bbe1456685aa1d3bca68
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423735"
---
# <a name="icorpublishappdomainenum-interface"></a>Interface ICorPublishAppDomainEnum
Uma subclasse do [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) interface que fornece métodos para atravessar uma coleção de [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md) objetos que existem atualmente dentro de um processo.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método Next](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-next-method.md)|Obtém o número especificado de `ICorPublishAppDomain` instâncias da coleção, começando na posição atual.|  
  
## <a name="remarks"></a>Comentários  
 O `ICorPublishAppDomainEnum` interface implementa os métodos da interface abstrata, [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md).  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorPub.idl, CorPub.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Coclass CorpubPublish](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
