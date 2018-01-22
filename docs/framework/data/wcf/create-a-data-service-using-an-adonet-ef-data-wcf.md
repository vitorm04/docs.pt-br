---
title: "Como criar um serviço de dados usando uma fonte de dados do ADO.NET Entity Framework (WCF Data Services)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF Data Services, providers
- WCF Data Services, Entity Framework
ms.assetid: 6d11fec8-0108-42f5-8719-2a7866d04428
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e90b11800685707460171e5e2d250ef757979c44
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-create-a-data-service-using-an-adonet-entity-framework-data-source-wcf-data-services"></a>Como criar um serviço de dados usando uma fonte de dados do ADO.NET Entity Framework (WCF Data Services)
O [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] expõe dados de entidade como um serviço de dados. Esses dados de entidade são fornecidos pelo [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)][!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] quando a fonte de dados é um banco de dados relacional. Este tópico mostra como criar um modelo de dados com base no [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] em um aplicativo da Web [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] baseado em um banco de dados existente e usar esse modelo de dados para criar um novo serviço de dados.  
  
 O [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] também fornece uma ferramenta de linha de comando que pode gerar um modelo do [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] fora de um projeto do [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]. Para obter mais informações, consulte [como: Use EdmGen.exe para gerar o modelo e os arquivos de mapeamento](../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).  
  
### <a name="to-add-an-entity-framework-model-that-is-based-on-an-existing-database-to-an-existing-web-application"></a>Para adicionar um modelo do Entity Framework que está baseado em um banco de dados existente para um aplicativo da Web existente  
  
1.  Sobre o **projeto** menu, clique em **adicionar novo item**.  
  
2.  No **modelos** painel, clique no **dados** categoria e selecione **modelo de dados de entidade ADO.NET**.  
  
3.  Digite o nome do modelo e, em seguida, clique em **adicionar**.  
  
     A primeira página do assistente do [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] é exibida.  
  
4.  No **escolher o modelo de conteúdo** caixa de diálogo, selecione **gerar do banco de dados**. Clique em **Avançar**.  
  
5.  Clique o **nova Conexão** botão.  
  
6.  No **propriedades de Conexão** caixa de diálogo, digite o nome do servidor, selecione o método de autenticação, digite o nome do banco de dados e, em seguida, clique em **Okey**.  
  
     O **escolha sua Conexão de dados**caixa de diálogo é atualizada com as configurações de conexão de banco de dados.  
  
7.  Certifique-se de que o **salvar configurações de conexão de entidade no App. config como:** caixa de seleção é marcada. Clique em **Avançar**.  
  
8.  No **escolher seus objetos de banco de dados** objetos de selecionar tudo do banco de dados de caixa de diálogo que você pretende expor no serviço de dados.  
  
    > [!NOTE]
    >  Os objetos incluídos no modelo de dados não são expostos automaticamente pelo serviço de dados. Eles devem ser explicitamente expostos pelo próprio serviço. Para obter mais informações, consulte [Configurando o serviço de dados](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).  
  
9. Clique em **concluir** para concluir o assistente.  
  
     Isso cria um modelo de dados padrão com base no banco de dados específico. O [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] permite personalizar o modelo de dados. Para obter mais informações, consulte [Tarefas](http://msdn.microsoft.com/library/7166f1f1-4de8-4bd4-86b5-5e20a2ebaccb).  
  
### <a name="to-create-the-data-service-by-using-the-new-data-model"></a>Para criar o serviço de dados usando o novo modelo de dados  
  
1.  No [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)], abra o arquivo .edmx que representa o modelo de dados.  
  
2.  No **modelo navegador**, o modelo, clique **propriedades**e, em seguida, anote o nome do contêiner de entidade.  
  
3.  Em **Solution Explorer**, clique no nome do seu [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] do projeto e, em seguida, clique em **Adicionar Novo Item**.  
  
4.  No **Adicionar Novo Item** caixa de diálogo, selecione **WCF Data Service**.  
  
5.  Forneça um nome para o serviço e, em seguida, clique em **Okey**.  
  
     O [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] cria a marcação XML e arquivos de código para o novo serviço. Por padrão, a janela do editor de códigos é aberta.  
  
6.  No código para o serviço de dados, substitua o comentário `/* TODO: put your data source class name here */` na definição de classe que define o serviço de dados com o tipo que herda da classe <xref:System.Data.Objects.ObjectContext> e que é o contêiner de entidade do modelo de dados, que foi observado na etapa 2.  
  
7.  No código para o serviço de dados, permita que os clientes autorizados acessem os conjuntos de entidades que o serviço de dados expõe. Para obter mais informações, consulte [criando o serviço de dados](../../../../docs/framework/data/wcf/creating-the-data-service.md).  
  
8.  Para testar o serviço de dados Northwind.svc usando um navegador da Web, siga as instruções no tópico [acessando o serviço de um navegador da Web](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).  
  
## <a name="see-also"></a>Consulte também  
 [Defining WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md) (Definindo o WCF Data Services)  
 [Provedores de Serviços de Dados](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)  
 [Como criar um serviço de dados usando o provedor de reflexão](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md)  
 [Como criar um serviço de dados usando uma fonte de dados LINQ to SQL](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md)
