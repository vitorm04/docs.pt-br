---
title: Acessando o serviço de um navegador da Web (WCF Data Services Quickstart)
ms.date: 03/30/2017
ms.assetid: 5a6fa180-3094-4e6e-ba2b-8c80975d18d1
ms.openlocfilehash: b7fcead5eed2dd4c0c779d9a881563a39f88d094
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33363999"
---
# <a name="accessing-the-service-from-a-web-browser-wcf-data-services-quickstart"></a>Acessando o serviço de um navegador da Web (WCF Data Services Quickstart)
Nesta tarefa, você iniciará o [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] do Visual Studio e, opcionalmente, desabilite o feed de leitura no navegador da Web. Você será, em seguida, recuperar o documento de definição de serviço, bem como acessar os recursos de serviço de dados ao enviar solicitações HTTP GET por meio de um navegador da Web para os recursos expostos.  
  
> [!NOTE]
>  Por padrão, o Visual Studio automaticamente atribui um número de porta para o `localhost` URI em seu computador. Essa tarefa usa o número da porta `12345` nos exemplos do URI. Para obter mais informações sobre como definir um número de porta específico em seu projeto do Visual Studio, consulte [criando o serviço de dados](../../../../docs/framework/data/wcf/creating-the-data-service.md).  
  
### <a name="to-request-the-default-service-document-by-using-internet-explorer"></a>Para solicitar o documento padrão de serviço usando o Internet Explorer  
  
1.  No Internet Explorer, do **ferramentas** menu, selecione **opções da Internet**, clique no **conteúdo** , clique em **configurações**e desmarque  **Ativar visualização de feed**.  
  
     Isso garantirá que a leitura de feeds estará desabilitada. Se você não desabilitar essa funcionalidade, o navegador da Web tratará o documento codificado AtomPub retornado como um feed XML em vez de exibir os dados XML brutos.  
  
    > [!NOTE]
    >  Se seu navegador não puder exibir o feed como dados XML brutos, você ainda deverá ser capaz de exibir o feed como código-fonte para a página.  
  
2.  No Visual Studio, pressione a tecla F5 para iniciar a depuração do aplicativo.  
  
3.  Abra um navegador da Web no computador local. Na barra de endereços, digite a seguinte URL:  
  
    ```  
    http://localhost:12345/northwind.svc  
    ```  
  
     Isso retorna o documento padrão de serviço, que contém uma lista de conjuntos de entidades que são expostos por esse serviço de dados.  
  
### <a name="to-access-entity-set-resources-from-a-web-browser"></a>Para acessar os recursos do conjunto de entidades de um navegador da Web  
  
1.  Na barra de endereços do seu navegador da Web, digite a seguinte URL:  
  
    ```  
    http://localhost:12345/northwind.svc/Customers  
    ```  
  
     Isso retorna um conjunto de todos os clientes no banco de dados de exemplo Northwind.  
  
2.  Na barra de endereços do seu navegador da Web, digite a seguinte URL:  
  
    ```  
    http://localhost:12345/northwind.svc/Customers('ALFKI')  
    ```  
  
     Isso retorna uma instância de entidade para o cliente específico, `ALFKI`.  
  
3.  Na barra de endereços do seu navegador da Web, digite a seguinte URL:  
  
    ```  
    http://localhost:12345/northwind.svc/Customers('ALFKI')/Orders  
    ```  
  
     Isso percorre a relação entre clientes e pedidos para retornar um conjunto de todos os pedidos para o cliente específico `ALFKI`.  
  
4.  Na barra de endereços do seu navegador da Web, digite a seguinte URL:  
  
    ```  
    http://localhost:12345/northwind.svc/Customers('ALFKI')/Orders?$filter=OrderID eq 10643  
    ```  
  
     Isso filtra os pedidos que pertencem ao cliente específico `ALFKI` de modo que somente uma ordem específica seja retornada com base no valor `OrderID` fornecido.  
  
## <a name="next-steps"></a>Próximas etapas  
 Você acessou com êxito o [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] de um navegador da Web, com o navegador emitindo solicitações HTTP GET para recursos especificados. Um navegador da Web fornece uma maneira fácil para experimentar a sintaxe de endereçamento de solicitações e exibir os resultados. No entanto, um serviço de dados de produção geralmente não é acessado por esse método. Normalmente, os aplicativos interagem com o serviço de dados por meio do aplicativo código ou linguagens de script. Em seguida, você criará um aplicativo cliente que usa as bibliotecas de cliente para acessar os recursos do serviço de dados como se fossem objetos common language runtime (CLR):  
  
 [Criando o aplicativo cliente do .NET Framework](../../../../docs/framework/data/wcf/creating-the-dotnet-client-application-wcf-data-services-quickstart.md)  
  
## <a name="see-also"></a>Consulte também  
 [Acessando recursos do serviço de dados](../../../../docs/framework/data/wcf/accessing-data-service-resources-wcf-data-services.md)
