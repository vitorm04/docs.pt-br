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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b66bf65ba6165902eb90191a262f2715424d8b7e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="federation-sample"></a>Exemplo de federação
Este exemplo demonstra segurança federada.  
  
## <a name="sample-details"></a>Detalhes de exemplo  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]fornece suporte para implantação de arquiteturas de segurança federada por meio de `wsFederationHttpBinding`. O `wsFederationHttpBinding` fornece uma associação segura, confiável e interoperável que envolve o uso do HTTP como o mecanismo de transporte subjacente para comunicação de solicitação/resposta e Text/XML como formato de conexão para a codificação. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Federação no [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], consulte [federação](../../../../docs/framework/wcf/feature-details/federation.md).  
  
 O cenário é composto de 4 partes:  
  
-   Serviço livraria  
  
-   Livraria STS  
  
-   HomeRealm STS  
  
-   Cliente livraria  
  
 O serviço livraria dá suporte a duas operações, `BrowseBooks` e `BuyBook`. Permitir acesso anônimo para o `BrowseBooks` operação, mas requer acesso autenticado para acessar o `BuyBooks` operação. A autenticação assume a forma de um token emitido pelo STS livraria. O arquivo de configuração para o serviço livraria aponta clientes para o STS livraria usando o `wsFederationHttpBinding`.  
  
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
  
 O STS livraria requer que os clientes se autenticar usando um token emitido pelo STS HomeRealm. Novamente, o arquivo de configuração para o STS livraria aponta clientes para o STS HomeRealm usando o `wsFederationHttpBinding`.  
  
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
  
 A sequência de eventos ao acessar o `BuyBook` operação é o seguinte:  
  
1.  O cliente autentica para o STS HomeRealm usando credenciais do Windows.  
  
2.  HomeRealm STS emite um token que pode ser usado para autenticar para o STS livraria.  
  
3.  O cliente autentica para o STS livraria usando o token emitido pelo STS HomeRealm.  
  
4.  O STS livraria emite um token que pode ser usado para autenticar o serviço livraria.  
  
5.  O cliente autenticado para o serviço de livraria usando o token emitido pelo STS livraria.  
  
6.  O cliente acessa o `BuyBook` operação.  
  
 Consulte as seguintes instruções sobre como configurar e executar esse exemplo.  
  
> [!NOTE]
>  Você deve ter permissões de gravação para o **wwwroot** diretório para executar este exemplo.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Abra a janela de comando do SDK. No exemplo de caminho, execute bat. Isso cria os diretórios virtuais necessários para a amostra e instala os certificados necessários com permissões apropriadas.  
  
    > [!NOTE]
    >  O arquivo em lotes bat é projetado para ser executado de um Prompt de comando do SDK do Windows. Isso requer que a variável de ambiente MSSDK apontar para o diretório onde o SDK está instalado. Essa variável de ambiente é definida automaticamente em um Prompt de comando do SDK do Windows. Em [!INCLUDE[wv](../../../../includes/wv-md.md)], certifique-se de que o gerenciamento de compatibilidade do IIS 6.0 está instalado porque o conjunto de backup usa scripts de administrador do IIS. Execução do script de configuração em [!INCLUDE[wv](../../../../includes/wv-md.md)] requer privilégios de administrador.  
  
2.  Abra FederationSample.sln no Visual Studio e selecione **compilar solução** do **criar** menu. Isso cria os arquivos de projeto comum, o serviço livraria livraria STS, HomeRealm STS e implanta-os no IIS. Isso também cria o aplicativo de cliente livraria e coloca o BookStoreClient.exe executável na pasta FederationSample\BookStoreClient\bin\Debug.  
  
3.  Clique duas vezes em BookStoreClient.exe. A janela BookStoreClient é exibida.  
  
4.  Você pode procurar os livros disponíveis na livraria clicando **procurar manuais**.  
  
5.  Para adquirir um catálogo específico, selecione o catálogo na lista e clique em **comprar catálogo**. O aplicativo é iniciado e é autenticado usando a autenticação do Windows com o serviço de Token de segurança HomeRealm.  
  
     O exemplo é configurado para permitir que usuários Compre livros que custam r $15 ou menos. Tentando comprar livros que custam mais do que os resultados de r $15 no cliente que está recebendo uma mensagem de acesso negado do serviço de armazenamento do catálogo.  
  
    > [!NOTE]
    >  O exemplo não atualiza o limite de crédito do usuário após uma compra. Repetidamente, você pode comprar manuais no limite de crédito (fixo) do usuário.  
  
#### <a name="to-clean-up"></a>Para limpar  
  
1.  Execute Cleanup.bat. Isso exclui os diretórios virtuais que foram criados durante o conjunto de backup e também remove os certificados instalados durante a instalação.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\Federation`  
  
## <a name="see-also"></a>Consulte também
