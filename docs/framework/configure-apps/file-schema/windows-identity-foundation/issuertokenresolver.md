---
title: <issuerTokenResolver>
ms.date: 03/30/2017
ms.assetid: f74392f6-3f5b-4880-bd8a-3a9130d31e65
author: BrucePerlerMS
ms.openlocfilehash: 67d7e0aa5b6b05bfe8b17a1b1efebb1fbddbb0eb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152665"
---
# <a name="issuertokenresolver"></a>\<emissorTokenResolver>
Registra o resolver token emissor usado pelos manipuladores na coleção de manipuladores de tokens. O resolver token do emissor é usado para resolver o token de assinatura em tokens e mensagens recebidas.  
  
[**\<>de configuração**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<>de configuração de identidade**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>de segurançaTokenHandlers**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<Configuradodefalha>**](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<emissorTokenResolver>**  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <issuerTokenResolver type=xs:string>  
        </issuerTokenResolver>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|type|Especifica o tipo de solução de token do emissor. Deve ser <xref:System.IdentityModel.Tokens.IssuerTokenResolver> a classe ou um tipo <xref:System.IdentityModel.Tokens.IssuerTokenResolver> que deriva da classe. Obrigatórios.|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<Configuradodefalha>](securitytokenhandlerconfiguration.md)|Fornece configuração para uma coleção de manipuladores de tokens de segurança.|  
  
## <a name="remarks"></a>Comentários  
 O resolver token do emissor é usado para resolver o token de assinatura em tokens e mensagens recebidas. Ele é usado para recuperar o material criptográfico que é usado para verificar a assinatura. Você deve `type` especificar o atributo. O tipo especificado <xref:System.IdentityModel.Tokens.IssuerTokenResolver> pode ser um ou um <xref:System.IdentityModel.Tokens.IssuerTokenResolver> tipo personalizado que deriva da classe.  
  
 Alguns manipuladores de token permitem que você especifique as configurações de resolução de token sitor na configuração. As configurações em manipuladores de token individuais anulam as especificadas na coleção de manipuladores de tokens de segurança.  
  
> [!NOTE]
> Especificando `<issuerTokenResolver>` o elemento como elemento filho do [ \<](identityconfiguration.md) elemento identityConfiguration>foi preterido, mas ainda é suportado para compatibilidade retrógrada. As configurações `<securityTokenHandlerConfiguration>` do elemento sobrepõem as do `<identityConfiguration>` elemento.  
  
## <a name="example"></a>Exemplo  
 O XML a seguir mostra a configuração de um resolver token <xref:System.IdentityModel.Tokens.IssuerTokenResolver>de emissor que é baseado em uma classe personalizada que deriva de . O token resolver mantém um dicionário de pares de chave de`<AddAudienceKeyPair>`audiência que é inicializado a partir de um elemento de configuração personalizado ( ) definido para a classe. A classe substitui <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> o método para processar esse elemento. A substituição é mostrada no exemplo a seguir; no entanto, os métodos que ele chama não são mostrados para a brevidade. Para o exemplo completo, veja a `CustomToken` amostra.  
  
```xml  
<issuerTokenResolver type="SimpleWebToken.CustomIssuerTokenResolver, SimpleWebToken">  
  <AddAudienceKeyPair  symmetricKey="wAVkldQiFypTQ+kdNdGWCYCHRcee8XmXxOvgmak8vSY=" audience="http://localhost:19851/" />  
</issuerTokenResolver>  
```  
  
## <a name="example"></a>Exemplo
  
```csharp
public override void LoadCustomConfiguration(System.Xml.XmlNodeList nodelist)  
{  
    foreach (XmlNode node in nodelist)  
    {  
        XmlDictionaryReader rdr = XmlDictionaryReader.CreateDictionaryReader(new XmlTextReader(new StringReader(node.OuterXml)));  
        rdr.MoveToContent();  
  
        string symmetricKey = rdr.GetAttribute("symmetricKey");  
        string audience = rdr.GetAttribute("audience");  
  
        this.AddAudienceKeyPair(audience, symmetricKey);  
    }  
}  
```
  
## <a name="see-also"></a>Confira também

- <xref:System.IdentityModel.Tokens.IssuerTokenResolver>
