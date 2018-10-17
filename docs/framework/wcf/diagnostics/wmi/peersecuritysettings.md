---
title: PeerSecuritySettings
ms.date: 03/30/2017
ms.assetid: 24ae0d35-f3a3-419b-afd6-686e22aae27b
author: BrucePerlerMS
ms.openlocfilehash: 18caaf2750fa3a263c09176e975204258330752c
ms.sourcegitcommit: e42d09e5966dd9fd02847d3e7eeb4ec0877069f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2018
ms.locfileid: "49371622"
---
# <a name="peersecuritysettings"></a>PeerSecuritySettings
PeerSecuritySettings  
  
## <a name="syntax"></a>Sintaxe  
  
```csharp
class PeerSecuritySettings  
{  
  string Mode;  
  PeerTransportSecuritySettings Transport;  
};  
```  
  
## <a name="methods"></a>Métodos  
 A classe PeerSecuritySettings não define quaisquer métodos.  
  
## <a name="properties"></a>Propriedades  
 A classe PeerSecuritySettings tem as seguintes propriedades:  
  
### <a name="mode"></a>Modo  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 Se no nível da mensagem e segurança em nível de transporte são usados por um ponto de extremidade configurado com a associação.  
  
### <a name="transport"></a>Transporte  
 Tipo de dados: PeerTransportSecuritySettings  
  
 Tipo de acesso: somente leitura  
  
 Configurações de segurança de transporte.  
  
## <a name="requirements"></a>Requisitos  
  
|MOF|Declarado em Servicemodel.mof.|  
|---------|-----------------------------------|  
|Namespace|Definido no root\ServiceModel|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.PeerSecuritySettings>
