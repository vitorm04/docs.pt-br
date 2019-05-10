---
title: Exemplo de federação
ms.date: 03/30/2017
ms.assetid: 7e9da0ca-e925-4644-aa96-8bfaf649d4bb
ms.openlocfilehash: 0d3e9b3aa8d94136fae2d26b2b297776d5b7ea9e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64650075"
---
# <a name="federation-sample"></a><span data-ttu-id="878de-102">Exemplo de federação</span><span class="sxs-lookup"><span data-stu-id="878de-102">Federation Sample</span></span>
<span data-ttu-id="878de-103">Este exemplo demonstra a segurança federada.</span><span class="sxs-lookup"><span data-stu-id="878de-103">This sample demonstrates federated security.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="878de-104">Detalhes de exemplo</span><span class="sxs-lookup"><span data-stu-id="878de-104">Sample Details</span></span>  
 <span data-ttu-id="878de-105">Windows Communication Foundation (WCF) oferece suporte para implantação de arquiteturas de segurança federada por meio de `wsFederationHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="878de-105">Windows Communication Foundation (WCF) provides support for deploying federated security architectures through the `wsFederationHttpBinding`.</span></span> <span data-ttu-id="878de-106">O `wsFederationHttpBinding` fornece uma associação segura, confiável e interoperável que envolve o uso de HTTP como o mecanismo de transporte subjacente para comunicação de solicitação/resposta e Text/XML como formato de conexão para a codificação.</span><span class="sxs-lookup"><span data-stu-id="878de-106">The `wsFederationHttpBinding` provides a secure, reliable, and interoperable binding that involves the use of HTTP as the underlying transport mechanism for request/reply communication, and Text/XML as the wire format for encoding.</span></span> <span data-ttu-id="878de-107">Para obter mais informações sobre a federação no WCF, consulte [federação](../../../../docs/framework/wcf/feature-details/federation.md).</span><span class="sxs-lookup"><span data-stu-id="878de-107">For more information about Federation in WCF, see [Federation](../../../../docs/framework/wcf/feature-details/federation.md).</span></span>  
  
 <span data-ttu-id="878de-108">O cenário é composto por 4 partes:</span><span class="sxs-lookup"><span data-stu-id="878de-108">The scenario is made up of 4 pieces:</span></span>  
  
- <span data-ttu-id="878de-109">Serviço livraria</span><span class="sxs-lookup"><span data-stu-id="878de-109">BookStore service</span></span>  
  
- <span data-ttu-id="878de-110">Livraria STS</span><span class="sxs-lookup"><span data-stu-id="878de-110">BookStore STS</span></span>  
  
- <span data-ttu-id="878de-111">HomeRealm STS</span><span class="sxs-lookup"><span data-stu-id="878de-111">HomeRealm STS</span></span>  
  
- <span data-ttu-id="878de-112">Cliente livraria</span><span class="sxs-lookup"><span data-stu-id="878de-112">BookStore Client</span></span>  
  
 <span data-ttu-id="878de-113">O serviço de livraria dá suporte a duas operações, `BrowseBooks` e `BuyBook`.</span><span class="sxs-lookup"><span data-stu-id="878de-113">The BookStore service supports two operations, `BrowseBooks` and `BuyBook`.</span></span> <span data-ttu-id="878de-114">Ele permite o acesso anônimo para o `BrowseBooks` operação, mas requer acesso autenticado para acessar o `BuyBooks` operação.</span><span class="sxs-lookup"><span data-stu-id="878de-114">It allows anonymous access to the `BrowseBooks` operation, but requires authenticated access to access the `BuyBooks` operation.</span></span> <span data-ttu-id="878de-115">A autenticação assume a forma de um token emitido pelo STS livraria.</span><span class="sxs-lookup"><span data-stu-id="878de-115">The authentication takes the form of a token issued by the BookStore STS.</span></span> <span data-ttu-id="878de-116">O arquivo de configuração para o serviço livraria aponta os clientes para o STS da livraria usando o `wsFederationHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="878de-116">The configuration file for the BookStore Service points clients to the BookStore STS using the `wsFederationHttpBinding`.</span></span>  
  
```xml  
<wsFederationHttpBinding>  
<!-- This is the Service binding for the BuyBooks endpoint. It redirects clients to the BookStore STS -->  
    <binding name='BuyBookBinding'>  
        <security mode="Message">  
            <message>  
                <issuerMetadata  
  address='http://localhost/FederationSample/BookStoreSTS/STS.svc/mex' >  
                    <identity>  
                        <dns value ='BookStoreSTS.com'/>  
                    </identity>  
                </issuerMetadata>  
            </message>  
        </security>  
    </binding>  
</wsFederationHttpBinding>  
```  
  
 <span data-ttu-id="878de-117">O STS da livraria, em seguida, exige que os clientes se autenticar usando um token emitido pelo STS HomeRealm.</span><span class="sxs-lookup"><span data-stu-id="878de-117">The BookStore STS then requires that clients authenticate using a token issued by the HomeRealm STS.</span></span> <span data-ttu-id="878de-118">Novamente, o arquivo de configuração para o STS da livraria aponta os clientes para o STS HomeRealm usando o `wsFederationHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="878de-118">Again, the configuration file for the BookStore STS points clients to the HomeRealm STS using the `wsFederationHttpBinding`.</span></span>  
  
```xml  
<wsFederationHttpBinding>  
 <!-- This is the binding for the clients requesting tokens from this STS. It redirects clients to the HomeRealm STS -->  
    <binding name='BookStoreSTSBinding'>  
        <security mode='Message'>  
            <message>  
                <issuerMetadata  
 address='http://localhost/FederationSample/HomeRealmSTS/STS.svc/mex' >  
                    <identity>  
                        <dns value ='HomeRealmSTS.com' />  
                    </identity>  
                </issuerMetadata>  
            </message>  
        </security>  
    </binding>  
</wsFederationHttpBinding>  
```  
  
 <span data-ttu-id="878de-119">A sequência de eventos ao acessar o `BuyBook` operação é da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="878de-119">The sequence of events when accessing the `BuyBook` operation is as follows:</span></span>  
  
1. <span data-ttu-id="878de-120">O cliente é autenticado para o STS HomeRealm usando as credenciais do Windows.</span><span class="sxs-lookup"><span data-stu-id="878de-120">The client authenticates to the HomeRealm STS using Windows credentials.</span></span>  
  
2. <span data-ttu-id="878de-121">O STS HomeRealm emite um token que pode ser usado para se autenticar no STS livraria.</span><span class="sxs-lookup"><span data-stu-id="878de-121">The HomeRealm STS issues a token that can be used to authenticate to the BookStore STS.</span></span>  
  
3. <span data-ttu-id="878de-122">O cliente é autenticado para o STS da livraria usando o token emitido pelo STS HomeRealm.</span><span class="sxs-lookup"><span data-stu-id="878de-122">The client authenticates to the BookStore STS using the token issued by the HomeRealm STS.</span></span>  
  
4. <span data-ttu-id="878de-123">O STS da livraria emite um token que pode ser usado para autenticar o serviço de livraria.</span><span class="sxs-lookup"><span data-stu-id="878de-123">The BookStore STS issues a token that can be used to authenticate to the BookStore Service.</span></span>  
  
5. <span data-ttu-id="878de-124">O cliente é autenticado para o serviço de livraria usando o token emitido pelo STS livraria.</span><span class="sxs-lookup"><span data-stu-id="878de-124">The client authenticates to the BookStore service using the token issued by the BookStore STS.</span></span>  
  
6. <span data-ttu-id="878de-125">O cliente acessa o `BuyBook` operação.</span><span class="sxs-lookup"><span data-stu-id="878de-125">The client accesses the `BuyBook` operation.</span></span>  
  
 <span data-ttu-id="878de-126">Consulte as instruções a seguir sobre como configurar e executar esse exemplo.</span><span class="sxs-lookup"><span data-stu-id="878de-126">See the following instructions about how to set up and run this sample.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="878de-127">Você deve ter permissões de gravação para o **wwwroot** diretório para executar este exemplo.</span><span class="sxs-lookup"><span data-stu-id="878de-127">You must have Write permissions to the **wwwroot** directory to run this sample.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="878de-128">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="878de-128">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="878de-129">Abra a janela de comando do SDK.</span><span class="sxs-lookup"><span data-stu-id="878de-129">Open the SDK command window.</span></span> <span data-ttu-id="878de-130">No exemplo de caminho, execute Setup. bat.</span><span class="sxs-lookup"><span data-stu-id="878de-130">In the sample path, run Setup.bat.</span></span> <span data-ttu-id="878de-131">Isso cria os diretórios virtuais necessários para o exemplo e instala os certificados necessários com permissões apropriadas.</span><span class="sxs-lookup"><span data-stu-id="878de-131">This creates the virtual directories required for the sample and installs the required certificates with appropriate permissions.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="878de-132">O arquivo em lotes de Setup. bat foi projetado para ser executado a partir de um Prompt de comando do SDK do Windows.</span><span class="sxs-lookup"><span data-stu-id="878de-132">The Setup.bat batch file is designed to be run from a Windows SDK Command Prompt.</span></span> <span data-ttu-id="878de-133">Ele requer que a variável de ambiente MSSDK apontar para o diretório onde o SDK está instalado.</span><span class="sxs-lookup"><span data-stu-id="878de-133">It requires that the MSSDK environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="878de-134">Essa variável de ambiente é definido automaticamente dentro de um Prompt de comando do SDK do Windows.</span><span class="sxs-lookup"><span data-stu-id="878de-134">This environment variable is automatically set within a Windows SDK Command Prompt.</span></span> <span data-ttu-id="878de-135">Em [!INCLUDE[wv](../../../../includes/wv-md.md)], você deve garantir que o gerenciamento de compatibilidade do IIS 6.0 está instalado porque o conjunto de backup usa scripts de administrador do IIS.</span><span class="sxs-lookup"><span data-stu-id="878de-135">On [!INCLUDE[wv](../../../../includes/wv-md.md)], you must ensure that IIS 6.0 Management Compatibility is installed because the set up uses IIS administrator scripts.</span></span> <span data-ttu-id="878de-136">Execução do script de configuração em [!INCLUDE[wv](../../../../includes/wv-md.md)] requer privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="878de-136">Running the set-up script on [!INCLUDE[wv](../../../../includes/wv-md.md)] requires administrator privileges.</span></span>  
  
2. <span data-ttu-id="878de-137">Abra FederationSample.sln no Visual Studio e selecione **compilar solução** da **Build** menu.</span><span class="sxs-lookup"><span data-stu-id="878de-137">Open FederationSample.sln in Visual Studio and select **Build Solution** from the **Build** menu.</span></span> <span data-ttu-id="878de-138">Isso cria os arquivos de projeto comum, o serviço de livraria, livraria STS, HomeRealm STS e os implanta no IIS.</span><span class="sxs-lookup"><span data-stu-id="878de-138">This builds the common project files, Bookstore service, Bookstore STS, HomeRealm STS, and deploys them in IIS.</span></span> <span data-ttu-id="878de-139">Isso também criará o aplicativo de cliente da livraria e coloca o BookStoreClient.exe executável na pasta FederationSample\BookStoreClient\bin\Debug.</span><span class="sxs-lookup"><span data-stu-id="878de-139">This also builds the Bookstore client application and places the executable BookStoreClient.exe in the FederationSample\BookStoreClient\bin\Debug folder.</span></span>  
  
3. <span data-ttu-id="878de-140">Clique duas vezes em BookStoreClient.exe.</span><span class="sxs-lookup"><span data-stu-id="878de-140">Double-click BookStoreClient.exe.</span></span> <span data-ttu-id="878de-141">A janela BookStoreClient é exibida.</span><span class="sxs-lookup"><span data-stu-id="878de-141">The BookStoreClient window is displayed.</span></span>  
  
4. <span data-ttu-id="878de-142">Você pode procurar os livros disponíveis na livraria clicando **livros procurar**.</span><span class="sxs-lookup"><span data-stu-id="878de-142">You can browse the books available in the bookstore by clicking **Browse Books**.</span></span>  
  
5. <span data-ttu-id="878de-143">Para comprar um livro específico, selecione o catálogo na lista e clique em **comprar o livro**.</span><span class="sxs-lookup"><span data-stu-id="878de-143">To purchase a particular book, select the book in the list and click **Buy Book**.</span></span> <span data-ttu-id="878de-144">O aplicativo é iniciado e é autenticado usando a autenticação do Windows com o serviço de Token de segurança HomeRealm.</span><span class="sxs-lookup"><span data-stu-id="878de-144">The application starts up and authenticates using Windows authentication with the HomeRealm Security Token Service.</span></span>  
  
     <span data-ttu-id="878de-145">O exemplo é configurado para permitir aos usuários comprar livros que custam US $15 ou menos.</span><span class="sxs-lookup"><span data-stu-id="878de-145">The sample is configured to allow users to purchase books that cost $15 or less.</span></span> <span data-ttu-id="878de-146">Tentando comprar livros que custam mais do que os resultados de US $15 no cliente recebendo uma mensagem de acesso negado do serviço de Store de livro.</span><span class="sxs-lookup"><span data-stu-id="878de-146">Attempting to buy books that cost more than $15 results in the client getting an Access Denied message from the Book Store Service.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="878de-147">O exemplo não atualiza o limite de crédito do usuário depois de uma compra.</span><span class="sxs-lookup"><span data-stu-id="878de-147">The sample does not update the user’s credit limit after a purchase.</span></span> <span data-ttu-id="878de-148">Repetidamente, você pode comprar livros dentro do limite de crédito (fixa) do usuário.</span><span class="sxs-lookup"><span data-stu-id="878de-148">You can repeatedly purchase books within the user’s (fixed) credit limit.</span></span>  
  
#### <a name="to-clean-up"></a><span data-ttu-id="878de-149">Para limpar</span><span class="sxs-lookup"><span data-stu-id="878de-149">To clean up</span></span>  
  
1. <span data-ttu-id="878de-150">Execute CleanUp.</span><span class="sxs-lookup"><span data-stu-id="878de-150">Run Cleanup.bat.</span></span> <span data-ttu-id="878de-151">Isso exclui os diretórios virtuais que foram criados durante a instalação e também remove os certificados instalados durante a instalação.</span><span class="sxs-lookup"><span data-stu-id="878de-151">This deletes the virtual directories that were created during set up and also removes the certificates installed during setup.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="878de-152">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="878de-152">The samples may already be installed on your machine.</span></span> <span data-ttu-id="878de-153">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="878de-153">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="878de-154">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="878de-154">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="878de-155">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="878de-155">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\Federation`  
