---
title: "Criando o serviço de dados"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 34d1d971-5e18-4c22-9bf6-d3612e27ea59
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7d890e4c2041ae4c70a79adfc0ab4141402fcd3f
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="creating-the-data-service"></a>Criando o serviço de dados
Nesta tarefa, você criará um serviço de dados de exemplo que usa [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] para expor um [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] feed com base no banco de dados de exemplo Northwind. A tarefa envolve as seguintes etapas básicas:  
  
1.  Criar um aplicativo Web [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)].  
  
2.  Definir o modelo de dados usando as ferramentas do [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)].  
  
3.  Adicionar o serviço de dados para o aplicativo Web.  
  
4.  Habilitar o acesso ao serviço de dados.  
  
> [!NOTE]
>  O aplicativo Web [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] que você cria quando conclui essa tarefa é executado no Servidor de Desenvolvimento do [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] fornecido pelo [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]. O Servidor de Desenvolvimento do [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] somente dá suporte a acesso do computador local. Para facilitar o teste e a solução de problemas do serviço de dados durante o desenvolvimento, execute o aplicativo que hospeda o serviço de dados usando o IIS (Serviços de Informações da Internet). Para obter mais informações, consulte [como: desenvolver um WCF Data Service em execução no IIS](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md).  
  
### <a name="to-create-the-aspnet-web-application"></a>Para criar o aplicativo Web do ASP.NET  
  
1.  Em [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)], no **arquivo** menu, selecione **novo**e, em seguida, selecione **projeto**.  
  
2.  No **novo projeto** caixa de diálogo, em um [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] ou [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] selecionar o **Web** modelo e selecione **aplicativo Web ASP.NET**.  
  
    > [!NOTE]
    >  Se você usar o [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] Web Developer, deverá criar um novo site em vez de um novo aplicativo Web.  
  
3.  Tipo `NorthwindService` como o nome do projeto.  
  
4.  Clique em **OK**.  
  
5.  (Opcional) Especifique um número de porta específica para seu aplicativo Web. Observação: o número da porta `12345` é usado no restante do início rápido.  
  
    1.  Em **Solution Explorer**, clique no nome do [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] projeto a que você acabou de criado e, em seguida, clique em **propriedades**.  
  
    2.  Selecione o **Web** guia e defina o valor da **porta específica** caixa de texto `12345`.  
  
### <a name="to-define-the-data-model"></a>Para definir o modelo de dados  
  
1.  Em **Solution Explorer**, clique no nome do [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] do projeto e, em seguida, clique em **Adicionar Novo Item.**  
  
2.  No **Adicionar Novo Item** caixa de diálogo, clique o **dados** modelo e selecione **modelo de dados de entidade ADO.NET**.  
  
3.  Para o nome do modelo de dados, digite `Northwind.edmx`.  
  
4.  No [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] assistente, selecione **gerar do banco de dados**e, em seguida, clique em **próximo**.  
  
5.  Conecte o modelo de dados para o banco de dados seguindo um destes procedimentos e, em seguida, clique em **próximo**:  
  
    -   Se você não tiver uma conexão de banco de dados já configurado, clique em **nova Conexão** e criar uma nova conexão. Para obter mais informações, consulte [como: criar conexões com bancos de dados do SQL Server](http://go.microsoft.com/fwlink/?LinkId=123631). Essa instância do [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] deve ter o banco de dados de exemplo Northwind anexado.  
  
         \- ou -  
  
    -   Se você tiver uma conexão de banco de dados já configurada para se conectar ao banco de dados Northwind, selecione a conexão da lista de conexões.  
  
6.  Na página final do assistente, selecione as caixas de seleção para todas as tabelas no banco de dados e desmarque as caixas de seleção para exibições e procedimentos armazenados.  
  
7.  Clique em **concluir** para fechar o assistente.  
  
    > [!NOTE]
    >  Esse modelo de dados gerado expõe as propriedades de chave estrangeira em tipos de entidade. Os modelos de dados criados usando o [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] 2008 não incluem essas propriedades de chave estrangeira. Devido a isso, você deverá atualizar as classes de serviço de dados do cliente de todos os aplicativos cliente que tenham sido criados para acessar o serviço de dados Northwind que foi criado usando o [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] 2008 antes de tentar acessar essa versão do serviço de dados Northwind.  
  
### <a name="to-create-the-data-service"></a>Para criar o serviço de dados  
  
1.  Em **Solution Explorer**, clique no nome do seu [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] do projeto e, em seguida, clique em **Adicionar Novo Item**.  
  
2.  No **Adicionar Novo Item** caixa de diálogo, selecione **WCF Data Service**.  
  
3.  Para o nome do serviço, digite `Northwind`.  
  
     O [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]Visual Studio cria a marcação XML e arquivos de código para o novo serviço. Por padrão, a janela do editor de códigos é aberta. Em **Solution Explorer**, o serviço terá o nome do Northwind, com a extensão. svc.cs ou. svc.vb.  
  
4.  No código do serviço de dados, substitua o comentário `/* TODO: put your data source class name here */` na definição da classe que define o serviço de dados pelo tipo que é o contêiner de entidade do modelo de dados, que, neste caso, é `NorthwindEntities`. A definição da classe deve ter a seguinte aparência:  
  
     [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart service/cs/northwind.svc.cs#servicedefinition)]
     [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart service/vb/northwind.svc.vb#servicedefinition)]  
  
### <a name="to-enable-access-to-data-service-resources"></a>Para restringir o acesso a recursos do serviço de dados  
  
1.  No código para o serviço de dados, substitua o código de espaço reservado na função `InitializeService` pelo seguinte:  
  
     [!code-csharp[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart service/cs/northwind.svc.cs#allreadconfig)]
     [!code-vb[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart service/vb/northwind.svc.vb#allreadconfig)]  
  
     Isso permite que clientes autorizados tenham acesso de leitura e gravação aos recursos para os conjuntos de entidades especificados.  
  
    > [!NOTE]
    >  Qualquer cliente que possa acessar o aplicativo [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] também poderá acessar os recursos expostos pelo serviço de dados. Em um serviço de dados de produção, para impedir o acesso não autorizado a recursos, você também deverá proteger o próprio aplicativo. Para obter mais informações, consulte [protegendo o WCF Data Services](../../../../docs/framework/data/wcf/securing-wcf-data-services.md).  
  
## <a name="next-steps"></a>Próximas etapas  
 Você criou com êxito um novo serviço de dados que expõe um [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed baseado no banco de dados de exemplo Northwind e você tiver habilitado o acesso ao feed para clientes que têm permissões no [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplicativo Web. Em seguida, você iniciará o serviço de dados de [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] e terão acesso a [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed enviando solicitações HTTP GET por meio de um navegador da Web:  
  
 [Acessando o serviço de um navegador da Web](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)  
  
## <a name="see-also"></a>Consulte também  
 [ADO.NET Entity Data Model Tools](http://msdn.microsoft.com/library/91076853-0881-421b-837a-f582f36be527) (Ferramentas de modelo de dados de entidade do ADO.NET)
