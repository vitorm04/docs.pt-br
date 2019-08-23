---
title: <issuerTokenResolver>
ms.date: 03/30/2017
ms.assetid: f74392f6-3f5b-4880-bd8a-3a9130d31e65
author: BrucePerlerMS
ms.openlocfilehash: da591940910b16d42ef8ab1a05c4b244dbe543f4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942635"
---
# <a name="issuertokenresolver"></a>\<issuerTokenResolver>
Registra o resolvedor de token do emissor que é usado por manipuladores na coleção de manipulador de token. O resolvedor de token do emissor é usado para resolver o token de assinatura em mensagens e tokens de entrada.  
  
 \<system.identityModel>  
\<identityConfiguration>  
\<securityTokenHandlers>  
\<securityTokenHandlerConfiguration>  
\<issuerTokenResolver>  
  
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
|tipo|Especifica o tipo do resolvedor de token emissor. Deve ser a <xref:System.IdentityModel.Tokens.IssuerTokenResolver> classe ou um tipo derivado <xref:System.IdentityModel.Tokens.IssuerTokenResolver> da classe. Necessário.|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|Fornece a configuração para uma coleção de manipuladores de token de segurança.|  
  
## <a name="remarks"></a>Comentários  
 O resolvedor de token do emissor é usado para resolver o token de assinatura em mensagens e tokens de entrada. Ele é usado para recuperar o material criptográfico que é usado para verificar a assinatura. Você deve especificar o `type` atributo. O tipo especificado pode ser <xref:System.IdentityModel.Tokens.IssuerTokenResolver> ou um tipo personalizado que deriva <xref:System.IdentityModel.Tokens.IssuerTokenResolver> da classe.  
  
 Alguns manipuladores de token permitem que você especifique as configurações do resolvedor de token do emissor na configuração. As configurações em manipuladores de token individuais substituem aquelas especificadas na coleção do manipulador de token de segurança.  
  
> [!NOTE]
> A especificação `<issuerTokenResolver>` do elemento como um elemento filho [ \<do elemento > identityConfiguration](identityconfiguration.md) foi preterida, mas ainda tem suporte para compatibilidade com versões anteriores. As configurações no `<securityTokenHandlerConfiguration>` elemento substituem aquelas `<identityConfiguration>` no elemento.  
  
## <a name="example"></a>Exemplo  
 O XML a seguir mostra a configuração para um resolvedor de token de emissor baseado em uma classe personalizada que deriva <xref:System.IdentityModel.Tokens.IssuerTokenResolver>de. O resolvedor de token mantém um dicionário de pares de chave de público-alvo que é inicializado`<AddAudienceKeyPair>`a partir de um elemento de configuração personalizado () definido para a classe. A classe substitui o <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> método para processar esse elemento. A substituição é mostrada no exemplo a seguir; no entanto, os métodos que ele chama não são mostrados para fins de brevidade. Para obter o exemplo completo, consulte `CustomToken` o exemplo.  
  
```xml  
<issuerTokenResolver type="SimpleWebToken.CustomIssuerTokenResolver, SimpleWebToken">  
  <AddAudienceKeyPair  symmetricKey="wAVkldQiFypTQ+kdNdGWCYCHRcee8XmXxOvgmak8vSY=" audience="http://localhost:19851/" />  
</issuerTokenResolver>  
```  
  
## <a name="example"></a>Exemplo  
  
```  
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
