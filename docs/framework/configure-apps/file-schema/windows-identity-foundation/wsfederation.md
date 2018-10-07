---
title: '&lt;wsFederation&gt;'
ms.date: 03/30/2017
ms.assetid: c537f770-68bd-4f82-96ad-6424ad91369f
author: BrucePerlerMS
ms.openlocfilehash: 66596bbc7171a33318b835a552b7fb364d6833f7
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/06/2018
ms.locfileid: "48838540"
---
# <a name="ltwsfederationgt"></a>&lt;wsFederation&gt;
Fornece configuração para o <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM).  
  
\<IdentityModel >  
\<federationConfiguration >  
\<wsFederation >  
  
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
|AuthenticationType|Um URI que especifica o tipo de autenticação. Define o parâmetro wauth a solicitação de entrada WS-Federation. Opcional. O padrão é uma cadeia de caracteres vazia, que especifica que o parâmetro wauth não está incluído na solicitação.|  
|atualização|A desejado idade máxima de solicitações de autenticação, em minutos. Define o parâmetro wfresh a solicitação de entrada WS-Federation. Opcional. O padrão é zero. Opcional. **Aviso:** na próxima versão do .NET Framework 4.5, o `freshness` atributo será do tipo `xs:string` e seu valor padrão será `null`.|  
|homeRealm|O realm inicial do provedor de identidade (IP) a ser usado para autenticação. Define o parâmetro whr a solicitação de entrada WS-Federation. Opcional. O padrão é uma cadeia de caracteres vazia, que especifica que o parâmetro whr não está incluído na solicitação.|  
|emissor|O URI do emissor do token pretendido. Define a base URL de WS-Federation as solicitações de entrada e solicitações de saída necessárias.|  
|persistentCookiesOnPassiveRedirects|Especifica se os cookies persistentes são emitidos na autenticação. Opcional. O padrão é "false", os cookies não são emitidos.|  
|passiveRedirectEnabled|Especifica se o WSFAM está habilitado para redirecionar automaticamente as solicitações não autorizadas para um STS. Opcional. O padrão é "true", solicitações não autorizadas sejam redirecionadas automaticamente.|  
|Política|Uma URL que especifica o local da política para usar em solicitações de entrada relevante. O padrão é uma cadeia de caracteres vazia. Define o parâmetro de wp de solicitação de entrada do Web Services Federation. Opcional. O padrão é uma cadeia de caracteres vazia, que especifica que o parâmetro wp não está incluído na solicitação.|  
|território|O URI do realm solicitante. (Um URI que identifica a terceira parte confiável (RP) para o serviço de token de segurança (STS).) Define o parâmetro de solicitação de wtrealm WS-Federation sign-in de solicitação. Necessário.|  
|Resposta|Uma URL que identifica o endereço no qual o terceira parte confiável (RP) aplicativo gostaria de receber respostas do Security Token Service (STS). Define o parâmetro wreply a solicitação de entrada WS-Federation. Opcional. O padrão é uma cadeia de caracteres vazia, que especifica que o parâmetro wreply não está incluído na solicitação.|  
|solicitação|A solicitação de emissão de token. Define o parâmetro wreq a solicitação de entrada WS-Federation. Opcional. O padrão é uma cadeia de caracteres vazia, que especifica que o parâmetro wreq não está incluído na solicitação. Não incluindo o wreq ou o parâmetro wreqptr na solicitação implica que o STS Saiba que tipo de token para emitir.|  
|requestPtr|Uma URL que especifica o local da solicitação de emissão de token. Define o parâmetro wreqptr da solicitação. Opcional. O padrão é uma cadeia de caracteres vazia, que especifica que o parâmetro wreqptr não está incluído na solicitação. Não incluindo o wreq ou o parâmetro wreqptr na solicitação implica que o STS Saiba que tipo de token para emitir.|  
|requireHttps|Especifica se a comunicação com o serviço de token de segurança (STS) deve usar o protocolo HTTPS. Opcional. O padrão é "true", o HTTPS deve ser usado.|  
|recurso|Um URI que identifica o recurso sendo acessado, a terceira parte confiável (RP), como o para o serviço de token de segurança (STS). Opcional. Define o parâmetro wres a solicitação de entrada WS-Federation. Opcional. O padrão é uma cadeia de caracteres vazia, que especifica que o parâmetro wres não está incluído na solicitação. **Observação:** wres é um parâmetro herdado. Especifique o `realm` atributo para usar o parâmetro wtrealm em vez disso.|  
|signInQueryString|Fornece um ponto de extensibilidade para especificar parâmetros de consulta de aplicativo definido na URL de solicitação de entrada do Web Services Federation. Opcional. O padrão é uma cadeia de caracteres vazia, que especifica que nenhum parâmetro adicional deve ser incluído na solicitação. Os parâmetros são especificados como um fragmento da cadeia de caracteres de consulta usando o seguinte formato: `"param1=value1&param2=value2&param3=value3"` e assim por diante. **Observação:** em um arquivo de configuração de "&" caractere na cadeia de caracteres de consulta deve ser especificado usando a sua referência de entidade, `&`.|  
|signOutQueryString|Fornece um ponto de extensibilidade para especificar parâmetros de consulta de aplicativo definido na URL de solicitação de entrada do Web Services Federation. Opcional. O padrão é uma cadeia de caracteres vazia, que especifica que nenhum parâmetro adicional deve ser incluído na solicitação. Os parâmetros são especificados como um fragmento da cadeia de caracteres de consulta usando o seguinte formato: `"param1=value1&param2=value2&param3=value3"` e assim por diante. **Observação:** em um arquivo de configuração de "&" caractere na cadeia de caracteres de consulta deve ser especificado usando a sua referência de entidade, `&`.|  
|signOutReply|Especifica a URL à qual o cliente deverá ser redirecionado pelo serviço de token de segurança (STS) durante a saída por meio do protocolo WS-Federation passiva. Define o parâmetro wreply em uma solicitação de saída do WS-Federation. Opcional. O padrão é uma cadeia de caracteres vazia, que especifica que nenhum parâmetro adicional deve ser incluído na solicitação.|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<federationConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)|Contém as configurações que configuram os <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) e o <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).|  
  
## <a name="remarks"></a>Comentários  
 Você pode usar o `<wsFederation>` elemento para configurar definições de parâmetro padrão WS-Federation e o comportamento padrão para o WSFAM. Configurações de parâmetro de WS-Federation definidas de acordo com o `<wsFederation>` elemento conjunto equivalentes propriedades expostas pelo <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> classe. Essas propriedades permanecem os mesmos para cada solicitação emitida pelo WSFAM. Você pode alterar os parâmetros de WS-Federation dinamicamente durante a solicitação de processamento, adicionando manipuladores de eventos para os eventos expostos pelo WSFAM; Por exemplo, o <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.RedirectingToIdentityProvider> eventos. Para obter mais informações, consulte a documentação para o <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> classe.  
  
 O `<wsFederation>` elemento é representado pelo <xref:System.IdentityModel.Services.Configuration.WSFederationElement> classe. O objeto de configuração é representado pelo <xref:System.IdentityModel.Services.Configuration.WsFederationConfiguration> classe. Uma única <xref:System.IdentityModel.Services.Configuration.WsFederationConfiguration> instância é definida na <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> objeto é acessado por meio o <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> propriedade e fornece configuração para o WSFAM.  
  
## <a name="example"></a>Exemplo  
 O XML a seguir mostra um `<wsFederation>` elemento que especifica configurações para o WSFAM.  
  
> [!WARNING]
>  Neste exemplo, o WSFAM não é necessário para usar HTTPS. Isso ocorre porque o `requireHttps` atributo o `<wsFederation>` é definido `false`. Essa configuração não é recomendada para a maioria dos ambientes de produção, como ele pode representar um risco de segurança.  
  
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
  
## <a name="see-also"></a>Consulte também  
 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>  
 <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType>
