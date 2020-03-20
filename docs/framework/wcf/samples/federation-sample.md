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
# <a name="federation-sample"></a>Exemplo de federação
Esta amostra demonstra segurança federada.  
  
## <a name="sample-details"></a>Detalhes de exemplo  
 A Windows Communication Foundation (WCF) oferece suporte para `wsFederationHttpBinding`a implantação de arquiteturas de segurança federadas através do . O `wsFederationHttpBinding` fornece uma vinculação segura, confiável e interoperável que envolve o uso do HTTP como mecanismo de transporte subjacente para comunicação de solicitação/resposta e texto/XML como o formato de fio para codificação. Para obter mais informações sobre a Federação no WCF, consulte [Federação](../../../../docs/framework/wcf/feature-details/federation.md).  
  
 O cenário é composto por 4 peças:  
  
- Serviço bookstore  
  
- Livraria STS  
  
- HomeRealm STS  
  
- Cliente bookstore  
  
 O serviço BookStore suporta `BrowseBooks` duas `BuyBook`operações e . Permite acesso anônimo `BrowseBooks` à operação, mas requer acesso `BuyBooks` autenticado para acessar a operação. A autenticação assume a forma de um token emitido pela BookStore STS. O arquivo de configuração do Serviço BookStore aponta `wsFederationHttpBinding`os clientes para o STS da BookStore usando o .  
  
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
  
 O BookStore STS exige então que os clientes se autentiquem usando um token emitido pelo HomeRealm STS. Novamente, o arquivo de configuração do BookStore STS aponta `wsFederationHttpBinding`os clientes para o HomeRealm STS usando o .  
  
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
  
 A seqüência de `BuyBook` eventos ao acessar a operação é a seguinte:  
  
1. O cliente autentica-se no HomeRealm STS usando credenciais do Windows.  
  
2. O HomeRealm STS emite um token que pode ser usado para autenticar o STS da BookStore.  
  
3. O cliente autentica-se no STS da BookStore usando o token emitido pelo HomeRealm STS.  
  
4. O BookStore STS emite um token que pode ser usado para autenticar no Serviço BookStore.  
  
5. O cliente autentica-se no serviço BookStore usando o token emitido pelo STS da BookStore.  
  
6. O cliente acessa a `BuyBook` operação.  
  
 Veja as instruções a seguir sobre como configurar e executar esta amostra.  
  
> [!NOTE]
> Você deve ter permissões de gravação para o diretório **wwwroot** para executar esta amostra.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Abra a janela de comando SDK. No caminho da amostra, execute Setup.bat. Isso cria os diretórios virtuais necessários para a amostra e instala os certificados necessários com permissões apropriadas.  
  
    > [!NOTE]
    > O arquivo de lote Setup.bat foi projetado para ser executado a partir de um prompt de comando do Windows SDK. Requer que a variável ambiente MSSDK aponte para o diretório onde o SDK está instalado. Essa variável de ambiente é definida automaticamente dentro de um prompt de comando Do Windows SDK. No Windows Vista, você deve garantir que a compatibilidade de gerenciamento do IIS 6.0 esteja instalada porque a configuração usa scripts de administrador iis. A execução do script de configuração no Windows Vista requer privilégios de administrador.  
  
2. Abra FederationSample.sln no Visual Studio e selecione **Build Solution** no menu **Build.** Isso constrói os arquivos comuns do projeto, serviço de livraria, livraria STS, HomeRealm STS, e os implanta no IIS. Isso também cria o aplicativo cliente Livraria e coloca o executável BookStoreClient.exe na pasta FederationSample\BookStoreClient\bin\Debug.  
  
3. Clique duas vezes em BookStoreClient.exe. A janela BookStoreClient é exibida.  
  
4. Você pode navegar pelos livros disponíveis na livraria clicando em **Procurar Livros**.  
  
5. Para comprar um livro específico, selecione o livro na lista e clique em **Comprar Livro**. O aplicativo é iniciado e autentica do uso da autenticação do Windows com o HomeRealm Security Token Service.  
  
     A amostra é configurada para permitir que os usuários comprem livros que custam US$ 15 ou menos. Tentar comprar livros que custam mais de US$ 15 resulta no cliente recebendo uma mensagem de acesso negado do Serviço de Livraria.  
  
    > [!NOTE]
    > A amostra não atualiza o limite de crédito do usuário após uma compra. Você pode comprar livros repetidamente dentro do limite de crédito (fixo) do usuário.  
  
#### <a name="to-clean-up"></a>Para limpar  
  
1. Executar Cleanup.bat. Isso exclui os diretórios virtuais que foram criados durante a configuração e também remove os certificados instalados durante a configuração.  
  
> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\Federation`  
