---
title: 'Como: habilitar a detecção de reprodução do token'
ms.date: 03/30/2017
ms.assetid: 5a9f5771-f5f6-4100-8501-406aa20d731a
author: BrucePerlerMS
ms.openlocfilehash: a357f153d61b6a8e1e105639bd68647dabdc26f8
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59336519"
---
# <a name="how-to-enable-token-replay-detection"></a><span data-ttu-id="32f49-102">Como: habilitar a detecção de reprodução do token</span><span class="sxs-lookup"><span data-stu-id="32f49-102">How To: Enable Token Replay Detection</span></span>
## <a name="applies-to"></a><span data-ttu-id="32f49-103">Aplica-se a</span><span class="sxs-lookup"><span data-stu-id="32f49-103">Applies To</span></span>  
  
-   <span data-ttu-id="32f49-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="32f49-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>  
  
-   <span data-ttu-id="32f49-105">Web Forms do ASP.NET®</span><span class="sxs-lookup"><span data-stu-id="32f49-105">ASP.NET® Web Forms</span></span>  
  
## <a name="summary"></a><span data-ttu-id="32f49-106">Resumo</span><span class="sxs-lookup"><span data-stu-id="32f49-106">Summary</span></span>  
 <span data-ttu-id="32f49-107">Estas instruções fornecem procedimentos passo a passo detalhados para habilitar a detecção de reprodução de token em um aplicativo ASP.NET que usa o WIF.</span><span class="sxs-lookup"><span data-stu-id="32f49-107">This How-To provides detailed step-by-step procedures for enabling token replay detection in an ASP.NET application that uses WIF.</span></span> <span data-ttu-id="32f49-108">Ele também fornece instruções sobre como testar o aplicativo para verificar se a detecção de reprodução de token está habilitada.</span><span class="sxs-lookup"><span data-stu-id="32f49-108">It also provides instructions for how to test the application to verify that token replay detection is enabled.</span></span> <span data-ttu-id="32f49-109">Essas instruções não têm tópicos de explicações detalhados para criar um STS (Serviço de Token de Segurança), e usa o STS de Desenvolvimento que vem com a Ferramenta de Identidade e Acesso.</span><span class="sxs-lookup"><span data-stu-id="32f49-109">This How-To does not have detailed instructions for creating a Security Token Service (STS), and instead uses the Development STS that comes with the Identity and Access tool.</span></span> <span data-ttu-id="32f49-110">O STS de Desenvolvimento não efetua a autenticação real e destina-se somente a testes.</span><span class="sxs-lookup"><span data-stu-id="32f49-110">The Development STS does not perform real authentication and is intended for testing purposes only.</span></span> <span data-ttu-id="32f49-111">Você precisará instalar a Ferramenta de Identidade e Acesso para concluir estas instruções.</span><span class="sxs-lookup"><span data-stu-id="32f49-111">You will need to install the Identity and Access tool to complete this How-To.</span></span> <span data-ttu-id="32f49-112">Ele pode ser baixado do seguinte local: [Ferramenta de identidade e acesso](https://go.microsoft.com/fwlink/?LinkID=245849)</span><span class="sxs-lookup"><span data-stu-id="32f49-112">It can be downloaded from the following location: [Identity and Access Tool](https://go.microsoft.com/fwlink/?LinkID=245849)</span></span>  
  
## <a name="contents"></a><span data-ttu-id="32f49-113">Conteúdo</span><span class="sxs-lookup"><span data-stu-id="32f49-113">Contents</span></span>  
  
-   <span data-ttu-id="32f49-114">Objetivos</span><span class="sxs-lookup"><span data-stu-id="32f49-114">Objectives</span></span>  
  
-   <span data-ttu-id="32f49-115">Visão geral</span><span class="sxs-lookup"><span data-stu-id="32f49-115">Overview</span></span>  
  
-   <span data-ttu-id="32f49-116">Resumo das etapas</span><span class="sxs-lookup"><span data-stu-id="32f49-116">Summary of Steps</span></span>  
  
-   <span data-ttu-id="32f49-117">Etapa 1 – criar um aplicativo ASP.NET Web Forms simples e habilitar a detecção de reprodução</span><span class="sxs-lookup"><span data-stu-id="32f49-117">Step 1 – Create a Simple ASP.NET Web Forms Application and Enable Replay Detection</span></span>  
  
-   <span data-ttu-id="32f49-118">Etapa 2 – testar sua solução</span><span class="sxs-lookup"><span data-stu-id="32f49-118">Step 2 – Test Your Solution</span></span>  
  
## <a name="objectives"></a><span data-ttu-id="32f49-119">Objetivos</span><span class="sxs-lookup"><span data-stu-id="32f49-119">Objectives</span></span>  
  
-   <span data-ttu-id="32f49-120">Criar um aplicativo simples do ASP.NET que usa o WIF e o STS de desenvolvimento por meio da ferramenta de identidade e acesso</span><span class="sxs-lookup"><span data-stu-id="32f49-120">Create a simple ASP.NET application that uses WIF and the Development STS from the Identity and Access Tool</span></span>  
  
-   <span data-ttu-id="32f49-121">Habilitar a detecção de reprodução de token e verificar se ela está funcionando</span><span class="sxs-lookup"><span data-stu-id="32f49-121">Enable token replay detection and verify that it is working</span></span>  
  
## <a name="overview"></a><span data-ttu-id="32f49-122">Visão geral</span><span class="sxs-lookup"><span data-stu-id="32f49-122">Overview</span></span>  
 <span data-ttu-id="32f49-123">Um ataque de repetição ocorre quando um cliente tenta autenticar uma terceira parte confiável com um token STS já utilizado pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="32f49-123">A replay attack occurs when a client attempts to authenticate to a relying party with an STS token that the client has already used.</span></span> <span data-ttu-id="32f49-124">Para evitar esse ataque, o WIF contém um cache de detecção de reprodução de tokens STS usados anteriormente.</span><span class="sxs-lookup"><span data-stu-id="32f49-124">To help prevent this attack, WIF contains a replay detection cache of previously used STS tokens.</span></span> <span data-ttu-id="32f49-125">Quando habilitada, a detecção de reprodução verifica o token de solicitação de entrada e verifica se o token foi usado anteriormente ou não.</span><span class="sxs-lookup"><span data-stu-id="32f49-125">When enabled, replay detection checks the token of the incoming request and verifies whether or not the token has been previously used.</span></span> <span data-ttu-id="32f49-126">Se o token já foi usado, a solicitação é recusada e uma exceção <xref:System.IdentityModel.Tokens.SecurityTokenReplayDetectedException> é gerada.</span><span class="sxs-lookup"><span data-stu-id="32f49-126">If the token has been used already, the request is refused and a <xref:System.IdentityModel.Tokens.SecurityTokenReplayDetectedException> exception is thrown.</span></span>  
  
 <span data-ttu-id="32f49-127">As etapas a seguir demonstram as alterações de configuração necessárias para habilitar a detecção de reprodução.</span><span class="sxs-lookup"><span data-stu-id="32f49-127">The following steps demonstrate the configuration changes required to enable replay detection.</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="32f49-128">Resumo das etapas</span><span class="sxs-lookup"><span data-stu-id="32f49-128">Summary of Steps</span></span>  
  
-   <span data-ttu-id="32f49-129">Etapa 1 – criar um aplicativo ASP.NET Web Forms simples e habilitar a detecção de reprodução</span><span class="sxs-lookup"><span data-stu-id="32f49-129">Step 1 – Create a Simple ASP.NET Web Forms Application and Enable Replay Detection</span></span>  
  
-   <span data-ttu-id="32f49-130">Etapa 2 – testar sua solução</span><span class="sxs-lookup"><span data-stu-id="32f49-130">Step 2 – Test Your Solution</span></span>  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application-and-enable-replay-detection"></a><span data-ttu-id="32f49-131">Etapa 1 – criar um aplicativo ASP.NET Web Forms simples e habilitar a detecção de reprodução</span><span class="sxs-lookup"><span data-stu-id="32f49-131">Step 1 – Create a Simple ASP.NET Web Forms Application and Enable Replay Detection</span></span>  
 <span data-ttu-id="32f49-132">Nesta etapa, você criará um novo aplicativo ASP.NET Web Forms e modificará o arquivo *Web.config* para habilitar a detecção de reprodução.</span><span class="sxs-lookup"><span data-stu-id="32f49-132">In this step, you will create a new ASP.NET Web Forms application and modify the *Web.config* file to enable replay detection.</span></span>  
  
#### <a name="to-create-a-simple-aspnet-application"></a><span data-ttu-id="32f49-133">Para criar um aplicativo ASP.NET simples</span><span class="sxs-lookup"><span data-stu-id="32f49-133">To create a simple ASP.NET application</span></span>  
  
1. <span data-ttu-id="32f49-134">Inicie o Visual Studio, clique em **Arquivo**, **Novo** e, depois, em **Projeto**.</span><span class="sxs-lookup"><span data-stu-id="32f49-134">Start Visual Studio and click **File**, **New**, and then **Project**.</span></span>  
  
2. <span data-ttu-id="32f49-135">Na janela **Novo Projeto**, clique em **Aplicativo ASP.NET Web Forms**.</span><span class="sxs-lookup"><span data-stu-id="32f49-135">In the **New Project** window, click **ASP.NET Web Forms Application**.</span></span>  
  
3. <span data-ttu-id="32f49-136">Em **Nome**, insira `TestApp` e pressione **OK**.</span><span class="sxs-lookup"><span data-stu-id="32f49-136">In **Name**, enter `TestApp` and press **OK**.</span></span>  
  
4. <span data-ttu-id="32f49-137">Clique com o botão direito do mouse no projeto **TestApp** em **Gerenciador de Soluções** e selecione **Identidade e Acesso**.</span><span class="sxs-lookup"><span data-stu-id="32f49-137">Right-click the **TestApp** project under **Solution Explorer**, then select **Identity and Access**.</span></span>  
  
5. <span data-ttu-id="32f49-138">A janela **Identidade e Acesso** é exibida.</span><span class="sxs-lookup"><span data-stu-id="32f49-138">The **Identity and Access** window appears.</span></span> <span data-ttu-id="32f49-139">Em **Provedores**, selecione **Testar o aplicativo com o STS de Desenvolvimento Local** e clique em **Aplicar**.</span><span class="sxs-lookup"><span data-stu-id="32f49-139">Under **Providers**, select **Test your application with the Local Development STS**, then click **Apply**.</span></span>  
  
6. <span data-ttu-id="32f49-140">Adicione o elemento **\<tokenReplayDetection>** a seguir para o arquivo de configuração *Web.config* imediatamente após os elementos **\<system.identityModel>** e **\<identityConfiguration>**, conforme mostrado:</span><span class="sxs-lookup"><span data-stu-id="32f49-140">Add the following **\<tokenReplayDetection>** element to the *Web.config* configuration file immediately following the **\<system.identityModel>** and **\<identityConfiguration>** elements, like shown:</span></span>  
  
    ```xml  
    <system.identityModel>  
        <identityConfiguration>  
            <tokenReplayDetection enabled="true"/>  
    ```  
  
## <a name="step-2--test-your-solution"></a><span data-ttu-id="32f49-141">Etapa 2 – testar sua solução</span><span class="sxs-lookup"><span data-stu-id="32f49-141">Step 2 – Test Your Solution</span></span>  
 <span data-ttu-id="32f49-142">Nesta etapa, você testará seu aplicativo ASP.NET habilitado para WIF para verificar se a detecção de reprodução foi habilitada.</span><span class="sxs-lookup"><span data-stu-id="32f49-142">In this step, you will test your WIF-enabled ASP.NET application to verify that replay detection has been enabled.</span></span>  
  
#### <a name="to-test-your-wif-enabled-aspnet-application-for-replay-detection"></a><span data-ttu-id="32f49-143">Para testar seu aplicativo ASP.NET habilitado para WIF quanto à detecção de reprodução</span><span class="sxs-lookup"><span data-stu-id="32f49-143">To test your WIF-enabled ASP.NET application for replay detection</span></span>  
  
1. <span data-ttu-id="32f49-144">Execute a solução pressionando a tecla **F5**.</span><span class="sxs-lookup"><span data-stu-id="32f49-144">Run the solution by pressing the **F5** key.</span></span> <span data-ttu-id="32f49-145">A Home Page ASP.NET padrão deverá ser apresentada a você e você deverá ser autenticado automaticamente com o nome de usuário *Terry*, que é o usuário padrão que é retornado pelo STS de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="32f49-145">You should be presented with the default ASP.NET Home Page and automatically authenticated with the username *Terry*, which is the default user that is returned by the Development STS.</span></span>  
  
2. <span data-ttu-id="32f49-146">Pressione botão **Voltar** do navegador.</span><span class="sxs-lookup"><span data-stu-id="32f49-146">Press the browser’s **Back** button.</span></span> <span data-ttu-id="32f49-147">Você deve ser apresentado com uma **erro de servidor no aplicativo '/'** página com a seguinte descrição: *ID1062: Reprodução foi detectada para: Token: 'Samlsecuritytoken'*, seguido por um *AssertionId* e uma *emissor*.</span><span class="sxs-lookup"><span data-stu-id="32f49-147">You should be presented with a **Server Error in ‘/’ Application** page with the following description: *ID1062: Replay has been detected for: Token: 'System.IdentityModel.Tokens.SamlSecurityToken'*, followed by an *AssertionId* and an *Issuer*.</span></span>  
  
     <span data-ttu-id="32f49-148">Você está vendo esta página de erro porque uma exceção do tipo <xref:System.IdentityModel.Tokens.SecurityTokenReplayDetectedException> foi gerada quando a reprodução do token foi detectada.</span><span class="sxs-lookup"><span data-stu-id="32f49-148">You are seeing this error page because an exception of type <xref:System.IdentityModel.Tokens.SecurityTokenReplayDetectedException> was thrown when the token replay was detected.</span></span> <span data-ttu-id="32f49-149">Esse erro ocorre porque você está tentando enviar novamente a solicitação POST inicial de quando o token foi apresentado pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="32f49-149">This error occurs because you are attempting to re-send the initial POST request when the token was first presented.</span></span> <span data-ttu-id="32f49-150">O botão **Voltar** não causará esse comportamento em solicitações subsequentes para o servidor.</span><span class="sxs-lookup"><span data-stu-id="32f49-150">The **Back** button will not cause this behavior on subsequent requests to the server.</span></span>
