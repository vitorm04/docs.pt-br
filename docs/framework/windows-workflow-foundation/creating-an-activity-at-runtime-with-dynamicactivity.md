---
title: "Criando uma atividade em tempo de execução com o DynamicActivity"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1af85cc6-912d-449e-90c5-c5db3eca5ace
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d40fe3601cb8ad7c4f77cf50825da1deace5644e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="creating-an-activity-at-runtime-with-dynamicactivity"></a>Criando uma atividade em tempo de execução com o DynamicActivity
<xref:System.Activities.DynamicActivity> é um concreto, classe lacradas com um construtor público. <xref:System.Activities.DynamicActivity> pode ser usado para reunir a funcionalidade de atividade em tempo de execução usando os DOM de uma atividade.  
  
## <a name="dynamicactivity-features"></a>Recursos de DynamicActivity  
 <xref:System.Activities.DynamicActivity> tem acesso às propriedades de execução, os argumentos e variáveis, mas nenhum o acesso aos serviços de tempo de execução como atividades filhos de programação ou o rastreamento.  
  
 As propriedades de nível superior podem ser definidas usando objetos de <xref:System.Activities.Argument> de fluxo de trabalho. No código obrigatório, esses argumentos são criados usando propriedades de CLR em um novo tipo. Em XAML, são declarados usando `x:Class` e marcas de `x:Member` .  
  
 Atividades construídas usando a interface de <xref:System.Activities.DynamicActivity> com o designer que usa <xref:System.ComponentModel.ICustomTypeDescriptor>. As atividades criadas no designer podem ser carregadas dinamicamente usando <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A>, como demonstrado no procedimento a seguir.  
  
#### <a name="to-create-an-activity-at-runtime-using-imperative-code"></a>Para criar uma atividade em tempo de execução usando o código obrigatório  
  
1.  Abra[!INCLUDE[vs2010](../../../includes/vs2010-md.md)].  
  
2.  Selecione **arquivo**, **novo**, **projeto**. Selecione **Workflow 4.0** em **Visual C#** no **tipos de projeto** janela e selecione o **v2010** nó. Selecione **aplicativo de Console de fluxo de trabalho sequencial** no **modelos** janela. Nomeie o novo projeto DynamicActivitySample.  
  
3.  Workflow1.xaml no projeto HelloActivity e selecione **excluir**.  
  
4.  Abra Module.vb. Adicione a seguinte diretiva para a parte superior do arquivo.  
  
    ```  
    using System.Collections.Generic;  
    ```  
  
5.  Substitua o conteúdo do método de `Main` com o código a seguir, que cria uma atividade de <xref:System.Activities.Statements.Sequence> que contém uma única atividade de <xref:System.Activities.Statements.WriteLine> e a atribui à propriedade de <xref:System.Activities.DynamicActivity.Implementation%2A> de uma nova atividade dinâmico.  
  
    ```csharp  
    //Define the input argument for the activity  
    var textOut = new InArgument<string>();  
    //Create the activity, property, and implementation  
                Activity dynamicWorkflow = new DynamicActivity()  
                {  
                    Properties =   
                    {  
                        new DynamicActivityProperty  
                        {  
                            Name = "Text",  
                            Type = typeof(InArgument<String>),  
                            Value = textOut  
                        }  
                    },  
                    Implementation = () => new Sequence()  
                    {  
                        Activities =   
                        {  
                            new WriteLine()  
                            {  
                                Text = new InArgument<string>(env => textOut.Get(env))  
                            }  
                        }  
                    }  
                };  
    //Execute the activity with a parameter dictionary  
                WorkflowInvoker.Invoke(dynamicWorkflow, new Dictionary<string, object> { { "Text", "Hello World!" } });  
                Console.ReadLine();  
    ```  
  
6.  Executar o aplicativo. Uma janela de console com o texto "Olá, mundo!" Exibe.  
  
#### <a name="to-create-an-activity-at-runtime-using-xaml"></a>Para criar uma atividade em tempo de execução usando XAML  
  
1.  Abra [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].  
  
2.  Selecione **arquivo**, **novo**, **projeto**. Selecione **Workflow 4.0** em **Visual C#** no **tipos de projeto** janela e selecione o **v2010** nó. Selecione **aplicativo de Console do fluxo de trabalho** no **modelos** janela. Nomeie o novo projeto DynamicActivitySample.  
  
3.  Workflow1.xaml aberto no projeto de HelloActivity. Clique o **argumentos** opção na parte inferior do designer. Crie um novo argumento de `In` chamado `TextToWrite` de tipo `String`.  
  
4.  Arraste um **WriteLine** atividade a partir de **primitivos** seção da caixa de ferramentas para a superfície de designer. Atribuir o valor `TextToWrite` para o **texto** propriedade da atividade.  
  
5.  Abra Module.vb. Adicione a seguinte diretiva para a parte superior do arquivo.  
  
    ```  
    using System.Activities.XamlIntegration;  
    ```  
  
6.  Substitua o conteúdo do método de `Main` com o código a seguir.  
  
    ```  
    Activity act2 = ActivityXamlServices.Load(@"Workflow1.xaml");  
                    results = WorkflowInvoker.Invoke(act2, new Dictionary<string, object> { { "TextToWrite", "HelloWorld!" } });  
    Console.ReadLine();  
    ```  
  
7.  Executar o aplicativo. Uma janela de console com o texto "Olá, mundo!" é exibida.  
  
8.  Clique no arquivo Workflow1.xaml no **Solution Explorer** e selecione **Exibir código**. Observe que a classe da atividade é criada com `x:Class` e a propriedade é criada com `x:Property`.  
  
## <a name="see-also"></a>Consulte também  
 [Criando fluxos de trabalho, atividades e expressões de design usando o código obrigatório](../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md)  
 [Criação de DynamicActivity](../../../docs/framework/windows-workflow-foundation/samples/dynamicactivity-creation.md)
