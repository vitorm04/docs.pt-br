---
title: Exemplo de federação
ms.date: 03/30/2017
ms.assetid: 7e9da0ca-e925-4644-aa96-8bfaf649d4bb
ms.openlocfilehash: 271790e08476533fc1d83e22c5a0daf2f1eaa42a
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716932"
---
# <a name="federation-sample"></a><span data-ttu-id="0d39c-102">Exemplo de federação</span><span class="sxs-lookup"><span data-stu-id="0d39c-102">Federation Sample</span></span>
<span data-ttu-id="0d39c-103">Este exemplo demonstra a segurança federada.</span><span class="sxs-lookup"><span data-stu-id="0d39c-103">This sample demonstrates federated security.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="0d39c-104">Detalhes de exemplo</span><span class="sxs-lookup"><span data-stu-id="0d39c-104">Sample Details</span></span>  
 <span data-ttu-id="0d39c-105">O Windows Communication Foundation (WCF) oferece suporte para a implantação de arquiteturas de segurança federada por meio do `wsFederationHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="0d39c-105">Windows Communication Foundation (WCF) provides support for deploying federated security architectures through the `wsFederationHttpBinding`.</span></span> <span data-ttu-id="0d39c-106">O `wsFederationHttpBinding` fornece uma associação segura, confiável e interoperável que envolve o uso de HTTP como o mecanismo de transporte subjacente para a comunicação de solicitação/resposta e Text/XML como o formato de conexão para codificação.</span><span class="sxs-lookup"><span data-stu-id="0d39c-106">The `wsFederationHttpBinding` provides a secure, reliable, and interoperable binding that involves the use of HTTP as the underlying transport mechanism for request/reply communication, and Text/XML as the wire format for encoding.</span></span> <span data-ttu-id="0d39c-107">Para obter mais informações sobre Federação no WCF, consulte [Federação](../../../../docs/framework/wcf/feature-details/federation.md).</span><span class="sxs-lookup"><span data-stu-id="0d39c-107">For more information about Federation in WCF, see [Federation](../../../../docs/framework/wcf/feature-details/federation.md).</span></span>  
  
 <span data-ttu-id="0d39c-108">O cenário é composto de quatro partes:</span><span class="sxs-lookup"><span data-stu-id="0d39c-108">The scenario is made up of 4 pieces:</span></span>  
  
- <span data-ttu-id="0d39c-109">Serviço de livraria</span><span class="sxs-lookup"><span data-stu-id="0d39c-109">BookStore service</span></span>  
  
- <span data-ttu-id="0d39c-110">STS da livraria</span><span class="sxs-lookup"><span data-stu-id="0d39c-110">BookStore STS</span></span>  
  
- <span data-ttu-id="0d39c-111">STS HomeRealm</span><span class="sxs-lookup"><span data-stu-id="0d39c-111">HomeRealm STS</span></span>  
  
- <span data-ttu-id="0d39c-112">Cliente de livraria</span><span class="sxs-lookup"><span data-stu-id="0d39c-112">BookStore Client</span></span>  
  
 <span data-ttu-id="0d39c-113">O serviço de Livrarte dá suporte a duas operações, `BrowseBooks` e `BuyBook`.</span><span class="sxs-lookup"><span data-stu-id="0d39c-113">The BookStore service supports two operations, `BrowseBooks` and `BuyBook`.</span></span> <span data-ttu-id="0d39c-114">Ele permite acesso anônimo à operação de `BrowseBooks`, mas requer acesso autenticado para acessar a operação de `BuyBooks`.</span><span class="sxs-lookup"><span data-stu-id="0d39c-114">It allows anonymous access to the `BrowseBooks` operation, but requires authenticated access to access the `BuyBooks` operation.</span></span> <span data-ttu-id="0d39c-115">A autenticação assume a forma de um token emitido pelo STS da livraria.</span><span class="sxs-lookup"><span data-stu-id="0d39c-115">The authentication takes the form of a token issued by the BookStore STS.</span></span> <span data-ttu-id="0d39c-116">O arquivo de configuração para o serviço de Livrartes aponta os clientes para o STS da livraria usando o `wsFederationHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="0d39c-116">The configuration file for the BookStore Service points clients to the BookStore STS using the `wsFederationHttpBinding`.</span></span>  
  
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
  
 <span data-ttu-id="0d39c-117">Em seguida, o STS da livraria requer que os clientes se autentiquem usando um token emitido pelo STS HomeRealm.</span><span class="sxs-lookup"><span data-stu-id="0d39c-117">The BookStore STS then requires that clients authenticate using a token issued by the HomeRealm STS.</span></span> <span data-ttu-id="0d39c-118">Novamente, o arquivo de configuração para o STS de Livrarte aponta os clientes para o STS HomeRealm usando o `wsFederationHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="0d39c-118">Again, the configuration file for the BookStore STS points clients to the HomeRealm STS using the `wsFederationHttpBinding`.</span></span>  
  
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
  
 <span data-ttu-id="0d39c-119">A sequência de eventos ao acessar a operação de `BuyBook` é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="0d39c-119">The sequence of events when accessing the `BuyBook` operation is as follows:</span></span>  
  
1. <span data-ttu-id="0d39c-120">O cliente é autenticado no STS HomeRealm usando as credenciais do Windows.</span><span class="sxs-lookup"><span data-stu-id="0d39c-120">The client authenticates to the HomeRealm STS using Windows credentials.</span></span>  
  
2. <span data-ttu-id="0d39c-121">O STS HomeRealm emite um token que pode ser usado para autenticar o STS da livraria.</span><span class="sxs-lookup"><span data-stu-id="0d39c-121">The HomeRealm STS issues a token that can be used to authenticate to the BookStore STS.</span></span>  
  
3. <span data-ttu-id="0d39c-122">O cliente é autenticado no STS da livraria usando o token emitido pelo STS HomeRealm.</span><span class="sxs-lookup"><span data-stu-id="0d39c-122">The client authenticates to the BookStore STS using the token issued by the HomeRealm STS.</span></span>  
  
4. <span data-ttu-id="0d39c-123">O STS da livraria emite um token que pode ser usado para autenticar o serviço de livraria.</span><span class="sxs-lookup"><span data-stu-id="0d39c-123">The BookStore STS issues a token that can be used to authenticate to the BookStore Service.</span></span>  
  
5. <span data-ttu-id="0d39c-124">O cliente é autenticado no serviço de livraria usando o token emitido pelo STS da livraria.</span><span class="sxs-lookup"><span data-stu-id="0d39c-124">The client authenticates to the BookStore service using the token issued by the BookStore STS.</span></span>  
  
6. <span data-ttu-id="0d39c-125">O cliente acessa a operação de `BuyBook`.</span><span class="sxs-lookup"><span data-stu-id="0d39c-125">The client accesses the `BuyBook` operation.</span></span>  
  
 <span data-ttu-id="0d39c-126">Consulte as instruções a seguir sobre como configurar e executar este exemplo.</span><span class="sxs-lookup"><span data-stu-id="0d39c-126">See the following instructions about how to set up and run this sample.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0d39c-127">Você deve ter permissões de gravação para o diretório **wwwroot** para executar este exemplo.</span><span class="sxs-lookup"><span data-stu-id="0d39c-127">You must have Write permissions to the **wwwroot** directory to run this sample.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="0d39c-128">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="0d39c-128">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="0d39c-129">Abra a janela de comando do SDK.</span><span class="sxs-lookup"><span data-stu-id="0d39c-129">Open the SDK command window.</span></span> <span data-ttu-id="0d39c-130">No caminho de exemplo, execute Setup. bat.</span><span class="sxs-lookup"><span data-stu-id="0d39c-130">In the sample path, run Setup.bat.</span></span> <span data-ttu-id="0d39c-131">Isso cria os diretórios virtuais necessários para o exemplo e instala os certificados necessários com as permissões apropriadas.</span><span class="sxs-lookup"><span data-stu-id="0d39c-131">This creates the virtual directories required for the sample and installs the required certificates with appropriate permissions.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="0d39c-132">O arquivo em lotes setup. bat foi projetado para ser executado em um prompt de comando SDK do Windows.</span><span class="sxs-lookup"><span data-stu-id="0d39c-132">The Setup.bat batch file is designed to be run from a Windows SDK Command Prompt.</span></span> <span data-ttu-id="0d39c-133">Ele requer que a variável de ambiente MSSDK aponte para o diretório em que o SDK está instalado.</span><span class="sxs-lookup"><span data-stu-id="0d39c-133">It requires that the MSSDK environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="0d39c-134">Essa variável de ambiente é definida automaticamente em um prompt de comando SDK do Windows.</span><span class="sxs-lookup"><span data-stu-id="0d39c-134">This environment variable is automatically set within a Windows SDK Command Prompt.</span></span> <span data-ttu-id="0d39c-135">No [!INCLUDE[wv](../../../../includes/wv-md.md)], você deve garantir que a compatibilidade de gerenciamento do IIS 6,0 esteja instalada porque a configuração usa scripts de administrador do IIS.</span><span class="sxs-lookup"><span data-stu-id="0d39c-135">On [!INCLUDE[wv](../../../../includes/wv-md.md)], you must ensure that IIS 6.0 Management Compatibility is installed because the set up uses IIS administrator scripts.</span></span> <span data-ttu-id="0d39c-136">A execução do script de configuração no [!INCLUDE[wv](../../../../includes/wv-md.md)] requer privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="0d39c-136">Running the set-up script on [!INCLUDE[wv](../../../../includes/wv-md.md)] requires administrator privileges.</span></span>  
  
2. <span data-ttu-id="0d39c-137">Abra FederationSample. sln no Visual Studio e selecione **Compilar solução** no menu **Compilar** .</span><span class="sxs-lookup"><span data-stu-id="0d39c-137">Open FederationSample.sln in Visual Studio and select **Build Solution** from the **Build** menu.</span></span> <span data-ttu-id="0d39c-138">Isso cria os arquivos de projeto comuns, o serviço de livraria, o STS de livraria, o STS HomeRealm e os implanta no IIS.</span><span class="sxs-lookup"><span data-stu-id="0d39c-138">This builds the common project files, Bookstore service, Bookstore STS, HomeRealm STS, and deploys them in IIS.</span></span> <span data-ttu-id="0d39c-139">Isso também cria o aplicativo cliente de livraria e coloca o executável BookStoreClient. exe na pasta FederationSample\BookStoreClient\bin\Debug</span><span class="sxs-lookup"><span data-stu-id="0d39c-139">This also builds the Bookstore client application and places the executable BookStoreClient.exe in the FederationSample\BookStoreClient\bin\Debug folder.</span></span>  
  
3. <span data-ttu-id="0d39c-140">Clique duas vezes em BookStoreClient. exe.</span><span class="sxs-lookup"><span data-stu-id="0d39c-140">Double-click BookStoreClient.exe.</span></span> <span data-ttu-id="0d39c-141">A janela BookStoreClient é exibida.</span><span class="sxs-lookup"><span data-stu-id="0d39c-141">The BookStoreClient window is displayed.</span></span>  
  
4. <span data-ttu-id="0d39c-142">Você pode procurar os manuais disponíveis na livraria clicando em **Procurar livros**.</span><span class="sxs-lookup"><span data-stu-id="0d39c-142">You can browse the books available in the bookstore by clicking **Browse Books**.</span></span>  
  
5. <span data-ttu-id="0d39c-143">Para comprar um livro específico, selecione o livro na lista e clique em **comprar livro**.</span><span class="sxs-lookup"><span data-stu-id="0d39c-143">To purchase a particular book, select the book in the list and click **Buy Book**.</span></span> <span data-ttu-id="0d39c-144">O aplicativo inicia e autentica usando a autenticação do Windows com o serviço de token de segurança do HomeRealm.</span><span class="sxs-lookup"><span data-stu-id="0d39c-144">The application starts up and authenticates using Windows authentication with the HomeRealm Security Token Service.</span></span>  
  
     <span data-ttu-id="0d39c-145">O exemplo é configurado para permitir que os usuários adquiram livros que custam $15 ou menos.</span><span class="sxs-lookup"><span data-stu-id="0d39c-145">The sample is configured to allow users to purchase books that cost $15 or less.</span></span> <span data-ttu-id="0d39c-146">Tentar comprar livros que custam mais de $15 resultados no cliente que obtém uma mensagem de acesso negado do serviço de armazenamento de livros.</span><span class="sxs-lookup"><span data-stu-id="0d39c-146">Attempting to buy books that cost more than $15 results in the client getting an Access Denied message from the Book Store Service.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="0d39c-147">O exemplo não atualiza o limite de crédito do usuário após uma compra.</span><span class="sxs-lookup"><span data-stu-id="0d39c-147">The sample does not update the user’s credit limit after a purchase.</span></span> <span data-ttu-id="0d39c-148">Você pode comprar os livros repetidamente dentro do limite de crédito do usuário (fixo).</span><span class="sxs-lookup"><span data-stu-id="0d39c-148">You can repeatedly purchase books within the user’s (fixed) credit limit.</span></span>  
  
#### <a name="to-clean-up"></a><span data-ttu-id="0d39c-149">Para limpar</span><span class="sxs-lookup"><span data-stu-id="0d39c-149">To clean up</span></span>  
  
1. <span data-ttu-id="0d39c-150">Execute Cleanup. bat.</span><span class="sxs-lookup"><span data-stu-id="0d39c-150">Run Cleanup.bat.</span></span> <span data-ttu-id="0d39c-151">Isso exclui os diretórios virtuais que foram criados durante a configuração e também remove os certificados instalados durante a instalação.</span><span class="sxs-lookup"><span data-stu-id="0d39c-151">This deletes the virtual directories that were created during set up and also removes the certificates installed during setup.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="0d39c-152">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="0d39c-152">The samples may already be installed on your machine.</span></span> <span data-ttu-id="0d39c-153">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="0d39c-153">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="0d39c-154">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] amostras.</span><span class="sxs-lookup"><span data-stu-id="0d39c-154">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0d39c-155">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="0d39c-155">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\Federation`  
