---
title: 'Como: criar um serviço de dados usando uma fonte de dados LINQ to SQL (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, LINQ to SQL
- WCF Data Services, providers
ms.assetid: 3b01c2fd-8c6e-4bf5-b38f-9e61bdc3c328
ms.openlocfilehash: cde5b9903a1fd164ce106a6a408ac4bb79976642
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802284"
---
# <a name="how-to-create-a-data-service-using-a-linq-to-sql-data-source-wcf-data-services"></a>Como: criar um serviço de dados usando uma fonte de dados LINQ to SQL (WCF Data Services)

O WCF Data Services expõe os dados da entidade como um serviço de dados. O provedor de reflexão permite que você defina um modelo de dados baseado em qualquer classe que expõe Membros que retornam uma implementação de <xref:System.Linq.IQueryable%601>. Para poder fazer atualizações nos dados na fonte de dados, essas classes também devem implementar a interface <xref:System.Data.Services.IUpdatable>. Para obter mais informações, consulte [provedores de serviços de dados](data-services-providers-wcf-data-services.md). Este tópico mostra como criar LINQ to SQL classes que acessam o banco de dados de exemplo Northwind usando o provedor de reflexão, além de como criar o serviço de dado baseado nessas classes de dados.

## <a name="to-add-linq-to-sql-classes-to-a-project"></a>Para adicionar LINQ to SQL classes a um projeto

1. De dentro de um Visual Basic C# ou aplicativo, no menu **projeto** , clique em **Adicionar** > **novo item**.

2. Clique no modelo **classes de LINQ to SQL** .

3. Altere o nome para **Northwind. dbml**.

4. Clique em **Adicionar**.

     O arquivo Northwind. dbml é adicionado ao projeto e o Object Relational Designer (O/R Designer) é aberto.

5. Em **servidor**/**Gerenciador de banco de dados**, em Northwind, expanda **tabelas** e arraste a tabela `Customers` para a Object Relational Designer (o/R Designer).

     Uma classe de entidade `Customer` é criada e exibida na superfície de design.

6. Repita a etapa 6 para as tabelas `Orders`, `Order_Details`e `Products`.

7. Clique com o botão direito do mouse no novo arquivo. dbml que representa as classes de LINQ to SQL e clique em **Exibir código**.

     Isso cria uma nova página code-behind chamada Northwind.cs que contém uma definição de classe parcial para a classe que herda da classe <xref:System.Data.Linq.DataContext>, que nesse caso é `NorthwindDataContext`.

8. Substitua o conteúdo do arquivo de código Northwind.cs pelo código a seguir. Esse código implementa o provedor de reflexão estendendo o <xref:System.Data.Linq.DataContext> e as classes de dados geradas pelo LINQ to SQL:

     [!code-csharp[Astoria Linq Provider#Linq2SqlProvider](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_linq_provider/cs/northwind.cs#linq2sqlprovider)]
     [!code-vb[Astoria Linq Provider#Linq2SqlProvider](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_linq_provider/vb/northwind.vb#linq2sqlprovider)]

### <a name="to-create-a-data-service-by-using-a-linq-to-sql-based-data-model"></a>Para criar um serviço de dados usando um modelo de dados baseado em LINQ to SQL

1. Em **Gerenciador de soluções**, clique com o botão direito do mouse no nome do seu projeto ASP.net e clique em **Adicionar** > **novo item**.

2. Na caixa de diálogo **Adicionar novo item** , selecione o modelo do **WCF Data Service** na categoria **Web** .

   ![Modelo de item do WCF Data Service no Visual Studio 2015](./media/wcf-data-service-item-template.png)

   > [!NOTE]
   > O modelo do **WCF Data Service** está disponível no visual Studio 2015, mas não no visual Studio 2017 ou posterior.

3. Forneça um nome para o serviço e clique em **OK**.

     O Visual Studio cria a marcação XML e arquivos de código para o novo serviço. Por padrão, a janela do editor de códigos é aberta.

4. No código do serviço de dados, substitua o comentário `/* TODO: put your data source class name here */` na definição da classe que define o serviço de dados pelo tipo que é o contêiner de entidade do modelo de dados, que, neste caso, é `NorthwindDataContext`.

5. No código para o serviço de dados, substitua o código de espaço reservado na função `InitializeService` pelo seguinte:

     [!code-csharp[Astoria Linq Provider#EnableAccess](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_linq_provider/cs/northwind.svc.cs#enableaccess)]
     [!code-vb[Astoria Linq Provider#EnableAccess](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_linq_provider/vb/northwind.svc.vb#enableaccess)]

     Isso permite que clientes autorizados acessem recursos para os três conjuntos de entidades especificados.

6. Para testar o serviço de dados Northwind. svc usando um navegador da Web, siga as instruções no tópico [acessando o serviço em um navegador da Web](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).

## <a name="see-also"></a>Consulte também

- [Como criar um serviço de dados usando uma fonte de dados do ADO.NET Entity Framework](create-a-data-service-using-an-adonet-ef-data-wcf.md)
- [Como criar um serviço de dados usando o provedor de reflexão](create-a-data-service-using-rp-wcf-data-services.md)
- [Provedores de Serviços de Dados](data-services-providers-wcf-data-services.md)
