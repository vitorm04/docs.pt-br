---
title: 'Como: habilitar o rastreamento do WIF'
ms.date: 03/30/2017
ms.assetid: 271b6889-3454-46ff-96ab-9feb15e742ee
author: BrucePerlerMS
ms.openlocfilehash: 72e22fb5e0358c5f216bfe59d16ad030ce02e0eb
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64626054"
---
# <a name="how-to-enable-wif-tracing"></a><span data-ttu-id="81706-102">Como: habilitar o rastreamento do WIF</span><span class="sxs-lookup"><span data-stu-id="81706-102">How To: Enable WIF Tracing</span></span>
## <a name="applies-to"></a><span data-ttu-id="81706-103">Aplica-se a</span><span class="sxs-lookup"><span data-stu-id="81706-103">Applies To</span></span>  
  
- <span data-ttu-id="81706-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="81706-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>  
  
- <span data-ttu-id="81706-105">Web Forms do ASP.NET®</span><span class="sxs-lookup"><span data-stu-id="81706-105">ASP.NET® Web Forms</span></span>  
  
## <a name="summary"></a><span data-ttu-id="81706-106">Resumo</span><span class="sxs-lookup"><span data-stu-id="81706-106">Summary</span></span>  
 <span data-ttu-id="81706-107">Estas instruções fornecem procedimentos passo a passo detalhados para habilitar o rastreamento do WIF em um aplicativo ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="81706-107">This How-To provides detailed step-by-step procedures for enabling WIF tracing in an ASP.NET application.</span></span> <span data-ttu-id="81706-108">Elas também fornecem instruções para testar o aplicativo para verificar se o ouvinte de rastreamento e o registro estão funcionando corretamente.</span><span class="sxs-lookup"><span data-stu-id="81706-108">It also provides instructions testing the application to verify that the trace listener and log are working correctly.</span></span> <span data-ttu-id="81706-109">Essas instruções não têm tópicos de explicações detalhados para criar um STS (Serviço de Token de Segurança), e usa o STS de Desenvolvimento que vem com a Ferramenta de Identidade e Acesso.</span><span class="sxs-lookup"><span data-stu-id="81706-109">This How-To does not have detailed instructions for creating a Security Token Service (STS), and instead uses the Development STS that comes with the Identity and Access tool.</span></span> <span data-ttu-id="81706-110">O STS de Desenvolvimento não efetua a autenticação real e destina-se somente a testes.</span><span class="sxs-lookup"><span data-stu-id="81706-110">The Development STS does not perform real authentication and is intended for testing purposes only.</span></span> <span data-ttu-id="81706-111">Você precisará instalar a Ferramenta de Identidade e Acesso para concluir estas instruções.</span><span class="sxs-lookup"><span data-stu-id="81706-111">You will need to install the Identity and Access tool to complete this How-To.</span></span> <span data-ttu-id="81706-112">Ele pode ser baixado do seguinte local: [Ferramenta de identidade e acesso](https://go.microsoft.com/fwlink/?LinkID=245849)</span><span class="sxs-lookup"><span data-stu-id="81706-112">It can be downloaded from the following location: [Identity and Access Tool](https://go.microsoft.com/fwlink/?LinkID=245849)</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="81706-113">Habilitar o rastreamento do WIF para aplicações passivas, ou seja, aplicativos que usam o protocolo Web Services Federation, pode expor o aplicativo a ataques de DoS (negação de serviço) ou à divulgação de informações para uma terceira parte mal-intencionada.</span><span class="sxs-lookup"><span data-stu-id="81706-113">Enabling WIF tracing for passive applications, that is, applications that use the WS-Federation protocol, can potentially expose the application to denial of service (DoS) attacks or to information disclosure to a malicious party.</span></span> <span data-ttu-id="81706-114">Isso inclui RPs passivos e STSes passivos.</span><span class="sxs-lookup"><span data-stu-id="81706-114">This includes both passive RPs and passive STSes.</span></span> <span data-ttu-id="81706-115">Por esse motivo, é recomendável que você não habilite o rastreamento do WIF para RPs passivos ou STSes em um ambiente de produção.</span><span class="sxs-lookup"><span data-stu-id="81706-115">For this reason, we recommend that you not enable WIF tracing for passive RPs or STSes in a production environment.</span></span>  
  
## <a name="contents"></a><span data-ttu-id="81706-116">Conteúdo</span><span class="sxs-lookup"><span data-stu-id="81706-116">Contents</span></span>  
  
- <span data-ttu-id="81706-117">Objetivos</span><span class="sxs-lookup"><span data-stu-id="81706-117">Objectives</span></span>  
  
- <span data-ttu-id="81706-118">Visão geral</span><span class="sxs-lookup"><span data-stu-id="81706-118">Overview</span></span>  
  
- <span data-ttu-id="81706-119">Resumo das etapas</span><span class="sxs-lookup"><span data-stu-id="81706-119">Summary of Steps</span></span>  
  
- <span data-ttu-id="81706-120">Etapa 1 – criar um aplicativo ASP.NET Web Forms simples e habilitar o rastreamento</span><span class="sxs-lookup"><span data-stu-id="81706-120">Step 1 – Create a Simple ASP.NET Web Forms Application and Enable Tracing</span></span>  
  
- <span data-ttu-id="81706-121">Etapa 2 – testar sua solução</span><span class="sxs-lookup"><span data-stu-id="81706-121">Step 2 – Test Your Solution</span></span>  
  
## <a name="objectives"></a><span data-ttu-id="81706-122">Objetivos</span><span class="sxs-lookup"><span data-stu-id="81706-122">Objectives</span></span>  
  
- <span data-ttu-id="81706-123">Criar um aplicativo simples do ASP.NET que usa o WIF e o STS de desenvolvimento por meio da ferramenta de identidade e acesso</span><span class="sxs-lookup"><span data-stu-id="81706-123">Create a simple ASP.NET application that uses WIF and the Development STS from the Identity and Access Tool</span></span>  
  
- <span data-ttu-id="81706-124">Habilitar o rastreamento e verificar se ele está funcionando</span><span class="sxs-lookup"><span data-stu-id="81706-124">Enable tracing and verify that it is working</span></span>  
  
## <a name="overview"></a><span data-ttu-id="81706-125">Visão geral</span><span class="sxs-lookup"><span data-stu-id="81706-125">Overview</span></span>  
 <span data-ttu-id="81706-126">O rastreamento permite depurar e solucionar problemas de vários tipos de problemas com o WIF, incluindo tokens, cookies, declarações, mensagens de protocolo e muito mais.</span><span class="sxs-lookup"><span data-stu-id="81706-126">Tracing enables you to debug and troubleshoot many types of issues with WIF, including tokens, cookies, claims, protocol messages, and more.</span></span> <span data-ttu-id="81706-127">O rastreamento do WIF é semelhante ao rastreamento do WCF; por exemplo, você pode escolher o detalhamento dos rastreamentos para exibir tudo, desde mensagens críticas até todas as mensagens.</span><span class="sxs-lookup"><span data-stu-id="81706-127">WIF tracing is similar to WCF tracing; for example, you can choose the verbosity of traces to display everything from critical messages to all messages.</span></span> <span data-ttu-id="81706-128">Os rastreamentos do WIF podem ser gerados em arquivos **.xml** ou em arquivos **.svclog** que podem ser exibidos usando a ferramenta Visualizador de Rastreamento de Serviço.</span><span class="sxs-lookup"><span data-stu-id="81706-128">WIF traces can be generated in **.xml** files or in **.svclog** files that are viewable by using the Service Trace Viewer Tool.</span></span> <span data-ttu-id="81706-129">Essa ferramenta está localizada na **bin** diretório do SDK do Windows caminho de instalação no seu computador, por exemplo: **C:\Program Files\Microsoft SDKs\Windows\v7.1\Bin\SvcTraceViewer.exe**.</span><span class="sxs-lookup"><span data-stu-id="81706-129">This tool is located in the **bin** directory of the Windows SDK install path on your computer, for example: **C:\Program Files\Microsoft SDKs\Windows\v7.1\Bin\SvcTraceViewer.exe**.</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="81706-130">Resumo das etapas</span><span class="sxs-lookup"><span data-stu-id="81706-130">Summary of Steps</span></span>  
  
- <span data-ttu-id="81706-131">Etapa 1 – criar um aplicativo ASP.NET Web Forms simples e habilitar o rastreamento</span><span class="sxs-lookup"><span data-stu-id="81706-131">Step 1 – Create a Simple ASP.NET Web Forms Application and Enable Tracing</span></span>  
  
- <span data-ttu-id="81706-132">Etapa 2 – testar sua solução</span><span class="sxs-lookup"><span data-stu-id="81706-132">Step 2 – Test Your Solution</span></span>  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application-and-enable-tracing"></a><span data-ttu-id="81706-133">Etapa 1 – criar um aplicativo ASP.NET Web Forms simples e habilitar o rastreamento</span><span class="sxs-lookup"><span data-stu-id="81706-133">Step 1 – Create a Simple ASP.NET Web Forms Application and Enable Tracing</span></span>  
 <span data-ttu-id="81706-134">Nesta etapa, você criará um novo aplicativo ASP.NET Web Forms e modificará o arquivo *Web.config* para habilitar o rastreamento.</span><span class="sxs-lookup"><span data-stu-id="81706-134">In this step, you will create a new ASP.NET Web Forms application and modify the *Web.config* file to enable tracing.</span></span>  
  
#### <a name="to-create-a-simple-aspnet-application"></a><span data-ttu-id="81706-135">Para criar um aplicativo ASP.NET simples</span><span class="sxs-lookup"><span data-stu-id="81706-135">To create a simple ASP.NET application</span></span>  
  
1. <span data-ttu-id="81706-136">Inicie o Visual Studio, clique em **Arquivo**, **Novo** e, depois, em **Projeto**.</span><span class="sxs-lookup"><span data-stu-id="81706-136">Start Visual Studio and click **File**, **New**, and then **Project**.</span></span>  
  
2. <span data-ttu-id="81706-137">Na janela **Novo Projeto**, clique em **Aplicativo ASP.NET Web Forms**.</span><span class="sxs-lookup"><span data-stu-id="81706-137">In the **New Project** window, click **ASP.NET Web Forms Application**.</span></span>  
  
3. <span data-ttu-id="81706-138">Em **Nome**, insira `TestApp` e pressione **OK**.</span><span class="sxs-lookup"><span data-stu-id="81706-138">In **Name**, enter `TestApp` and press **OK**.</span></span>  
  
4. <span data-ttu-id="81706-139">Clique com o botão direito do mouse no projeto **TestApp** em **Gerenciador de Soluções** e selecione **Identidade e Acesso**.</span><span class="sxs-lookup"><span data-stu-id="81706-139">Right-click the **TestApp** project under **Solution Explorer**, then select **Identity and Access**.</span></span>  
  
5. <span data-ttu-id="81706-140">A janela **Identidade e Acesso** é exibida.</span><span class="sxs-lookup"><span data-stu-id="81706-140">The **Identity and Access** window appears.</span></span> <span data-ttu-id="81706-141">Em **Provedores**, selecione **Testar o aplicativo com o STS de Desenvolvimento Local** e clique em **Aplicar**.</span><span class="sxs-lookup"><span data-stu-id="81706-141">Under **Providers**, select **Test your application with the Local Development STS**, then click **Apply**.</span></span>  
  
6. <span data-ttu-id="81706-142">Crie uma nova pasta chamada **logs** na raiz do **c:** unidade, como mostrado: **C:\logs**</span><span class="sxs-lookup"><span data-stu-id="81706-142">Create a new folder in named **logs** in the root of the **C:** drive, like shown: **C:\logs**</span></span>  
  
7. <span data-ttu-id="81706-143">Adicione o elemento **\<System.Diagnostics>** a seguir para o arquivo de configuração *Web.config* imediatamente após o fechamento do elemento **\</configSections>**, conforme mostrado:</span><span class="sxs-lookup"><span data-stu-id="81706-143">Add the following **\<system.diagnostics>** element to the *Web.config* configuration file immediately following the closing **\</configSections>** element, like shown:</span></span>  
  
    ```xml  
    <configuration>  
        <configSections>  
            ...
        </configSections>  
        <system.diagnostics>  
            <sources>  
                <source name="System.IdentityModel" switchValue="Verbose">  
                    <listeners>  
                        <add name="xml" type="System.Diagnostics.XmlWriterTraceListener" initializeData="C:\logs\WIF.xml" />  
                    </listeners>  
                </source>  
            </sources>  
            <trace autoflush="true" />  
        </system.diagnostics>  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="81706-144">O local do diretório especificado no atributo **initializeData** deve existir antes que o registro em log possa começar.</span><span class="sxs-lookup"><span data-stu-id="81706-144">The directory location specified in the **initializeData** attribute must exist before logging can begin.</span></span> <span data-ttu-id="81706-145">Se o local não existir, nenhum log será criado.</span><span class="sxs-lookup"><span data-stu-id="81706-145">If the location does not exist, no logs will be created.</span></span>  
  
     <span data-ttu-id="81706-146">As configurações acima habilitarão o rastreamento **Detalhado** do WIF e salvarão o log resultante para o arquivo **C:\logsWIF.xml**.</span><span class="sxs-lookup"><span data-stu-id="81706-146">The configuration settings above will enable **Verbose** tracing for WIF and save the resulting log to the **C:logsWIF.xml** file.</span></span>  
  
## <a name="step-2--test-your-solution"></a><span data-ttu-id="81706-147">Etapa 2 – testar sua solução</span><span class="sxs-lookup"><span data-stu-id="81706-147">Step 2 – Test Your Solution</span></span>  
 <span data-ttu-id="81706-148">Nesta etapa, você testará seu aplicativo ASP.NET habilitado para WIF para verificar se os logs estão sendo registrados.</span><span class="sxs-lookup"><span data-stu-id="81706-148">In this step, you will test your WIF-enabled ASP.NET application to verify that logs are being recorded.</span></span>  
  
#### <a name="to-test-your-wif-enabled-aspnet-application-for-successful-tracing"></a><span data-ttu-id="81706-149">Para testar seu aplicativo ASP.NET habilitado para WIF visando um rastreamento bem-sucedido</span><span class="sxs-lookup"><span data-stu-id="81706-149">To test your WIF-enabled ASP.NET application for successful tracing</span></span>  
  
1. <span data-ttu-id="81706-150">Execute a solução pressionando a tecla **F5**.</span><span class="sxs-lookup"><span data-stu-id="81706-150">Run the solution by pressing the **F5** key.</span></span> <span data-ttu-id="81706-151">A Home Page ASP.NET padrão deverá ser apresentada a você e você deverá ser autenticado automaticamente com o nome de usuário *Terry*, que é o usuário padrão que é retornado pelo STS de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="81706-151">You should be presented with the default ASP.NET Home Page and automatically authenticated with the username *Terry*, which is the default user that is returned by the Development STS.</span></span>  
  
2. <span data-ttu-id="81706-152">Feche a janela do navegador e, em seguida, navegue até a pasta **C:\logs**.</span><span class="sxs-lookup"><span data-stu-id="81706-152">Close the browser window and then navigate to the **C:\logs** folder.</span></span> <span data-ttu-id="81706-153">Abra o arquivo **C:\logs\WIF.xml** usando um editor de texto.</span><span class="sxs-lookup"><span data-stu-id="81706-153">Open the **C:\logs\WIF.xml** file using a text editor.</span></span>  
  
3. <span data-ttu-id="81706-154">Inspecione o arquivo **WIF.xml** e verifique se ele contém entradas começando com **\<E2ETraceEvent>**.</span><span class="sxs-lookup"><span data-stu-id="81706-154">Inspect the **WIF.xml** file and verify that it contains entries starting with **\<E2ETraceEvent>**.</span></span> <span data-ttu-id="81706-155">Esses rastreamentos conterão elementos **\<TraceRecord>** com descrições para a atividade rastreada, tais como **Validando SecurityToken**.</span><span class="sxs-lookup"><span data-stu-id="81706-155">These traces will contain **\<TraceRecord>** elements with descriptions for the traced activity, such as **Validating SecurityToken**.</span></span>
