---
title: Como criar um aplicativo Web ASP.NET MVC baseado em declarações usando o WIF
ms.date: 03/30/2017
ms.assetid: 0efb76bc-9f7b-4afe-be1c-2a57c917010b
author: BrucePerlerMS
ms.openlocfilehash: 4a003acbf4e182a0493368b586a3add229d8b526
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/29/2018
ms.locfileid: "47455507"
---
# <a name="how-to-build-claims-aware-aspnet-mvc-web-application-using-wif"></a>Como criar um aplicativo Web ASP.NET MVC baseado em declarações usando o WIF
## <a name="applies-to"></a>Aplica-se a  
  
-   Microsoft® Windows® Identity Foundation (WIF)  
  
-   ASP.NET® MVC  
  
## <a name="summary"></a>Resumo  
 Estas Instruções fornecem procedimentos passo a passo detalhados para criar um aplicativo Web ASP.NET MVC simples baseado em declarações. Também fornecem instruções sobre como testar o aplicativo Web ASP.NET MVC simples baseado em declarações para uma implementação bem-sucedida da autenticação baseada em declarações. Estas Instruções não contêm instruções detalhadas para a criação de um STS (Serviço de Token de Segurança) e pressupõe que você já tenha configurado um.  
  
## <a name="contents"></a>Conteúdo  
  
-   Objetivos  
  
-   Resumo das etapas  
  
-   Etapa 1 – Criar um aplicativo ASP.NET MVC simples  
  
-   Etapa 2 – Configurar um aplicativo ASP.NET MVC para autenticação baseada em declarações  
  
-   Etapa 3 – Testar a solução  
  
-   Itens relacionados  
  
## <a name="objectives"></a>Objetivos  
  
-   Configurar um aplicativo Web ASP.NET MVC para autenticação baseada em declarações  
  
-   Testar um aplicativo Web ASP.NET MVC bem-sucedido baseado em declarações  
  
## <a name="summary-of-steps"></a>Resumo das etapas  
  
-   Etapa 1 – Criar um aplicativo ASP.NET MVC simples  
  
-   Etapa 2 – Configurar um aplicativo ASP.NET MVC para autenticação baseada em declarações  
  
-   Etapa 3 – Testar a solução  
  
## <a name="step-1--create-simple-aspnet-mvc-application"></a>Etapa 1 – Criar um aplicativo ASP.NET MVC simples  
 Nesta etapa, você criará um novo aplicativo ASP.NET MVC.  
  
#### <a name="to-create-simple-aspnet-mvc-application"></a>Para criar um aplicativo ASP.NET MVC simples  
  
1.  Inicie o Visual Studio, clique em **Arquivo**, **Novo** e, depois, em **Projeto**.  
  
2.  Na janela **Novo Projeto**, clique em **Aplicativo Web ASP.NET MVC 3**.  
  
3.  Em **Nome**, insira `TestApp` e pressione **OK**.  
  
4.  Na caixa de diálogo **Novo Projeto ASP.NET MVC 3**, selecione **Aplicativo da Internet** nos modelos disponíveis, verifique se o **Mecanismo de Exibição** está definido como **Razor** e, em seguida, clique em **OK**.  
  
5.  Quando o novo projeto for aberto, clique com o botão direito do mouse no projeto **TestApp** no **Gerenciador de Soluções** e selecione a opção **Propriedades**.  
  
6.  Na página de propriedades do projeto, clique na guia **Web** à esquerda e verifique se a opção **Usar Servidor Web do IIS Local** é selecionada.  
  
## <a name="step-2--configure-aspnet-mvc-application-for-claims-based-authentication"></a>Etapa 2 – Configurar um aplicativo ASP.NET MVC para autenticação baseada em declarações  
 Nesta etapa, você adicionará entradas de configuração ao arquivo de configuração *Web.config* do aplicativo Web ASP.NET MVC para torná-lo baseado em declarações.  
  
#### <a name="to-configure-aspnet-mvc-application-for-claims-based-authentication"></a>Para configurar um aplicativo ASP.NET MVC para autenticação baseada em declarações  
  
1.  Adicione as definições de seção de configuração a seguir ao arquivo de configuração *Web.config*. Elas definem as seções de configuração exigidas pelo Windows Identity Foundation. Adicione as definições imediatamente após o elemento de abertura **\<configuration>**:  
  
    ```xml  
    <configSections>  
        <section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
        <section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
    </configSections>  
    ```  
  
2.  Adicione um elemento **\<location>** que habilita o acesso aos metadados de federação do aplicativo:  
  
    ```xml  
    <location path="FederationMetadata">  
        <system.web>  
            <authorization>  
                <allow users="*" />  
            </authorization>  
        </system.web>  
    </location>  
    ```  
  
3.  Adicione as seguintes entradas de configuração nos elementos **\<system.web>** para negar usuários, desabilitar a autenticação nativa e permitir que o WIF gerencie a autenticação.  
  
    ```xml  
    <authorization>  
        <deny users="?" />  
    </authorization>  
    <authentication mode="None" />  
    ```  
  
4.  Adicione as entradas de configuração relacionadas ao Windows Identity Foundation a seguir e garanta que a URL e o número da porta do aplicativo ASP.NET correspondam aos valores na entrada **\<audienceUris>**, no atributo **realm** do elemento **\<wsFederation>** e no atributo **reply** do elemento **\<wsFederation>**. Também garanta que o valor **issuer** se ajuste à URL do STS (Serviço de Token de Segurança).  
  
    ```xml  
    <system.identityModel>  
        <identityConfiguration>  
            <audienceUris>  
                <add value="http://localhost:28503/" />  
            </audienceUris>  
            <issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
                <trustedIssuers>  
                    <add thumbprint="1234567890ABCDEFGHIJKLMNOPQRSTUVWXYZ1234" name="YourSTSName" />  
                </trustedIssuers>   
            </issuerNameRegistry>  
            <certificateValidation certificateValidationMode="None" />  
        </identityConfiguration>  
    </system.identityModel>  
    <system.identityModel.services>  
        <federationConfiguration>  
            <cookieHandler requireSsl="false" />  
            <wsFederation passiveRedirectEnabled="true" issuer="http://localhost:13922/wsFederationSTS/Issue" realm="http://localhost:28503/" reply="http://localhost:28503/" requireHttps="false" />  
        </federationConfiguration>  
    </system.identityModel.services>  
    ```  
  
5.  Adicione uma referência ao assembly <xref:System.IdentityModel>.  
  
6.  Compile a solução para verificar se há erros.  
  
## <a name="step-3--test-your-solution"></a>Etapa 3 – Testar a solução  
 Nesta etapa, você testará o aplicativo Web ASP.NET MVC configurado para a autenticação baseada em declarações. Para executar um teste básico, você adicionará um código simples que exibe as declarações no token emitido pelo STS (Serviço de Token de Segurança).  
  
#### <a name="to-test-your-aspnet-mvc-application-for-claims-based-authentication"></a>Para testar o aplicativo ASP.NET MVC para autenticação baseada em declarações  
  
1.  No **Gerenciador de Soluções**, expanda a pasta **Controladores** e abra o arquivo *HomeController.cs* no editor. Adicione o seguinte código ao método **Index**:  
  
    ```csharp  
    public ActionResult Index()  
    {  
        ViewBag.ClaimsIdentity = Thread.CurrentPrincipal.Identity;  
  
        return View();  
    }  
    ```  
  
2.  No **Gerenciador de Soluções**, expanda **Exibições** e, em seguida, as pastas **Página Inicial** e abra o arquivo *Index.cshtml* no editor. Exclua seu conteúdo e adicione a seguinte marcação:  
  
    ```html  
    @{  
        ViewBag.Title = "Home Page";  
    }  
  
    <h2>Welcome: @ViewBag.ClaimsIdentity.Name</h2>  
    <h3>Values from Identity</h3>  
    <table>  
        <tr>  
            <th>  
                IsAuthenticated   
            </th>  
            <td>  
                @ViewBag.ClaimsIdentity.IsAuthenticated   
            </td>  
        </tr>  
        <tr>  
            <th>  
                Name   
            </th>          
            <td>  
                @ViewBag.ClaimsIdentity.Name  
            </td>          
        </tr>  
    </table>  
    <h3>Claims from ClaimsIdentity</h3>  
    <table>  
        <tr>  
            <th>  
                Claim Type  
            </th>  
            <th>  
                Claim Value  
            </th>  
            <th>  
                Value Type  
            </th>  
            <th>  
                Subject Name  
            </th>          
            <th>  
                Issuer Name  
            </th>          
        </tr>  
            @foreach (System.Security.Claims.Claim claim in ViewBag.ClaimsIdentity.Claims ) {  
        <tr>  
            <td>  
                @claim.Type  
            </td>  
            <td>  
                @claim.Value  
            </td>  
            <td>  
                @claim.ValueType  
            </td>  
            <td>  
                @claim.Subject.Name  
            </td>  
            <td>  
                @claim.Issuer  
            </td>  
        </tr>  
    }  
    </table>  
    ```  
  
3.  Execute a solução pressionando a tecla **F5**.  
  
4.  Você deverá ver a página que exibe as declarações no token que foi emitido por você pelo Serviço de Token de Segurança.  
  
## <a name="related-items"></a>Itens relacionados  
  
-   [Como criar um aplicativo Web Forms do ASP.NET com reconhecimento de declarações usando WIF](../../../docs/framework/security/how-to-build-claims-aware-aspnet-web-forms-app-using-wif.md)
