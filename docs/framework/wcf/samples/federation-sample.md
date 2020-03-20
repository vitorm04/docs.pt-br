---
title: Exemplo de federação
ms.date: 03/30/2017
ms.assetid: 7e9da0ca-e925-4644-aa96-8bfaf649d4bb
ms.openlocfilehash: 9ec462f88c0e3a039b7f288554be3e28f13ece08
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144663"
---
# <a name="federation-sample"></a><span data-ttu-id="87cfc-102">Exemplo de federação</span><span class="sxs-lookup"><span data-stu-id="87cfc-102">Federation Sample</span></span>
<span data-ttu-id="87cfc-103">Esta amostra demonstra segurança federada.</span><span class="sxs-lookup"><span data-stu-id="87cfc-103">This sample demonstrates federated security.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="87cfc-104">Detalhes de exemplo</span><span class="sxs-lookup"><span data-stu-id="87cfc-104">Sample Details</span></span>  
 <span data-ttu-id="87cfc-105">A Windows Communication Foundation (WCF) oferece suporte para `wsFederationHttpBinding`a implantação de arquiteturas de segurança federadas através do .</span><span class="sxs-lookup"><span data-stu-id="87cfc-105">Windows Communication Foundation (WCF) provides support for deploying federated security architectures through the `wsFederationHttpBinding`.</span></span> <span data-ttu-id="87cfc-106">O `wsFederationHttpBinding` fornece uma vinculação segura, confiável e interoperável que envolve o uso do HTTP como mecanismo de transporte subjacente para comunicação de solicitação/resposta e texto/XML como o formato de fio para codificação.</span><span class="sxs-lookup"><span data-stu-id="87cfc-106">The `wsFederationHttpBinding` provides a secure, reliable, and interoperable binding that involves the use of HTTP as the underlying transport mechanism for request/reply communication, and Text/XML as the wire format for encoding.</span></span> <span data-ttu-id="87cfc-107">Para obter mais informações sobre a Federação no WCF, consulte [Federação](../../../../docs/framework/wcf/feature-details/federation.md).</span><span class="sxs-lookup"><span data-stu-id="87cfc-107">For more information about Federation in WCF, see [Federation](../../../../docs/framework/wcf/feature-details/federation.md).</span></span>  
  
 <span data-ttu-id="87cfc-108">O cenário é composto por 4 peças:</span><span class="sxs-lookup"><span data-stu-id="87cfc-108">The scenario is made up of 4 pieces:</span></span>  
  
- <span data-ttu-id="87cfc-109">Serviço bookstore</span><span class="sxs-lookup"><span data-stu-id="87cfc-109">BookStore service</span></span>  
  
- <span data-ttu-id="87cfc-110">Livraria STS</span><span class="sxs-lookup"><span data-stu-id="87cfc-110">BookStore STS</span></span>  
  
- <span data-ttu-id="87cfc-111">HomeRealm STS</span><span class="sxs-lookup"><span data-stu-id="87cfc-111">HomeRealm STS</span></span>  
  
- <span data-ttu-id="87cfc-112">Cliente bookstore</span><span class="sxs-lookup"><span data-stu-id="87cfc-112">BookStore Client</span></span>  
  
 <span data-ttu-id="87cfc-113">O serviço BookStore suporta `BrowseBooks` duas `BuyBook`operações e .</span><span class="sxs-lookup"><span data-stu-id="87cfc-113">The BookStore service supports two operations, `BrowseBooks` and `BuyBook`.</span></span> <span data-ttu-id="87cfc-114">Permite acesso anônimo `BrowseBooks` à operação, mas requer acesso `BuyBooks` autenticado para acessar a operação.</span><span class="sxs-lookup"><span data-stu-id="87cfc-114">It allows anonymous access to the `BrowseBooks` operation, but requires authenticated access to access the `BuyBooks` operation.</span></span> <span data-ttu-id="87cfc-115">A autenticação assume a forma de um token emitido pela BookStore STS.</span><span class="sxs-lookup"><span data-stu-id="87cfc-115">The authentication takes the form of a token issued by the BookStore STS.</span></span> <span data-ttu-id="87cfc-116">O arquivo de configuração do Serviço BookStore aponta `wsFederationHttpBinding`os clientes para o STS da BookStore usando o .</span><span class="sxs-lookup"><span data-stu-id="87cfc-116">The configuration file for the BookStore Service points clients to the BookStore STS using the `wsFederationHttpBinding`.</span></span>  
  
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
  
 <span data-ttu-id="87cfc-117">O BookStore STS exige então que os clientes se autentiquem usando um token emitido pelo HomeRealm STS.</span><span class="sxs-lookup"><span data-stu-id="87cfc-117">The BookStore STS then requires that clients authenticate using a token issued by the HomeRealm STS.</span></span> <span data-ttu-id="87cfc-118">Novamente, o arquivo de configuração do BookStore STS aponta `wsFederationHttpBinding`os clientes para o HomeRealm STS usando o .</span><span class="sxs-lookup"><span data-stu-id="87cfc-118">Again, the configuration file for the BookStore STS points clients to the HomeRealm STS using the `wsFederationHttpBinding`.</span></span>  
  
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
  
 <span data-ttu-id="87cfc-119">A seqüência de `BuyBook` eventos ao acessar a operação é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="87cfc-119">The sequence of events when accessing the `BuyBook` operation is as follows:</span></span>  
  
1. <span data-ttu-id="87cfc-120">O cliente autentica-se no HomeRealm STS usando credenciais do Windows.</span><span class="sxs-lookup"><span data-stu-id="87cfc-120">The client authenticates to the HomeRealm STS using Windows credentials.</span></span>  
  
2. <span data-ttu-id="87cfc-121">O HomeRealm STS emite um token que pode ser usado para autenticar o STS da BookStore.</span><span class="sxs-lookup"><span data-stu-id="87cfc-121">The HomeRealm STS issues a token that can be used to authenticate to the BookStore STS.</span></span>  
  
3. <span data-ttu-id="87cfc-122">O cliente autentica-se no STS da BookStore usando o token emitido pelo HomeRealm STS.</span><span class="sxs-lookup"><span data-stu-id="87cfc-122">The client authenticates to the BookStore STS using the token issued by the HomeRealm STS.</span></span>  
  
4. <span data-ttu-id="87cfc-123">O BookStore STS emite um token que pode ser usado para autenticar no Serviço BookStore.</span><span class="sxs-lookup"><span data-stu-id="87cfc-123">The BookStore STS issues a token that can be used to authenticate to the BookStore Service.</span></span>  
  
5. <span data-ttu-id="87cfc-124">O cliente autentica-se no serviço BookStore usando o token emitido pelo STS da BookStore.</span><span class="sxs-lookup"><span data-stu-id="87cfc-124">The client authenticates to the BookStore service using the token issued by the BookStore STS.</span></span>  
  
6. <span data-ttu-id="87cfc-125">O cliente acessa a `BuyBook` operação.</span><span class="sxs-lookup"><span data-stu-id="87cfc-125">The client accesses the `BuyBook` operation.</span></span>  
  
 <span data-ttu-id="87cfc-126">Veja as instruções a seguir sobre como configurar e executar esta amostra.</span><span class="sxs-lookup"><span data-stu-id="87cfc-126">See the following instructions about how to set up and run this sample.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="87cfc-127">Você deve ter permissões de gravação para o diretório **wwwroot** para executar esta amostra.</span><span class="sxs-lookup"><span data-stu-id="87cfc-127">You must have Write permissions to the **wwwroot** directory to run this sample.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="87cfc-128">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="87cfc-128">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="87cfc-129">Abra a janela de comando SDK.</span><span class="sxs-lookup"><span data-stu-id="87cfc-129">Open the SDK command window.</span></span> <span data-ttu-id="87cfc-130">No caminho da amostra, execute Setup.bat.</span><span class="sxs-lookup"><span data-stu-id="87cfc-130">In the sample path, run Setup.bat.</span></span> <span data-ttu-id="87cfc-131">Isso cria os diretórios virtuais necessários para a amostra e instala os certificados necessários com permissões apropriadas.</span><span class="sxs-lookup"><span data-stu-id="87cfc-131">This creates the virtual directories required for the sample and installs the required certificates with appropriate permissions.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="87cfc-132">O arquivo de lote Setup.bat foi projetado para ser executado a partir de um prompt de comando do Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="87cfc-132">The Setup.bat batch file is designed to be run from a Windows SDK Command Prompt.</span></span> <span data-ttu-id="87cfc-133">Requer que a variável ambiente MSSDK aponte para o diretório onde o SDK está instalado.</span><span class="sxs-lookup"><span data-stu-id="87cfc-133">It requires that the MSSDK environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="87cfc-134">Essa variável de ambiente é definida automaticamente dentro de um prompt de comando Do Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="87cfc-134">This environment variable is automatically set within a Windows SDK Command Prompt.</span></span> <span data-ttu-id="87cfc-135">No Windows Vista, você deve garantir que a compatibilidade de gerenciamento do IIS 6.0 esteja instalada porque a configuração usa scripts de administrador iis.</span><span class="sxs-lookup"><span data-stu-id="87cfc-135">On Windows Vista, you must ensure that IIS 6.0 Management Compatibility is installed because the set up uses IIS administrator scripts.</span></span> <span data-ttu-id="87cfc-136">A execução do script de configuração no Windows Vista requer privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="87cfc-136">Running the set-up script on Windows Vista requires administrator privileges.</span></span>  
  
2. <span data-ttu-id="87cfc-137">Abra FederationSample.sln no Visual Studio e selecione **Build Solution** no menu **Build.**</span><span class="sxs-lookup"><span data-stu-id="87cfc-137">Open FederationSample.sln in Visual Studio and select **Build Solution** from the **Build** menu.</span></span> <span data-ttu-id="87cfc-138">Isso constrói os arquivos comuns do projeto, serviço de livraria, livraria STS, HomeRealm STS, e os implanta no IIS.</span><span class="sxs-lookup"><span data-stu-id="87cfc-138">This builds the common project files, Bookstore service, Bookstore STS, HomeRealm STS, and deploys them in IIS.</span></span> <span data-ttu-id="87cfc-139">Isso também cria o aplicativo cliente Livraria e coloca o executável BookStoreClient.exe na pasta FederationSample\BookStoreClient\bin\Debug.</span><span class="sxs-lookup"><span data-stu-id="87cfc-139">This also builds the Bookstore client application and places the executable BookStoreClient.exe in the FederationSample\BookStoreClient\bin\Debug folder.</span></span>  
  
3. <span data-ttu-id="87cfc-140">Clique duas vezes em BookStoreClient.exe.</span><span class="sxs-lookup"><span data-stu-id="87cfc-140">Double-click BookStoreClient.exe.</span></span> <span data-ttu-id="87cfc-141">A janela BookStoreClient é exibida.</span><span class="sxs-lookup"><span data-stu-id="87cfc-141">The BookStoreClient window is displayed.</span></span>  
  
4. <span data-ttu-id="87cfc-142">Você pode navegar pelos livros disponíveis na livraria clicando em **Procurar Livros**.</span><span class="sxs-lookup"><span data-stu-id="87cfc-142">You can browse the books available in the bookstore by clicking **Browse Books**.</span></span>  
  
5. <span data-ttu-id="87cfc-143">Para comprar um livro específico, selecione o livro na lista e clique em **Comprar Livro**.</span><span class="sxs-lookup"><span data-stu-id="87cfc-143">To purchase a particular book, select the book in the list and click **Buy Book**.</span></span> <span data-ttu-id="87cfc-144">O aplicativo é iniciado e autentica do uso da autenticação do Windows com o HomeRealm Security Token Service.</span><span class="sxs-lookup"><span data-stu-id="87cfc-144">The application starts up and authenticates using Windows authentication with the HomeRealm Security Token Service.</span></span>  
  
     <span data-ttu-id="87cfc-145">A amostra é configurada para permitir que os usuários comprem livros que custam US$ 15 ou menos.</span><span class="sxs-lookup"><span data-stu-id="87cfc-145">The sample is configured to allow users to purchase books that cost $15 or less.</span></span> <span data-ttu-id="87cfc-146">Tentar comprar livros que custam mais de US$ 15 resulta no cliente recebendo uma mensagem de acesso negado do Serviço de Livraria.</span><span class="sxs-lookup"><span data-stu-id="87cfc-146">Attempting to buy books that cost more than $15 results in the client getting an Access Denied message from the Book Store Service.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="87cfc-147">A amostra não atualiza o limite de crédito do usuário após uma compra.</span><span class="sxs-lookup"><span data-stu-id="87cfc-147">The sample does not update the user’s credit limit after a purchase.</span></span> <span data-ttu-id="87cfc-148">Você pode comprar livros repetidamente dentro do limite de crédito (fixo) do usuário.</span><span class="sxs-lookup"><span data-stu-id="87cfc-148">You can repeatedly purchase books within the user’s (fixed) credit limit.</span></span>  
  
#### <a name="to-clean-up"></a><span data-ttu-id="87cfc-149">Para limpar</span><span class="sxs-lookup"><span data-stu-id="87cfc-149">To clean up</span></span>  
  
1. <span data-ttu-id="87cfc-150">Executar Cleanup.bat.</span><span class="sxs-lookup"><span data-stu-id="87cfc-150">Run Cleanup.bat.</span></span> <span data-ttu-id="87cfc-151">Isso exclui os diretórios virtuais que foram criados durante a configuração e também remove os certificados instalados durante a configuração.</span><span class="sxs-lookup"><span data-stu-id="87cfc-151">This deletes the virtual directories that were created during set up and also removes the certificates installed during setup.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="87cfc-152">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="87cfc-152">The samples may already be installed on your machine.</span></span> <span data-ttu-id="87cfc-153">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="87cfc-153">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="87cfc-154">Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="87cfc-154">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="87cfc-155">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="87cfc-155">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\Federation`  
