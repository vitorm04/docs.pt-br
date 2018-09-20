---
title: Como acessar um serviço de um aplicativo de fluxo de trabalho
ms.date: 03/30/2017
ms.assetid: 925ef8ea-5550-4c9d-bb7b-209e20c280ad
ms.openlocfilehash: 5bc18b446d4bf818c874839a421793a997ddc543
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45513880"
---
# <a name="how-to-access-a-service-from-a-workflow-application"></a>Como acessar um serviço de um aplicativo de fluxo de trabalho
Este tópico descreve como chamar um serviço de fluxo de trabalho de um aplicativo de console do fluxo de trabalho. Ele depende da conclusão do [como: criar um serviço de fluxo de trabalho com atividades de mensagens](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md) tópico. Embora este tópico descreve como chamar um serviço de fluxo de trabalho de um aplicativo de fluxo de trabalho, os mesmos métodos podem ser usados para chamar qualquer serviço do Windows Communication Foundation (WCF) de um aplicativo de fluxo de trabalho.

### <a name="create-a-workflow-console-application-project"></a>Crie um projeto de aplicativo de Console do fluxo de trabalho

1.  Inicie o [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].

2.  Carregar o projeto MyWFService criado na [como: criar um serviço de fluxo de trabalho com atividades de mensagens](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md) tópico.

3.  Clique com botão direito do **MyWFService** solução na **Gerenciador de soluções** e selecione **Add**, **novo projeto**. Selecione **fluxo de trabalho** na **modelos instalados** e **aplicativo de Console do fluxo de trabalho** na lista de tipos de projeto. Nomeie o projeto MyWFClient e usar o local padrão, conforme mostrado na ilustração a seguir.

     ![Adicionar caixa de diálogo Novo projeto](../../../../docs/framework/wcf/feature-details/media/addnewprojectdlg.JPG "AddNewProjectDlg")

     Clique o **Okey** botão para ignorar a **diálogo Adicionar novo projeto**.

4.  Depois que o projeto é criado, o arquivo de Workflow1.xaml é aberto no designer. Clique o **caixa de ferramentas** tab para abrir a caixa de ferramentas se não estiver já aberto e clique no apontador para manter a janela da caixa de ferramentas aberta.

5.  Pressione **Ctrl**+**F5** para compilar e iniciar o serviço. Como antes, o ASP.NET Development Server é iniciado e o Internet Explorer exibe a página de Ajuda do WCF. Observe o URI para essa página, você deve usá-lo na próxima etapa.

     ![IE exibindo a página de Ajuda do WCF e o URI](../../../../docs/framework/wcf/feature-details/media/iewcfhelppagewuri.JPG "IEWCFHelpPageWURI")

6.  Clique com botão direito do **MyWFClient** project na **Gerenciador de soluções** e selecione **Add** > **referência de serviço**. Clique o **Discover** botão para pesquisar a solução atual para todos os serviços. Clique no triângulo ao lado de Service1.xamlx na lista de serviços. Clique no triângulo ao lado de Service1 para listar os contratos implementados pelo serviço Service1. Expanda o **Service1** nó na **Services** lista. A operação de eco é exibida na **operações** lista conforme mostrado na ilustração a seguir.

     ![Adicionar caixa de diálogo de referência de serviço](../../../../docs/framework/wcf/feature-details/media/addservicereference.JPG "Adicionarreferenciaservico")

     Mantenha o namespace padrão e clique em **Okey** para ignorar a **Add Service Reference** caixa de diálogo. A seguinte caixa de diálogo é exibida.

     ![A caixa de diálogo de notificação de referência do serviço de add](../../../../docs/framework/wcf/feature-details/media/asrdlg.JPG "ASRDlg")

     Clique em **Okey** para ignorar a caixa de diálogo. Em seguida, pressione CTRL + SHIFT + B para compilar a solução. Observe, na caixa de ferramentas foi adicionada uma nova seção chamada **MyWFClient.ServiceReference1.Activities**. Expanda esta seção e observe a atividade de eco que tenha sido adicionada, conforme mostrado na ilustração a seguir.

     ![Atividade na caixa de ferramentas de eco](../../../../docs/framework/wcf/feature-details/media/echoactivity.JPG "EchoActivity")

7.  Arraste e solte uma <!--zz <xref:System.ServiceModel.Activities.Sequence>--> `System.ServiceModel.Activities.Sequence` atividade na superfície do designer. Ele está sob o **fluxo de controle** seção da caixa de ferramentas.

8.  Com o <!--zz <xref:System.ServiceModel.Activities.Sequence>--> `System.ServiceModel.Activities.Sequence` atividade em foco, clique no **variáveis** vincular e adicione uma variável de cadeia de caracteres denominada `inString`. Dê à variável um valor padrão de `"Hello, world"` , bem como uma variável de cadeia de caracteres denominada `outString` conforme mostrado no diagrama a seguir.

     ![Adicionando uma variável](../../../../docs/framework/wcf/feature-details/media/instringvar.JPG "inStringVar")

9. Arraste e solte uma **Echo** atividade para o <!--zz <xref:System.ServiceModel.Activities.Sequence>--> `System.ServiceModel.Activities.Sequence`. Na janela Propriedades, associar a `inMsg` argumento para o `inString` variável e o `outMsg` argumento para o `outString` variável, conforme mostrado na ilustração a seguir. Isso transmite o valor da `inString` variável para a operação e, em seguida, usa o valor de retorno e o coloca no `outString` variável.

     ![Associando os argumentos a variáveis](../../../../docs/framework/wcf/feature-details/media/argumentbind.JPG "ArgumentBind")

10. Arraste e solte uma **WriteLine** abaixo da atividade de **eco** atividade para exibir a cadeia de caracteres retornada pela chamada de serviço. O **WriteLine** atividade está localizada na **primitivos** nó na caixa de ferramentas. Associar o **texto** argumento do **WriteLine** atividade para o `outString` variável digitando `outString` na caixa de texto no **WriteLine** atividade. O fluxo de trabalho agora deve ser semelhante a ilustração a seguir.

     ![O fluxo de trabalho de cliente completa](../../../../docs/framework/wcf/feature-details/media/completeclientwf.JPG "CompleteClientWF")

11. A solução MyWFService com o botão direito e selecione **definir projetos de inicialização...** . Selecione o **vários projetos de inicialização** botão de opção e selecione **inicie** para cada projeto na **ação** coluna, conforme mostrado na ilustração a seguir.

     ![Opções de projetos de inicialização](../../../../docs/framework/wcf/feature-details/media/startupprojects.JPG "StartupProjects")

12. Pressione Ctrl + F5 para iniciar o serviço e o cliente. O ASP.NET Development Server hospeda o serviço, o Internet Explorer exibe a página de Ajuda do WCF e o aplicativo de fluxo de trabalho do cliente é iniciado em uma janela do console e exibe a cadeia de caracteres retornada do serviço ("Hello, world").

## <a name="see-also"></a>Consulte também

- [Serviços de fluxo de trabalho](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [Como criar um serviço de fluxo de trabalho com atividades de mensagens](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md)
- [Consumir um serviço do WCF de um fluxo de trabalho em um projeto Web](https://go.microsoft.com/fwlink/?LinkId=207725)