---
title: Interface ICorPublishProcess
ms.date: 03/30/2017
api_name:
- ICorPublishProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess
helpviewer_keywords:
- ICorPublishProcess interface [.NET Framework debugging]
ms.assetid: 6d1dc41b-8aa2-4889-bb00-1cbccc00c123
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 08dfa3ddbfd9cffdb0cb88d0325e5703a854668a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61993506"
---
# <a name="icorpublishprocess-interface"></a>Interface ICorPublishProcess
Fornece métodos que acessam informações a serem exibidos sobre um processo.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método EnumAppDomains](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-enumappdomains-method.md)|Obtém uma [ICorPublishAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md) instância que contém os domínios de aplicativo no processo de referenciada por este `ICorPublishProcess`.|  
|[Método GetDisplayName](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-getdisplayname-method.md)|Obtém o caminho completo do executável para o processo referenciado por este `ICorPublishProcess`.|  
|[Método GetProcessID](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-getprocessid-method.md)|Obtém o identificador de sistema operacional para o processo referenciado por este `ICorPublishProcess`.|  
|[Método IsManaged](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-ismanaged-method.md)|Obtém um valor que indica se o processo é referenciada por este `ICorPublishProcess` é conhecido por estar em execução para código gerenciado.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorPub.idl, CorPub.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Coclass CorpubPublish](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
