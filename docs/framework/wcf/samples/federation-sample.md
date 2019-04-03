---
title: Exemplo de federação
ms.date: 03/30/2017
ms.assetid: 7e9da0ca-e925-4644-aa96-8bfaf649d4bb
ms.openlocfilehash: e9f0c47a1bafe715a40d150a77543ca71a249920
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58816597"
---
# <a name="federation-sample"></a>Exemplo de federação
Este exemplo demonstra a segurança federada.  
  
## <a name="sample-details"></a>Detalhes de exemplo  
 Windows Communication Foundation (WCF) oferece suporte para implantação de arquiteturas de segurança federada por meio de `wsFederationHttpBinding`. O `wsFederationHttpBinding` fornece uma associação segura, confiável e interoperável que envolve o uso de HTTP como o mecanismo de transporte subjacente para comunicação de solicitação/resposta e Text/XML como formato de conexão para a codificação. Para obter mais informações sobre a federação no WCF, consulte [federação](../../../../docs/framework/wcf/feature-details/federation.md).  
  
 O cenário é composto por 4 partes:  
  
-   Serviço livraria  
  
-   Livraria STS  
  
-   HomeRealm STS  
  
-   Cliente livraria  
  
 O serviço de livraria dá suporte a duas operações, `BrowseBooks` e `BuyBook`. Ele permite o acesso anônimo para o `BrowseBooks` operação, mas requer acesso autenticado para acessar o `BuyBooks` operação. A autenticação assume a forma de um token emitido pelo STS livraria. O arquivo de configuração para o serviço livraria aponta os clientes para o STS da livraria usando o `wsFederationHttpBinding`.  
  
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
  
 O STS da livraria, em seguida, exige que os clientes se autenticar usando um token emitido pelo STS HomeRealm. Novamente, o arquivo de configuração para o STS da livraria aponta os clientes para o STS HomeRealm usando o `wsFederationHttpBinding`.  
  
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
  
 A sequência de eventos ao acessar o `BuyBook` operação é da seguinte maneira:  
  
1.  O cliente é autenticado para o STS HomeRealm usando as credenciais do Windows.  
  
2.  O STS HomeRealm emite um token que pode ser usado para se autenticar no STS livraria.  
  
3.  O cliente é autenticado para o STS da livraria usando o token emitido pelo STS HomeRealm.  
  
4.  O STS da livraria emite um token que pode ser usado para autenticar o serviço de livraria.  
  
5.  O cliente é autenticado para o serviço de livraria usando o token emitido pelo STS livraria.  
  
6.  O cliente acessa o `BuyBook` operação.  
  
 Consulte as instruções a seguir sobre como configurar e executar esse exemplo.  
  
> [!NOTE]
>  Você deve ter permissões de gravação para o **wwwroot** diretório para executar este exemplo.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Abra a janela de comando do SDK. No exemplo de caminho, execute Setup. bat. Isso cria os diretórios virtuais necessários para o exemplo e instala os certificados necessários com permissões apropriadas.  
  
    > [!NOTE]
    >  O arquivo em lotes de Setup. bat foi projetado para ser executado a partir de um Prompt de comando do SDK do Windows. Ele requer que a variável de ambiente MSSDK apontar para o diretório onde o SDK está instalado. Essa variável de ambiente é definido automaticamente dentro de um Prompt de comando do SDK do Windows. Em [!INCLUDE[wv](../../../../includes/wv-md.md)], você deve garantir que o gerenciamento de compatibilidade do IIS 6.0 está instalado porque o conjunto de backup usa scripts de administrador do IIS. Execução do script de configuração em [!INCLUDE[wv](../../../../includes/wv-md.md)] requer privilégios de administrador.  
  
2.  Abra FederationSample.sln no Visual Studio e selecione **compilar solução** da **Build** menu. Isso cria os arquivos de projeto comum, o serviço de livraria, livraria STS, HomeRealm STS e os implanta no IIS. Isso também criará o aplicativo de cliente da livraria e coloca o BookStoreClient.exe executável na pasta FederationSample\BookStoreClient\bin\Debug.  
  
3.  Clique duas vezes em BookStoreClient.exe. A janela BookStoreClient é exibida.  
  
4.  Você pode procurar os livros disponíveis na livraria clicando **livros procurar**.  
  
5.  Para comprar um livro específico, selecione o catálogo na lista e clique em **comprar o livro**. O aplicativo é iniciado e é autenticado usando a autenticação do Windows com o serviço de Token de segurança HomeRealm.  
  
     O exemplo é configurado para permitir aos usuários comprar livros que custam US $15 ou menos. Tentando comprar livros que custam mais do que os resultados de US $15 no cliente recebendo uma mensagem de acesso negado do serviço de Store de livro.  
  
    > [!NOTE]
    >  O exemplo não atualiza o limite de crédito do usuário depois de uma compra. Repetidamente, você pode comprar livros dentro do limite de crédito (fixa) do usuário.  
  
#### <a name="to-clean-up"></a>Para limpar  
  
1.  Execute CleanUp. Isso exclui os diretórios virtuais que foram criados durante a instalação e também remove os certificados instalados durante a instalação.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\Federation`  
  
