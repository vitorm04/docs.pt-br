---
title: Como hospedar um serviço do WCF em um aplicativo gerenciado
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 5eb29db0-b6dc-4e77-8c68-0a62f79d743b
caps.latest.revision: 42
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5f2671dc381e0d3ef8f55ced01268de6205fcb7d
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-host-a-wcf-service-in-a-managed-application"></a>Como hospedar um serviço do WCF em um aplicativo gerenciado
Para hospedar um serviço dentro de um aplicativo gerenciado, o código inserido para o serviço dentro do código de aplicativo gerenciado, definir um ponto de extremidade para o serviço de imperativa no código, declarativamente por meio de configuração ou usando os pontos de extremidade padrão e, em seguida, criar um instância do <xref:System.ServiceModel.ServiceHost>.  
  
 Para iniciar o recebimento de mensagens, chame <xref:System.ServiceModel.ICommunicationObject.Open%2A> em <xref:System.ServiceModel.ServiceHost>. Isso cria e abre o ouvinte para o serviço. Hospedar um serviço dessa maneira é conhecida como "hospedagem interna" porque o aplicativo gerenciado está fazendo o trabalho de hospedagem em si. Para fechar o serviço, chame <xref:System.ServiceModel.Channels.CommunicationObject.Close%2A?displayProperty=nameWithType> em <xref:System.ServiceModel.ServiceHost>.  
  
 Um serviço também pode ser hospedado em um serviço gerenciado do Windows, no Internet Information Services (IIS) ou no serviço de ativação de processo para Windows (WAS). Para obter mais informações sobre opções de um serviço de hospedagem, consulte [serviços de hospedagem](../../../docs/framework/wcf/hosting-services.md).  
  
 Hospedar um serviço em um aplicativo gerenciado é a opção mais flexível porque ela exige a menor infra-estrutura para implantar. Para obter mais informações sobre hospedagem de serviços em aplicativos gerenciados, consulte [hospedando um aplicativo gerenciado](../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md).  
  
 O procedimento a seguir demonstra como implementar um serviço hospedado automaticamente em um aplicativo de console.  
  
### <a name="to-create-a-self-hosted-service"></a>Para criar um serviço auto-hospedado  
  
1.  Abra [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] e selecione **novo**, **projeto...**  do **arquivo** menu.  
  
2.  No **modelos instalados** lista, selecione **Visual C#**, **Windows** ou **Visual Basic**, **Windows**. Dependendo de seu [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] configurações, um ou ambos podem estar sob o **outras linguagens** nó no **modelos instalados** lista.  
  
3.  Selecione **aplicativo de Console** do **Windows** lista. Tipo `SelfHost` no **nome** caixa e clique em **Okey**.  
  
4.  Clique com botão direito **SelfHost** na **Solution Explorer** e selecione **adicionar referência...** . Selecione **System. ServiceModel** do **.NET** guia e clique em **Okey**.  
  
    > [!TIP]
    >  Se o **Solution Explorer** janela não estiver visível, selecione **Solution Explorer** do **exibição** menu.  
  
5.  Clique duas vezes em **Program.cs** ou **Module1. vb** na **Solution Explorer** para abri-lo na janela de código, se ainda não estiver aberto. Adicione as instruções a seguir na parte superior do arquivo.  
  
     [!code-csharp[CFX_SelfHost4#1](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#1)]
     [!code-vb[CFX_SelfHost4#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#1)]  
  
6.  Definir e implementar um contrato de serviço. Este exemplo define um `HelloWorldService` que retorna uma mensagem com base na entrada para o serviço.  
  
     [!code-csharp[CFX_SelfHost4#2](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#2)]
     [!code-vb[CFX_SelfHost4#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#2)]  
  
    > [!NOTE]
    >  Para obter mais informações sobre como definir e implementar uma interface de serviço, consulte [como: definir um contrato de serviço](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md) e [como: implementar um contrato de serviço](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md).  
  
7.  Na parte superior do `Main` método, crie uma instância do <xref:System.Uri> classe com o endereço base para o serviço.  
  
     [!code-csharp[CFX_SelfHost4#3](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#3)]
     [!code-vb[CFX_SelfHost4#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#3)]  
  
8.  Criar uma instância do <xref:System.ServiceModel.ServiceHost> classe, passando um <xref:System.Type> que representa o tipo de serviço e a base de identificador de recurso uniforme (URI) para resolver o <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Type%2CSystem.Uri%5B%5D%29>. Habilitar a publicação de metadados e, em seguida, chame o <xref:System.ServiceModel.ICommunicationObject.Open%2A> método o <xref:System.ServiceModel.ServiceHost> para inicializar o serviço e prepará-lo para receber mensagens.  
  
     [!code-csharp[CFX_SelfHost4#4](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#4)]
     [!code-vb[CFX_SelfHost4#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#4)]       
  
    > [!NOTE]
    >  Este exemplo usa pontos de extremidade padrão, e nenhum arquivo de configuração é necessário para este serviço. Se nenhum ponto de extremidade estiverem configurados, o tempo de execução cria um ponto de extremidade para cada endereço base para cada contrato de serviço implementado pelo serviço. Para obter mais informações sobre pontos de extremidade padrão, consulte [configuração simplificada](../../../docs/framework/wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
9. Pressione CTRL+SHIFT+B para criar a solução.  
  
### <a name="to-test-the-service"></a>Para testar o serviço  
  
1.  Pressione Ctrl + F5 para executar o serviço.  
  
2.  Abra **cliente de teste do WCF**.  
  
    > [!TIP]
    >  Para abrir **cliente de teste do WCF**, abra um [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] prompt de comando e execute **WcfTestClient.exe**.  
  
3.  Selecione **Adicionar serviço...**  do **arquivo** menu.  
  
4.  Tipo `http://localhost:8080/hello` para a caixa de endereço e clique em **Okey**.  
  
    > [!TIP]
    >  Verifique se o serviço está em execução ou a etapa atual falhar. Se você tiver alterado o endereço base no código, em seguida, use o endereço base modificado nesta etapa.  
  
5.  Clique duas vezes em **SayHello** sob o **meus projetos de serviço** nó. Digite seu nome no **valor** coluna o **solicitação** lista e clique em **Invoke**. Será exibida uma mensagem de resposta no **resposta** lista.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria um <xref:System.ServiceModel.ServiceHost> objeto para hospedar um serviço do tipo `HelloWorldService`e, em seguida, chama o <xref:System.ServiceModel.ICommunicationObject.Open%2A> método <xref:System.ServiceModel.ServiceHost>. Um endereço base é fornecido no código, a publicação de metadados está habilitada e pontos de extremidade padrão são usados.  
  
 [!code-csharp[CFX_SelfHost4#5](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#5)]
 [!code-vb[CFX_SelfHost4#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#5)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Uri>  
 <xref:System.Configuration.ConfigurationManager.AppSettings%2A>  
 <xref:System.Configuration.ConfigurationManager>  
 [Como hospedar um serviço WCF no IIS](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)  
 [Auto-hospedagem](../../../docs/framework/wcf/samples/self-host.md)  
 [Hospedando serviços](../../../docs/framework/wcf/hosting-services.md)  
 [Como definir um contrato de serviço](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)  
 [Como implementar um contrato de serviço](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)  
 [Ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
 [Usando associações para configurar serviços e clientes](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [Associações fornecidas pelo sistema](../../../docs/framework/wcf/system-provided-bindings.md)
