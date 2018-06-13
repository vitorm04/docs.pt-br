---
title: Correlação baseada em conteúdo
ms.date: 03/30/2017
ms.assetid: f46a2b68-8d24-4122-bbee-9573fc3f9fb4
ms.openlocfilehash: 48009420788b8678f842c4368926e04f8a745a52
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33494209"
---
# <a name="content-based-correlation"></a>Correlação baseada em conteúdo
Quando os serviços de fluxo de trabalho se comunicar com clientes e outros serviços, geralmente há alguns dados de mensagens trocadas que relaciona exclusivamente uma mensagem para uma determinada instância. Correlação baseada em conteúdo usa esses dados na mensagem, como um número ou a ordem de ID de cliente, para rotear mensagens para a instância de fluxo de trabalho adequado. Este tópico explica como usar a correlação baseada em conteúdo em fluxos de trabalho.  
  
## <a name="using-content-based-correlation"></a>Usando a correlação baseada em conteúdo  
 Correlação baseada em conteúdo é usada quando um serviço de fluxo de trabalho tem vários métodos que são acessados por um único cliente e uma parte dos dados nas mensagens trocadas identifica a instância desejada.  
  
> [!NOTE]
>  Correlação baseada em conteúdo é útil quando a correlação de contexto não pode ser usada porque a associação não é uma das ligações de troca de contexto com suporte. Para obter mais informações sobre a correlação de contexto, consulte [intercâmbio de contexto](../../../../docs/framework/wcf/feature-details/context-exchange-correlation.md).  
  
 Cada atividade mensagens nessas comunicações deve especificar o local dos dados na mensagem que identifica exclusivamente a instância. Isso é feito fornecendo uma <xref:System.ServiceModel.MessageQuerySet>, usando um <xref:System.ServiceModel.Activities.QueryCorrelationInitializer> ou <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A>, que consulta a mensagem para a parte ou partes de dados que identificam exclusivamente a instância.  
  
> [!WARNING]
>  Os dados que são usados para identificar a instância são transformados em uma chave de correlação. Deve-se ter cuidado para garantir que os dados usados para correlação são exclusivos ou então colisões na chave de hash podem ocorrer e gerar mensagens acabe sendo enviado. Por exemplo, uma correlação baseada apenas em um nome de cliente pode causar um conflito porque pode haver vários clientes com o mesmo nome. Os dois-pontos (`:`) não deve ser usado como parte dos dados usados para correlacionar a mensagem porque ele já é usado para delimitar a consulta de mensagem chave e valor para formar a cadeia de caracteres que é transformado em hash posteriormente.  
  
 No exemplo a seguir, inicial <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> em um serviço de fluxo de trabalho retorna um `OrderId`, que é passado novamente pelo cliente na chamada para o seguinte <xref:System.ServiceModel.Activities.Receive> atividade no serviço de fluxo de trabalho.  
  
 [!code-csharp[CFX_ContentCorrelation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_contentcorrelation/cs/program.cs#1)]  
  
 O exemplo anterior mostra uma correlação baseada em conteúdo que é inicializada através de <xref:System.ServiceModel.Activities.SendReply>. O <xref:System.ServiceModel.MessageQuerySet> Especifica que os dados usados para identificar mensagens subsequentes para este serviço são o `OrderId`.  
  
 [!code-csharp[CFX_ContentCorrelation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_contentcorrelation/cs/program.cs#2)]  
  
 O <xref:System.ServiceModel.Activities.Receive> atividade que segue o <xref:System.ServiceModel.Activities.SendReply> no fluxo de trabalho segue a correlação que foi inicializada pelo <xref:System.ServiceModel.Activities.SendReply>. As duas atividades compartilham o mesmo <xref:System.ServiceModel.Activities.CorrelationHandle>, mas cada uma tem seu próprio <xref:System.ServiceModel.MessageQuerySet> e <xref:System.ServiceModel.XPathMessageQuery> que especifica onde os dados que identificam nessa mensagem específica. Sobre a atividade que inicializa a correlação, isso <xref:System.ServiceModel.MessageQuerySet> é especificado no <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> propriedade e para qualquer das seguintes <xref:System.ServiceModel.Activities.Receive> atividades, for especificado usando o <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> propriedade.  
  
 [!code-csharp[CFX_ContentCorrelation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_contentcorrelation/cs/program.cs#3)]  
  
 Uma correlação baseada em conteúdo pode ser inicializada por qualquer atividade de mensagens (<xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply>, <xref:System.ServiceModel.Activities.ReceiveReply>) quando os dados fluem como parte de uma mensagem. Se a parte específica de dados de fluxo não como parte de uma mensagem, pode ser inicializado explicitamente usando o <xref:System.ServiceModel.Activities.InitializeCorrelation> atividade. Se várias partes de dados são necessários para identificar exclusivamente a mensagem, várias consultas podem ser adicionadas para o <xref:System.ServiceModel.MessageQuerySet>. Nestes exemplos, uma <xref:System.ServiceModel.Activities.CorrelationHandle> foi fornecido explicitamente para cada uma das atividades usando o `CorrelatesWith` ou `CorrelationHandle` propriedades, mas se houver apenas uma correlação necessária para todo o fluxo de trabalho, como neste exemplo onde tudo o que se correlaciona em `OrderId`, o gerenciamento de identificador de correlação implícita fornecido pelo <xref:System.ServiceModel.Activities.WorkflowServiceHost> é suficiente.  
  
## <a name="using-the-initializecorrelation-activity"></a>Usando a atividade de InitializeCorrelation  
 No exemplo anterior, o `OrderId` fluíram para o chamador por meio de <xref:System.ServiceModel.Activities.SendReply> atividade e isso é onde a correlação foi inicializada. O mesmo comportamento pode ser feito usando o <xref:System.ServiceModel.Activities.InitializeCorrelation> atividade. O <xref:System.ServiceModel.Activities.InitializeCorrelation> atividade leva o <xref:System.ServiceModel.Activities.CorrelationHandle> e um dicionário de itens que representam os dados usados para mapear a mensagem para a instância correta. Para usar o <xref:System.ServiceModel.Activities.InitializeCorrelation> atividade no exemplo anterior, remova o <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> do <xref:System.ServiceModel.Activities.SendReply> atividade e inicializar a correlação usando o <xref:System.ServiceModel.Activities.InitializeCorrelation> atividade.  
  
 [!code-csharp[CFX_ContentCorrelation#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_contentcorrelation/cs/program.cs#4)]  
  
 O <xref:System.ServiceModel.Activities.InitializeCorrelation> atividade é usada no fluxo de trabalho, após as variáveis que mantêm os dados são populados mas antes de <xref:System.ServiceModel.Activities.Receive> atividade que se correlaciona com o inicializado <xref:System.ServiceModel.Activities.CorrelationHandle>.  
  
 [!code-csharp[CFX_ContentCorrelation#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_contentcorrelation/cs/program.cs#5)]  
  
## <a name="configuring-xpath-queries-using-the-workflow-designer"></a>Configuração de consultas XPath usando o Designer de fluxo de trabalho  
 Nos exemplos anteriores, as atividades e as consultas XPath usadas em consultas de mensagens foram especificadas no código. O designer de fluxo de trabalho do [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] também fornece a capacidade de gerar XPaths de `DataContract` tipos para correlação baseada em conteúdo. O XPath primeiro configurado no exemplo anterior foi configurado para o <xref:System.ServiceModel.Activities.SendReply>.  
  
 [!code-csharp[CFX_ContentCorrelation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_contentcorrelation/cs/program.cs#2)]  
  
 Para configurar o XPath para uma atividade de mensagens no designer de fluxo de trabalho, selecione a atividade no designer de fluxo de trabalho. Se a atividade está inicializando a correlação, como no exemplo anterior, clique no botão de reticências para o **CorrelationInitializers** propriedade o **propriedades** janela. Isso exibe o **adicionar inicializadores de correlação** janela da caixa de diálogo. Essa caixa de diálogo, você pode especificar o tipo de correlação e selecione o conteúdo que é usado para a correlação. O <xref:System.ServiceModel.Activities.CorrelationHandle> especificada na variável de **adicionar inicializador** caixa e o tipo de correlação e usados para a correlação de dados é selecionado do **consultas XPath** seção da caixa de diálogo.  
  
 ![Caixa de diálogo de CorrelationInitializer](../../../../docs/framework/wcf/feature-details/media/correlationinitializerdlg.jpg "CorrelationInitializerDlg")  
  
 A segunda consulta XPath no exemplo anterior foi configurada no <xref:System.ServiceModel.Activities.Receive> atividade.  
  
 [!code-csharp[CFX_ContentCorrelation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_contentcorrelation/cs/program.cs#3)]  
  
 Para configurar a consulta XPath para uma atividade de mensagens que não inicializa a correlação, selecione a atividade no designer de fluxo de trabalho e, em seguida, clique no botão de reticências para o **CorrelatesOn** propriedade o  **Propriedades** janela. Isso exibe o **definição de CorrelatesOn** janela da caixa de diálogo.  
  
 ![Definição de CorrelatesOn](../../../../docs/framework/wcf/feature-details/media/correlatesondialog.jpg "CorrelatesOnDialog")  
  
 Nessa caixa de diálogo que você especificar o <xref:System.ServiceModel.Activities.CorrelationHandle> e escolha os itens a **consultas XPath** lista para criar a consulta XPath.
