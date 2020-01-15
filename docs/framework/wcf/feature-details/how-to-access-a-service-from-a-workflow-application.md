---
title: Como acessar um serviço de um aplicativo de fluxo de trabalho
ms.date: 03/30/2017
ms.assetid: 925ef8ea-5550-4c9d-bb7b-209e20c280ad
ms.openlocfilehash: c524dc07106f039d9dc6c17ee6fb966321b6da24
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964525"
---
# <a name="how-to-access-a-service-from-a-workflow-application"></a>Como acessar um serviço de um aplicativo de fluxo de trabalho
Este tópico descreve como chamar um serviço de fluxo de trabalho de um aplicativo de console de fluxo de trabalho. Depende da conclusão do tópico [como: criar um serviço de fluxo de trabalho com atividades de mensagens](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md) . Embora este tópico descreva como chamar um serviço de fluxo de trabalho de um aplicativo de fluxo de trabalho, os mesmos métodos podem ser usados para chamar qualquer serviço de Windows Communication Foundation (WCF) de um aplicativo de fluxo de trabalho.

### <a name="create-a-workflow-console-application-project"></a>Criar um projeto de aplicativo do console de fluxo de trabalho

1. Inicie o Visual Studio 2012.

2. Carregue o projeto MyWFService criado no tópico [como: criar um serviço de fluxo de trabalho com atividades de mensagens](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md) .

3. Clique com o botão direito do mouse na solução **MyWFService** na **Gerenciador de soluções** e selecione **Adicionar**, **novo projeto**. Selecione **fluxo de trabalho** nos **modelos instalados** e no **aplicativo de console de fluxo de trabalho** na lista de tipos de projeto. Nomeie o projeto MyWFClient e use o local padrão, conforme mostrado na ilustração a seguir.

     ![Caixa de diálogo Adicionar Novo Projeto](./media/how-to-access-a-service-from-a-workflow-application/add-new-project-dialog.jpg)

     Clique no botão **OK** para ignorar a **caixa de diálogo Adicionar novo projeto**.

4. Depois que o projeto é criado, o arquivo workflow1. XAML é aberto no designer. Clique na guia **caixa de ferramentas** para abrir a caixa de ferramentas se ela ainda não estiver aberta e clique na anotação para manter a janela caixa de ferramentas aberta.

5. Pressione **Ctrl**+**F5** para compilar e iniciar o serviço. Como antes, o ASP.NET Development Server é iniciado e o Internet Explorer exibe a página de ajuda do WCF. Observe o URI desta página, pois você deve usá-la na próxima etapa.

     ![IE Exibindo página de ajuda do WCF e URI](./media/how-to-access-a-service-from-a-workflow-application/ie-wcf-help-page-uri.jpg)

6. Clique com o botão direito do mouse no projeto **MyWFClient** na **Gerenciador de soluções** e selecione **Adicionar** > **referência de serviço**. Clique no botão **descobrir** para pesquisar a solução atual em busca de qualquer serviço. Clique no triângulo ao lado de Service1. xamlx na lista de serviços. Clique no triângulo ao lado de Service1 para listar os contratos implementados pelo serviço Service1. Expanda o nó **Service1** na lista de **Serviços** . A operação de eco é exibida na lista de **operações** , conforme mostrado na ilustração a seguir.

     ![Caixa de diálogo Adicionar Referência de Serviço](./media/how-to-access-a-service-from-a-workflow-application/add-service-reference.jpg)

     Mantenha o namespace padrão e clique em **OK** para ignorar a caixa de diálogo **Adicionar referência de serviço** . A caixa de diálogo a seguir é exibida.

     ![Caixa de diálogo de notificação Adicionar Referência de Serviço](./media/how-to-access-a-service-from-a-workflow-application/add-service-reference-dialog.jpg)

     Clique em **OK** para ignorar a caixa de diálogo. Em seguida, pressione CTRL + SHIFT + B para compilar a solução. Observe na caixa de ferramentas uma nova seção foi adicionada chamada **MyWFClient. ServiceReference1. Activities**. Expanda esta seção e observe a atividade Echo que foi adicionada conforme mostrado na ilustração a seguir.

     ![Atividade de eco na caixa de ferramentas](./media/how-to-access-a-service-from-a-workflow-application/echo-activity-toolbox.jpg)

7. Arraste e solte uma atividade de <xref:System.Activities.Statements.Sequence> na superfície do designer. Está na seção **fluxo de controle** da caixa de ferramentas.

8. Com a <xref:System.Activities.Statements.Sequence> atividade em foco, clique no link **variáveis** e adicione uma variável de cadeia de caracteres chamada `inString`. Dê à variável um valor padrão de `"Hello, world"`, bem como uma variável de cadeia de caracteres chamada `outString`, conforme mostrado no diagrama a seguir.

     ![Adicionando uma variável instring](./media/how-to-access-a-service-from-a-workflow-application/add-instring-variable.jpg)

9. Arraste e solte uma atividade **Echo** na <xref:System.Activities.Statements.Sequence>. Na janela Propriedades, associe o argumento `inMsg` à variável `inString` e o argumento `outMsg` à variável `outString`, conforme mostrado na ilustração a seguir. Isso passa o valor da variável `inString` para a operação e, em seguida, pega o valor de retorno e a coloca na variável `outString`.

     ![Associando os argumentos a variáveis](./media/how-to-access-a-service-from-a-workflow-application/bind-arguments-variables.jpg)

10. Arraste e solte uma atividade **WriteLine** abaixo da atividade **Echo** para exibir a cadeia de caracteres retornada pela chamada de serviço. A atividade **WriteLine** está localizada no nó **primitivos** na caixa de ferramentas. Vincule o argumento **Text** da atividade **writeline** à variável `outString` digitando `outString` na caixa de texto na atividade **WriteLine** . O fluxo de trabalho agora deve ser semelhante à ilustração a seguir.

     ![O fluxo de trabalho de cliente completo](./media/how-to-access-a-service-from-a-workflow-application/complete-client-workflow.jpg)

11. Clique com o botão direito do mouse na solução MyWFService e selecione **definir projetos de inicialização...** . Selecione o botão de opção **vários projetos de inicialização** e selecione **Iniciar** para cada projeto na coluna **ação** , conforme mostrado na ilustração a seguir.

     ![Opções de projetos de inicialização](./media/how-to-access-a-service-from-a-workflow-application/startup-project-options.jpg)

12. Pressione CTRL + F5 para iniciar o serviço e o cliente. O ASP.NET Development Server hospeda o serviço, o Internet Explorer exibe a página de ajuda do WCF e o aplicativo de fluxo de trabalho do cliente é iniciado em uma janela do console e exibe a cadeia de caracteres retornada do serviço ("Olá, mundo").

## <a name="see-also"></a>Veja também

- [Serviços de fluxo de trabalho](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [Como criar um serviço de fluxo de trabalho com atividades de mensagens](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md)
- [Consumindo um serviço WCF de um fluxo de trabalho em um projeto Web](https://docs.microsoft.com/archive/blogs/endpoint/how-to-consume-a-wcf-service-from-a-wf4-workflow)
