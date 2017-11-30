---
title: Usando a atividade de InvokePowerShell
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 956251a0-31ca-4183-bf76-d277c08585df
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5ea3106f87dae64204ea0c02a1388ed8893c858b
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/28/2017
---
# <a name="using-the-invokepowershell-activity"></a>Usando a atividade de InvokePowerShell
O exemplo de InvokePowerShell demonstra como chamar comandos do Windows PowerShell que usam a atividade de `InvokePowerShell` .  
  
## <a name="demonstrates"></a>Demonstra  
  
-   Inovação simples de comandos do Windows PowerShell.  
  
-   Recuperar valores do canal de saída do Windows PowerShell e armazená-las em variáveis de fluxo de trabalho.  
  
-   Passar dados em janelas PowerShell como o pipeline de entrada para um comando executando.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\PowerShell`  
  
## <a name="discussion"></a>Discussão  
 Este exemplo contém os três projetos.  
  
|Nome do projeto|Descrição|Arquivos de chave|  
|------------------|-----------------|----------------|  
|CodedClient|Um aplicativo cliente de exemplo que use a atividade de PowerShell.|-   **Program.CS**: cria programaticamente um sequência de fluxo de trabalho que chama a atividade de InvokePowerShell.|  
|DesignerClient|Um conjunto de atividades personalizados que contêm a atividade personalizado de `InvokePowerShell` e outras atividades personalizados diversos, e um fluxo de trabalho que os usa.|<ul><li>Atividades:<br /><br /> <ul><li>**PrintCollection.cs**: uma atividade de auxiliar que imprime todos os itens em uma coleção para o console.</li><li>**ReadLine.cs**: uma atividade de auxiliar para leitura de entrada do console.</li></ul></li><li>O sistema de arquivos:<br /><br /> <ul><li>**Copy.XAML**: uma atividade que copia um arquivo.</li><li>**CreateFile.xaml**: uma atividade que cria um arquivo.</li><li>**DeleteFile.xaml**: uma atividade que exclui um arquivo.</li><li>**MakeDir.xaml**: uma atividade que cria um diretório.</li><li>**Move.XAML**: uma atividade que move um arquivo.</li><li>**ReadFile.xaml**: uma atividade que lê um arquivo e retorna seu conteúdo.</li><li>**TestPath.xaml**: uma atividade que verifica a existência de um caminho.</li></ul></li><li>Processo:<br /><br /> <ul><li>**GetProcess.xaml**: uma atividade que obtém uma lista de processos em execução.</li><li>**StopProcess.xaml**: uma atividade que impede que um processo específico.</li></ul></li><li>**Program.CS**: chama o fluxo de trabalho Sequence1.</li><li>**Sequence1.XAML**: um fluxo de trabalho com base em sequência.</li></ul>|  
|PowerShell|A atividade de `InvokePowerShell` e seus criadores associados.|Arquivos de atividade<br /><br /> -   **ExecutePowerShell.cs**: lógica de execução principal da atividade.<br />-   **InvokePowerShell.cs**: O wrapper em torno de lógica de execução principal, que contém uma versão genérica (valor de retorno) e uma versão não genérico (valor de retorno não). Esta é a interface pública para atividades.<br />-   **NoPersistZone.cs**: esta atividade impede que todas as atividades filho persistentes. Essa classe é usada dentro da implementação de atividade de `InvokePowerShell` para impedir que a atividade é mid de- execução persistentes.<br /><br /> Arquivos de designer:<br /><br /> 1.  **ArgumentDictionaryEditor.cs**: caixa de diálogo de um Windows que permite que o usuário edite os argumentos do `InvokePowerShell` atividade.<br />2.  **GenericInvokePowerShellDesigner.xaml** e **GenericInvokePowerShellDesigner.xaml.cs**: define a aparência de genérica `InvokePowerShell` atividade em [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)].<br />3.  **InvokePowerShellDesigner.xaml** e **InvokePowerShellDesigner.cs**: define a aparência de não-genérica `InvokePowerShell` atividade em [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)].|  
  
 Projetos de cliente são discutidos primeiro, pois é mais fácil compreender que a funcionalidade interna de atividade de PowerShell seu uso é compreendido uma vez.  
  
## <a name="using-this-sample"></a>Usando este exemplo  
 As seguintes seções descrevem como usar os três projetos no exemplo.  
  
### <a name="using-the-coded-client-project"></a>Usando o cliente codificado Projeto  
 O cliente de exemplo cria programaticamente uma atividade de sequência, que contém exemplos de vários métodos diferentes de usar a atividade de `InvokePowerShell` . A primeira chamada inicia o Bloco De Notas.  
  
```  
new InvokePowerShell()  
{  
    CommandText = "notepad"  
},  
```  
  
 A segunda chamada obter uma lista dos processos em execução no computador local.  
  
```  
new InvokePowerShell<Process>()  
{  
    CommandText = "Get-Process",  
    Output = processes1,  
},  
```  
  
 `Output` é a variável usada para armazenar a saída do comando.  
  
 A chamada a seguir demonstra como reproduzir uma etapa de pré processamento em cada saída individuais de chamada de PowerShell. `InitializationAction` é definido para a função essa saída uma representação de cadeia de caracteres para cada processo. A coleção dessas cadeias de caracteres é retornada na variável de `Output` pela atividade de `InvokePowerShell<string>` .  
  
 Chamadas de sucesso de `InvokePowerShell` demonstram passar dados na atividade e obter saída e erros para fora.  
  
### <a name="using-the-designer-client-project"></a>Usando o cliente do Project designer  
 O projeto de DesignerClient consiste em um conjunto de atividades personalizados, quase que são compiladas que contêm a atividade de `InvokePowerShell` . A maioria das atividades chamam a versão não genérico de atividade de `InvokePowerShell` , e não espera um valor de retorno. Outras atividades usam a versão genérica de atividade de `InvokePowerShell` , e usam após o processo de argumento de `InitializationAction` os resultados.  
  
## <a name="using-the-powershell-project"></a>Usando PowerShell Projeto  
 A ação principal da atividade ocorre na classe de `ExecutePowerShell` . Porque a execução de comandos de PowerShell não deve bloquear o segmento principal de fluxo de trabalho, a atividade é projetado para ser uma atividade assíncrono herança da classe de <xref:System.Activities.AsyncCodeActivity> .  
  
 O método de <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> é chamado em tempo de execução de fluxo de trabalho para iniciar a execução da atividade. Inicia chamando APIs de PowerShell para criar um pipeline de PowerShell.  
  
```  
runspace = RunspaceFactory.CreateRunspace();  
runspace.Open();  
pipeline = runspace.CreatePipeline();  
```  
  
 Então cria um comando de PowerShell e preenchê-los com parâmetros e variáveis.  
  
```  
Command cmd = new Command(this.CommandText, this.IsScript);   
// loop over parameters and run: cmd.Parameters.Add(...)  
// loop over variables and run: runspace.SessionStateProxy.SetVariable(...)  
pipeline.Commands.Add(cmd);  
```  
  
 Entradas corretamente em também são enviados ao pipeline no momento. Finalmente, a pipeline é empacotada em um objeto de `PipelineInvokerAsyncResult` e retornada. O objeto de `PipelineInvokerAsyncResult` registra um ouvinte e chama o pipeline.  
  
```  
pipeline.InvokeAsync();  
```  
  
 Quando a execução for concluído, a saída e erros são armazenados no mesmo objeto de `PipelineInvokerAsyncResult` , e o controle é entregado de volta para o tempo de execução de fluxo de trabalho chamando o método de retorno originalmente passado <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A>.  
  
 No final da execução do método, o tempo de execução de fluxo de trabalho chama o método de <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> de atividade.  
  
 A classe de `InvokePowerShell` envolve a classe de `ExecutePowerShellCommand` e cria duas versões de atividade; uma versão genérica e não uma versão genérica. A versão não genérico retorna a saída de execução de PowerShell diretamente, enquanto a versão genérica transforma os resultados individuais para o tipo genérico.  
  
 A versão genérica da atividade é implementada como um fluxo de trabalho sequencial que chama `ExecutePowerShellCommand` e posteriores processos seus resultados. Para cada elemento na coleção de resultado, a etapa de pré processamento chama `InitializationAction` se é definida. Se não, fazer uma conversão simples.  
  
```  
new ForEach<PSObject>  
{  
    Values = psObjects,  
    Body = new ActivityAction<PSObject>  
    {  
        Argument = psObject,  
        Handler = new Sequence  
        {  
            Activities =  
            {  
                new If  
                {  
                    Condition = // Is InitializationAction set?  
                    Then = new InvokeFunc<PSObject, TResult>  
                    {  
                        Argument = psObject,  
                        Result = outputObject,  
                        Func = this.InitializationAction  
                    },  
                    Else = new Assign<TResult>  
                    {  
                        To = outputObject,  
                        Value = new InArgument<TResult>(ctx => (TResult) psObject.Get(ctx).BaseObject),  
                    }  
                },  
                new AddToCollection<TResult>  
                {  
                    Collection = outputObjects,  
                    Item = outputObject  
                },  
            }  
        }  
    }  
},  
```  
  
 Para cada uma das duas atividades de `InvokePowerShell` (genéricos, e não genéricas), um designer foi criado. InvokePowerShellDesigner.xaml e seu arquivo associado .cs definem a aparência em [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)] para a versão não genérico de atividade de `InvokePowerShell` . Dentro de InvokePowerShellDesigner.xaml, <xref:System.Windows.Controls.DockPanel> é usado para representar a interface gráfica.  
  
```  
<DockPanel x:Uid="DockPanel_1" LastChildFill="True">  
        <TextBlock x:Uid="TextBlock_1" Text="CommandText" />  
        <TextBox x:Uid="TextBox_1" Text="{Binding Path=ModelItem.CommandText, Mode=TwoWay}"  
                 TextWrapping="WrapWithOverflow"  AcceptsReturn="True" MinLines="4" MaxLines="4"  
                 Background="{x:Null}" Margin="3" />  
    </DockPanel>  
```  
  
 Observe que a propriedade de `Text` da caixa de texto é uma associação bidirecional que garante que o valor da propriedade de `CommandText` da atividade é equivalente ao valor conectado no designer.  
  
 GenericInvokePowerShellDesigner.xaml e seu arquivo associado .cs definem a interface gráfica para atividades genérica de `InvokePowerShell` . O designer é ligeiramente mais complicado porque ela permite que os usuários definir `InitializationAction`. O elemento chave é o uso de <xref:System.Activities.Presentation.WorkflowItemPresenter> para permitir ao arrastar e soltar de atividades filhos na superfície do designer de `InvokePowerShell` .  
  
```  
<sap:WorkflowItemPresenter x:Uid="sap:WorkflowItemPresenter_1" Margin="0,10,0,10"  
    HintText="Drop Activities Here"  
    AllowedItemType="{x:Type sa:Activity}"  
    Item="{Binding Path=ModelItem.InitializationAction.Handler, Mode=TwoWay}"  
    Grid.Row="1" Grid.Column="1" />  
```  
  
 A personalização do designer não para com os arquivos .xaml que definem a aparência da atividade na tela de design. As caixas de diálogo usadas para exibir os parâmetros da atividade também podem ser personalizadas. Esses parâmetros e variáveis de PowerShell afetam o comportamento de comandos de PowerShell. A atividade expõe como <!--zz <xref:System.Collections.Generic.Dictionary%601>--> `System.Collections.Generic.Dictionary` tipos. ArgumentDictionaryEditor.cs, PropertyEditorResources.xaml e PropertyEditorResources.cs definem a caixa de diálogo que permite que você edite esses tipos.  
  
## <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
 Você deve instalar o Windows PowerShell para executar esse exemplo. O Windows PowerShell pode ser instalado neste local: [do Windows PowerShell](http://go.microsoft.com/fwlink/?LinkId=150383).  
  
#### <a name="to-run-the-coded-client"></a>Para executar o cliente codificado  
  
1.  PowerShell.sln aberto usando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Clique com o botão direito do mouse na solução e construa-a.  
  
3.  Clique com botão direito do **CodedClient** do projeto e selecione **definir como projeto de inicialização**.  
  
4.  Pressione CTRL+F5 para executar o aplicativo.  
  
#### <a name="to-run-the-designer-client"></a>Para executar o cliente de designer  
  
1.  PowerShell.sln aberto usando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Clique com o botão direito do mouse na solução e construa-a.  
  
3.  Clique com botão direito do **DesignerClient** do projeto e selecione **definir como projeto de inicialização**.  
  
4.  Pressione CTRL+F5 para executar o aplicativo.  
  
## <a name="known-issues"></a>Problemas conhecidos  
  
1.  Se fazer referência ao assembly ou projeto de atividade de `InvokePowerShell` de outro projeto resulta em um erro de compilação, você precisará adicionar manualmente o elemento de `<SpecificVersion>True</SpecificVersion>` o arquivo .csproj o novo projeto na linha que referencia `InvokePowerShell`.  
  
2.  Se o Windows PowerShell não estiver instalado, a seguinte mensagem de erro é exibida no Visual Studio assim que você adicionar um `InvokePowerShell` atividade em um fluxo de trabalho:`Workflow Designer encountered problems with your document. Could not load file or assembly ‘System.Management.Automation’ ... or one of its dependencies. The system cannot find the file specified.`  
  
3.  No Windows 2.0, PowerShell programaticamente chamando `$input.MoveNext()` falha e scripts usando o produto de `$input.MoveNext()` erros não intencional e resultados. Para resolver esse problema, considere usar o verbo `foreach` de PowerShell em vez de chamar `MoveNext()` para percorrer uma matriz.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\PowerShell`