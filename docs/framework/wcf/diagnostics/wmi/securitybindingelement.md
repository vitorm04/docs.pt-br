---
title: SecurityBindingElement
ms.date: 03/30/2017
ms.assetid: ef93b6e6-3524-48a8-94d3-c8837f1872f9
author: BrucePerlerMS
ms.openlocfilehash: 19c65b3028ad63b8a78205d00f44cc32322648d5
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47069968"
---
# <a name="securitybindingelement"></a>SecurityBindingElement
SecurityBindingElement  
  
## <a name="syntax"></a>Sintaxe  
  
```  
class SecurityBindingElement : BindingElement  
{  
  string DefaultAlgorithmSuite;  
  boolean IncludeTimestamp;  
  string KeyEntropyMode;  
  LocalServiceSecuritySettings LocalServiceSecuritySettings;  
  string MessageSecurityVersion;  
  string SecurityHeaderLayout;  
};  
```  
  
## <a name="methods"></a>Métodos  
 A classe SecurityBindingElement não define quaisquer métodos.  
  
## <a name="properties"></a>Propriedades  
 A classe SecurityBindingElement tem as seguintes propriedades:  
  
### <a name="defaultalgorithmsuite"></a>defaultAlgorithmSuite  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 Especifica os algoritmos para usar com a associação.  
  
### <a name="includetimestamp"></a>includeTimestamp  
 Tipo de dados: boolean  
  
 Tipo de acesso: somente leitura  
  
 Um valor booliano que especifica se cada mensagem contém um carimbo de hora.  
  
### <a name="keyentropymode"></a>keyEntropyMode  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 A origem da entropia usada para criar chaves.  
  
### <a name="localservicesecuritysettings"></a>LocalServiceSecuritySettings  
 Tipo de dados: LocalServiceSecuritySettings  
  
 Tipo de acesso: somente leitura  
  
 As propriedades específicas de segurança de associação para o serviço local.  
  
### <a name="messagesecurityversion"></a>messageSecurityVersion  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 A versão usada para segurança de mensagem.  
  
### <a name="securityheaderlayout"></a>securityHeaderLayout  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 A ordem dos elementos no cabeçalho de segurança para essa associação.  
  
## <a name="requirements"></a>Requisitos  
  
|MOF|Declarado em Servicemodel.mof.|  
|---------|-----------------------------------|  
|Namespace|Definido no root\ServiceModel|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Channels.SecurityBindingElement>
