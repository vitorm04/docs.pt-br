---
title: Usando a atividade de Interoperabilidade em um fluxo de trabalho do .NET Framework 4
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9bb747f0-eb33-4f70-84cd-317382372dcd
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0a02d6dbc7c6f6583a174bd10853d8c8070ac273
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="using-the-interop-activity-in-a-net-framework-4-workflow"></a>Usando a atividade de Interoperabilidade em um fluxo de trabalho do .NET Framework 4
As atividades criada usando [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] ou [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] pode ser usado em um fluxo de trabalho [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] usando a atividade de <xref:System.Activities.Statements.Interop> . Este tópico fornece uma visão geral de usar a atividade de <xref:System.Activities.Statements.Interop> .  
  
> [!NOTE]
>  O <xref:System.Activities.Statements.Interop> não aparecerá na caixa de ferramentas de designer da fluxo de trabalho, a menos que o projeto do fluxo de trabalho tem seu **Framework de destino** configuração definida como **.Net Framework 4** ou posterior.  
  
## <a name="using-the-interop-activity-in-net-framework-45-workflows"></a>Usando a atividade de Interoperabilidade em fluxos de trabalho do .NET Framework 4.5  
 Neste tópico, uma biblioteca de atividade de [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] é criada que contém uma atividade de `DiscountCalculator` . `DiscountCalculator` calcula desconto com base em uma quantidade de compra e consiste em <xref:System.Workflow.Activities.SequenceActivity> que contém <xref:System.Workflow.Activities.PolicyActivity>.  
  
> [!NOTE]
>  A atividade de [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] criada neste tópico usa <xref:System.Workflow.Activities.PolicyActivity> para implementar a lógica de atividade. Não é necessário para usar uma atividade personalizado de [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] ou a atividade de <xref:System.Activities.Statements.Interop> para usar regras em um fluxo de trabalho [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] . Para obter um exemplo do uso de regras em um [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] fluxo de trabalho sem usar o <xref:System.Activities.Statements.Interop> atividade, consulte o [atividade de política no .NET Framework 4.5](../../../docs/framework/windows-workflow-foundation/samples/policy-activity-in-net-framework-4-5.md) exemplo.  
  
#### <a name="to-create-the-net-framework-35-activity-library-project"></a>Para criar o projeto de biblioteca de atividade do .NET Framework 3.5  
  
1.  Abra [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] e selecione **novo** e **projeto...** do **arquivo** menu.  
  
2.  Expanda o **outros tipos de projetos** nó o **modelos instalados** painel e selecione **soluções do Visual Studio**.  
  
3.  Selecione **solução em branco** do **soluções do Visual Studio** lista. Tipo `PolicyInteropDemo` no **nome** caixa e clique em **Okey**.  
  
4.  Clique com botão direito **PolicyInteropDemo** na **Solution Explorer** e selecione **adicionar** e, em seguida, **novo projeto...** .  
  
    > [!TIP]
    >  Se o **Solution Explorer** janela não estiver visível, selecione **Solution Explorer** do **exibição** menu.  
  
5.  No **modelos instalados** lista, selecione **Visual C#** e **fluxo de trabalho**. Selecione **.NET Framework 3.5** na lista de lista suspensa de versão do .NET Framework e, em seguida, selecione **biblioteca de atividades de fluxo de trabalho** do **modelos** lista.  
  
6.  Tipo `PolicyActivityLibrary` no **nome** caixa e clique em **Okey**.  
  
7.  Clique com botão direito **Activity1.cs** na **Solution Explorer** e selecione **excluir**. Clique em **Okey** para confirmar.  
  
#### <a name="to-create-the-discountcalculator-activity"></a>Para criar a atividade de DiscountCalculator  
  
1.  Clique com botão direito **PolicyActivityLibrary** na **Solution Explorer** e selecione **adicionar** e, em seguida, **atividade...** .  
  
2.  Selecione **atividade (com separação de código)** do **itens do Visual C#** lista. Tipo `DiscountCalculator` no **nome** caixa e clique em **Okey**.  
  
3.  Clique com botão direito **DiscountCalculator.xoml** na **Solution Explorer** e selecione **Exibir código**.  
  
4.  Adicione as seguintes três propriedades para a classe de `DiscountCalculator` .  
  
    ```csharp  
    public partial class DiscountCalculator : SequenceActivity  
    {  
        public double Subtotal { get; set; }  
        public double DiscountPercent { get; set; }  
        public double Total { get; set; }  
    }  
    ```  
  
5.  Clique com botão direito **DiscountCalculator.xoml** na **Solution Explorer** e selecione **Designer de exibição**.  
  
6.  Arraste um **política** atividade do **v 3.0 do fluxo de trabalho do Windows** seção o **caixa de ferramentas** e solte-o no **DiscountCalculator** atividade .  
  
    > [!TIP]
    >  Se o **caixa de ferramentas** janela não estiver visível, selecione **caixa de ferramentas** do **exibição** menu.  
  
#### <a name="to-configure-the-rules"></a>Para configurar as regras  
  
1.  Clique em recém-adicionado **política** atividade para selecioná-la, se não ainda estiver selecionada.  
  
2.  Clique o **RuleSetReference** propriedade o **propriedades** janela para selecioná-la e clique no botão de reticências à direita da propriedade.  
  
    > [!TIP]
    >  Se o **propriedades** janela não estiver visível, escolha **janela propriedades** do **exibição** menu.  
  
3.  Selecione **clique em novo...** .  
  
4.  Clique em **Adicionar regra**.  
  
5.  Digite a seguinte expressão para o **condição** caixa.  
  
    ```  
    this.Subtotal >= 50 && this.Subtotal < 100  
    ```  
  
6.  Digite a seguinte expressão para o **ações, em seguida,** caixa.  
  
    ```  
    this.DiscountPercent = 0.075  
    ```  
  
7.  Clique em **Adicionar regra**.  
  
8.  Digite a seguinte expressão para o **condição** caixa.  
  
    ```  
    this.Subtotal >= 100  
    ```  
  
9. Digite a seguinte expressão para o **ações, em seguida,** caixa.  
  
    ```  
    this.DiscountPercent = 0.15  
    ```  
  
10. Clique em **Adicionar regra**.  
  
11. Digite a seguinte expressão para o **condição** caixa.  
  
    ```  
    this.DiscountPercent > 0  
    ```  
  
12. Digite a seguinte expressão para o **ações, em seguida,** caixa.  
  
    ```  
    this.Total = this.Subtotal - this.Subtotal * this.DiscountPercent  
    ```  
  
13. Digite a seguinte expressão para o **ações Else** caixa.  
  
    ```  
    this.Total = this.Subtotal  
    ```  
  
14. Clique em **Okey** para fechar o **Editor de conjunto de regra** caixa de diálogo.  
  
15. Certifique-se de que o recém-criado <xref:System.Workflow.Activities.Rules.RuleSet> está selecionado no **nome** lista e clique em **Okey**.  
  
16. Pressione CTRL+SHIFT+B para criar a solução.  
  
 As regras adicionadas à atividade de `DiscountCalculator` neste procedimento são mostradas no exemplo de código.  
  
```  
Rule1: IF this.Subtotal >= 50 && this.Subtotal < 100   
       THEN this.DiscountPercent = 0.075   
  
Rule2: IF this. Subtotal >= 100   
       THEN this.DiscountPercent = 0.15   
  
Rule3: IF this.DiscountPercent > 0   
       THEN this.Total = this.Subtotal - this.Subtotal * this.DiscountPercent   
       ELSE this.Total = this.Subtotal  
```  
  
 Quando <xref:System.Workflow.Activities.PolicyActivity> executa, essas três regras valor e alteram `Subtotal`, `DiscountPercent`, e valores de propriedade de `Total` de atividade de `DiscountCalculator` para calcular o desconto desejado.  
  
## <a name="using-the-discountcalculator-activity-with-the-interop-activity"></a>Usando a atividade de DiscountCalculator com a atividade de Interoperabilidade  
 Para usar a atividade de `DiscountCalculator` em um fluxo de trabalho [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] , a atividade de <xref:System.Activities.Statements.Interop> é usada. Em fluxos de trabalho desta seção dois são criados, um código e um uso de utilizando o designer de fluxo de trabalho, que mostram como usar a atividade de <xref:System.Activities.Statements.Interop> com a atividade de `DiscountCalculator` . O mesmo aplicativo host é usado para ambos os fluxos de trabalho.  
  
#### <a name="to-create-the-host-application"></a>Para criar o aplicativo host  
  
1.  Clique com botão direito **PolicyInteropDemo** na **Solution Explorer** e selecione **adicionar**e, em seguida, **novo projeto...** .  
  
2.  Certifique-se de que **.NET Framework 4.5** está selecionado na lista suspensa de versão do .NET Framework e selecione **aplicativo de Console do fluxo de trabalho** do **itens do Visual C#** lista.  
  
3.  Tipo `PolicyInteropHost` para o **nome** caixa e clique em **Okey**.  
  
4.  Clique com botão direito **PolicyInteropHost** na **Solution Explorer** e selecione **propriedades**.  
  
5.  No **framework de destino** suspensa lista, altere a seleção de **.NET Framework 4 Client Profile** para **.NET Framework 4.5**. Clique em **Sim** para confirmar.  
  
6.  Clique com botão direito **PolicyInteropHost** na **Solution Explorer** e selecione **adicionar referência...** .  
  
7.  Selecione **PolicyActivityLibrary** do **projetos** guia e clique em **Okey**.  
  
8.  Clique com botão direito **PolicyInteropHost** na **Solution Explorer** e selecione **adicionar referência...** .  
  
9. Selecione **System.Workflow.Activities**, **System.Workflow.ComponentModel**e, em seguida, **System.Workflow.Runtime** do **.NET**guia e clique em **Okey**.  
  
10. Clique com botão direito **PolicyInteropHost** na **Solution Explorer** e selecione **definir como projeto de inicialização**.  
  
11. Pressione CTRL+SHIFT+B para criar a solução.  
  
### <a name="using-the-interop-activity-in-code"></a>Usando a atividade de Interoperabilidade no código  
 Nesse exemplo, uma definição de fluxo de trabalho é criada usando o código que contém a atividade de <xref:System.Activities.Statements.Interop> e a atividade de `DiscountCalculator` . Este fluxo de trabalho é chamado usando <xref:System.Activities.WorkflowInvoker> e os resultados de avaliação de regras são gravados no console usando uma atividade de <xref:System.Activities.Statements.WriteLine> .  
  
##### <a name="to-use-the-interop-activity-in-code"></a>Para usar a atividade de Interoperabilidade no código  
  
1.  Clique com botão direito **Program.cs** na **Solution Explorer** e selecione **Exibir código**.  
  
2.  Adicione a seguinte declaração de `using` na parte superior do arquivo.  
  
    ```csharp  
    using PolicyActivityLibrary;  
    ```  
  
3.  Remova o conteúdo do método de `Main` e substituí-los com o código a seguir.  
  
    ```csharp  
    static void Main(string[] args)  
    {  
        CalculateDiscountUsingCodeWorkflow();  
    }  
    ```  
  
4.  Crie um novo método na classe de `Program` chamada `CalculateDiscountUsingCodeWorkflow` que contém o código a seguir.  
  
    ```csharp  
    static void CalculateDiscountUsingCodeWorkflow()  
    {  
        Variable<double> Subtotal = new Variable<double>  
        {  
            Default = 75.99,  
            Name = "Subtotal"  
        };  
  
        Variable<double> DiscountPercent = new Variable<double>  
        {  
            Name = "DiscountPercent"  
        };  
  
        Variable<double> Total = new Variable<double>  
        {  
            Name = "Total"  
        };  
  
        Activity wf = new Sequence  
        {  
            Variables = { Subtotal, DiscountPercent, Total },  
            Activities =   
            {  
                new Interop  
                {  
                    ActivityType = typeof(DiscountCalculator),  
                    ActivityProperties =   
                    {  
                        { "Subtotal", new InArgument<double>(Subtotal) },  
                        { "DiscountPercentOut", new OutArgument<double>(DiscountPercent) },  
                        { "TotalOut", new OutArgument<double>(Total) }  
                    }  
                },  
                new WriteLine  
                {  
                    Text =  new InArgument<string>(env =>   
                        string.Format("Subtotal: {0:C}, Discount {1}%, Total {2:C}",   
                        Subtotal.Get(env), DiscountPercent.Get(env) * 100, Total.Get(env)))  
                }  
            }  
        };  
  
        WorkflowInvoker.Invoke(wf);  
    }  
    ```  
  
    > [!NOTE]
    >  `Subtotal`, `DiscountPercent`, e as propriedades de `Total` de atividade de `DiscountCalculator` são surgidos como argumentos de atividade de <xref:System.Activities.Statements.Interop> , e limite a variáveis locais de fluxo de trabalho na coleção de <xref:System.Activities.Statements.Interop> de atividade de <xref:System.Activities.Statements.Interop.ActivityProperties%2A> . `Subtotal` é adicionado como um argumento de <xref:System.Activities.ArgumentDirection.In> porque os fluxos de dados de `Subtotal` na atividade de <xref:System.Activities.Statements.Interop> , e `DiscountPercent` e `Total` são adicionados como argumentos de <xref:System.Activities.ArgumentDirection.Out> porque os fluxos de dados fora de atividade de <xref:System.Activities.Statements.Interop> . Observe que os dois argumentos de <xref:System.Activities.ArgumentDirection.Out> são acrescentados com os nomes `DiscountPercentOut` e `TotalOut` para indicar que representam argumentos de <xref:System.Activities.ArgumentDirection.Out> . O tipo de `DiscountCalculator` é especificado como <xref:System.Activities.Statements.Interop>de atividade de <xref:System.Activities.Statements.Interop.ActivityType%2A> .  
  
5.  Pressione CTRL+F5 para compilar e executar o aplicativo. Substitua valores diferentes para o valor de `Subtotal` para testar para fora os diferentes níveis de desconto fornecidos pela atividade de `DiscountCalculator` .  
  
    ```csharp  
    Variable<double> Subtotal = new Variable<double>  
    {  
        Default = 75.99, // Change this value.  
        Name = "Subtotal"  
    };  
    ```  
  
### <a name="using-the-interop-activity-in-the-workflow-designer"></a>Usando a atividade de Interoperabilidade em Designer de Fluxo de Trabalho  
 Nesse exemplo, um trabalho são criados usando o designer de trabalho. Este fluxo de trabalho tem a mesma funcionalidade que o exemplo anterior, a não ser que o que em vez de usar uma atividade de <xref:System.Activities.Statements.WriteLine> para exibir o desconto, o aplicativo host recupere e exibe informações de desconto quando o fluxo de trabalho completa. Além disso, em vez de usar variáveis locais de fluxo de trabalho para conter os dados, os argumentos são criados no designer de fluxo de trabalho e os valores são passados host quando o fluxo de trabalho é chamado.  
  
##### <a name="to-host-the-policyactivity-using-a-workflow-designer-created-workflow"></a>Para hospedar o PolicyActivity que usa um trabalho Designer- criou trabalho  
  
1.  Clique com botão direito **Workflow1.xaml** na **Solution Explorer** e selecione **excluir**. Clique em **Okey** para confirmar.  
  
2.  Clique com botão direito **PolicyInteropHost** na **Solution Explorer** e selecione **adicionar**, **Novo Item...** .  
  
3.  Expanda o **itens do Visual C#** nó e selecione **fluxo de trabalho**. Selecione **atividade** do **itens do Visual C#** lista.  
  
4.  Tipo `DiscountWorkflow` para o **nome** caixa e clique em **adicionar**.  
  
5.  Clique o **argumentos** botão no lado inferior esquerdo do designer de fluxo de trabalho para exibir o **argumentos** painel.  
  
6.  Clique em **criar argumento**.  
  
7.  Tipo `Subtotal` no **nome** caixa, selecione **na** do **direção** lista suspensa, selecione **duplo** da **Tipo de argumento** lista suspensa e, em seguida, pressione ENTER para salvar o argumento.  
  
    > [!NOTE]
    >  Se **duplo** não está no **tipo de argumento** lista suspensa, selecione **procurar tipos...** , tipo `System.Double` no **nome do tipo** caixa e clique em **Okey**.  
  
8.  Clique em **criar argumento**.  
  
9. Tipo `DiscountPercent` no **nome** caixa, selecione **Out** do **direção** lista suspensa, selecione **duplo** da **Tipo de argumento** lista suspensa e, em seguida, pressione ENTER para salvar o argumento.  
  
10. Clique em **criar argumento**.  
  
11. Tipo `Total` no **nome** caixa, selecione **Out** do **direção** lista suspensa, selecione **duplo** da **Tipo de argumento** lista suspensa e, em seguida, pressione ENTER para salvar o argumento.  
  
12. Clique o **argumentos** botão no lado inferior esquerdo do designer de fluxo de trabalho para fechar o **argumentos** painel.  
  
13. Arraste um **sequência** atividade do **fluxo de controle** seção o **caixa de ferramentas** e solte-o para a superfície de designer de fluxo de trabalho.  
  
14. Arraste um **Interop** atividade do **migração** seção o **caixa de ferramentas** e solte-o no **sequência** atividade.  
  
15. Clique o **Interop** atividade no **clique para procurar...** rótulo, digite **DiscountCalculator** no **nome do tipo** caixa e clique em **Okey**.  
  
    > [!NOTE]
    >  Quando a atividade de <xref:System.Activities.Statements.Interop> é adicionada ao fluxo de trabalho e o tipo de `DiscountCalculator` é especificado como seu <xref:System.Activities.Statements.Interop.ActivityType%2A>, a atividade de <xref:System.Activities.Statements.Interop> expõe três argumentos de <xref:System.Activities.ArgumentDirection.In> e três argumentos de <xref:System.Activities.ArgumentDirection.Out> que representam as três propriedades públicas de atividade de `DiscountCalculator` . O <xref:System.Activities.ArgumentDirection.In> argumentos têm o mesmo nome que as três propriedades públicas e os três <xref:System.Activities.ArgumentDirection.Out> argumentos têm os mesmos nomes com **Out** acrescentado ao nome da propriedade. As seguintes etapas, os argumentos de fluxo de trabalho criados nas etapas anteriores são associados aos argumentos de atividade de <xref:System.Activities.Statements.Interop> .  
  
16. Tipo `DiscountPercent` para o **insira uma expressão VB** caixa à direita do **DiscountPercentOut** propriedade e pressione TAB.  
  
17. Tipo `Subtotal` para o **insira uma expressão VB** caixa à direita do **Subtotal** propriedade e pressione TAB.  
  
18. Tipo `Total` para o **insira uma expressão VB** caixa à direita do **TotalOut** propriedade e pressione TAB.  
  
19. Clique com botão direito **Program.cs** na **Solution Explorer** e selecione **Exibir código**.  
  
20. Adicione a seguinte declaração de `using` na parte superior do arquivo.  
  
    ```csharp  
    using System.Collections.Generic;  
    ```  
  
21. Comente a chamada ao método de `CalculateDiscountInCode` no método de `Main` e adicione o seguinte código.  
  
    > [!NOTE]
    >  Se você não tiver usado o procedimento anterior e o código de `Main` de opção estiver presente, substitua o conteúdo de `Main` com o código a seguir.  
  
    ```csharp  
    static void Main(string[] args)  
    {  
        CalculateDiscountUsingDesignerWorkflow();  
        //CalculateDiscountUsingCodeWorkflow();  
    }  
    ```  
  
22. Crie um novo método na classe de `Program` chamada `CalculateDiscountUsingDesignerWorkflow` que contém o código a seguir.  
  
    ```csharp  
    static void CalculateDiscountUsingDesignerWorkflow()  
    {  
        double SubtotalValue = 125.99;  
        Dictionary<string, object> wfargs = new Dictionary<string, object>  
        {  
            {"Subtotal", SubtotalValue}  
        };  
  
        Activity wf = new DiscountWorkflow();  
  
        IDictionary<string, object> outputs =  
            WorkflowInvoker.Invoke(wf, wfargs);  
  
        Console.WriteLine("Subtotal: {0:C}, Discount {1}%, Total {2:C}",  
            SubtotalValue, (double)outputs["DiscountPercent"] * 100,  
            outputs["Total"]);  
    }  
    ```  
  
23. Pressione CTRL+F5 para compilar e executar o aplicativo. Para especificar um valor diferente de `Subtotal` , altere o valor de `SubtotalValue` no código a seguir.  
  
    ```csharp  
    double SubtotalValue = 125.99; // Change this value.  
    ```  
  
## <a name="rules-features-overview"></a>Visão geral dos recursos de regras  
 O mecanismo de regras de [!INCLUDE[wf1](../../../includes/wf1-md.md)] fornece suporte para processar regras de uma maneira prioridade- base com suporte para encadear frente. As regras podem ser avaliadas para um único item ou para itens em uma coleção. Para uma visão geral das regras e de informações na funcionalidade das regras de específico, por favor consulte a tabela a seguir.  
  
|Recurso de regras|Documentação|  
|-------------------|-------------------|  
|Visão geral das regras|[Introdução ao mecanismo de regras do Windows Workflow Foundation](http://go.microsoft.com/fwlink/?LinkID=152836)|  
|RuleSet|[Usando conjuntos de regras em fluxos de trabalho](http://go.microsoft.com/fwlink/?LinkId=178516) e<xref:System.Workflow.Activities.Rules.RuleSet>|  
|Avaliação das regras|[Avaliação de regras no conjunto de regras](http://go.microsoft.com/fwlink/?LinkId=178517)|  
|Encadeamento das regras|[Controle o encadeamento de encaminhamento](http://go.microsoft.com/fwlink/?LinkId=178518) e [encadeamento de regras de encaminhamento](http://go.microsoft.com/fwlink/?LinkId=178519)|  
|Coleções de processamento nas regras|[Coleções de regras de processamento](http://go.microsoft.com/fwlink/?LinkId=178520)|  
|Usando o PolicyActivity|[Usando a atividade de PolicyActivity](http://go.microsoft.com/fwlink/?LinkId=178521) e<xref:System.Workflow.Activities.PolicyActivity>|  
  
 Fluxos de trabalho criados em [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] não usam todos os recursos de regras fornecidos por [!INCLUDE[wf1](../../../includes/wf1-md.md)], como condições declarativas de atividade e atividades condicionais como <xref:System.Workflow.Activities.ConditionedActivityGroup> e <xref:System.Workflow.Activities.ReplicatorActivity>. Se necessário, essa funcionalidade está disponível para os fluxos de trabalho criados usando [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] e [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)]. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Orientação de migração](../../../docs/framework/windows-workflow-foundation/migration-guidance.md).
