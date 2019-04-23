---
title: SecurityBindingElement
ms.date: 03/30/2017
ms.assetid: ef93b6e6-3524-48a8-94d3-c8837f1872f9
ms.openlocfilehash: 1d367d0c5d14e6e75539dd2b20cdffcf2b34963d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59975553"
---
# <a name="securitybindingelement"></a>SecurityBindingElement
SecurityBindingElement  
  
## <a name="syntax"></a>Sintaxe  
  
```csharp
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
  
### <a name="defaultalgorithmsuite"></a>DefaultAlgorithmSuite  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: Somente leitura  
  
 Especifica os algoritmos para usar com a associação.  
  
### <a name="includetimestamp"></a>IncludeTimestamp  
 Tipo de dados: boolean  
  
 Tipo de acesso: Somente leitura  
  
 Um valor booliano que especifica se cada mensagem contém um carimbo de hora.  
  
### <a name="keyentropymode"></a>KeyEntropyMode  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: Somente leitura  
  
 A origem da entropia usada para criar chaves.  
  
### <a name="localservicesecuritysettings"></a>LocalServiceSecuritySettings  
 Tipo de dados: LocalServiceSecuritySettings  
  
 Tipo de acesso: Somente leitura  
  
 As propriedades específicas de segurança de associação para o serviço local.  
  
### <a name="messagesecurityversion"></a>MessageSecurityVersion  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: Somente leitura  
  
 A versão usada para segurança de mensagem.  
  
### <a name="securityheaderlayout"></a>SecurityHeaderLayout  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: Somente leitura  
  
 A ordem dos elementos no cabeçalho de segurança para essa associação.  
  
## <a name="requirements"></a>Requisitos  
  
|MOF|Declarado em Servicemodel.mof.|  
|---------|-----------------------------------|  
|Namespace|Definido no root\ServiceModel|  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Channels.SecurityBindingElement>
