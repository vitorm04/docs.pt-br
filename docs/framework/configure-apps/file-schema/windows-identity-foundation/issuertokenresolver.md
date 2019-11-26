---
title: <issuerTokenResolver>
ms.date: 03/30/2017
ms.assetid: f74392f6-3f5b-4880-bd8a-3a9130d31e65
author: BrucePerlerMS
ms.openlocfilehash: 451750a1facd9a886b53427a8d54580d1a939fa5
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73968506"
---
# <a name="issuertokenresolver"></a>\<issuerTokenResolver >
Registra o resolvedor de token do emissor que é usado por manipuladores na coleção de manipulador de token. O resolvedor de token do emissor é usado para resolver o token de assinatura em mensagens e tokens de entrada.  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. identityModel >** ](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlers >** ](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlerConfiguration**](securitytokenhandlerconfiguration.md) >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<issuerTokenResolver >**  
  
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
|tipo|Especifica o tipo do resolvedor de token emissor. Deve ser a classe <xref:System.IdentityModel.Tokens.IssuerTokenResolver> ou um tipo derivado da classe <xref:System.IdentityModel.Tokens.IssuerTokenResolver>. Necessário.|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration >](securitytokenhandlerconfiguration.md)|Fornece a configuração para uma coleção de manipuladores de token de segurança.|  
  
## <a name="remarks"></a>Comentários  
 O resolvedor de token do emissor é usado para resolver o token de assinatura em mensagens e tokens de entrada. Ele é usado para recuperar o material criptográfico que é usado para verificar a assinatura. Você deve especificar o atributo `type`. O tipo especificado pode ser <xref:System.IdentityModel.Tokens.IssuerTokenResolver> ou um tipo personalizado derivado da classe <xref:System.IdentityModel.Tokens.IssuerTokenResolver>.  
  
 Alguns manipuladores de token permitem que você especifique as configurações do resolvedor de token do emissor na configuração. As configurações em manipuladores de token individuais substituem aquelas especificadas na coleção do manipulador de token de segurança.  
  
> [!NOTE]
> A especificação do elemento `<issuerTokenResolver>` como um elemento filho do elemento [\<identityConfiguration >](identityconfiguration.md) foi preterida, mas ainda tem suporte para compatibilidade com versões anteriores. As configurações no elemento `<securityTokenHandlerConfiguration>` substituem aquelas no elemento `<identityConfiguration>`.  
  
## <a name="example"></a>Exemplo  
 O XML a seguir mostra a configuração para um resolvedor de token de emissor baseado em uma classe personalizada que deriva de <xref:System.IdentityModel.Tokens.IssuerTokenResolver>. O resolvedor de token mantém um dicionário de pares de chave de público-alvo que é inicializado a partir de um elemento de configuração personalizado (`<AddAudienceKeyPair>`) definido para a classe. A classe substitui o método <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> para processar esse elemento. A substituição é mostrada no exemplo a seguir; no entanto, os métodos que ele chama não são mostrados para fins de brevidade. Para obter o exemplo completo, consulte o exemplo de `CustomToken`.  
  
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
  
## <a name="see-also"></a>Consulte também

- <xref:System.IdentityModel.Tokens.IssuerTokenResolver>
