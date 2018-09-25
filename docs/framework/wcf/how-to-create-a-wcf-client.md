---
title: Como criar um cliente do Windows Communication Foundation
ms.date: 09/14/2018
helpviewer_keywords:
- clients [WCF], running
- WCF clients [WCF], running
ms.assetid: a67884cc-1c4b-416b-8c96-5c954099f19f
ms.openlocfilehash: 1eadb5008575a1a53d685db14d68e42d0dce1360
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47070670"
---
# <a name="how-to-create-a-windows-communication-foundation-client"></a>Como criar um cliente do Windows Communication Foundation

Esta é a quarta das seis tarefas necessárias para criar um aplicativo do Windows Communication Foundation (WCF). Para obter uma visão geral de todas as seis tarefas, confira o tópico [Tutorial de introdução](../../../docs/framework/wcf/getting-started-tutorial.md).

Este tópico descreve como recuperar metadados de um serviço WCF e usá-lo para criar um proxy do WCF que pode acessar o serviço. Essa tarefa é concluída usando o **adicionar referência de serviço** funcionalidade fornecida pelo Visual Studio. Essa ferramenta obtém os metadados do ponto de extremidade de MEX do serviço e gera um arquivo de código-fonte gerenciado para um proxy de cliente na linguagem escolhida (por padrão, C#). Além de criar o proxy de cliente, a ferramenta também cria ou atualiza o arquivo de configuração do cliente, o que permite que o aplicativo cliente se conecte ao serviço em um de seus pontos de extremidade.

> [!NOTE]
> Você também pode usar o [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ferramenta para gerar a classe de proxy e a configuração em vez de usar **Add Service Reference** no Visual Studio.

> [!NOTE]
> Ao chamar um serviço WCF de um projeto de biblioteca de classes no Visual Studio, você pode usar o **adicionar referência de serviço** recurso para gerar automaticamente um proxy e um arquivo de configuração associado. O arquivo de configuração não será usado pelo projeto de biblioteca de classes. Você precisará adicionar as configurações no arquivo de configuração gerado para o arquivo App. config para o executável que chama a biblioteca de classes.

O aplicativo cliente usa a classe proxy gerada para se comunicar com o serviço. Esse procedimento é descrito na [como: usar um cliente](../../../docs/framework/wcf/how-to-use-a-wcf-client.md).

## <a name="to-create-a-windows-communication-foundation-client"></a>Para criar um cliente do Windows Communication Foundation

1. Crie um novo projeto de aplicativo de console no Visual Studio. Clique com botão direito na solução no guia de Introdução **Gerenciador de soluções** e selecione **Add** > **novo projeto**. No **adicionar novo projeto** caixa de diálogo, no lado esquerdo, selecione o **área de trabalho do Windows** categoria sob **Visual c#** ou **Visual Basic**. Selecione o **aplicativo de Console (.NET Framework)** modelo e, em seguida, nomeie o projeto **GettingStartedClient**.

2. Adicione uma referência a System. ServiceModel ao projeto GettingStartedClient. Clique com botão direito no **referências** pasta sob o projeto GettingStartedClient no **Gerenciador de soluções**e, em seguida, selecione **Add Reference**. No **adicionar referência** caixa de diálogo, selecione **Framework** no lado esquerdo da caixa de diálogo, sob **Assemblies**. Localize e selecione **System. ServiceModel**e, em seguida, escolha **Okey**. Salve a solução selecionando **arquivo** > **Salvar tudo**.

3. Adicione uma referência de serviço para o serviço da Calculadora.

   1. Primeiro, inicie o aplicativo de console GettingStartedHost.

   2. Quando o host estiver em execução, clique com botão direito do **referências** pasta sob o projeto GettingStartedClient no **Gerenciador de soluções** e selecione **Add**  >   **Referência de serviço**.

   3. Insira a seguinte URL na caixa de endereço de **adicionar referência de serviço** caixa de diálogo: [http://localhost:8000/GettingStartedClient/Service](http://localhost:8000/GettingStartedClient/Service)

   4. Escolher **acesse**.

   O CalculatorService é exibido na **Services** caixa de listagem. Clique duas vezes em CalculatorService para expandi-la e mostrará os contratos de serviço implementados pelo serviço. Deixe o namespace padrão como-está e escolha **Okey**.

    Quando você adiciona uma referência a um serviço usando o Visual Studio, um novo item aparece no **Gerenciador de soluções** sob o **referências de serviço** pasta sob o projeto GettingStartedClient. Se você usar o [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ferramenta, um arquivo de código-fonte e o arquivo App. config são gerados.

    Você também pode usar a ferramenta de linha de comando [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) com as opções apropriadas para criar o código do cliente. O exemplo a seguir produz um arquivo de código e um arquivo de configuração para o serviço. O primeiro exemplo mostra como gerar o proxy no VB, e o segundo mostra como gerar o proxy em c#:

    ```shell
    svcutil.exe /language:vb /out:generatedProxy.vb /config:app.config http://localhost:8000/GettingStartedClient/service
    ```

    ```shell
    svcutil.exe /language:cs /out:generatedProxy.cs /config:app.config http://localhost:8000/GettingStartedClient/service
    ```

## <a name="next-steps"></a>Próximas etapas

Você criou o proxy de aplicativo cliente usará para chamar o serviço da Calculadora. Vá para o próximo tópico na série.

> [!div class="nextstepaction"]
> [Como configurar um cliente](../../../docs/framework/wcf/how-to-configure-a-basic-wcf-client.md)

## <a name="see-also"></a>Consulte também

- [Ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
- [Introdução](../../../docs/framework/wcf/samples/getting-started-sample.md)
- [Auto-hospedagem](../../../docs/framework/wcf/samples/self-host.md)
- [Como publicar metadados para um serviço usando um arquivo de configuração](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [Como usar o Svcutil.exe para baixar documentos de metadados](../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-download-metadata-documents.md)
