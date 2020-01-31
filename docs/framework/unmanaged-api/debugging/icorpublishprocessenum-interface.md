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
ms.openlocfilehash: 188ff8feabd704d828256a09aca20f9db2227f2c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790502"
---
# <a name="icorpublishprocessenum-interface"></a>Interface ICorPublishProcessEnum
Uma subclasse da interface [ICorPublishEnum](icorpublishenum-interface.md) que fornece métodos para atravessar uma coleção de objetos [ICorPublishProcess](icorpublishprocess-interface.md) .  
  
## <a name="methods"></a>{1&gt;Métodos&lt;1}  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método Next](icorpublishprocessenum-next-method.md)|Obtém o número especificado de instâncias de `ICorPublishProcess` da coleção, começando na posição atual.|  
  
## <a name="remarks"></a>Comentários  
 A interface `ICorPublishProcessEnum` implementa os métodos da interface abstrata, [ICorPublishEnum](icorpublishenum-interface.md).  
  
 Uma instância de `ICorPublishProcessEnum` é criada pelo método [ICorPublish:: EnumProcesses](icorpublish-enumprocesses-method.md) . A passagem da coleção de objetos de `ICorPublishProcess` é baseada nos critérios de filtro fornecidos no momento em que a instância de `ICorPublishProcessEnum` foi criada.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorPub. idl, CorPub. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Depurando interfaces](debugging-interfaces.md)
- [Coclass CorpubPublish](corpubpublish-coclass.md)
