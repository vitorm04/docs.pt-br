---
title: Como criar um cliente do Windows Communication Foundation
ms.date: 03/30/2017
helpviewer_keywords:
- clients [WCF], running
- WCF clients [WCF], running
ms.assetid: a67884cc-1c4b-416b-8c96-5c954099f19f
ms.openlocfilehash: e5655a6fdc06e69d801cb38b7ee7412450f0d34c
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/16/2018
ms.locfileid: "45674137"
---
# <a name="how-to-create-a-windows-communication-foundation-client"></a>Como criar um cliente do Windows Communication Foundation

Esta é a quarta das seis tarefas necessárias para criar um aplicativo do Windows Communication Foundation (WCF). Para obter uma visão geral de todas as seis tarefas, confira o tópico [Tutorial de introdução](../../../docs/framework/wcf/getting-started-tutorial.md).

Este tópico descreve como recuperar metadados de um serviço WCF e usá-lo para criar um proxy do WCF que pode acessar o serviço. Essa tarefa é concluída usando a funcionalidade Adicionar Referência de Serviço fornecida pelo Visual Studio. Essa ferramenta obtém os metadados do ponto de extremidade de MEX do serviço e gera um arquivo de código-fonte gerenciado para um proxy de cliente na linguagem escolhida (por padrão, C#). Além de criar o proxy de cliente, a ferramenta também cria ou atualiza o arquivo de configuração do cliente, o que permite que o aplicativo cliente se conecte ao serviço em um de seus pontos de extremidade.

> [!NOTE]
> Você também pode usar o [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ferramenta para gerar a classe de proxy e a configuração em vez de usar Adicionar referência de serviço dentro do Visual Studio.

> [!WARNING]
> Ao chamar um serviço WCF de um projeto de biblioteca de classes no [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] você pode usar o recurso Adicionar referência de serviço para gerar automaticamente um proxy e um arquivo de configuração associado.  O arquivo de configuração não será usado pelo projeto de biblioteca de classes. Você precisará adicionar as configurações no arquivo de configuração gerado para o arquivo app.config do executável que chamará a biblioteca de classes.

 O aplicativo cliente usa a classe proxy gerada para se comunicar com o serviço. Esse procedimento é descrito na [como: usar um cliente](../../../docs/framework/wcf/how-to-use-a-wcf-client.md).

## <a name="to-create-a-windows-communication-foundation-client"></a>Para criar um cliente do Windows Communication Foundation

1.  Crie um novo projeto de aplicativo de console clicando-se na solução guia de Introdução, selecionar, **Add**, **novo projeto**. Na caixa de diálogo **Adicionar Novo Projeto** no lado esquerdo da caixa de diálogo, selecione **Windows** no **C#** ou no **VB**. Na seção central da caixa de diálogo, selecione **Aplicativo de Console**. Nomeie o projeto `GettingStartedClient`.

2.  Defina a estrutura de destino do projeto GettingStartedClient como .NET Framework 4.5 com o botão direito clicando em **GettingStartedClient** no Gerenciador de soluções e selecionando **propriedades**. Na caixa suspensa rotulada **Estrutura de Destino**, selecione **.NET Framework 4.5**. Definição da estrutura de destino de um projeto VB é um pouco diferente, na caixa de diálogo de propriedades de projeto GettingStartedClient, clique o **Compile** guia no lado esquerdo da tela e, em seguida, clique no **avançado Opções de compilação** botão no canto inferior esquerdo da caixa de diálogo. Em seguida, selecione **.NET Framework 4.5** na caixa suspensa rotulada **Estrutura de Destino**.

     Definindo a estrutura de destino fará com que o Visual Studio 2011 recarregue a solução, pressione **Okey** quando solicitado.

3.  Adicione uma referência a System. ServiceModel ao projeto de GettingStartedClient clicando com o **referência** pasta sob o projeto GettingStartedClient no Gerenciador de soluções e selecione **Add** Referência. Na caixa de diálogo **Adicionar Referência**, selecione **Estrutura** no lado esquerdo da caixa de diálogo. Na caixa de texto Pesquisar Assemblies, digite `System.ServiceModel`. Na seção central da caixa de diálogo, selecione **System.ServiceModel**, clique no botão **Adicionar** e no botão **Fechar**. Salve a solução clicando o **Salvar tudo** botão abaixo do menu principal.

4.  Em seguida, você adicionar uma referência de serviço para o serviço da Calculadora. Para poder fazer isso, você deve iniciar o aplicativo de controle GettingStartedHost. Quando o host estiver em execução, clique com botão direito do **referências** pasta sob o projeto GettingStartedClient no **Gerenciador de soluções** e selecione **Add**  >   **Referência de serviço**. Digite a seguinte URL na caixa de endereço do **Add Service Reference** caixa de diálogo: [ http://localhost:8000/GettingStartedClient/Service ](http://localhost:8000/GettingStartedClient/Service) e clique no **vá** botão. O CalculatorService deve ser exibido na caixa de lista de serviços. Clique duas vezes em CalculatorService e ele será expandido e mostrará os contratos de serviço implementados pelo serviço. Deixe o namespace padrão como está e clique o **Okey** botão.

     Quando você adiciona uma referência a um serviço usando o Visual Studio, um novo item aparece no Gerenciador de Soluções sob a pasta Referências de Serviço no projeto GettingStartedClient.  Se você usar o [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ferramenta serão gerados um arquivo de código-fonte e o arquivo App. config.

     Você também pode usar a ferramenta de linha de comando [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) com as opções apropriadas para criar o código do cliente. O exemplo a seguir produz um arquivo de código e um arquivo de configuração para o serviço. O primeiro exemplo mostra como gerar o proxy no VB e o segundo mostra como gerar o proxy no C#:

    ```
    svcutil.exe /language:vb /out:generatedProxy.vb /config:app.config http://localhost:8000/GettingStartedClient/service
    ```

    ```csharp
    svcutil.exe /language:cs /out:generatedProxy.cs /config:app.config http://localhost:8000/GettingStartedClient/service
    ```

 Agora você criou o proxy que o aplicativo cliente usará para chamar o serviço de calculadora. Vá para o próximo tópico da série: [como: configurar um cliente](../../../docs/framework/wcf/how-to-configure-a-basic-wcf-client.md)

## <a name="see-also"></a>Consulte também

- [Ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
- [Introdução](../../../docs/framework/wcf/samples/getting-started-sample.md)
- [Auto-hospedagem](../../../docs/framework/wcf/samples/self-host.md)
- [Como publicar metadados para um serviço usando um arquivo de configuração](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [Como usar o Svcutil.exe para baixar documentos de metadados](../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-download-metadata-documents.md)
