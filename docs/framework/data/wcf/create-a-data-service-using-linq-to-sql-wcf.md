---
title: 'Como: Criar um serviço de dados usando um LINQ para a fonte de dados SQL (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, LINQ to SQL
- WCF Data Services, providers
ms.assetid: 3b01c2fd-8c6e-4bf5-b38f-9e61bdc3c328
ms.openlocfilehash: 7447a9f2ab0b2a9cca396ee947a0eb5fe2cc8715
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54608567"
---
# <a name="how-to-create-a-data-service-using-a-linq-to-sql-data-source-wcf-data-services"></a>Como: Criar um serviço de dados usando um LINQ para a fonte de dados SQL (WCF Data Services)

WCF Data Services expõe dados de entidade como um serviço de dados. O provedor de reflexão permite que você defina um modelo de dados com base em qualquer classe que expõe membros que retornam um <xref:System.Linq.IQueryable%601> implementação. Para poder fazer atualizações nos dados na fonte de dados, essas classes também devem implementar o <xref:System.Data.Services.IUpdatable> interface. Para obter mais informações, consulte [provedores de serviços de dados](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md). Este tópico mostra como criar LINQ to SQL classes que acessam o banco de dados de exemplo Northwind usando o provedor de reflexão, bem como para criar o serviço de dados com base nessas classes de dados.

## <a name="to-add-linq-to-sql-classes-to-a-project"></a>Para adicionar LINQ to SQL classes a um projeto

1. De dentro de um aplicativo Visual Basic ou c#, sobre o **projeto** menu, clique em **Add** > **Novo Item**.

2. Clique o **Classes LINQ to SQL** modelo.

3. Altere o nome para **dbml**.

4. Clique em **Adicionar**.

     O arquivo dbml é adicionado ao projeto e abre o Object Relational Designer (O/R Designer).

5. Na **Server**/**Database Explorer**, em Northwind, expanda **tabelas** e arraste o `Customers` tabela em Object Relational Designer (O/R Designer).

     Um `Customer` classe de entidade é criada e aparece na superfície de design.

6. Repita a etapa 6 para o `Orders`, `Order_Details`, e `Products` tabelas.

7. O novo arquivo. dbml que representa o LINQ para classes SQL e clique com o botão direito **Exibir código**.

     Isso cria uma página code-behind novo chamada Northwind.cs que contém uma definição de classe parcial para a classe que herda de <xref:System.Data.Linq.DataContext> classe, que nesse caso é `NorthwindDataContext`.

8. Substitua o conteúdo do arquivo de código Northwind.cs com o código a seguir. Esse código implementa o provedor de reflexão, estendendo o <xref:System.Data.Linq.DataContext> e classes de dados geradas pelo LINQ to SQL:

     [!code-csharp[Astoria Linq Provider#Linq2SqlProvider](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria linq provider/cs/northwind.cs#linq2sqlprovider)]
     [!code-vb[Astoria Linq Provider#Linq2SqlProvider](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria linq provider/vb/northwind.vb#linq2sqlprovider)]

### <a name="to-create-a-data-service-by-using-a-linq-to-sql-based-data-model"></a>Para criar um serviço de dados usando um LINQ ao modelo de dados baseado em SQL

1. Na **Gerenciador de soluções**, clique com botão direito no nome do seu projeto ASP.NET e, em seguida, clique em **Add** > **Novo Item**.

2. No **Adicionar Novo Item** caixa de diálogo, selecione o **WCF Data Service** modelo a partir o **Web** categoria.

   ![Modelo de item do WCF Data Service no Visual Studio 2015](media/wcf-data-service-item-template.png)

   > [!NOTE]
   > O **WCF Data Service** modelo estará disponível no Visual Studio 2015, mas não no Visual Studio 2017.

3. Forneça um nome para o serviço e, em seguida, clique em **Okey**.

     O Visual Studio cria a marcação XML e os arquivos de código do novo serviço. Por padrão, a janela do editor de códigos é aberta.

4. No código do serviço de dados, substitua o comentário `/* TODO: put your data source class name here */` na definição da classe que define o serviço de dados pelo tipo que é o contêiner de entidade do modelo de dados, que, neste caso, é `NorthwindDataContext`.

5. No código para o serviço de dados, substitua o código de espaço reservado na função `InitializeService` pelo seguinte:

     [!code-csharp[Astoria Linq Provider#EnableAccess](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria linq provider/cs/northwind.svc.cs#enableaccess)]
     [!code-vb[Astoria Linq Provider#EnableAccess](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria linq provider/vb/northwind.svc.vb#enableaccess)]

     Isso permite que os clientes autorizados acessem recursos para os três conjuntos de entidade especificada.

6. Para testar o serviço de dados SVC usando um navegador da Web, siga as instruções no tópico [acessar o serviço de um navegador da Web](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).

## <a name="see-also"></a>Consulte também

- [Como: Criar um serviço de dados usando uma fonte de dados do ADO.NET Entity Framework](../../../../docs/framework/data/wcf/create-a-data-service-using-an-adonet-ef-data-wcf.md)
- [Como: Criar um serviço de dados usando o provedor de reflexão](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md)
- [Provedores de Serviços de Dados](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)