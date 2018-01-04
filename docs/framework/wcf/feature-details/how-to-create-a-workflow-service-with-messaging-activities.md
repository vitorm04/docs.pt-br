---
title: "Como criar um serviço de fluxo de trabalho com atividades de mensagens"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 53d094e2-6901-4aa1-88b8-024b27ccf78b
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 24456bbbefe305a3e9620e5396c8d300163e00d4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-workflow-service-with-messaging-activities"></a>Como criar um serviço de fluxo de trabalho com atividades de mensagens
Este tópico descreve como criar um serviço de fluxo de trabalho simples usando atividades de mensagem. Este tópico enfoca a mecânica de criação de um serviço de fluxo de trabalho em que o serviço que consiste exclusivamente atividades de mensagens. Em um serviço do mundo real, o fluxo de trabalho contém muitas outras atividades. O serviço implementa uma operação chamada Echo, que usa uma cadeia de caracteres e retorna a cadeia de caracteres para o chamador. Este tópico é o primeiro em uma série de tópicos de dois. O próximo tópico [como: acessar um fluxo de trabalho do aplicativo de serviço de um](../../../../docs/framework/wcf/feature-details/how-to-access-a-service-from-a-workflow-application.md) discute como criar um aplicativo de fluxo de trabalho que possa chamar o serviço criado neste tópico.  
  
### <a name="to-create-a-workflow-service-project"></a>Para criar um projeto de serviço de fluxo de trabalho  
  
1.  Inicie o [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
2.  Clique o **arquivo** menu, selecione **novo**e, em seguida, **projeto** para exibir o **caixa de diálogo Novo projeto**. Selecione **fluxo de trabalho** da lista de modelos instalados e **aplicativo de serviço de fluxo de trabalho WCF** da lista de tipos de projeto. Nomeie o projeto `MyWFService` e usar o local padrão, conforme mostrado na ilustração a seguir.  
  
     Clique o **Okey** botão para ignorar o **caixa de diálogo Novo projeto**.  
  
3.  Quando o projeto é criado, o arquivo Service1.xamlx é aberto no designer, conforme mostrado na ilustração a seguir.  
  
     ![O fluxo de trabalho padrão exibido no designer de](../../../../docs/framework/wcf/feature-details/media/defaultworkflowservice.JPG "DefaultWorkflowService")  
  
     Clique com botão direito a atividade de rotulado **serviço sequencial** e selecione **excluir**.  
  
### <a name="to-implement-the-workflow-service"></a>Para implementar o serviço de fluxo de trabalho  
  
1.  Selecione o **caixa de ferramentas** guia no lado esquerdo da tela para exibir a caixa de ferramentas e clique em anotações para manter a janela aberta. Expanda o **mensagens** seção da caixa de ferramentas para exibir as atividades de mensagens e os modelos de atividade de mensagens, conforme mostrado na ilustração a seguir.  
  
     ![A caixa de ferramentas com guia mensagens expandida](../../../../docs/framework/wcf/feature-details/media/wfdesignertoolbox.JPG "WFDesignerToolbox")  
  
2.  Arraste e solte um **ReceiveAndSendReply** modelo para o designer de fluxo de trabalho. Isso cria uma <!--zz <xref:System.ServiceModel.Activities.Sequence>--> `System.ServiceModel.Activities.Sequence` atividade com um **Receive** atividade seguido por um <xref:System.ServiceModel.Activities.SendReply> atividade conforme mostrado na ilustração a seguir.  
  
     ![Modelo ReceiveAndSendReply no designer](../../../../docs/framework/wcf/feature-details/media/receiveandsendreply.JPG "ReceiveAndSendReply")  
  
     Observe que o <xref:System.ServiceModel.Activities.SendReply> da atividade <xref:System.ServiceModel.Activities.SendReply.Request%2A> está definida como `Receive`, o nome do <xref:System.ServiceModel.Activities.Receive> atividade à qual o <xref:System.ServiceModel.Activities.SendReply> atividade está respondendo.  
  
3.  No <xref:System.ServiceModel.Activities.Receive> tipo de atividade `Echo` na caixa de texto rotulada **OperationName**. Define o nome da operação de serviço implementa.  
  
     ![Especifique o nome da operação](../../../../docs/framework/wcf/feature-details/media/defineoperation.JPG "DefineOperation")  
  
4.  Com o <xref:System.ServiceModel.Activities.Receive> atividade selecionada, abra a janela Propriedades, se não estiver aberto clicando o **exibição** menu e selecionando **janela propriedades**. No **janela propriedades** Role para baixo até ver **CanCreateInstance** e clique na caixa de seleção, conforme mostrado na ilustração a seguir. Essa configuração permite que o host de serviço de fluxo de trabalho criar uma nova instância do serviço (se necessário) quando uma mensagem é recebida.  
  
     ![Propriedade CanCreateInstance](../../../../docs/framework/wcf/feature-details/media/cancreateinstance.JPG "CanCreateInstance")  
  
5.  Selecione o <!--zz <xref:System.ServiceModel.Activities.Sequence>--> `System.ServiceModel.Activities.Sequence` atividade e clique no **variáveis** botão no canto inferior esquerdo do designer. Exibe o editor de variáveis. Clique o **criar variável** link para adicionar uma variável para armazenar a cadeia de caracteres enviada à operação. Nome da variável `msg` e defina seu **variável** digite a cadeia de caracteres, conforme mostrado na ilustração a seguir.  
  
     ![Adicionar uma variável](../../../../docs/framework/wcf/feature-details/media/addvariable.JPG "AddVariable")  
  
     Clique o **variáveis** novamente para fechar o editor de variáveis.  
  
6.  Clique o **definir.** link no **conteúdo** caixa de texto de <xref:System.ServiceModel.Activities.Receive> atividade para exibir o **definição de conteúdo** caixa de diálogo. Selecione o **parâmetros** botão de opção, clique no **adicionar um novo parâmetro** link, digite `inMsg` no **nome** caixa de texto, selecione **cadeia de caracteres**no **tipo** suspensa da caixa de lista e digite `msg` no **atribuir a** caixa de texto conforme mostrado na ilustração a seguir.  
  
     ![Adicionando parâmetros conteúdo](../../../../docs/framework/wcf/feature-details/media/parameterscontent.jpg "ParametersContent")  
  
     Especifica que a atividade de recebimento recebe o parâmetro de cadeia de caracteres e é de associação de dados para o `msg` variável. Clique em **Okey** para fechar o **definição de conteúdo** caixa de diálogo.  
  
7.  Clique o **definir...**  link no **conteúdo** caixa o <xref:System.ServiceModel.Activities.SendReply> atividade para exibir o **definição de conteúdo** caixa de diálogo. Selecione o **parâmetros** botão de opção, clique no **adicionar um novo parâmetro** link, digite `outMsg` no **nome** caixa de texto, selecione **cadeia de caracteres**no **tipo** caixa de listagem suspensa, e `msg` no **valor** caixa de texto conforme mostrado na ilustração a seguir.  
  
     ![Adicionando parâmetros conteúdo](../../../../docs/framework/wcf/feature-details/media/parameterscontent2.jpg "ParametersContent2")  
  
     Especifica que o <xref:System.ServiceModel.Activities.SendReply> atividade envia uma mensagem ou o tipo de contrato de mensagem e esses dados serão associados ao `msg` variável. Como esta é uma <xref:System.ServiceModel.Activities.SendReply> atividade, isso significa que os dados em `msg` é usado para popular a mensagem a atividade envia ao cliente. Clique em **Okey** para fechar o **definição de conteúdo** caixa de diálogo.  
  
8.  Salve e compile a solução clicando o **criar** menu e selecionando **compilar solução**.  
  
## <a name="configure-the-workflow-service-project"></a>Configurar o projeto de serviço de fluxo de trabalho  
 O serviço de fluxo de trabalho é concluído. Esta seção explica como configurar a solução de serviço de fluxo de trabalho para facilitar a hospedar e executar. Esta solução usa o ASP.NET Development Server para hospedar o serviço.  
  
#### <a name="to-set-project-start-up-options"></a>Para definir opções de inicialização do projeto  
  
1.  No **Solution Explorer**, clique com botão direito **MyWFService** e selecione **propriedades** para exibir o **propriedades do projeto** caixa de diálogo.  
  
2.  Selecione o **Web** guia e selecione **página específica** em **iniciar ação** e digite `Service1.xamlx` na caixa de texto, conforme mostrado na ilustração a seguir.  
  
     ![A caixa de diálogo de propriedades do projeto](../../../../docs/framework/wcf/feature-details/media/projectpropertiesdlg.JPG "ProjectPropertiesDlg")  
  
     Isso hospeda o serviço definido no Service1.xamlx no servidor de desenvolvimento ASP.NET.  
  
3.  Pressione Ctrl + F5 para iniciar o serviço. O ícone de servidor de desenvolvimento ASP.NET é exibido no lado inferior direito da área de trabalho, conforme mostrado na imagem a seguir.  
  
     ![O ícone do servidor ASP.NET Developer](../../../../docs/framework/wcf/feature-details/media/aspnetdevservericon.JPG "ASPNETDEVServerIcon")  
  
     Além disso, o Internet Explorer exibirá a página de Ajuda do serviço WCF para o serviço.  
  
     ![Página de Ajuda do WCF](../../../../docs/framework/wcf/feature-details/media/wcfhelppate.JPG "WCFHelpPate")  
  
4.  Continue para a [como: acessar um fluxo de trabalho do aplicativo de serviço de um](../../../../docs/framework/wcf/feature-details/how-to-access-a-service-from-a-workflow-application.md) tópico para criar um cliente de fluxo de trabalho que chama esse serviço.  
  
## <a name="see-also"></a>Consulte também  
 [Serviços de fluxo de trabalho](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [Visão geral dos serviços de fluxo de trabalho de hospedagem](../../../../docs/framework/wcf/feature-details/hosting-workflow-services-overview.md)  
 [Atividades de mensagens](../../../../docs/framework/wcf/feature-details/messaging-activities.md)
