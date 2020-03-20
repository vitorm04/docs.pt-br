---
title: <wsFederation>
ms.date: 03/30/2017
ms.assetid: c537f770-68bd-4f82-96ad-6424ad91369f
author: BrucePerlerMS
ms.openlocfilehash: 53f3943524c45a43ddb60553b8ff45f19df66b14
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152457"
---
# <a name="wsfederation"></a>\<wsFederation>
Fornece configuração <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> para o (WSFAM).  
  
[**\<>de configuração**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<federaçãoconfiguração>**](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>da WSFederation**  
  
## <a name="syntax"></a>Sintaxe  
  
```xml
<system.identityModel.services>  
  <federationConfiguration>  
    <wsFederation authenticationType=xs:string (URI)  
                  freshness=xs:decimal  
                  homerealm=xs:string (URI)  
                  issuer=xs:string (URI)  
                  persistentCookiesOnPassiveRedirects=xs:boolean  
                  passiveRedirectEnabled=xs:boolean  
                  policy=xs:string (URI)  
                  realm=xs:string (URI)  
                  reply=xs:string (URI)  
                  request=xs:string (URI)  
                  requestPtr=xs:string (URI)  
                  requireHttps=xs:boolean  
                  resource=xs:string (URI)  
                  signInQueryString=xs:string  
                  signOutQueryString=xs:string  
                  signOutReply=xs:string (URL)  
    </wsFederation>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|authenticationType|Um URI que especifica o tipo de autenticação. Define o parâmetro wauth de solicitação de login wuth da WS-Federação. Opcional. O padrão é uma seqüência de string vazia, que especifica que o parâmetro wauth não está incluído na solicitação.|  
|Frescor|A idade máxima desejada de pedidos de autenticação, em minutos. Define o parâmetro wfresh de solicitação de login ws-Federation. Opcional. O padrão é zero. Opcional. **Aviso:**  Na próxima versão do .NET Framework `freshness` 4.5, `xs:string` o atributo será `null`do tipo e seu valor padrão será .|  
|homeReal|O reino doméstico do provedor de identidade (IdP) para usar para autenticação. Define o parâmetro ws-federation de solicitação de solicitação whr. Opcional. O padrão é uma seqüência de string vazia, que especifica que o parâmetro whr não está incluído na solicitação.|  
|emissor|O URI do emissor de token pretendido. Define a URL base das solicitações de login da WS-Federation e solicitações de saída necessárias.|  
|persistenteCookiesonPassiveRedirects|Especifica se os cookies persistentes são emitidos na autenticação. Opcional. O padrão é "falso", os cookies não são emitidos.|  
|passivoRedirectEnabled|Especifica se o WSFAM está habilitado a redirecionar automaticamente solicitações não autorizadas para um STS. Opcional. O padrão é "verdadeiro", as solicitações não autorizadas são automaticamente redirecionadas.|  
|policy|Uma URL que especifica a localização da diretiva relevante para usar nas solicitações de login. O padrão é uma cadeia de caracteres vazia. Define o parâmetro wp de solicitação de login ws-federation. Opcional. O padrão é uma seqüência de string vazia, que especifica que o parâmetro wp não está incluído na solicitação.|  
|Reino|O URI do reino solicitante. (Um URI que identifica a parte de dependência (RP) para o serviço de token de segurança (STS).) Define o parâmetro de solicitação wtrealm WS-Federation sign-in request-. Obrigatórios.|  
|Resposta|Uma URL que identifica o endereço no qual o aplicativo de parte de fundo (RP) gostaria de receber respostas do Security Token Service (STS). Define o parâmetro wreply de solicitação de solicitação wreply do WS-Federation. Opcional. O padrão é uma seqüência de string vazia, que especifica que o parâmetro wreply não está incluído na solicitação.|  
|solicitação|O pedido de emissão de tokens. Define o parâmetro wreq de solicitação wreq de solicitação wreq da WS-Federação. Opcional. O padrão é uma seqüência de string vazia, que especifica que o parâmetro wreq não está incluído na solicitação. Não incluir o wreq ou o parâmetro wreqptr na solicitação implica que o STS sabe que tipo de token emitir.|  
|solicitarPtr|Uma URL que especifica a localização da solicitação de emissão de tokens. Define o parâmetro de solicitação wreqptr. Opcional. O padrão é uma seqüência de string vazia, que especifica que o parâmetro wreqptr não está incluído na solicitação. Não incluir o wreq ou o parâmetro wreqptr na solicitação implica que o STS sabe que tipo de token emitir.|  
|requeremHttps|Especifica se a comunicação com o serviço de token de segurança (STS) deve usar o protocolo HTTPS. Opcional. O padrão é "verdadeiro", HTTPS deve ser usado.|  
|recurso|Um URI que identifica o recurso que está sendo acessado, o rp (relying party) para o serviço de token de segurança (STS). Opcional. Define o parâmetro ws-federation de solicitação wres. Opcional. O padrão é uma seqüência de string vazia, que especifica que o parâmetro wres não está incluído na solicitação. **Nota:** wres é um parâmetro legado. Especifique o atributo `realm` para usar o parâmetro wtrealm em vez disso.|  
|signInQueryString|Fornece um ponto de extensibilidade para especificar parâmetros de consulta definidos pelo aplicativo na URL de solicitação de login do WS-Federation. Opcional. O padrão é uma seqüência de string vazia, que especifica que nenhum parâmetro adicional deve ser incluído na solicitação. Os parâmetros são especificados como um fragmento `"param1=value1&param2=value2&param3=value3"` de seqüência de consulta usando o seguinte formulário: e assim por diante. **Nota:**  Em um arquivo de configuração, o caractere '&' na seqüência de consultas deve ser especificado usando sua referência de entidade, `&`.|  
|signOutQueryString|Fornece um ponto de extensibilidade para especificar parâmetros de consulta definidos pelo aplicativo na URL de solicitação de login do WS-Federation. Opcional. O padrão é uma seqüência de string vazia, que especifica que nenhum parâmetro adicional deve ser incluído na solicitação. Os parâmetros são especificados como um fragmento `"param1=value1&param2=value2&param3=value3"` de seqüência de consulta usando o seguinte formulário: e assim por diante. **Nota:**  Em um arquivo de configuração, o caractere '&' na seqüência de consultas deve ser especificado usando sua referência de entidade, `&`.|  
|signOutReply|Especifica a URL para a qual o cliente deve ser redirecionado pelo serviço de token de segurança (STS) durante a saída passiva através do protocolo WS-Federação. Define o parâmetro wreply em uma solicitação de saída wS-Federação. Opcional. O padrão é uma seqüência de string vazia, que especifica que nenhum parâmetro adicional deve ser incluído na solicitação.|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<federaçãoconfiguração>](federationconfiguration.md)|Contém as configurações que <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> configuram o (WSFAM) e o <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).|  
  
## <a name="remarks"></a>Comentários  
 Você pode `<wsFederation>` usar o elemento para configurar as configurações padrão do parâmetro WS-Federation e o comportamento padrão do WSFAM. Configurações de parâmetros WS-Federação definidas sob `<wsFederation>` <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> o conjunto de elementos propriedades equivalentes expostas pela classe. Essas propriedades permanecem as mesmas para todas as solicitações emitidas pelo WSFAM. Você pode alterar os parâmetros do WS-Federation dinamicamente durante o processamento de solicitações adicionando manipuladores de eventos para os eventos expostos pelo WSFAM; por exemplo, <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.RedirectingToIdentityProvider> o evento. Para obter mais informações, <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> consulte a documentação da aula.  
  
 O `<wsFederation>` elemento é <xref:System.IdentityModel.Services.Configuration.WSFederationElement> representado pela classe. O objeto de configuração <xref:System.IdentityModel.Services.Configuration.WsFederationConfiguration> em si é representado pela classe. Uma <xref:System.IdentityModel.Services.Configuration.WsFederationConfiguration> única instância é <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> definida no objeto <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> que é acessado através da propriedade e fornece configuração para o WSFAM.  
  
## <a name="example"></a>Exemplo  
 O XML a `<wsFederation>` seguir mostra um elemento que especifica as configurações para o WSFAM.  
  
> [!WARNING]
> Neste exemplo, o WSFAM não é obrigado a usar HTTPS. Isso porque `requireHttps` o atributo `<wsFederation>` no `false`elemento está definido . Esta configuração não é recomendada para a maioria dos ambientes de produção, pois pode apresentar um risco de segurança.  
  
```xml
<wsFederation passiveRedirectEnabled="true"
              issuer="http://localhost:15839/wsFederationSTS/Issue"
              realm="http://localhost:50969/"
              reply="http://localhost:50969/"
              requireHttps="false"
              signOutReply="http://localhost:50969/SignedOutPage.html"
              signOutQueryString="Param1=value2&Param2=value2"
              persistentCookiesOnPassiveRedirects="true" />
```  
  
## <a name="see-also"></a>Confira também

- <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>
- <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType>
