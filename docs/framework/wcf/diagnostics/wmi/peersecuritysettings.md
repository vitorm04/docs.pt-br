---
title: PeerSecuritySettings
ms.date: 03/30/2017
ms.assetid: 24ae0d35-f3a3-419b-afd6-686e22aae27b
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 58b372f26fee7dc180d75731fd4855db569c87c7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33484512"
---
# <a name="peersecuritysettings"></a>PeerSecuritySettings
PeerSecuritySettings  
  
## <a name="syntax"></a>Sintaxe  
  
```  
class PeerSecuritySettings  
{  
  string Mode;  
  PeerTransportSecuritySettings Transport;  
};  
```  
  
## <a name="methods"></a>Métodos  
 A classe PeerSecuritySettings não define nenhum método.  
  
## <a name="properties"></a>Propriedades  
 A classe PeerSecuritySettings tem as seguintes propriedades:  
  
### <a name="mode"></a>Modo  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 Se nível de mensagem e segurança em nível de transporte são usados por um ponto de extremidade configurado com a associação.  
  
### <a name="transport"></a>Transporte  
 Tipo de dados: PeerTransportSecuritySettings  
  
 Tipo de acesso: somente leitura  
  
 Configurações de segurança de transporte.  
  
## <a name="requirements"></a>Requisitos  
  
|MOF|Declarado em Servicemodel.mof.|  
|---------|-----------------------------------|  
|Namespace|Definido em root\ServiceModel|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.PeerSecuritySettings>
