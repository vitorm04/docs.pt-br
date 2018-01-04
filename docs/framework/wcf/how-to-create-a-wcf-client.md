---
title: Como criar um cliente do Windows Communication Foundation
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- clients [WCF], running
- WCF clients [WCF], running
ms.assetid: a67884cc-1c4b-416b-8c96-5c954099f19f
caps.latest.revision: "64"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2591cad6354ec40f1fb6ead265c84a67adf3eec8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-windows-communication-foundation-client"></a>Como criar um cliente do Windows Communication Foundation
Esta é a quarta das seis tarefas necessárias para criar um aplicativo [!INCLUDE[indigo1](../../../includes/indigo1-md.md)]. Para obter uma visão geral de todos os seis das tarefas, consulte o [Tutorial de Introdução](../../../docs/framework/wcf/getting-started-tutorial.md) tópico.  
  
 Este tópico descreve como recuperar metadados de um serviço [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] e usá-los para criar um proxy [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] que possa acessar o serviço. Essa tarefa é concluída usando a funcionalidade Adicionar Referência de Serviço fornecida pelo Visual Studio. Essa ferramenta obtém os metadados do ponto de extremidade de MEX do serviço e gera um arquivo de código-fonte gerenciado para um proxy de cliente na linguagem escolhida (por padrão, C#). Além de criar o proxy de cliente, a ferramenta também cria ou atualiza o arquivo de configuração do cliente, o que permite que o aplicativo cliente se conecte ao serviço em um de seus pontos de extremidade.  
  
> [!NOTE]
>  Você também pode usar o [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ferramenta para gerar a classe proxy e a configuração em vez de usar Adicionar referência de serviço dentro do Visual Studio.  
  
> [!WARNING]
>  Ao chamar um serviço [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] de um projeto de biblioteca de classes no [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] você pode usar o recurso de Adicionar Referência de Serviço para gerar automaticamente um proxy e um arquivo de configuração associado.  O arquivo de configuração não será usado pelo projeto de biblioteca de classes. Você precisará adicionar as configurações no arquivo de configuração gerado para o arquivo app.config do executável que chamará a biblioteca de classes.  
  
 O aplicativo cliente usa a classe proxy gerada para se comunicar com o serviço. Este procedimento é descrito em [como: usar um cliente](../../../docs/framework/wcf/how-to-use-a-wcf-client.md).  
  
### <a name="to-create-a-windows-communication-foundation-client"></a>Para criar um cliente do Windows Communication Foundation  
  
1.  Criar um novo projeto de aplicativo de console clicando na solução Introdução, selecionar, **adicionar**, **novo projeto**. No **adicionar novo projeto** caixa de diálogo no lado esquerdo da caixa de diálogo Selecionar **Windows** em **c#** ou **VB**. Na seção central da caixa de diálogo Selecionar **aplicativo de Console**. Nomeie o projeto `GettingStartedClient`.  
  
2.  Definir a estrutura de destino do projeto GettingStartedClient .NET Framework 4.5, clique com o botão direito em **GettingStartedClient** no Gerenciador de soluções e selecionando **propriedades**. Na caixa suspensa rotulada **Framework de destino** selecione **.NET Framework 4.5**. Configuração da estrutura de destino para um projeto VB é um pouco diferente, a caixa de diálogo de propriedades de projeto GettingStartedClient, clique o **compilar** guia no lado esquerdo da tela e, em seguida, clique no **avançado Opções de compilação** botão no canto inferior esquerdo da caixa de diálogo. Em seguida, selecione **.NET Framework 4.5** na caixa suspensa rotulada **Framework de destino**.  
  
     Definir a estrutura de destino fará com que o Visual Studio 2011 recarregar a solução, pressione **Okey** quando solicitado.  
  
3.  Adicione uma referência a System. ServiceModel para o projeto GettingStartedClient clicando com o **referência** pasta no projeto no Gerenciador de soluções e selecione GettingStartedClient **adicionar** Referência. No **adicionar referência** caixa de diálogo Selecionar **Framework** no lado esquerdo da caixa de diálogo. Na caixa de texto Pesquisar Assemblies, digite `System.ServiceModel`. Na seção central da caixa de diálogo Selecionar **System. ServiceModel**, clique no **adicionar** botão e, em seguida, clique no **fechar** botão. Salve a solução clicando o **Salvar tudo** botão abaixo do menu principal.  
  
4.  Em seguida, você adicionará uma referência de serviço para Calculator Service. Para poder fazer isso, você deve iniciar o aplicativo de controle GettingStartedHost. Quando o host estiver em execução, você pode clique com botão direito na pasta de referências no projeto GettingStartedClient no Gerenciador de soluções e selecione Adicionar referência de serviço e digite a URL a seguir na caixa de endereço da caixa de diálogo Adicionar referência de serviço: HYPERLINK "http:/ / localhost:8000/ServiceModelSamples/serviço "ServiceModelSamples/http://localhost:8000/serviço e clique no **vá** botão. O CalculatorService deve ser exibido na caixa de listagem Serviços, clique duas vezes em CalculatorService e ele será expandido e mostrará os contratos de serviço implementados pelo serviço. Deixe o namespace padrão como está e clique no **Okey** botão.  
  
     Quando você adiciona uma referência a um serviço usando o Visual Studio, um novo item aparece no Gerenciador de Soluções sob a pasta Referências de Serviço no projeto GettingStartedClient.  Se você usar o [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ferramenta serão gerados um arquivo de código fonte e o arquivo App. config.  
  
     Você também pode usar a ferramenta de linha de comando [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) com as opções apropriadas para criar o código de cliente. O exemplo a seguir produz um arquivo de código e um arquivo de configuração para o serviço. O primeiro exemplo mostra como gerar o proxy no VB e o segundo mostra como gerar o proxy no C#:  
  
    ```  
    svcutil.exe /language:vb /out:generatedProxy.vb /config:app.config http://localhost:8000/ServiceModelSamples/service  
    ```  
  
    ```csharp  
    svcutil.exe /language:cs /out:generatedProxy.cs /config:app.config http://localhost:8000/ServiceModelSamples/service  
    ```  
  
 Agora você criou o proxy que o aplicativo cliente usará para chamar o serviço de calculadora. Vá para o próximo tópico na série: [como: configurar um cliente](../../../docs/framework/wcf/how-to-configure-a-basic-wcf-client.md)  
  
## <a name="see-also"></a>Consulte também  
 [Ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
 [Introdução](../../../docs/framework/wcf/samples/getting-started-sample.md)  
 [Auto-hospedagem](../../../docs/framework/wcf/samples/self-host.md)  
 [Como publicar metadados para um serviço usando um arquivo de configuração](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 [Como usar o Svcutil.exe para baixar documentos de metadados](../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-download-metadata-documents.md)
