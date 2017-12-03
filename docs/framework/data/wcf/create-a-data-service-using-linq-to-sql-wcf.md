---
title: "Como: criar um serviço de dados usando um LINQ para a fonte de dados SQL (WCF Data Services)"
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
helpviewer_keywords:
- WCF Data Services, LINQ to SQL
- WCF Data Services, providers
ms.assetid: 3b01c2fd-8c6e-4bf5-b38f-9e61bdc3c328
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 52529689242342afa8920a7b01b532a24337f562
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-create-a-data-service-using-a-linq-to-sql-data-source-wcf-data-services"></a>Como: criar um serviço de dados usando um LINQ para a fonte de dados SQL (WCF Data Services)
O [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] expõe dados de entidade como um serviço de dados. O provedor de reflexão permite definir um modelo de dados com base em qualquer classe que expõe membros que retornam um <xref:System.Linq.IQueryable%601> implementação. Para poder fazer atualizações em dados na fonte de dados, essas classes também devem implementar o <xref:System.Data.Services.IUpdatable> interface. Para obter mais informações, consulte [provedores de serviços de dados](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md). Este tópico mostra como criar LINQ para classes do SQL que acessa o banco de dados de exemplo Northwind usando o provedor de reflexão, bem como para criar o serviço de dados com base nessas classes de dados.  
  
### <a name="to-add-linq-to-sql-classes-to-a-project"></a>Para adicionar o LINQ para classes do SQL para um projeto  
  
1.  De dentro de um aplicativo Visual Basic ou c#, sobre o **projeto** menu, clique em **Adicionar Novo Item**.  
  
2.  Clique o **Classes LINQ to SQL** modelo.  
  
3.  Altere o nome para **dbml**.  
  
4.  Clique em **Adicionar**.  
  
     O arquivo dbml é adicionado ao projeto e abre o Object Relational Designer (O/R Designer).  
  
5.  Em **servidor**/**Pesquisador de objetos de banco de dados**, em Northwind, expanda **tabelas** e arraste o `Customers` tabela sobre o Object Relational Designer (O/R Designer).  
  
     Um `Customer` classe da entidade é criada e aparece na superfície de design.  
  
6.  Repita a etapa 6 para o `Orders`, `Order_Details`, e `Products` tabelas.  
  
7.  Clique no novo arquivo dbml que representa o LINQ para classes do SQL e clique em **Exibir código**.  
  
     Isso cria uma nova página de código por trás chamada Northwind.cs que contém uma definição de classe parcial para a classe que herda do <xref:System.Data.Linq.DataContext> classe, que nesse caso é `NorthwindDataContext`.  
  
8.  Substitua o conteúdo do arquivo de código Northwind.cs com o código a seguir. Esse código implementa o provedor de reflexão, estendendo o <xref:System.Data.Linq.DataContext> e classes de dados gerados pelo LINQ to SQL:  
  
     [!code-csharp[Astoria Linq Provider#Linq2SqlProvider](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria linq provider/cs/northwind.cs#linq2sqlprovider)]
     [!code-vb[Astoria Linq Provider#Linq2SqlProvider](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria linq provider/vb/northwind.vb#linq2sqlprovider)]  
  
### <a name="to-create-a-data-service-by-using-a-linq-to-sql-based-data-model"></a>Para criar um serviço de dados usando um LINQ no modelo de dados baseado em SQL  
  
1.  Em **Solution Explorer**, clique no nome do seu projeto do ASP.NET e, em seguida, clique em **Adicionar Novo Item**.  
  
2.  No **Adicionar Novo Item** caixa de diálogo, selecione **WCF Data Service**.  
  
3.  Forneça um nome para o serviço e, em seguida, clique em **Okey**.  
  
     O Visual Studio cria a marcação XML e os arquivos de código do novo serviço. Por padrão, a janela do editor de códigos é aberta.  
  
4.  No código do serviço de dados, substitua o comentário `/* TODO: put your data source class name here */` na definição da classe que define o serviço de dados pelo tipo que é o contêiner de entidade do modelo de dados, que, neste caso, é `NorthwindDataContext`.  
  
5.  No código para o serviço de dados, substitua o código de espaço reservado na função `InitializeService` pelo seguinte:  
  
     [!code-csharp[Astoria Linq Provider#EnableAccess](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria linq provider/cs/northwind.svc.cs#enableaccess)]
     [!code-vb[Astoria Linq Provider#EnableAccess](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria linq provider/vb/northwind.svc.vb#enableaccess)]  
  
     Isso permite que clientes autorizados acessem recursos para os três conjuntos de entidade especificada.  
  
6.  Para testar o serviço de dados Northwind.svc usando um navegador da Web, siga as instruções no tópico [acessando o serviço de um navegador da Web](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).  
  
## <a name="see-also"></a>Consulte também  
 [Como: criar um serviço de dados usando uma fonte de dados do ADO.NET Entity Framework](../../../../docs/framework/data/wcf/create-a-data-service-using-an-adonet-ef-data-wcf.md)  
 [Como: criar um serviço de dados usando o provedor de reflexão](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md)  
 [Provedores de serviços de dados](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)
