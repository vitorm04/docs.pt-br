---
title: Novidades no Windows Foundation Workflow no .NET 4.5
ms.date: 03/30/2017
ms.assetid: 195c43a8-e0a8-43d9-aead-d65a9e6751ec
ms.openlocfilehash: b907a592bd644bc7a9c4aa19cef78a49bf729561
ms.sourcegitcommit: 79066169e93d9d65203028b21983574ad9dcf6b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57212398"
---
# <a name="whats-new-in-windows-workflow-foundation-in-net-45"></a>Novidades no Windows Foundation Workflow no .NET 4.5

Windows Workflow Foundation (WF) no [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] apresenta muitos recursos novos, como novas atividades, recursos do designer e modelos de desenvolvimento de fluxo de trabalho. Muitos, mas não todos, os novos recursos do fluxo de trabalho introduzidos no [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] têm suporte no designer de fluxo de trabalho hospedado novamente. Para obter mais informações sobre os novos recursos que têm suporte, consulte [suporte para recursos do novo fluxo de trabalho Foundation 4.5 no Designer de fluxo de trabalho Rehosted](../../../docs/framework/windows-workflow-foundation/wf-features-in-the-rehosted-workflow-designer.md). Para obter mais informações sobre como migrar aplicativos de fluxo de trabalho de .NET 3.0 e 3.5 do .NET para usar a versão mais recente, consulte [diretrizes de migração](../../../docs/framework/windows-workflow-foundation/migration-guidance.md). Este tópico fornece uma visão geral dos novos recursos de fluxo de trabalho introduzidos no [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].

> [!WARNING]
> Os novos recursos do Windows Workflow Foundation introduzidos no [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] não estão disponíveis para projetos destinados a versões anteriores do framework. Se um projeto que visa o [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] novamente é destinado a uma versão anterior da estrutura, vários problemas podem ocorrer.
>
> - As expressões c# serão substituídas no designer com a mensagem **valor foi definido em XAML**.
> - Muitos erros de compilação ocorrerão, incluindo o seguinte.
>
> **O formato de arquivo não é compatível com a estrutura de destino atual. Para converter o formato de arquivo, salve o arquivo explicitamente. Essa mensagem de erro desaparecerá depois de salvar o arquivo e reabra o designer.**

## <a name="BKMK_Versioning"></a> Controle de versão de fluxo de trabalho

O [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] introduziu vários novos recursos de controle de versão com base na nova classe <xref:System.Activities.WorkflowIdentity>. O <xref:System.Activities.WorkflowIdentity> fornece a autores de aplicativo de fluxo de trabalho um mecanismo para mapear uma instância de fluxo de trabalho persistida com sua definição.

- Os desenvolvedores que usam a hospedagem do <xref:System.Activities.WorkflowApplication> podem usar o <xref:System.Activities.WorkflowIdentity> para habilitar hospedagem de várias versões de um fluxo de trabalho lado a lado. As instâncias de fluxo de trabalho persistidas podem ser carregadas usando a nova classe <xref:System.Activities.WorkflowApplicationInstance> e, em seguida, o <xref:System.Activities.WorkflowApplicationInstance.DefinitionIdentity%2A> pode ser usado pelo host para fornecer a versão correta da definição de fluxo de trabalho ao criar uma instância do <xref:System.Activities.WorkflowApplication>. Para obter mais informações, consulte [usando WorkflowIdentity e controle de versão](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md) e [como: Hospedar várias versões de uma fluxo de trabalho lado a lado](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md).

- O <xref:System.ServiceModel.WorkflowServiceHost> agora é um host de várias versões. Quando uma nova versão de um serviço de fluxo de trabalho é implantada, as novas instâncias são criadas usando o novo serviço, mas as instâncias existentes continuam usando a versão anterior. Para obter mais informações, consulte [controle de versão lado a lado no WorkflowServiceHost](../../../docs/framework/wcf/feature-details/side-by-side-versioning-in-workflowservicehost.md).

- A atualização dinâmica é introduzida, o que fornece um mecanismo para atualizar a definição de uma instância de fluxo de trabalho persistida. Para obter mais informações, consulte [atualização dinâmica](../../../docs/framework/windows-workflow-foundation/dynamic-update.md) e [como: Atualizar a definição de uma instância de fluxo de trabalho em execução](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md).

- Um script de banco de dados SqlWorkflowInstanceStoreSchemaUpgrade.sql é fornecido para atualizar bancos de dados de persistência criados usando os scripts de banco de dados do [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)]. Esse script atualiza bancos de dados de persistência do [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] para dar suporte aos novos recursos de controle de versão introduzidos no [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]. As instâncias de fluxo de trabalho persistidas no banco de dados recebem valores padrão do controle de versão e podem participar da execução lado a lado e da atualização dinâmica. Para obter mais informações, consulte [atualizando o .NET Framework 4 persistência bancos de dados ao controle de versão de fluxo de trabalho de suporte](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md#UpdatingWF4PersistenceDatabases).

## <a name="BKMK_NewActivities"></a> Atividades

A biblioteca de atividades embutida contém novas atividades e novos recursos para atividades existentes.

### <a name="BKMK_NoPersistScope"></a> Escopo do NoPersist

<xref:System.Activities.Statements.NoPersistScope> é uma nova atividade do contêiner que impede que um fluxo de trabalho seja persistido quando as atividades filhos do NoPersistScope estiverem em execução. Isso é útil em cenários onde não é apropriado para o fluxo de trabalho ser persistido, como quando o fluxo de trabalho estiver usando recursos específicos de computadores como os identificadores de arquivos ou durante as transações de banco de dados. Anteriormente, para impedir que a persistência ocorresse durante a execução de uma atividade, um <xref:System.Activities.NativeActivity> personalizado que usava <xref:System.Activities.NoPersistHandle> era necessário.

### <a name="BKMK_NewFlowchartCapabilities"></a> Novos recursos de fluxograma

Os fluxogramas são atualizados para [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] e têm os seguintes novos recursos:

- A propriedade `DisplayName` de uma atividade <xref:System.Activities.Statements.FlowSwitch%601> ou <xref:System.Activities.Statements.FlowDecision> é editável. Isso permitirá que o designer de atividade mostre mais informações sobre a finalidade da atividade.

- Os fluxogramas têm uma nova propriedade chamada <xref:System.Activities.Statements.Flowchart.ValidateUnconnectedNodes%2A>; o padrão para essa propriedade é `False`. Se essa propriedade for definida como `True`, os nós de fluxograma desconectados gerarão erros de validação.

## <a name="support-for-partial-trust"></a>Suporte para confiança parcial

Os fluxos de trabalho no [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)] exigiam um domínio de aplicativo totalmente confiável. No [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], os fluxos de trabalho podem operar em um ambiente de confiança parcial. Em um ambiente de confiança parcial, os componentes de terceiros podem ser usados sem conceder a eles acesso completo aos recursos do host. Algumas preocupações sobre fluxos de trabalho em execução em confiança parcial são as seguintes:

1. Usar os componentes legados (incluindo regras) contidos na atividade <xref:System.Activities.Statements.Interop> não tem suporte em confiança parcial.

2. Fluxos de trabalho em execução em confiança parcial no <xref:System.ServiceModel.WorkflowServiceHost> não têm suporte.

3. Manter exceções em um cenário de confiança parcial é uma ameaça potencial de segurança. Para desabilitar a persistência de exceções, uma extensão do tipo <xref:System.Activities.ExceptionPersistenceExtension> deve ser adicionada ao projeto para deixar de persistir exceções. O exemplo de código a seguir demonstra como implementar esse tipo.

    ```csharp
    public class ExceptionPersistenceExtension
    {
        public ExceptionPersistenceExtension()
        {
            this.PersistExceptions = false;
        }
        public bool PersistExceptions { get; set; }
    }
    ```

     Se as exceções não tiverem que ser serializadas, verifique se as exceções são usadas dentro de um <xref:System.Activities.Statements.NoPersistScope>.

4. Os autores de atividade devem substituir <xref:System.Activities.Activity.CacheMetadata%2A> para evitar que o tempo de execução do fluxo de trabalho execute automaticamente a reflexão em relação ao tipo. Os argumentos e as atividades filho devem ser não null e <xref:System.Activities.ActivityMetadata.Bind%2A> deve ser chamado explicitamente. Para obter mais informações sobre substituição <xref:System.Activities.Activity.CacheMetadata%2A>, consulte [expõem dados com CacheMetadata](../../../docs/framework/windows-workflow-foundation/exposing-data-with-cachemetadata.md). Além disso, as instâncias dos argumentos que são de um tipo que está `internal` ou **privada** deve ser explicitamente criado no <xref:System.Activities.Activity.CacheMetadata%2A> para evitar serem criadas por reflexão.

5. Os tipos não usarão <xref:System.Runtime.Serialization.ISerializable> ou <xref:System.SerializableAttribute> para serialização; os tipos que tiverem que ser serializados devem oferecer suporte a <xref:System.Runtime.Serialization.DataContractSerializer>.

6. Expressões que usam <xref:System.Activities.Expressions.LambdaValue%601> exigem <xref:System.Security.Permissions.ReflectionPermissionAttribute.RestrictedMemberAccess%2A> e, dessa forma, não funcionarão em confiança parcial. Os fluxos de trabalho que usam <xref:System.Activities.Expressions.LambdaValue%601> devem substituir essas expressões pelas atividades que derivam de <xref:System.Activities.CodeActivity%601>. .

7. As expressões não podem ser criadas com <xref:System.Activities.XamlIntegration.TextExpressionCompiler> ou o compilador hospedado do Visual Basic em confiança parcial, mas as expressões criadas anteriormente podem ser executadas.

8. Um único assembly que usa [transparência de nível 2](https://aka.ms/Level2Transparency) não pode ser usada [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] em confiança total, e [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] em confiança parcial.

## <a name="BKMK_NewDesignerCapabilites"></a> Novos recursos do Designer

### <a name="BKMK_DesignerSearch"></a> Pesquisa do Designer

Para tornar os fluxos de trabalho maiores mais gerenciáveis, os fluxos de trabalho podem agora ser pesquisados por palavra-chave. Esse recurso só está disponível no Visual Studio; Esse recurso não está disponível em um designer hospedado novamente. Há dois tipos de pesquisas disponível:

- Localização rápida, iniciada com **Ctrl + F** ou **editar**, **localizar e substituir**, **localização rápida**.

- Localizar nos arquivos, iniciada com **Ctrl + Shift + F** ou **editar**, **localizar e substituir**, **localizar nos arquivos**.

Observe que Substituir não tem suporte.

#### <a name="BKMK_QuickFind"></a> Localização rápida

As palavras-chave pesquisadas em fluxos de trabalho corresponderão aos seguintes itens do designer:

- Propriedades de objetos <xref:System.Activities.Activity>, <xref:System.Activities.Statements.FlowNode>, <xref:System.Activities.Statements.State>, <xref:System.Activities.Statements.Transition> e outros itens de controle de fluxo personalizado.

- Variáveis

- Arguments

- Expressões

A Localização Rápida é executada na árvore do <xref:System.Activities.Presentation.Model.ModelItem> do designer. A Localização Rápida não localizará namespaces importados na definição de fluxo de trabalho.

#### <a name="BKMK_FindInFiles"></a> Localizar nos arquivos

As palavras-chave pesquisadas em fluxos de trabalho coincidirão com o conteúdo real dos arquivos de fluxo de trabalho. Os resultados da pesquisa serão mostrados no painel de exibição Localizar Resultados do Visual Studio. Clicar duas vezes no item de resultado navegará até a atividade que contém a correspondência no designer de fluxo de trabalho.

### <a name="BKMK_VariableDeleteContextMenu"></a> Excluir item de menu de contexto no designer de variável e argumento

No [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], as variáveis e os argumentos somente podem ser excluídos no designer usando o teclado. A partir do [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], as variáveis e os argumentos podem ser excluídos com o menu de contexto.

A captura de tela a seguir mostra o menu de contexto do designer de variável e argumento.

![Variável e o Menu de contexto do Designer do argumento](../../../docs/framework/windows-workflow-foundation/media/designercontextmenu.png "DesignerContextMenu")

### <a name="BKMK_AutoSurround"></a> Envolvimento automático com sequência

Como um fluxo de trabalho ou algumas atividades do contêiner (como <xref:System.Activities.Statements.NoPersistScope>) só podem conter uma única atividade do corpo, adicionar uma segunda atividade exigia que o desenvolvedor excluísse a primeira atividade, adicionasse uma atividade <xref:System.Activities.Statements.Sequence> e, em seguida, adicionasse as duas atividades para a atividade de sequência. A partir do [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], ao adicionar uma segunda atividade para a superfície do designer, uma atividade de `Sequence` será criada automaticamente para incluir as duas atividades.

A captura de tela a seguir mostra uma atividade de `WriteLine` no `Body` de um `NoPersistScope`.

![Automático&#45;coloque o local de destino](../../../docs/framework/windows-workflow-foundation/media/autosurround1.png "AutoSurround1")

A captura de tela a seguir mostra a atividade de `Sequence` criada automaticamente no `Body` quando um segundo `WriteLine` é solto abaixo do primeiro.

![Atividade de sequência criada automaticamente](../../../docs/framework/windows-workflow-foundation/media/autosurround2.png "AutoSurround2")

### <a name="BKMK_PanMode"></a> Modo panorâmico

Para navegar mais facilmente um grande fluxo de trabalho no designer, o modo panorâmico pode ser habilitado, permitindo que o desenvolvedor clique e arraste para mover a parte visível do fluxo de trabalho, em vez de precisar usar as barras de rolagem. O botão para ativar o modo de superfície está no canto inferior direito do designer.

A captura de tela a seguir mostra o botão de panorâmica qual está localizado no canto inferior direito do designer de fluxo de trabalho.

![Botão de panorâmica no designer de fluxo de trabalho](../../../docs/framework/windows-workflow-foundation/media/panbutton.png "PanButton")

O botão do meio do mouse ou a barra de espaço também podem ser usados para executar uma panorâmica do designer de fluxo de trabalho.

### <a name="BKMK_MultiSelect"></a> Multi-select

Várias atividades podem ser selecionadas ao mesmo tempo, arrastando um retângulo ao redor delas (quando o modo panorâmico não está habilitado), ou mantendo pressionada a tecla CTRL e clicando nas atividades desejadas.

Várias seleções de atividade também podem ser arrastadas e soltadas dentro do designer, e também podem ser interagidas usando o menu de contexto.

### <a name="BKMK_DocumentOutline"></a> Exibição de estrutura de tópicos de itens de fluxo de trabalho

Para facilitar a navegação de fluxos de trabalho hierárquicos, os componentes de um fluxo de trabalho são mostrados em uma exibição de destaque em estilo de árvore. O modo de exibição de estrutura de tópicos é exibido na **Document Outline** modo de exibição. Para abrir essa exibição, no menu superior, selecione **modo de exibição**, **Other Windows**, **Document Outline**, ou pressione Ctrl W, U. Clicar em um nó na exibição de destaque navegará para a atividade correspondente no designer de fluxo de trabalho, e a exibição da estrutura será atualizada para mostrar as atividades que estão selecionadas no designer.

A seguinte captura de tela de fluxo de trabalho concluído do [Tutorial de Introdução](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md) mostra a exibição de estrutura de tópicos com um fluxo de trabalho sequencial.

![Modo de exibição no Designer de fluxo de trabalho de estrutura de tópicos](../../../docs/framework/windows-workflow-foundation/media/outlineviewinworkflowdesigner.jpg "OutlineViewinWorkflowDesigner")

### <a name="BKMK_CSharpExpressions"></a> Expressões em c#

Antes do [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], todas as expressões em fluxos de trabalho podiam ser escritas no Visual Basic. No [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], as expressões do Visual Basic são usadas apenas para os projetos criados usando o Visual Basic. Os projetos do Visual C# agora usam o C# para expressões. Um editor de expressão C# completamente funcional é fornecido com recursos como realce de gramática e intellisense. Os projetos do fluxo de trabalho C# criados em versões anteriores que usam expressões do Visual Basic continuarão funcionando.

As expressões C# são validadas em tempo de design. Os erros em expressões C# serão marcados com um sublinhado vermelho ondulado.

Para obter mais informações sobre expressões c#, consulte [expressões c#](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md).

### <a name="BKMK_Visibility"></a> Mais controle da visibilidade da barra de shell e cabeçalho itens

Em um designer hospedado novamente, alguns dos controles padrão de interface do usuário não podem ter o significado de um fluxo de trabalho específico, e podem ser desativados. No [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], essa personalização é suportada apenas pela barra de shell na parte inferior do designer. No [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], a visibilidade dos itens de cabeçalho do shell na parte superior do designer pode ser ajustada definindo o <xref:System.Activities.Presentation.View.DesignerView.WorkflowShellHeaderItemsVisibility%2A> com o valor apropriado <xref:System.Activities.Presentation.View.ShellHeaderItemsVisibility>.

### <a name="BKMK_AutoConnect"></a> Conexão automática e inserção automática em fluxos de trabalho de fluxograma e de máquina de estado

No [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], as conexões entre nós em um fluxo de trabalho de fluxograma precisavam ser adicionadas manualmente. No [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], os nós de fluxograma e da máquina de estado têm pontos de conexão automática que se tornam visíveis quando uma atividade é arrastada da caixa de ferramentas na superfície do designer. Soltar uma atividade em um destes pontos adiciona automaticamente a atividade junto com a conexão necessária.

A captura de tela a seguir mostra os pontos de anexação que ficam visíveis quando uma atividade é arrastada da caixa de ferramentas.

![Nó de início de fluxograma mostrando pontos de conexão automática](../../../docs/framework/windows-workflow-foundation/media/autoconnect1.png "Autoconnect1")

As atividades também podem ser arrastadas em conexões entre nós de fluxograma e estados para inserção automática do nó entre dois outros nós. A captura de tela a seguir mostra a linha de conexão realçada em que as atividades podem ser arrastadas da caixa de ferramentas e soltas.

![Automático&#45;inserir um identificador para soltar atividades](../../../docs/framework/windows-workflow-foundation/media/autoinsert.png "Autoinsert")

### <a name="BKMK_Annotations"></a> Anotações do Designer

Para facilitar o desenvolvimento de fluxos de trabalho maiores, o designer agora permite adicionar anotações para ajudar a controlar o processo de design. A anotação pode ser adicionada a atividades, estados, nós de fluxograma, variáveis e argumentos. A captura de tela a seguir mostra o menu de contexto usado para adicionar anotações para o designer.

![Menu de contexto de anotação](../../../docs/framework/windows-workflow-foundation/media/annotationdialog.png "annotationdialog")

### <a name="debugging-states"></a>Estados de depuração

No [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], os elementos que não são de atividade não podem dar suporte a pontos de interrupção de depuração porque eles não eram unidades de execução. Esta versão fornece um mecanismo para adicionar pontos de interrupção a objetos <xref:System.Activities.Statements.State>. Quando um ponto de interrupção for definido em um <xref:System.Activities.Statements.State>, a execução será interrompida quando ocorrer a transição do estado antes que suas atividades de entrada ou gatilhos sejam agendados.

### <a name="BKMK_ActivityDelegates"></a> Definir e consumir objetos ActivityDelegate no designer

As atividades no [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] usavam objetos <xref:System.Activities.ActivityDelegate> para expor pontos de execução onde outras partes do fluxo de trabalho podiam interagir com a execução de um fluxo de trabalho, mas usar esses pontos de execução necessários geralmente exigia uma grande quantidade de código. Nesta versão, os desenvolvedores podem definir e consumir representantes de atividade usando o designer de fluxo de trabalho. Para obter mais informações, confira [Como: Definir e consumir representantes de atividade no Designer de fluxo de trabalho](/visualstudio/workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer).

### <a name="BKMK_BuildTimeValidation"></a> Validação em tempo de compilação

No [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], os erros de validação do fluxo de trabalho não eram contados como erros de compilação durante a compilação de um projeto de fluxo de trabalho. Isso significava que criar um projeto de fluxo de trabalho poderia ter êxito mesmo se houvesse erros de validação do fluxo de trabalho. No [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], os erros de validação do fluxo de trabalho causam a falha na compilação.

### <a name="BKMK_DesignTimeValidation"></a> Validação em segundo plano do tempo de design

No [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], os fluxos de trabalho eram validados como um processo de primeiro plano, o que poderia parar a interface do usuário durante processos de validação complexos ou demorados. A validação do fluxo de trabalho agora ocorre em um thread em segundo plano, de modo que a interface do usuário não seja bloqueada.

### <a name="BKMK_ViewState"></a> Estado de exibição localizado em um local separado em arquivos XAML

No [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], as informações de estado de exibição para um fluxo de trabalho são armazenadas no arquivo XAML em muitos lugares diferentes. Isso é inconveniente para os desenvolvedores que desejam ler XAML diretamente, ou gravar código para remover informações de estado de exibição. No [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], as informações de estado de exibição no arquivo XAML são serializadas como um elemento separado no arquivo XAML. Os desenvolvedores podem facilmente localizar e editar as informações de estado de exibição de uma atividade ou remover completamente o estado de exibição.

### <a name="BKMK_ExpressionExtensibility"></a> Extensibilidade de expressão

No [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], fornecemos uma maneira para que os desenvolvedores criem sua própria expressão e experiência de criação da expressão, que pode ser conectada ao designer de fluxo de trabalho.

### <a name="BKMK_BackwardCompatRehostedDesigner"></a> Inscreva-se para recursos do Workflow 4.5 no designer hospedado novamente

Para preservar a compatibilidade com versões anteriores, alguns novos recursos incluídos no [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] não estão habilitados por padrão no designer hospedado novamente. Este é para garantir que aplicativos existentes que usam o designer hospedado novamente não sejam interrompidos ao atualizar para a versão mais recente. Para habilitar novos recursos no designer hospedado novamente, defina <xref:System.Activities.Presentation.DesignerConfigurationService.TargetFrameworkName%2A> como ".NET Framework 4.5" ou defina membros individuais do conjunto de <xref:System.Activities.Presentation.DesignerConfigurationService> para habilitar recursos individuais.

## <a name="BKMK_NewWFModels"></a> Novos modelos de desenvolvimento de fluxo de trabalho

Além do fluxograma e de modelos sequenciais de desenvolvimento de fluxo de trabalho, esta versão inclui fluxos de trabalho da Máquina de Estado e serviços de fluxo de trabalho de primeiro contrato.

### <a name="BKMK_StateMachine"></a> Fluxos de trabalho de máquina de estado

Fluxos de trabalho de máquina de estado foram introduzidos como parte do .NET Framework 4, versão 4.0.1 na [Microsoft .NET Framework 4 Platform Update 1](https://go.microsoft.com/fwlink/?LinkID=215092). Essa atualização incluiu várias novas classes e atividades que permitiram que os desenvolvedores criassem fluxos de trabalho de máquina do estado. Essas classes e atividades foram atualizadas para o [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]. As atualizações incluem:

1. A capacidade de definir pontos de interrupção em estados

2. A capacidade de copiar e colar transições no designer de fluxo de trabalho

3. Suporte de designer para criação de transição do disparador compartilhado

4. Atividades usadas para criar fluxos de trabalho da máquina de estado, incluindo: <xref:System.Activities.Statements.StateMachine>, <xref:System.Activities.Statements.State> e <xref:System.Activities.Statements.Transition>.

Captura de tela a seguir mostra o fluxo de trabalho de máquina de estado concluído do [Tutorial de Introdução](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md) etapa [como: Criar um fluxo de trabalho de máquina de estado](../../../docs/framework/windows-workflow-foundation/how-to-create-a-state-machine-workflow.md).

![Fluxo de trabalho de máquina de estado concluído](../../../docs/framework/windows-workflow-foundation/media/wfstatemachinegettingstartedtutorialcomplete.JPG "WFStateMachineGettingStartedTutorialComplete")

Para obter mais informações sobre a criação de fluxos de trabalho de máquina de estado, consulte [fluxos de trabalho de máquina de estado](../../../docs/framework/windows-workflow-foundation/state-machine-workflows.md).

### <a name="BKMK_ContractFirst"></a> Desenvolvimento de fluxo de trabalho de primeiro contrato

A ferramenta de desenvolvimento de fluxo de trabalho de primeiro contrato permite que o desenvolvedor crie um contrato no código pela primeira vez, em seguida, com alguns cliques no Visual Studio, gerar automaticamente um modelo de atividade na caixa de ferramentas representando cada operação. Essas atividades são então usadas para criar um fluxo de trabalho que implementa as operações definidas pelo contrato. O designer de fluxo de trabalho validará o serviço de fluxo de trabalho para assegurar que essas operações sejam implementadas e a assinatura do fluxo de trabalho corresponda à assinatura do contrato. O desenvolvedor também pode associar um serviço de fluxo de trabalho a uma coleção de contratos implementados. Para obter mais informações sobre o desenvolvimento de serviço de fluxo de trabalho de primeiro contrato, consulte [como: Criar um serviço de fluxo de trabalho que consome um contrato de serviço existente](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md).
