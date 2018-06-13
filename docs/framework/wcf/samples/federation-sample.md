---
title: Exemplo de federação
ms.date: 03/30/2017
ms.assetid: 7e9da0ca-e925-4644-aa96-8bfaf649d4bb
ms.openlocfilehash: a9c2b91f7d8bdf24476c76fcd479b7f2fb44c90f
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33806842"
---
# <a name="federation-sample"></a><span data-ttu-id="29e3b-102">Exemplo de federação</span><span class="sxs-lookup"><span data-stu-id="29e3b-102">Federation Sample</span></span>
<span data-ttu-id="29e3b-103">Este exemplo demonstra segurança federada.</span><span class="sxs-lookup"><span data-stu-id="29e3b-103">This sample demonstrates federated security.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="29e3b-104">Detalhes de exemplo</span><span class="sxs-lookup"><span data-stu-id="29e3b-104">Sample Details</span></span>  
 <span data-ttu-id="29e3b-105">Windows Communication Foundation (WCF) oferece suporte para implantação de arquiteturas de segurança federada por meio de `wsFederationHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="29e3b-105">Windows Communication Foundation (WCF) provides support for deploying federated security architectures through the `wsFederationHttpBinding`.</span></span> <span data-ttu-id="29e3b-106">O `wsFederationHttpBinding` fornece uma associação segura, confiável e interoperável que envolve o uso do HTTP como o mecanismo de transporte subjacente para comunicação de solicitação/resposta e Text/XML como formato de conexão para a codificação.</span><span class="sxs-lookup"><span data-stu-id="29e3b-106">The `wsFederationHttpBinding` provides a secure, reliable, and interoperable binding that involves the use of HTTP as the underlying transport mechanism for request/reply communication, and Text/XML as the wire format for encoding.</span></span> <span data-ttu-id="29e3b-107">Para obter mais informações sobre a federação no WCF, consulte [federação](../../../../docs/framework/wcf/feature-details/federation.md).</span><span class="sxs-lookup"><span data-stu-id="29e3b-107">For more information about Federation in WCF, see [Federation](../../../../docs/framework/wcf/feature-details/federation.md).</span></span>  
  
 <span data-ttu-id="29e3b-108">O cenário é composto de 4 partes:</span><span class="sxs-lookup"><span data-stu-id="29e3b-108">The scenario is made up of 4 pieces:</span></span>  
  
-   <span data-ttu-id="29e3b-109">Serviço livraria</span><span class="sxs-lookup"><span data-stu-id="29e3b-109">BookStore service</span></span>  
  
-   <span data-ttu-id="29e3b-110">Livraria STS</span><span class="sxs-lookup"><span data-stu-id="29e3b-110">BookStore STS</span></span>  
  
-   <span data-ttu-id="29e3b-111">HomeRealm STS</span><span class="sxs-lookup"><span data-stu-id="29e3b-111">HomeRealm STS</span></span>  
  
-   <span data-ttu-id="29e3b-112">Cliente livraria</span><span class="sxs-lookup"><span data-stu-id="29e3b-112">BookStore Client</span></span>  
  
 <span data-ttu-id="29e3b-113">O serviço livraria dá suporte a duas operações, `BrowseBooks` e `BuyBook`.</span><span class="sxs-lookup"><span data-stu-id="29e3b-113">The BookStore service supports two operations, `BrowseBooks` and `BuyBook`.</span></span> <span data-ttu-id="29e3b-114">Permitir acesso anônimo para o `BrowseBooks` operação, mas requer acesso autenticado para acessar o `BuyBooks` operação.</span><span class="sxs-lookup"><span data-stu-id="29e3b-114">It allows anonymous access to the `BrowseBooks` operation, but requires authenticated access to access the `BuyBooks` operation.</span></span> <span data-ttu-id="29e3b-115">A autenticação assume a forma de um token emitido pelo STS livraria.</span><span class="sxs-lookup"><span data-stu-id="29e3b-115">The authentication takes the form of a token issued by the BookStore STS.</span></span> <span data-ttu-id="29e3b-116">O arquivo de configuração para o serviço livraria aponta clientes para o STS livraria usando o `wsFederationHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="29e3b-116">The configuration file for the BookStore Service points clients to the BookStore STS using the `wsFederationHttpBinding`.</span></span>  
  
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
  
 <span data-ttu-id="29e3b-117">O STS livraria requer que os clientes se autenticar usando um token emitido pelo STS HomeRealm.</span><span class="sxs-lookup"><span data-stu-id="29e3b-117">The BookStore STS then requires that clients authenticate using a token issued by the HomeRealm STS.</span></span> <span data-ttu-id="29e3b-118">Novamente, o arquivo de configuração para o STS livraria aponta clientes para o STS HomeRealm usando o `wsFederationHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="29e3b-118">Again, the configuration file for the BookStore STS points clients to the HomeRealm STS using the `wsFederationHttpBinding`.</span></span>  
  
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
  
 <span data-ttu-id="29e3b-119">A sequência de eventos ao acessar o `BuyBook` operação é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="29e3b-119">The sequence of events when accessing the `BuyBook` operation is as follows:</span></span>  
  
1.  <span data-ttu-id="29e3b-120">O cliente autentica para o STS HomeRealm usando credenciais do Windows.</span><span class="sxs-lookup"><span data-stu-id="29e3b-120">The client authenticates to the HomeRealm STS using Windows credentials.</span></span>  
  
2.  <span data-ttu-id="29e3b-121">HomeRealm STS emite um token que pode ser usado para autenticar para o STS livraria.</span><span class="sxs-lookup"><span data-stu-id="29e3b-121">The HomeRealm STS issues a token that can be used to authenticate to the BookStore STS.</span></span>  
  
3.  <span data-ttu-id="29e3b-122">O cliente autentica para o STS livraria usando o token emitido pelo STS HomeRealm.</span><span class="sxs-lookup"><span data-stu-id="29e3b-122">The client authenticates to the BookStore STS using the token issued by the HomeRealm STS.</span></span>  
  
4.  <span data-ttu-id="29e3b-123">O STS livraria emite um token que pode ser usado para autenticar o serviço livraria.</span><span class="sxs-lookup"><span data-stu-id="29e3b-123">The BookStore STS issues a token that can be used to authenticate to the BookStore Service.</span></span>  
  
5.  <span data-ttu-id="29e3b-124">O cliente autenticado para o serviço de livraria usando o token emitido pelo STS livraria.</span><span class="sxs-lookup"><span data-stu-id="29e3b-124">The client authenticates to the BookStore service using the token issued by the BookStore STS.</span></span>  
  
6.  <span data-ttu-id="29e3b-125">O cliente acessa o `BuyBook` operação.</span><span class="sxs-lookup"><span data-stu-id="29e3b-125">The client accesses the `BuyBook` operation.</span></span>  
  
 <span data-ttu-id="29e3b-126">Consulte as seguintes instruções sobre como configurar e executar esse exemplo.</span><span class="sxs-lookup"><span data-stu-id="29e3b-126">See the following instructions about how to set up and run this sample.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="29e3b-127">Você deve ter permissões de gravação para o **wwwroot** diretório para executar este exemplo.</span><span class="sxs-lookup"><span data-stu-id="29e3b-127">You must have Write permissions to the **wwwroot** directory to run this sample.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="29e3b-128">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="29e3b-128">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="29e3b-129">Abra a janela de comando do SDK.</span><span class="sxs-lookup"><span data-stu-id="29e3b-129">Open the SDK command window.</span></span> <span data-ttu-id="29e3b-130">No exemplo de caminho, execute bat.</span><span class="sxs-lookup"><span data-stu-id="29e3b-130">In the sample path, run Setup.bat.</span></span> <span data-ttu-id="29e3b-131">Isso cria os diretórios virtuais necessários para a amostra e instala os certificados necessários com permissões apropriadas.</span><span class="sxs-lookup"><span data-stu-id="29e3b-131">This creates the virtual directories required for the sample and installs the required certificates with appropriate permissions.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="29e3b-132">O arquivo em lotes bat é projetado para ser executado de um Prompt de comando do SDK do Windows.</span><span class="sxs-lookup"><span data-stu-id="29e3b-132">The Setup.bat batch file is designed to be run from a Windows SDK Command Prompt.</span></span> <span data-ttu-id="29e3b-133">Isso requer que a variável de ambiente MSSDK apontar para o diretório onde o SDK está instalado.</span><span class="sxs-lookup"><span data-stu-id="29e3b-133">It requires that the MSSDK environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="29e3b-134">Essa variável de ambiente é definida automaticamente em um Prompt de comando do SDK do Windows.</span><span class="sxs-lookup"><span data-stu-id="29e3b-134">This environment variable is automatically set within a Windows SDK Command Prompt.</span></span> <span data-ttu-id="29e3b-135">Em [!INCLUDE[wv](../../../../includes/wv-md.md)], certifique-se de que o gerenciamento de compatibilidade do IIS 6.0 está instalado porque o conjunto de backup usa scripts de administrador do IIS.</span><span class="sxs-lookup"><span data-stu-id="29e3b-135">On [!INCLUDE[wv](../../../../includes/wv-md.md)], you must ensure that IIS 6.0 Management Compatibility is installed because the set up uses IIS administrator scripts.</span></span> <span data-ttu-id="29e3b-136">Execução do script de configuração em [!INCLUDE[wv](../../../../includes/wv-md.md)] requer privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="29e3b-136">Running the set-up script on [!INCLUDE[wv](../../../../includes/wv-md.md)] requires administrator privileges.</span></span>  
  
2.  <span data-ttu-id="29e3b-137">Abra FederationSample.sln no Visual Studio e selecione **compilar solução** do **criar** menu.</span><span class="sxs-lookup"><span data-stu-id="29e3b-137">Open FederationSample.sln in Visual Studio and select **Build Solution** from the **Build** menu.</span></span> <span data-ttu-id="29e3b-138">Isso cria os arquivos de projeto comum, o serviço livraria livraria STS, HomeRealm STS e implanta-os no IIS.</span><span class="sxs-lookup"><span data-stu-id="29e3b-138">This builds the common project files, Bookstore service, Bookstore STS, HomeRealm STS, and deploys them in IIS.</span></span> <span data-ttu-id="29e3b-139">Isso também cria o aplicativo de cliente livraria e coloca o BookStoreClient.exe executável na pasta FederationSample\BookStoreClient\bin\Debug.</span><span class="sxs-lookup"><span data-stu-id="29e3b-139">This also builds the Bookstore client application and places the executable BookStoreClient.exe in the FederationSample\BookStoreClient\bin\Debug folder.</span></span>  
  
3.  <span data-ttu-id="29e3b-140">Clique duas vezes em BookStoreClient.exe.</span><span class="sxs-lookup"><span data-stu-id="29e3b-140">Double-click BookStoreClient.exe.</span></span> <span data-ttu-id="29e3b-141">A janela BookStoreClient é exibida.</span><span class="sxs-lookup"><span data-stu-id="29e3b-141">The BookStoreClient window is displayed.</span></span>  
  
4.  <span data-ttu-id="29e3b-142">Você pode procurar os livros disponíveis na livraria clicando **procurar manuais**.</span><span class="sxs-lookup"><span data-stu-id="29e3b-142">You can browse the books available in the bookstore by clicking **Browse Books**.</span></span>  
  
5.  <span data-ttu-id="29e3b-143">Para adquirir um catálogo específico, selecione o catálogo na lista e clique em **comprar catálogo**.</span><span class="sxs-lookup"><span data-stu-id="29e3b-143">To purchase a particular book, select the book in the list and click **Buy Book**.</span></span> <span data-ttu-id="29e3b-144">O aplicativo é iniciado e é autenticado usando a autenticação do Windows com o serviço de Token de segurança HomeRealm.</span><span class="sxs-lookup"><span data-stu-id="29e3b-144">The application starts up and authenticates using Windows authentication with the HomeRealm Security Token Service.</span></span>  
  
     <span data-ttu-id="29e3b-145">O exemplo é configurado para permitir que usuários Compre livros que custam r $15 ou menos.</span><span class="sxs-lookup"><span data-stu-id="29e3b-145">The sample is configured to allow users to purchase books that cost $15 or less.</span></span> <span data-ttu-id="29e3b-146">Tentando comprar livros que custam mais do que os resultados de r $15 no cliente que está recebendo uma mensagem de acesso negado do serviço de armazenamento do catálogo.</span><span class="sxs-lookup"><span data-stu-id="29e3b-146">Attempting to buy books that cost more than $15 results in the client getting an Access Denied message from the Book Store Service.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="29e3b-147">O exemplo não atualiza o limite de crédito do usuário após uma compra.</span><span class="sxs-lookup"><span data-stu-id="29e3b-147">The sample does not update the user’s credit limit after a purchase.</span></span> <span data-ttu-id="29e3b-148">Repetidamente, você pode comprar manuais no limite de crédito (fixo) do usuário.</span><span class="sxs-lookup"><span data-stu-id="29e3b-148">You can repeatedly purchase books within the user’s (fixed) credit limit.</span></span>  
  
#### <a name="to-clean-up"></a><span data-ttu-id="29e3b-149">Para limpar</span><span class="sxs-lookup"><span data-stu-id="29e3b-149">To clean up</span></span>  
  
1.  <span data-ttu-id="29e3b-150">Execute Cleanup.bat.</span><span class="sxs-lookup"><span data-stu-id="29e3b-150">Run Cleanup.bat.</span></span> <span data-ttu-id="29e3b-151">Isso exclui os diretórios virtuais que foram criados durante o conjunto de backup e também remove os certificados instalados durante a instalação.</span><span class="sxs-lookup"><span data-stu-id="29e3b-151">This deletes the virtual directories that were created during set up and also removes the certificates installed during setup.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="29e3b-152">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="29e3b-152">The samples may already be installed on your machine.</span></span> <span data-ttu-id="29e3b-153">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="29e3b-153">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="29e3b-154">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="29e3b-154">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="29e3b-155">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="29e3b-155">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\Federation`  
  
## <a name="see-also"></a><span data-ttu-id="29e3b-156">Consulte também</span><span class="sxs-lookup"><span data-stu-id="29e3b-156">See Also</span></span>
