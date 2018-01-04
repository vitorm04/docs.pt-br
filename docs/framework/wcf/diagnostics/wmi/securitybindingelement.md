---
title: SecurityBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ef93b6e6-3524-48a8-94d3-c8837f1872f9
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 5de844bc2741768e1b3c53278f20ad4900ffaac1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
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
 A classe SecurityBindingElement não define nenhum método.  
  
## <a name="properties"></a>Propriedades  
 A classe SecurityBindingElement tem as seguintes propriedades:  
  
### <a name="defaultalgorithmsuite"></a>defaultAlgorithmSuite  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 Especifica os algoritmos para usar com a associação.  
  
### <a name="includetimestamp"></a>includeTimestamp  
 Tipo de dados: boolean  
  
 Tipo de acesso: somente leitura  
  
 Um valor booleano que especifica se cada mensagem contém um carimbo de hora.  
  
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
|Namespace|Definido em root\ServiceModel|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Channels.SecurityBindingElement>
