---
title: <add>de <claimTypeRequirements> elemento
ms.date: 03/30/2017
ms.assetid: 3234cd45-1478-468e-8b19-5c50815c4786
ms.openlocfilehash: f6948052c62684faa734b592f5bdfc2e7827a07a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153094"
---
# <a name="add-of-claimtyperequirements-element"></a>\<adicionar> \<de elemento de> claimTypeRequirements
Especifica os tipos de declarações obrigatórias e opcionais esperados para aparecer na credencial federada. Por exemplo, os serviços estabelecem os requisitos nas credenciais recebidas, que devem possuir um determinado conjunto de tipos de sinistros.  
  
[**\<>de configuração**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModelo>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<vinculações>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsfederationhttpvinculando>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<vinculação>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>de segurança**](security-of-custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<mensagem>**](message-element-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequirements>**](claimtyperequirements-for-message.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<adicionar>**
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<claimTypeRequirements>
  <add claimType="URI"
       isOptional="Boolean" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|Claimtype|Um URI que define o tipo de uma reclamação. Por exemplo, para comprar um produto de um site, o usuário deve apresentar um cartão de crédito válido com limite de crédito suficiente. O tipo de reclamação seria o uri do cartão de crédito.|  
|isOptional|Um valor booleano que especifica se isso é para uma reclamação opcional. Defina este `false` atributo para se esta é uma reivindicação necessária.<br /><br /> Você pode usar este atributo quando o serviço pede algumas informações, mas não exige isso. Por exemplo, se você exigir que o usuário digite seu primeiro nome, sobrenome e endereço, mas decida que esse número de telefone é opcional.|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<claimTypeRequirements>](claimtyperequirements-for-message.md)|Especifica uma coleção de tipos de sinistros necessários. Cada elemento é <xref:System.ServiceModel.Configuration.ClaimTypeElement>do tipo.<br /><br /> Em um cenário federado, os serviços estabelecem os requisitos das credenciais recebidas. Por exemplo, as credenciais recebidas devem possuir um certo conjunto de tipos de reclamações. Cada elemento desta coleção especifica os tipos de reivindicações necessárias e opcionais que se espera que apareçam em uma credencial federada.|  
  
## <a name="remarks"></a>Comentários  
 Em um cenário federado, os serviços estabelecem os requisitos das credenciais recebidas. Por exemplo, as credenciais recebidas devem possuir um certo conjunto de tipos de reclamações. Essa exigência se manifesta em uma política de segurança. Quando um cliente solicita credenciais de um serviço federado (por exemplo, CardSpace), ele coloca os requisitos em uma solicitação de token (RequestSecurityToken) para que o serviço federado possa emitir as credenciais que satisfaçam os requisitos em conformidade.  
  
## <a name="example"></a>Exemplo  
 A configuração a seguir adiciona dois requisitos de tipo de solicitação a uma vinculação de segurança.  
  
```xml  
<bindings>
  <wsFederationHttpBinding>
    <binding name="myFederatedBinding">
      <security mode="Message">
        <message issuedTokenType="urn:oasis:names:tc:SAML:1.0:assertion">
          <claimTypeRequirements>
            <add claimType="http://schemas.microsoft.com/ws/2005/05/identity/claims/EmailAddress" />
            <add claimType="http://schemas.microsoft.com/ws/2005/05/identity/claims/UserName"
                 optional="true" />
          </claimTypeRequirements>
        </message>
      </security>
    </binding>
  </wsFederationHttpBinding>
</bindings>
```  
  
## <a name="see-also"></a>Confira também

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
