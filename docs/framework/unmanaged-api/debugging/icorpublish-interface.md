---
title: Interface ICorPublish
ms.date: 03/30/2017
api_name:
- ICorPublish
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublish
helpviewer_keywords:
- ICorPublish interface [.NET Framework debugging]
ms.assetid: 87c4fcb2-7703-4a2e-afb6-42973381b960
topic_type:
- apiref
ms.openlocfilehash: 1bd2f537cfa6a27c24ba91ea7caa29dc9e71a74e
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396319"
---
# <a name="icorpublish-interface"></a>Interface ICorPublish
O serve como interface geral para publicar informações sobre processos e informações sobre os domínios de aplicativo nesses processos.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método EnumProcesses](icorpublish-enumprocesses-method.md)|Obtém uma instância de [ICorPublishProcessEnum](icorpublishprocessenum-interface.md) que contém os processos gerenciados em execução neste computador.|  
|[Método GetProcess](icorpublish-getprocess-method.md)|Obtém uma instância de [ICorPublishProcess](icorpublishprocess-interface.md) que representa o processo com o identificador especificado.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorPub. idl, CorPub. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Depurando interfaces](debugging-interfaces.md)
- [Coclass CorpubPublish](corpubpublish-coclass.md)
