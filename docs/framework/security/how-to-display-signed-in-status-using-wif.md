---
title: Como exibir o status de conexão usando o WIF
ms.date: 03/30/2017
ms.assetid: 4d1174e4-5397-4962-9a5f-3b1ad7b3fc14
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 53ef5e8b3fae976bacff3be9a50c323a22aef0e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33398912"
---
# <a name="how-to-display-signed-in-status-using-wif"></a>Como exibir o status de conexão usando o WIF
## <a name="applies-to"></a>Aplica-se a  
  
-   Microsoft® Windows® Identity Foundation (WIF) 4.5  
  
-   Web Forms do ASP.NET®  
  
## <a name="summary"></a>Resumo  
 Este tópico descreve como exibir o status de entrada em um aplicativo ASP.NET habilitado para WIF. O WIF fornece o mecanismo para fazer com que seu aplicativo reconheça declarações e para gerenciar autenticação e autorização para recursos do aplicativo.  
  
## <a name="contents"></a>Conteúdo  
  
-   Visão geral  
  
-   Resumo das etapas  
  
-   Etapa 1 – instalar a extensão de Identidade e Acesso  
  
-   Etapa 2 – criar um aplicativo ASP.NET de terceira parte confiável  
  
-   Etapa 3 – habilitar o STS de desenvolvimento local para autenticar usuários  
  
-   Etapa 4 – modificar seu aplicativo ASP.NET para exibir o status de entrada  
  
-   Etapa 5 – testar a integração entre o WIF e o seu aplicativo ASP.NET  
  
## <a name="overview"></a>Visão geral  
 Este tópico demonstra como criar um aplicativo com reconhecimento de declaração simples usando o WIF e como exibir facilmente se um usuário está conectado ou não. As etapas a seguir usam o STS de desenvolvimento local que está incluído com a extensão de Identidade e Acesso do Visual Studio. O STS de desenvolvimento local destina-se a um ambiente de teste e desenvolvimento para fornecer um método simples de integrar declarações em seu aplicativo. Ele nunca deve ser usado em um ambiente de produção, já que ele não executa autenticação real e credenciais não são necessárias. No entanto, o código obrigatório nas etapas a seguir é o mesmo para um aplicativo pronto para produção usando autenticação real.  
  
## <a name="summary-of-steps"></a>Resumo das etapas  
  
-   Etapa 1 – instalar a extensão de Identidade e Acesso  
  
-   Etapa 2 – criar um aplicativo ASP.NET de terceira parte confiável  
  
-   Etapa 3 – habilitar o STS de desenvolvimento local para autenticar usuários  
  
-   Etapa 4 – modificar seu aplicativo ASP.NET para exibir o status de entrada  
  
-   Etapa 5 – testar a integração entre o WIF e o seu aplicativo ASP.NET  
  
## <a name="step-1--install-the-identity-and-access-extension"></a>Etapa 1 – instalar a extensão de Identidade e Acesso  
 Essa etapa descreve como configurar a extensão de Identidade e Acesso para o Visual Studio 2012. Essa extensão automatiza o processo de configurar seu aplicativo para se comunicar com pontos de extremidade do STS.  
  
#### <a name="to-install-the-identity-and-access-extension"></a>Para instalar a extensão de Identidade e Acesso  
  
1.  Inicie o Visual Studio em modo elevado como administrador.  
  
2.  No Visual Studio, clique em **Ferramentas** e clique em **Gerenciador de Extensões**. A janela **Gerenciador de Extensões** é exibida.  
  
3.  Em **Gerenciador de Extensões**, clique em **Extensões Online** no menu à esquerda, então selecione **Galeria do Visual Studio**.  
  
4.  No canto superior direito do **Gerenciador de Extensões**, pesquise por *Identidade e Acesso*.  
  
5.  O item **Identidade e Acesso** aparecerá nos resultados da pesquisa. Clique nele e, em seguida, clique em **Baixar**.  
  
6.  A caixa de diálogo **Baixar e Instalar** aparecerá. Se concordar com os termos de licença, clique em **Instalar**.  
  
7.  Quando a instalação da extensão **Identidade e Acesso** for concluída, reinicie o Visual Studio no modo de administrador.  
  
## <a name="step-2--create-a-relying-party-aspnet-application"></a>Etapa 2 – criar um aplicativo ASP.NET de terceira parte confiável  
 Essa etapa descreve como criar um aplicativo de ASP.NET Web Forms de terceira parte confiável que integrará o WIF.  
  
#### <a name="to-create-a-simple-aspnet-application"></a>Para criar um aplicativo ASP.NET simples  
  
1.  Inicie o Visual Studio, clique em **Arquivo**, **Novo** e, depois, em **Projeto**.  
  
2.  Na janela **Novo Projeto**, clique em **Aplicativo ASP.NET Web Forms**.  
  
3.  Em **Nome**, insira `TestApp` e pressione **OK**.  
  
## <a name="step-3--enable-local-development-sts-to-authenticate-users"></a>Etapa 3 – habilitar o STS de desenvolvimento local para autenticar usuários  
 Essa etapa descreve como habilitar o STS de desenvolvimento local em seu aplicativo. O STS de desenvolvimento local é habilitado usando a extensão de Identidade e Acesso para o Visual Studio.  
  
#### <a name="to-enable-local-development-sts-in-your-aspnet-application"></a>Para habilitar o STS de desenvolvimento local em seu aplicativo ASP.NET  
  
1.  No Visual Studio, clique com o botão direito do mouse no projeto **TestApp** em **Gerenciador de Soluções** e selecione **Identidade e Acesso**.  
  
2.  A janela **Identidade e Acesso** é exibida. Em **Provedores**, selecione **Testar o aplicativo com o STS de Desenvolvimento Local** e clique em **Aplicar**.  
  
## <a name="step-4--modify-your-aspnet-application-to-display-sign-in-status"></a>Etapa 4 – modificar seu aplicativo ASP.NET para exibir o status de entrada  
 Essa etapa descreve como modificar seu aplicativo ASP.NET para exibir dinamicamente se o usuário atual está conectado. Depois que o provedor de STS tiver sido configurado, o WIF manipulará as declarações de entrada. Agora você precisa configurar o código do aplicativo para exibir o resultado da autenticação.  
  
#### <a name="to-display-sign-in-status"></a>Para exibir o status de entrada  
  
1.  No Visual Studio, abra o arquivo **Default.aspx** no projeto **TestApp**.  
  
2.  Substitua a marcação existente no arquivo **Default.aspx** pela seguinte:  
  
    ```  
    <%@ Page Language="C#" AutoEventWireup="true" CodeFile="Default.aspx.cs" Inherits="_Default" %>  
  
    <!DOCTYPE html>  
  
    <html>  
    <head runat="server">  
        <title>Logged In Status</title>  
    </head>  
    <body>  
        <asp:label ID="myLabel" runat="server" />  
    </body>  
    </html>  
    ```  
  
3.  Salve **Default.aspx** e, depois, abra seu arquivo code-behind chamado **Default.aspx.cs**.  
  
    > [!NOTE]
    >  **Default.aspx.cs** pode estar oculto sob **Default.aspx** no Gerenciador de Soluções. Se **Default.aspx.cs** não estiver visível, expanda **Default.aspx** clicando no triângulo ao lado dele.  
  
4.  Substitua o código existente em **Default.aspx.cs** pelo seguinte código:  
  
    ```csharp  
    using System;  
    using System.Web.UI;  
    using System.Security.Claims;  
  
    namespace TestApp  
    {  
        protected void Page_Load(object sender, EventArgs e)  
        {  
            ClaimsPrincipal claimsPrincipal = Thread.CurrentPrincipal as ClaimsPrincipal;  
  
            if (claimsPrincipal != null)  
            {  
                myLabel.Text = "You are signed in.";  
            }  
            else  
            {  
                myLabel.Text = "You are not signed in.";  
            }  
        }  
    }  
    ```  
  
5.  Salve **Default.aspx.cs** e compile o aplicativo.  
  
## <a name="step-5--test-the-integration-between-wif-and-your-aspnet-application"></a>Etapa 5 – testar a integração entre o WIF e o seu aplicativo ASP.NET  
 Esta etapa descreve como você pode testar a integração entre o WIF e o seu aplicativo ASP.NET.  
  
#### <a name="to-test-the-integration-between-wif-and-aspnet"></a>Para testar a integração entre o WIF e o ASP.NET  
  
1.  No Visual Studio, pressione **F5** para iniciar a depuração de seu aplicativo. Se nenhum erro for encontrado, uma nova janela do navegador será aberta.  
  
2.  Você pode perceber que o navegador redireciona silenciosamente a solicitação para o STS e, em seguida, abre a página Default.aspx. Se o WIF estiver configurado corretamente, você deverá ver o site exibir o seguinte texto: **"Você está conectado"**.
