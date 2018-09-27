---
title: Como habilitar a detecção de reprodução de tokens
ms.date: 03/30/2017
ms.assetid: 5a9f5771-f5f6-4100-8501-406aa20d731a
author: BrucePerlerMS
ms.openlocfilehash: 373177924a0a2e03bd43237510c918694cd5a340
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/27/2018
ms.locfileid: "47235991"
---
# <a name="how-to-enable-token-replay-detection"></a>Como habilitar a detecção de reprodução de tokens
## <a name="applies-to"></a>Aplica-se a  
  
-   Microsoft® Windows® Identity Foundation (WIF)  
  
-   Web Forms do ASP.NET®  
  
## <a name="summary"></a>Resumo  
 Estas instruções fornecem procedimentos passo a passo detalhados para habilitar a detecção de reprodução de token em um aplicativo ASP.NET que usa o WIF. Ele também fornece instruções sobre como testar o aplicativo para verificar se a detecção de reprodução de token está habilitada. Essas instruções não têm tópicos de explicações detalhados para criar um STS (Serviço de Token de Segurança), e usa o STS de Desenvolvimento que vem com a Ferramenta de Identidade e Acesso. O STS de Desenvolvimento não efetua a autenticação real e destina-se somente a testes. Você precisará instalar a Ferramenta de Identidade e Acesso para concluir estas instruções. O download pode ser feito na seguinte localização: [Ferramenta de Identidade e Acesso](https://go.microsoft.com/fwlink/?LinkID=245849)  
  
## <a name="contents"></a>Conteúdo  
  
-   Objetivos  
  
-   Visão geral  
  
-   Resumo das etapas  
  
-   Etapa 1 – criar um aplicativo ASP.NET Web Forms simples e habilitar a detecção de reprodução  
  
-   Etapa 2 – testar sua solução  
  
## <a name="objectives"></a>Objetivos  
  
-   Criar um aplicativo simples do ASP.NET que usa o WIF e o STS de desenvolvimento por meio da ferramenta de identidade e acesso  
  
-   Habilitar a detecção de reprodução de token e verificar se ela está funcionando  
  
## <a name="overview"></a>Visão geral  
 Um ataque de repetição ocorre quando um cliente tenta autenticar uma terceira parte confiável com um token STS já utilizado pelo cliente. Para evitar esse ataque, o WIF contém um cache de detecção de reprodução de tokens STS usados anteriormente. Quando habilitada, a detecção de reprodução verifica o token de solicitação de entrada e verifica se o token foi usado anteriormente ou não. Se o token já foi usado, a solicitação é recusada e uma exceção <xref:System.IdentityModel.Tokens.SecurityTokenReplayDetectedException> é gerada.  
  
 As etapas a seguir demonstram as alterações de configuração necessárias para habilitar a detecção de reprodução.  
  
## <a name="summary-of-steps"></a>Resumo das etapas  
  
-   Etapa 1 – criar um aplicativo ASP.NET Web Forms simples e habilitar a detecção de reprodução  
  
-   Etapa 2 – testar sua solução  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application-and-enable-replay-detection"></a>Etapa 1 – criar um aplicativo ASP.NET Web Forms simples e habilitar a detecção de reprodução  
 Nesta etapa, você criará um novo aplicativo ASP.NET Web Forms e modificará o arquivo *Web.config* para habilitar a detecção de reprodução.  
  
#### <a name="to-create-a-simple-aspnet-application"></a>Para criar um aplicativo ASP.NET simples  
  
1.  Inicie o Visual Studio, clique em **Arquivo**, **Novo** e, depois, em **Projeto**.  
  
2.  Na janela **Novo Projeto**, clique em **Aplicativo ASP.NET Web Forms**.  
  
3.  Em **Nome**, insira `TestApp` e pressione **OK**.  
  
4.  Clique com o botão direito do mouse no projeto **TestApp** em **Gerenciador de Soluções** e selecione **Identidade e Acesso**.  
  
5.  A janela **Identidade e Acesso** é exibida. Em **Provedores**, selecione **Testar o aplicativo com o STS de Desenvolvimento Local** e clique em **Aplicar**.  
  
6.  Adicione o elemento **\<tokenReplayDetection>** a seguir para o arquivo de configuração *Web.config* imediatamente após os elementos **\<system.identityModel>** e **\<identityConfiguration>**, conforme mostrado:  
  
    ```xml  
    <system.identityModel>  
        <identityConfiguration>  
            <tokenReplayDetection enabled="true"/>  
    ```  
  
## <a name="step-2--test-your-solution"></a>Etapa 2 – testar sua solução  
 Nesta etapa, você testará seu aplicativo ASP.NET habilitado para WIF para verificar se a detecção de reprodução foi habilitada.  
  
#### <a name="to-test-your-wif-enabled-aspnet-application-for-replay-detection"></a>Para testar seu aplicativo ASP.NET habilitado para WIF quanto à detecção de reprodução  
  
1.  Execute a solução pressionando a tecla **F5**. A Home Page ASP.NET padrão deverá ser apresentada a você e você deverá ser autenticado automaticamente com o nome de usuário *Terry*, que é o usuário padrão que é retornado pelo STS de desenvolvimento.  
  
2.  Pressione botão **Voltar** do navegador. Deverá ser apresentada a você uma página com um **Erro de servidor no aplicativo '/'** com a seguinte descrição: *ID1062: reprodução foi detectada para: Token: 'System.IdentityModel.Tokens.SamlSecurityToken'*, seguido por um *AssertionId* e um *Emissor*.  
  
     Você está vendo esta página de erro porque uma exceção do tipo <xref:System.IdentityModel.Tokens.SecurityTokenReplayDetectedException> foi gerada quando a reprodução do token foi detectada. Esse erro ocorre porque você está tentando enviar novamente a solicitação POST inicial de quando o token foi apresentado pela primeira vez. O botão **Voltar** não causará esse comportamento em solicitações subsequentes para o servidor.
