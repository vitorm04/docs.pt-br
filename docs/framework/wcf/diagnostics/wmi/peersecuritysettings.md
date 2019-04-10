---
title: PeerSecuritySettings
ms.date: 03/30/2017
ms.assetid: 24ae0d35-f3a3-419b-afd6-686e22aae27b
ms.openlocfilehash: 1c33e1ce710fea3b1698a6dab47a199e40388f5a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59217881"
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
  
 Tipo de acesso: Somente leitura  
  
 Se no nível da mensagem e segurança em nível de transporte são usados por um ponto de extremidade configurado com a associação.  
  
### <a name="transport"></a>Transporte  
 Tipo de dados: PeerTransportSecuritySettings  
  
 Tipo de acesso: Somente leitura  
  
 Configurações de segurança de transporte.  
  
## <a name="requirements"></a>Requisitos  
  
|MOF|Declarado em Servicemodel.mof.|  
|---------|-----------------------------------|  
|Namespace|Definido no root\ServiceModel|  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.PeerSecuritySettings>
