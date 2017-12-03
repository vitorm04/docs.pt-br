---
title: "Exemplo de federação"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7e9da0ca-e925-4644-aa96-8bfaf649d4bb
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a13632318902ce08678a01c3e63b3d12cc2f4f20
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="federation-sample"></a><span data-ttu-id="78df6-102">Exemplo de federação</span><span class="sxs-lookup"><span data-stu-id="78df6-102">Federation Sample</span></span>
<span data-ttu-id="78df6-103">Este exemplo demonstra segurança federada.</span><span class="sxs-lookup"><span data-stu-id="78df6-103">This sample demonstrates federated security.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="78df6-104">Detalhes de exemplo</span><span class="sxs-lookup"><span data-stu-id="78df6-104">Sample Details</span></span>  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="78df6-105">fornece suporte para implantação de arquiteturas de segurança federada por meio de `wsFederationHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="78df6-105"> provides support for deploying federated security architectures through the `wsFederationHttpBinding`.</span></span> <span data-ttu-id="78df6-106">O `wsFederationHttpBinding` fornece uma associação segura, confiável e interoperável que envolve o uso do HTTP como o mecanismo de transporte subjacente para comunicação de solicitação/resposta e Text/XML como formato de conexão para a codificação.</span><span class="sxs-lookup"><span data-stu-id="78df6-106">The `wsFederationHttpBinding` provides a secure, reliable, and interoperable binding that involves the use of HTTP as the underlying transport mechanism for request/reply communication, and Text/XML as the wire format for encoding.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="78df6-107">Federação no [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], consulte [federação](../../../../docs/framework/wcf/feature-details/federation.md).</span><span class="sxs-lookup"><span data-stu-id="78df6-107"> Federation in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], see [Federation](../../../../docs/framework/wcf/feature-details/federation.md).</span></span>  
  
 <span data-ttu-id="78df6-108">O cenário é composto de 4 partes:</span><span class="sxs-lookup"><span data-stu-id="78df6-108">The scenario is made up of 4 pieces:</span></span>  
  
-   <span data-ttu-id="78df6-109">Serviço livraria</span><span class="sxs-lookup"><span data-stu-id="78df6-109">BookStore service</span></span>  
  
-   <span data-ttu-id="78df6-110">Livraria STS</span><span class="sxs-lookup"><span data-stu-id="78df6-110">BookStore STS</span></span>  
  
-   <span data-ttu-id="78df6-111">HomeRealm STS</span><span class="sxs-lookup"><span data-stu-id="78df6-111">HomeRealm STS</span></span>  
  
-   <span data-ttu-id="78df6-112">Cliente livraria</span><span class="sxs-lookup"><span data-stu-id="78df6-112">BookStore Client</span></span>  
  
 <span data-ttu-id="78df6-113">O serviço livraria dá suporte a duas operações, `BrowseBooks` e `BuyBook`.</span><span class="sxs-lookup"><span data-stu-id="78df6-113">The BookStore service supports two operations, `BrowseBooks` and `BuyBook`.</span></span> <span data-ttu-id="78df6-114">Permitir acesso anônimo para o `BrowseBooks` operação, mas requer acesso autenticado para acessar o `BuyBooks` operação.</span><span class="sxs-lookup"><span data-stu-id="78df6-114">It allows anonymous access to the `BrowseBooks` operation, but requires authenticated access to access the `BuyBooks` operation.</span></span> <span data-ttu-id="78df6-115">A autenticação assume a forma de um token emitido pelo STS livraria.</span><span class="sxs-lookup"><span data-stu-id="78df6-115">The authentication takes the form of a token issued by the BookStore STS.</span></span> <span data-ttu-id="78df6-116">O arquivo de configuração para o serviço livraria aponta clientes para o STS livraria usando o `wsFederationHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="78df6-116">The configuration file for the BookStore Service points clients to the BookStore STS using the `wsFederationHttpBinding`.</span></span>  
  
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
  
 <span data-ttu-id="78df6-117">O STS livraria requer que os clientes se autenticar usando um token emitido pelo STS HomeRealm.</span><span class="sxs-lookup"><span data-stu-id="78df6-117">The BookStore STS then requires that clients authenticate using a token issued by the HomeRealm STS.</span></span> <span data-ttu-id="78df6-118">Novamente, o arquivo de configuração para o STS livraria aponta clientes para o STS HomeRealm usando o `wsFederationHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="78df6-118">Again, the configuration file for the BookStore STS points clients to the HomeRealm STS using the `wsFederationHttpBinding`.</span></span>  
  
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
  
 <span data-ttu-id="78df6-119">A sequência de eventos ao acessar o `BuyBook` operação é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="78df6-119">The sequence of events when accessing the `BuyBook` operation is as follows:</span></span>  
  
1.  <span data-ttu-id="78df6-120">O cliente autentica para o STS HomeRealm usando credenciais do Windows.</span><span class="sxs-lookup"><span data-stu-id="78df6-120">The client authenticates to the HomeRealm STS using Windows credentials.</span></span>  
  
2.  <span data-ttu-id="78df6-121">HomeRealm STS emite um token que pode ser usado para autenticar para o STS livraria.</span><span class="sxs-lookup"><span data-stu-id="78df6-121">The HomeRealm STS issues a token that can be used to authenticate to the BookStore STS.</span></span>  
  
3.  <span data-ttu-id="78df6-122">O cliente autentica para o STS livraria usando o token emitido pelo STS HomeRealm.</span><span class="sxs-lookup"><span data-stu-id="78df6-122">The client authenticates to the BookStore STS using the token issued by the HomeRealm STS.</span></span>  
  
4.  <span data-ttu-id="78df6-123">O STS livraria emite um token que pode ser usado para autenticar o serviço livraria.</span><span class="sxs-lookup"><span data-stu-id="78df6-123">The BookStore STS issues a token that can be used to authenticate to the BookStore Service.</span></span>  
  
5.  <span data-ttu-id="78df6-124">O cliente autenticado para o serviço de livraria usando o token emitido pelo STS livraria.</span><span class="sxs-lookup"><span data-stu-id="78df6-124">The client authenticates to the BookStore service using the token issued by the BookStore STS.</span></span>  
  
6.  <span data-ttu-id="78df6-125">O cliente acessa o `BuyBook` operação.</span><span class="sxs-lookup"><span data-stu-id="78df6-125">The client accesses the `BuyBook` operation.</span></span>  
  
 <span data-ttu-id="78df6-126">Consulte as seguintes instruções sobre como configurar e executar esse exemplo.</span><span class="sxs-lookup"><span data-stu-id="78df6-126">See the following instructions about how to set up and run this sample.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="78df6-127">Você deve ter permissões de gravação para o **wwwroot** diretório para executar este exemplo.</span><span class="sxs-lookup"><span data-stu-id="78df6-127">You must have Write permissions to the **wwwroot** directory to run this sample.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="78df6-128">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="78df6-128">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="78df6-129">Abra a janela de comando do SDK.</span><span class="sxs-lookup"><span data-stu-id="78df6-129">Open the SDK command window.</span></span> <span data-ttu-id="78df6-130">No exemplo de caminho, execute bat.</span><span class="sxs-lookup"><span data-stu-id="78df6-130">In the sample path, run Setup.bat.</span></span> <span data-ttu-id="78df6-131">Isso cria os diretórios virtuais necessários para a amostra e instala os certificados necessários com permissões apropriadas.</span><span class="sxs-lookup"><span data-stu-id="78df6-131">This creates the virtual directories required for the sample and installs the required certificates with appropriate permissions.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="78df6-132">O arquivo em lotes bat é projetado para ser executado de um Prompt de comando do SDK do Windows.</span><span class="sxs-lookup"><span data-stu-id="78df6-132">The Setup.bat batch file is designed to be run from a Windows SDK Command Prompt.</span></span> <span data-ttu-id="78df6-133">Isso requer que a variável de ambiente MSSDK apontar para o diretório onde o SDK está instalado.</span><span class="sxs-lookup"><span data-stu-id="78df6-133">It requires that the MSSDK environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="78df6-134">Essa variável de ambiente é definida automaticamente em um Prompt de comando do SDK do Windows.</span><span class="sxs-lookup"><span data-stu-id="78df6-134">This environment variable is automatically set within a Windows SDK Command Prompt.</span></span> <span data-ttu-id="78df6-135">Em [!INCLUDE[wv](../../../../includes/wv-md.md)], certifique-se de que o gerenciamento de compatibilidade do IIS 6.0 está instalado porque o conjunto de backup usa scripts de administrador do IIS.</span><span class="sxs-lookup"><span data-stu-id="78df6-135">On [!INCLUDE[wv](../../../../includes/wv-md.md)], you must ensure that IIS 6.0 Management Compatibility is installed because the set up uses IIS administrator scripts.</span></span> <span data-ttu-id="78df6-136">Execução do script de configuração em [!INCLUDE[wv](../../../../includes/wv-md.md)] requer privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="78df6-136">Running the set-up script on [!INCLUDE[wv](../../../../includes/wv-md.md)] requires administrator privileges.</span></span>  
  
2.  <span data-ttu-id="78df6-137">Abra FederationSample.sln no Visual Studio e selecione **compilar solução** do **criar** menu.</span><span class="sxs-lookup"><span data-stu-id="78df6-137">Open FederationSample.sln in Visual Studio and select **Build Solution** from the **Build** menu.</span></span> <span data-ttu-id="78df6-138">Isso cria os arquivos de projeto comum, o serviço livraria livraria STS, HomeRealm STS e implanta-os no IIS.</span><span class="sxs-lookup"><span data-stu-id="78df6-138">This builds the common project files, Bookstore service, Bookstore STS, HomeRealm STS, and deploys them in IIS.</span></span> <span data-ttu-id="78df6-139">Isso também cria o aplicativo de cliente livraria e coloca o BookStoreClient.exe executável na pasta FederationSample\BookStoreClient\bin\Debug.</span><span class="sxs-lookup"><span data-stu-id="78df6-139">This also builds the Bookstore client application and places the executable BookStoreClient.exe in the FederationSample\BookStoreClient\bin\Debug folder.</span></span>  
  
3.  <span data-ttu-id="78df6-140">Clique duas vezes em BookStoreClient.exe.</span><span class="sxs-lookup"><span data-stu-id="78df6-140">Double-click BookStoreClient.exe.</span></span> <span data-ttu-id="78df6-141">A janela BookStoreClient é exibida.</span><span class="sxs-lookup"><span data-stu-id="78df6-141">The BookStoreClient window is displayed.</span></span>  
  
4.  <span data-ttu-id="78df6-142">Você pode procurar os livros disponíveis na livraria clicando **procurar manuais**.</span><span class="sxs-lookup"><span data-stu-id="78df6-142">You can browse the books available in the bookstore by clicking **Browse Books**.</span></span>  
  
5.  <span data-ttu-id="78df6-143">Para adquirir um catálogo específico, selecione o catálogo na lista e clique em **comprar catálogo**.</span><span class="sxs-lookup"><span data-stu-id="78df6-143">To purchase a particular book, select the book in the list and click **Buy Book**.</span></span> <span data-ttu-id="78df6-144">O aplicativo é iniciado e é autenticado usando a autenticação do Windows com o serviço de Token de segurança HomeRealm.</span><span class="sxs-lookup"><span data-stu-id="78df6-144">The application starts up and authenticates using Windows authentication with the HomeRealm Security Token Service.</span></span>  
  
     <span data-ttu-id="78df6-145">O exemplo é configurado para permitir que usuários Compre livros que custam r $15 ou menos.</span><span class="sxs-lookup"><span data-stu-id="78df6-145">The sample is configured to allow users to purchase books that cost $15 or less.</span></span> <span data-ttu-id="78df6-146">Tentando comprar livros que custam mais do que os resultados de r $15 no cliente que está recebendo uma mensagem de acesso negado do serviço de armazenamento do catálogo.</span><span class="sxs-lookup"><span data-stu-id="78df6-146">Attempting to buy books that cost more than $15 results in the client getting an Access Denied message from the Book Store Service.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="78df6-147">O exemplo não atualiza o limite de crédito do usuário após uma compra.</span><span class="sxs-lookup"><span data-stu-id="78df6-147">The sample does not update the user’s credit limit after a purchase.</span></span> <span data-ttu-id="78df6-148">Repetidamente, você pode comprar manuais no limite de crédito (fixo) do usuário.</span><span class="sxs-lookup"><span data-stu-id="78df6-148">You can repeatedly purchase books within the user’s (fixed) credit limit.</span></span>  
  
#### <a name="to-clean-up"></a><span data-ttu-id="78df6-149">Para limpar</span><span class="sxs-lookup"><span data-stu-id="78df6-149">To clean up</span></span>  
  
1.  <span data-ttu-id="78df6-150">Execute Cleanup.bat.</span><span class="sxs-lookup"><span data-stu-id="78df6-150">Run Cleanup.bat.</span></span> <span data-ttu-id="78df6-151">Isso exclui os diretórios virtuais que foram criados durante o conjunto de backup e também remove os certificados instalados durante a instalação.</span><span class="sxs-lookup"><span data-stu-id="78df6-151">This deletes the virtual directories that were created during set up and also removes the certificates installed during setup.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="78df6-152">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="78df6-152">The samples may already be installed on your machine.</span></span> <span data-ttu-id="78df6-153">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="78df6-153">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="78df6-154">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="78df6-154">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="78df6-155">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="78df6-155">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\Federation`  
  
## <a name="see-also"></a><span data-ttu-id="78df6-156">Consulte também</span><span class="sxs-lookup"><span data-stu-id="78df6-156">See Also</span></span>
