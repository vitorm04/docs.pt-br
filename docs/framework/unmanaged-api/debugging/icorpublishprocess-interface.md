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
ms.openlocfilehash: 3ae48df9e66890161c1aef944d37b0a279939d56
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790537"
---
# <a name="icorpublishprocess-interface"></a>Interface ICorPublishProcess
Fornece métodos que acessam informações a serem exibidas sobre um processo.  
  
## <a name="methods"></a>{1&gt;Métodos&lt;1}  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método EnumAppDomains](icorpublishprocess-enumappdomains-method.md)|Obtém uma instância de [ICorPublishAppDomainEnum](icorpublishappdomainenum-interface.md) que contém os domínios de aplicativo no processo referenciado por este `ICorPublishProcess`.|  
|[Método GetDisplayName](icorpublishprocess-getdisplayname-method.md)|Obtém o caminho completo do executável para o processo referenciado por este `ICorPublishProcess`.|  
|[Método GetProcessID](icorpublishprocess-getprocessid-method.md)|Obtém o identificador do sistema operacional para o processo referenciado por este `ICorPublishProcess`.|  
|[Método IsManaged](icorpublishprocess-ismanaged-method.md)|Obtém um valor que indica se o processo referenciado por essa `ICorPublishProcess` é conhecido por estar executando código gerenciado.|  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorPub. idl, CorPub. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Depurando interfaces](debugging-interfaces.md)
- [Coclass CorpubPublish](corpubpublish-coclass.md)
