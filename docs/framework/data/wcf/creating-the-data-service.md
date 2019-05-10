---
title: Criar um serviço de dados do WCF no Visual Studio
ms.date: 08/24/2018
dev_langs:
- csharp
- vb
ms.assetid: 34d1d971-5e18-4c22-9bf6-d3612e27ea59
ms.openlocfilehash: d23df38d479cb8f29f3e49225e96552ccdb84645
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64641146"
---
# <a name="create-the-data-service"></a>Criar o serviço de dados

Neste tópico, você cria um serviço de dados de exemplo que usa o WCF Data Services para expor um [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] feed com base no banco de dados de exemplo Northwind. A tarefa envolve as seguintes etapas básicas:

1. Crie um aplicativo Web ASP.NET.

2. Defina o modelo de dados usando as ferramentas do modelo de dados de entidade.

3. Adicionar o serviço de dados para o aplicativo Web.

4. Habilitar o acesso ao serviço de dados.

## <a name="create-the-aspnet-web-app"></a>Criar o aplicativo web ASP.NET

1. No Visual Studio, sobre o **arquivo** menu, selecione **New** > **projeto**.

1. No **novo projeto** caixa de diálogo, em Visual Basic ou Visual c#, selecione a **Web** categoria e, em seguida, selecione **aplicativo Web ASP.NET**.

1. Insira `NorthwindService` como o nome do projeto e, em seguida, selecione **Okey**.

1. No **novo aplicativo Web ASP.NET** caixa de diálogo, selecione **vazia** e, em seguida, selecione **Okey**.

1. (Opcional) Especifique um número de porta específica para seu aplicativo Web. Observação: o número da porta `12345` é usado nesta série de tópicos do guia de início rápido.

    1. Na **Gerenciador de soluções**, clique com botão direito no projeto ASP.NET que você acabou de criar e, em seguida, escolha **propriedades**.

    2. Selecione o **Web** guia e defina o valor da **porta específica** caixa de texto para `12345`.

## <a name="define-the-data-model"></a>Definir o modelo de dados

1. Na **Gerenciador de soluções**, clique no nome do projeto ASP.NET e, em seguida, clique em **Add** > **Novo Item**.

2. No **Adicionar Novo Item** caixa de diálogo, selecione o **dados** categoria e, em seguida, selecione **modelo de dados de entidade ADO.NET**.

3. Para o nome do modelo de dados, digite `Northwind.edmx`.

4. No **Assistente de modelo de dados de entidade**, selecione **EF Designer do banco de dados**e, em seguida, clique em **próxima**.

5. Conectar-se o modelo de dados no banco de dados de uma das seguintes etapas e, em seguida, clique em **próxima**:

    - Se você não tiver uma conexão de banco de dados já configurada, clique em **nova Conexão** e criar uma nova conexão. Para obter mais informações, confira [Como: Criar conexões com bancos de dados do SQL Server](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/s4yys16a(v=vs.90)). Esta instância do SQL Server deve ter o banco de dados de exemplo Northwind anexado.

         \- ou -

    - Se você tiver uma conexão de banco de dados já configurada para se conectar ao banco de dados Northwind, selecione a conexão da lista de conexões.

6. Na página final do assistente, selecione as caixas de seleção para todas as tabelas no banco de dados e desmarque as caixas de seleção para exibições e procedimentos armazenados.

7. Clique em **concluir** para fechar o assistente.

## <a name="create-the-wcf-data-service"></a>Criar o serviço de dados do WCF

1. Na **Gerenciador de soluções**, clique com botão direito no projeto do ASP.NET e, em seguida, escolha **Add** > **Novo Item**.

2. No **Adicionar Novo Item** caixa de diálogo, selecione o **WCF Data Service** modelo de item dos **Web** categoria.

   ![Modelo de item do WCF Data Service no Visual Studio 2015](media/wcf-data-service-item-template.png)

   > [!NOTE]
   > O **WCF Data Service** modelo estará disponível no Visual Studio 2015, mas não no Visual Studio 2017.

3. Para o nome do serviço, digite `Northwind`.

     O Visual Studio cria a marcação XML e os arquivos de código do novo serviço. Por padrão, a janela do editor de códigos é aberta. Na **Gerenciador de soluções**, o serviço tem o nome Northwind com a extensão *. svc.cs* ou *. svc*.

4. No código do serviço de dados, substitua o comentário `/* TODO: put your data source class name here */` na definição da classe que define o serviço de dados pelo tipo que é o contêiner de entidade do modelo de dados, que, neste caso, é `NorthwindEntities`. A definição da classe deve ter a seguinte aparência:

     [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#servicedefinition)]
     [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#servicedefinition)]

## <a name="enable-access-to-data-service-resources"></a>Habilitar o acesso aos recursos do serviço de dados

1. No código para o serviço de dados, substitua o código de espaço reservado na função `InitializeService` pelo seguinte:

     [!code-csharp[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#allreadconfig)]
     [!code-vb[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#allreadconfig)]

     Isso permite que clientes autorizados tenham acesso de leitura e gravação aos recursos para os conjuntos de entidades especificados.

    > [!NOTE]
    > Qualquer cliente que pode acessar o aplicativo ASP.NET também pode acessar os recursos expostos pelo serviço de dados. Em um serviço de dados de produção, para impedir o acesso não autorizado a recursos, você também deverá proteger o próprio aplicativo. Para obter mais informações, consulte [protegendo o WCF Data Services](../../../../docs/framework/data/wcf/securing-wcf-data-services.md).

## <a name="next-steps"></a>Próximas etapas

Você criou com êxito um novo serviço de dados que expõe um feed de OData com base no banco de dados de exemplo Northwind, e você tiver habilitado o acesso a feed para clientes que têm permissões no aplicativo Web do ASP.NET. Em seguida, inicie o serviço de dados do Visual Studio e acessar o feed enviando solicitações HTTP GET por meio de um navegador da Web OData:

> [!div class="nextstepaction"]
> [Acessar o serviço de um navegador da web](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)

## <a name="see-also"></a>Consulte também

- [Ferramentas de modelo de dados de entidade ADO.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))