---
title: Como criar um aplicativo ASP.NET Web Forms baseado em declarações usando o WIF
ms.date: 03/30/2017
ms.assetid: efb264dd-f47b-49a9-85ee-9f45d4425765
author: BrucePerlerMS
ms.openlocfilehash: 83b5808ced1bc6243294b23d9784ec7993e3ba4a
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47207148"
---
# <a name="how-to-build-claims-aware-aspnet-web-forms-application-using-wif"></a>Como criar um aplicativo ASP.NET Web Forms baseado em declarações usando o WIF
## <a name="applies-to"></a>Aplica-se a  
  
-   Microsoft® Windows® Identity Foundation (WIF)  
  
-   Web Forms do ASP.NET®  
  
## <a name="summary"></a>Resumo  
 Estas Instruções fornecem procedimentos passo a passo detalhados para criar um aplicativo Web ASP.NET Web Forms simples baseado em declarações. Também fornecem instruções sobre como testar o aplicativo Web ASP.NET Web Forms simples baseado em declarações para uma implementação bem-sucedida da autenticação federada. Estas Instruções não contêm instruções detalhadas para a criação de um STS (Serviço de Token de Segurança) e pressupõe que você já tenha configurado um.  
  
## <a name="contents"></a>Conteúdo  
  
-   Objetivos  
  
-   Resumo das etapas  
  
-   Etapa 1 – criar um aplicativo ASP.NET Web Forms simples  
  
-   Etapa 2 – Configurar um aplicativo ASP.NET Web Forms para autenticação baseada em declarações  
  
-   Etapa 3 – Testar a solução  
  
## <a name="objectives"></a>Objetivos  
  
-   Configurar um aplicativo ASP.NET Web Forms para autenticação baseada em declarações  
  
-   Testar um aplicativo Web ASP.NET Web Forms bem-sucedido baseado em declarações  
  
## <a name="summary-of-steps"></a>Resumo das etapas  
  
-   Etapa 1 – Criar um aplicativo ASP.NET Web Forms simples  
  
-   Etapa 2 – Configurar um aplicativo ASP.NET Web Forms para autenticação federada  
  
-   Etapa 3 – Testar a solução  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a>Etapa 1 – criar um aplicativo ASP.NET Web Forms simples  
 Nesta etapa, você criará um novo aplicativo ASP.NET Web Forms.  
  
#### <a name="to-create-a-simple-aspnet-application"></a>Para criar um aplicativo ASP.NET simples  
  
1.  Inicie o Visual Studio, clique em **Arquivo**, **Novo** e, depois, em **Projeto**.  
  
2.  Na janela **Novo Projeto**, clique em **Aplicativo ASP.NET Web Forms**.  
  
3.  Em **Nome**, insira `TestApp` e pressione **OK**.  
  
## <a name="step-2--configure-aspnet-web-forms-application-for-claims-based-authentication"></a>Etapa 2 – Configurar um aplicativo ASP.NET Web Forms para autenticação baseada em declarações  
 Nesta etapa, você adicionará entradas de configuração ao arquivo de configuração *Web.config* do aplicativo Web ASP.NET Web Forms para torná-lo baseado em declarações.  
  
#### <a name="to-configure-aspnet-application-for-claims-based-authentication"></a>Para configurar um aplicativo ASP.NET para autenticação baseada em declarações  
  
1.  Adicione as seguintes entradas de seção de configuração ao arquivo de configuração *Web.config* imediatamente após o elemento de abertura **\<configuration>**:  
  
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
  
4.  Adicione um elemento **\<system.webServer>** que define os módulos para autenticação federada. Observe que o atributo *PublicKeyToken* deve ser igual ao atributo *PublicKeyToken* das entradas **\<configSections>** adicionadas anteriormente:  
  
    ```xml  
    <system.webServer>  
      <modules>  
        <add name="WSFederationAuthenticationModule" type="System.IdentityModel.Services.WSFederationAuthenticationModule, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" preCondition="managedHandler" />  
        <add name="SessionAuthenticationModule" type="System.IdentityModel.Services.SessionAuthenticationModule, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" preCondition="managedHandler" />  
      </modules>  
    </system.webServer>  
    ```  
  
5.  Adicione as entradas de configuração relacionadas ao Windows Identity Foundation a seguir e garanta que a URL e o número da porta do aplicativo ASP.NET correspondam aos valores na entrada **\<audienceUris>**, no atributo **realm** do elemento **\<wsFederation>** e no atributo **reply** do elemento **\<wsFederation>**. Também garanta que o valor **issuer** se ajuste à URL do STS (Serviço de Token de Segurança).  
  
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
            <cookieHandler requireSsl="true" />  
            <wsFederation passiveRedirectEnabled="true" issuer="http://localhost:13922/wsFederationSTS/Issue" realm="http://localhost:28503/" reply="http://localhost:28503/" requireHttps="true" />  
        </federationConfiguration>  
    </system.identityModel.services>  
    ```  
  
6.  Adicione uma referência ao assembly <xref:System.IdentityModel>.  
  
7.  Compile a solução para verificar se não há erros.  
  
## <a name="step-3--test-your-solution"></a>Etapa 3 – Testar a solução  
 Nesta etapa, você testará o aplicativo Web ASP.NET Web Forms configurado para a autenticação baseada em declarações. Para executar um teste básico, você adicionará um código que exibe as declarações no token emitido pelo STS (Serviço de Token de Segurança).  
  
#### <a name="to-test-your-aspnet-web-form-application-for-claims-based-authentication"></a>Para testar o aplicativo ASP.NET Web Forms para autenticação baseada em declarações  
  
1.  Abra o arquivo **Default.aspx** no projeto **TestApp** e substitua sua marcação existente pela seguinte marcação:  
  
    ```  
    %@ Page Language="C#" AutoEventWireup="true" CodeFile="Default.aspx.cs" Inherits="_Default" %>  
  
    <!DOCTYPE html>  
  
    <html>  
    <head id="Head1" runat="server">  
        <title></title>  
    </head>  
    <body>  
        <h1><asp:label ID="signedIn" runat="server" /></h1>  
        <asp:label ID="claimType" runat="server" />  
        <asp:label ID="claimValue" runat="server" />  
        <asp:label ID="claimValueType" runat="server" />  
        <asp:label ID="claimSubjectName" runat="server" />  
        <asp:label ID="claimIssuer" runat="server" />  
    </body>  
    </html>  
    ```  
  
2.  Salve **Default.aspx** e, depois, abra seu arquivo code-behind chamado **Default.aspx.cs**.  
  
    > [!NOTE]
    >  **Default.aspx.cs** pode estar oculto sob **Default.aspx** no Gerenciador de Soluções. Se **Default.aspx.cs** não estiver visível, expanda **Default.aspx** clicando no triângulo ao lado dele.  
  
3.  Substitua o código existente no método **Page_Load** de **Default.aspx.cs** pelo seguinte código:  
  
    ```csharp  
    using System;  
    using System.IdentityModel;  
    using System.Security.Claims;  
    using System.Threading;  
    using System.Web.UI;  
  
    namespace TestApp  
    {  
        public partial class _Default : System.Web.UI.Page  
        {  
            protected void Page_Load(object sender, EventArgs e)  
            {  
                ClaimsPrincipal claimsPrincipal = Thread.CurrentPrincipal as ClaimsPrincipal;  
  
                if (claimsPrincipal != null)  
                {  
                    signedIn.Text = "You are signed in.";  
  
                    foreach (Claim claim in claimsPrincipal.Claims)  
                    {  
                        claimType.Text = claim.Type;  
                        claimValue.Text = claim.Value;  
                        claimValueType.Text = claim.ValueType;  
                        claimSubjectName.Text = claim.Subject.Name;  
                        claimIssuer.Text = claim.Issuer;  
                    }  
                }  
                else  
                {  
                    signedIn.Text = "You are not signed in.";  
                }  
            }  
        }  
    }  
    ```  
  
4.  Salve **Default.aspx.cs** e crie a solução.  
  
5.  Execute a solução pressionando a tecla **F5**.  
  
6.  Você deverá ver a página que exibe as declarações no token que foi emitido por você pelo Serviço de Token de Segurança.
