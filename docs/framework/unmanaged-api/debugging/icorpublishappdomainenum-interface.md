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
ms.openlocfilehash: 61cac0922423acabef3d47618d98ddf082d071da
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790672"
---
# <a name="icorpublishappdomainenum-interface"></a>Interface ICorPublishAppDomainEnum
Uma subclasse da interface [ICorPublishEnum](icorpublishenum-interface.md) que fornece métodos para atravessar uma coleção de objetos [ICorPublishAppDomain](icorpublishappdomain-interface.md) que existem atualmente dentro de um processo.  
  
## <a name="methods"></a>{1&gt;Métodos&lt;1}  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método Next](icorpublishappdomainenum-next-method.md)|Obtém o número especificado de instâncias de `ICorPublishAppDomain` da coleção, começando na posição atual.|  
  
## <a name="remarks"></a>Comentários  
 A interface `ICorPublishAppDomainEnum` implementa os métodos da interface abstrata, [ICorPublishEnum](icorpublishenum-interface.md).  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorPub. idl, CorPub. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Depurando interfaces](debugging-interfaces.md)
- [Coclass CorpubPublish](corpubpublish-coclass.md)
