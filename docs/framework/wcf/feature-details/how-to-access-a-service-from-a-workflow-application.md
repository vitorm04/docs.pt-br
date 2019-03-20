---
title: 'Como: Acessar um serviço de um aplicativo de fluxo de trabalho'
ms.date: 03/30/2017
ms.assetid: 925ef8ea-5550-4c9d-bb7b-209e20c280ad
ms.openlocfilehash: 790f8f24ed8a6c3b7592fb8e78befc8ee5e2214d
ms.sourcegitcommit: 462dc41a13942e467984e48f4018d1f79ae67346
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58185422"
---
# <a name="how-to-access-a-service-from-a-workflow-application"></a>Como: Acessar um serviço de um aplicativo de fluxo de trabalho
Este tópico descreve como chamar um serviço de fluxo de trabalho de um aplicativo de console do fluxo de trabalho. Ele depende da conclusão do [como: Criar um serviço de fluxo de trabalho com atividades de mensagens](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md) tópico. Embora este tópico descreve como chamar um serviço de fluxo de trabalho de um aplicativo de fluxo de trabalho, os mesmos métodos podem ser usados para chamar qualquer serviço do Windows Communication Foundation (WCF) de um aplicativo de fluxo de trabalho.

### <a name="create-a-workflow-console-application-project"></a>Crie um projeto de aplicativo de Console do fluxo de trabalho

1.  Inicie o Visual Studio 2012.

2.  Carregar o projeto MyWFService criado na [como: Criar um serviço de fluxo de trabalho com atividades de mensagens](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md) tópico.

3.  Clique com botão direito do **MyWFService** solução na **Gerenciador de soluções** e selecione **Add**, **novo projeto**. Selecione **fluxo de trabalho** na **modelos instalados** e **aplicativo de Console do fluxo de trabalho** na lista de tipos de projeto. Nomeie o projeto MyWFClient e usar o local padrão, conforme mostrado na ilustração a seguir.

     ![Caixa de diálogo Adicionar Novo Projeto](./media/how-to-access-a-service-from-a-workflow-application/add-new-project-dialog.jpg)

     Clique o **Okey** botão para ignorar a **diálogo Adicionar novo projeto**.

4.  Depois que o projeto é criado, o arquivo de Workflow1.xaml é aberto no designer. Clique o **caixa de ferramentas** tab para abrir a caixa de ferramentas se não estiver já aberto e clique no apontador para manter a janela da caixa de ferramentas aberta.

5.  Pressione **Ctrl**+**F5** para compilar e iniciar o serviço. Como antes, o ASP.NET Development Server é iniciado e o Internet Explorer exibe a página de Ajuda do WCF. Observe o URI para essa página, você deve usá-lo na próxima etapa.

     ![IE exibindo a página de Ajuda do WCF e o URI de](./media/how-to-access-a-service-from-a-workflow-application/ie-wcf-help-page-uri.jpg)

6.  Clique com botão direito do **MyWFClient** project na **Gerenciador de soluções** e selecione **Add** > **referência de serviço**. Clique o **Discover** botão para pesquisar a solução atual para todos os serviços. Clique no triângulo ao lado de Service1.xamlx na lista de serviços. Clique no triângulo ao lado de Service1 para listar os contratos implementados pelo serviço Service1. Expanda o **Service1** nó na **Services** lista. A operação de eco é exibida na **operações** lista conforme mostrado na ilustração a seguir.

     ![Caixa de diálogo Adicionar Referência de Serviço](./media/how-to-access-a-service-from-a-workflow-application/add-service-reference.jpg)

     Mantenha o namespace padrão e clique em **Okey** para ignorar a **Add Service Reference** caixa de diálogo. A seguinte caixa de diálogo é exibida.

     ![Adicionar caixa de diálogo de notificação de referência de serviço](./media/how-to-access-a-service-from-a-workflow-application/add-service-reference-dialog.jpg)

     Clique em **Okey** para ignorar a caixa de diálogo. Em seguida, pressione CTRL + SHIFT + B para compilar a solução. Observe, na caixa de ferramentas foi adicionada uma nova seção chamada **MyWFClient.ServiceReference1.Activities**. Expanda esta seção e observe a atividade de eco que tenha sido adicionada, conforme mostrado na ilustração a seguir.

     ![Atividade de eco na caixa de ferramentas](./media/how-to-access-a-service-from-a-workflow-application/echo-activity-toolbox.jpg)

7.  Arraste e solte um <xref:System.Activities.Statements.Sequence> atividade na superfície do designer. Ele está sob o **fluxo de controle** seção da caixa de ferramentas.

8.  Com o <xref:System.Activities.Statements.Sequence> atividade em foco, clique em de **variáveis** vincular e adicione uma variável de cadeia de caracteres denominada `inString`. Dê à variável um valor padrão de `"Hello, world"` , bem como uma variável de cadeia de caracteres denominada `outString` conforme mostrado no diagrama a seguir.

     ![Adicionando uma variável inString](./media/how-to-access-a-service-from-a-workflow-application/add-instring-variable.jpg)

9. Arraste e solte uma **Echo** atividade para o <xref:System.Activities.Statements.Sequence>. Na janela Propriedades, associar a `inMsg` argumento para o `inString` variável e o `outMsg` argumento para o `outString` variável, conforme mostrado na ilustração a seguir. Isso transmite o valor da `inString` variável para a operação e, em seguida, usa o valor de retorno e o coloca no `outString` variável.

     ![Associando os argumentos a variáveis](./media/how-to-access-a-service-from-a-workflow-application/bind-arguments-variables.jpg)

10. Arraste e solte uma **WriteLine** abaixo da atividade de **eco** atividade para exibir a cadeia de caracteres retornada pela chamada de serviço. O **WriteLine** atividade está localizada na **primitivos** nó na caixa de ferramentas. Associar o **texto** argumento do **WriteLine** atividade para o `outString` variável digitando `outString` na caixa de texto no **WriteLine** atividade. O fluxo de trabalho agora deve ser semelhante a ilustração a seguir.

     ![O fluxo de trabalho de cliente concluído](./media/how-to-access-a-service-from-a-workflow-application/complete-client-workflow.jpg)

11. A solução MyWFService com o botão direito e selecione **definir projetos de inicialização...** . Selecione o **vários projetos de inicialização** botão de opção e selecione **inicie** para cada projeto na **ação** coluna, conforme mostrado na ilustração a seguir.

     ![Opções de projetos de inicialização](./media/how-to-access-a-service-from-a-workflow-application/startup-project-options.jpg)

12. Pressione Ctrl + F5 para iniciar o serviço e o cliente. O ASP.NET Development Server hospeda o serviço, o Internet Explorer exibe a página de Ajuda do WCF e o aplicativo de fluxo de trabalho do cliente é iniciado em uma janela do console e exibe a cadeia de caracteres retornada do serviço ("Hello, world").

## <a name="see-also"></a>Consulte também

- [Serviços de fluxo de trabalho](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [Como: Criar um serviço de fluxo de trabalho com atividades de mensagem](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md)
- [Consumir um serviço do WCF de um fluxo de trabalho em um projeto Web](https://go.microsoft.com/fwlink/?LinkId=207725)
