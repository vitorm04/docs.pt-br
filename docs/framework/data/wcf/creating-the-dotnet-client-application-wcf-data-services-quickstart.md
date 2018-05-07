---
title: Criando o aplicativo cliente do .NET Framework (Início rápido do WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 41ade767-eeab-437d-9121-9797e8fb8045
ms.openlocfilehash: 09981a7aee2db24d8464bbc7412b82a57ec8115b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="creating-the-net-framework-client-application-wcf-data-services-quickstart"></a>Criando o aplicativo cliente do .NET Framework (Início rápido do WCF Data Services)
Esta é a tarefa final o [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] início rápido. Nesta tarefa, você irá adicionar um aplicativo de console para a solução, adicione uma referência para o [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] feed para este novo aplicativo de cliente e acesso a [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed do aplicativo cliente usando as classes de serviço de dados de cliente gerada e o cliente bibliotecas.  
  
> [!NOTE]
>  Um aplicativo cliente baseado no .NET framework não é necessário para acessar um feed de dados. O serviço de dados pode ser acessado por qualquer componente do aplicativo que consome um feed do [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]. Para obter mais informações, consulte [usando um serviço de dados em um aplicativo cliente](../../../../docs/framework/data/wcf/using-a-data-service-in-a-client-application-wcf-data-services.md).  
  
### <a name="to-create-the-client-application-by-using-visual-studio"></a>Para criar o aplicativo cliente usando Visual Studio  
  
1.  Em **Solution Explorer**, a solução, clique **adicionar**e, em seguida, clique em **novo projeto**.  
  
2.  Em **tipos de projeto**, clique em **Windows**e, em seguida, selecione **aplicativo WPF** no **modelos** painel.  
  
3.  Digite `NorthwindClient` para o nome do projeto e clique **Okey**.  
  
4.  Abra o arquivo MainWindow.xaml e substitua o XAML pelo seguinte código:  
  
     [!code-xaml[Astoria Quickstart Client#Window1Xaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart client/vb/window1.xaml#window1xaml)]  
  
### <a name="to-add-a-data-service-reference-to-the-project"></a>Para adicionar uma referência de serviço de dados ao projeto  
  
1.  O projeto NorthwindClient, clique **adicionar referência de serviço**e, em seguida, clique em **Discover**.  
  
     Isso exibe o serviço de dados Northwind que você criou na primeira tarefa.  
  
2.  No **Namespace** caixa de texto, digite `Northwind`e, em seguida, clique em **Okey**.  
  
     Isso adiciona um novo arquivo de código ao projeto, que contém classes de dados que são usadas para acessar e interagir com os recursos do serviço de dados como objetos. As classes de dados são criadas no namespace `NorthwindClient.Northwind`.  
  
### <a name="to-access-data-service-data-in-the-wpf-application"></a>Para acessar dados do serviço de dados no aplicativo WPF  
  
1.  Em **Solution Explorer** em **NorthwindClient**, clique com o botão direito e clique em **adicionar referência**.  
  
2.  Na caixa de diálogo Adicionar referência, clique o **.NET** guia, selecione o assembly de DLL e, em seguida, clique em **Okey**. Em **Solution Explorer** em **NorthwindClient**, abra a página de código para o arquivo MainWindow. XAML e adicione o seguinte `using` instrução (`Imports` no Visual Basic).  
  
     [!code-csharp[Astoria Quickstart Client#Using](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart client/cs/window1.xaml.cs#using)]
     [!code-vb[Astoria Quickstart Client#Using](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart client/vb/window1.xaml.vb#using)]  
  
3.  Insira o código a seguir que consulta esse serviço de dados e associa o resultado a uma classe <xref:System.Data.Services.Client.DataServiceCollection%601> na classe `MainWindow`:  
  
    > [!NOTE]
    >  Você deve substituir o nome de host `localhost:12345` pelo servidor e a porta que está hospedando sua instância do serviço de dados Northwind.  
  
     [!code-csharp[Astoria Quickstart Client#QueryCode](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart client/cs/window1.xaml.cs#querycode)]
     [!code-vb[Astoria Quickstart Client#QueryCode](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart client/vb/window1.xaml.vb#querycode)]  
  
4.  Insira o seguinte código que salvar as alterações na classe `MainWindow`:  
  
     [!code-csharp[Astoria Quickstart Client#SaveChanges](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart client/cs/window1.xaml.cs#savechanges)]
     [!code-vb[Astoria Quickstart Client#SaveChanges](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart client/vb/window1.xaml.vb#savechanges)]  
  
### <a name="to-build-and-run-the-northwindclient-application"></a>Para compilar e executar o aplicativo NorthwindClient  
  
1.  Em **Solution Explorer**, com o botão direito no projeto NorthwindClient e selecione **definir como projeto de inicialização**.  
  
2.  Pressione F5 para iniciar o aplicativo.  
  
     Isso compila a solução e inicia o aplicativo cliente. Os dados são solicitados do serviço e exibidos no console.  
  
3.  Editar um valor na **quantidade** coluna da grade de dados e, em seguida, clique **salvar**.  
  
     As alterações são salvas no serviço de dados.  
  
    > [!NOTE]
    >  Esta versão do aplicativo NorthwindClient não dá suporte a adição e exclusão de entidades.  
  
## <a name="next-steps"></a>Próximas etapas  
 Você criou com êxito o aplicativo cliente que acessa o feed do [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] Northwind de exemplo. Você também concluiu o início rápido do [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]. Para obter mais informações sobre como acessar uma [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] do feed de um [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] aplicativo, consulte [biblioteca de cliente do WCF Data Services](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md).  
  
## <a name="see-also"></a>Consulte também  
 [Introdução](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)  
 [Recursos](../../../../docs/framework/data/wcf/wcf-data-services-resources.md)
