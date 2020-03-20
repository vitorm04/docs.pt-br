---
title: Criando uma atividade em runtime com o DynamicActivity
ms.date: 03/30/2017
ms.assetid: 1af85cc6-912d-449e-90c5-c5db3eca5ace
ms.openlocfilehash: 871108fd09e9127b3f9e06174f05a47c7fd7682c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182985"
---
# <a name="creating-an-activity-at-runtime-with-dynamicactivity"></a>Criando uma atividade em runtime com o DynamicActivity
<xref:System.Activities.DynamicActivity> é um concreto, classe lacradas com um construtor público. <xref:System.Activities.DynamicActivity> pode ser usado para reunir a funcionalidade de atividade em runtime usando os DOM de uma atividade.  
  
## <a name="dynamicactivity-features"></a>Recursos de DynamicActivity  
 <xref:System.Activities.DynamicActivity> tem acesso às propriedades de execução, os argumentos e variáveis, mas nenhum o acesso aos serviços de tempo de execução como atividades filhos de programação ou o rastreamento.  
  
 As propriedades de nível superior podem ser definidas usando objetos de <xref:System.Activities.Argument> de fluxo de trabalho. No código obrigatório, esses argumentos são criados usando propriedades de CLR em um novo tipo. Em XAML, são declarados usando `x:Class` e marcas de `x:Member` .  
  
 Atividades construídas usando a interface de <xref:System.Activities.DynamicActivity> com o designer que usa <xref:System.ComponentModel.ICustomTypeDescriptor>. As atividades criadas no designer podem ser carregadas dinamicamente usando <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A>, como demonstrado no procedimento a seguir.  
  
#### <a name="to-create-an-activity-at-runtime-using-imperative-code"></a>Para criar uma atividade em runtime usando o código obrigatório  
  
1. OpenVisual Studio 2010.  
  
2. Selecione **Arquivo,** **Novo,** **Projeto**. Selecione **Workflow 4.0** em **Visual C#** na janela **Tipos de projeto** e selecione o nó **v2010.** Selecione **aplicativo de console de fluxo de trabalho seqüencial** na janela **Modelos.** Nomeie o novo projeto DynamicActivitySample.  
  
3. Clique com o botão direito do mouse Workflow1.xaml no projeto HelloActivity e **selecione Excluir**.  
  
4. Abra Program.cs. Adicione a seguinte diretiva para a parte superior do arquivo.  
  
    ```csharp  
    using System.Collections.Generic;  
    ```  
  
5. Substitua o conteúdo do método de `Main` com o código a seguir, que cria uma atividade de <xref:System.Activities.Statements.Sequence> que contém uma única atividade de <xref:System.Activities.Statements.WriteLine> e a atribui à propriedade de <xref:System.Activities.DynamicActivity.Implementation%2A> de uma nova atividade dinâmico.  
  
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
  
6. Execute o aplicativo. Uma janela de console com o texto "Hello World!" Exibe.  
  
#### <a name="to-create-an-activity-at-runtime-using-xaml"></a>Para criar uma atividade em runtime usando XAML  
  
1. Open Visual Studio 2010.  
  
2. Selecione **Arquivo,** **Novo,** **Projeto**. Selecione **Workflow 4.0** em **Visual C#** na janela **Tipos de projeto** e selecione o nó **v2010.** Selecione **O aplicativo do console de fluxo de trabalho** na janela **Modelos.** Nomeie o novo projeto DynamicActivitySample.  
  
3. Workflow1.xaml aberto no projeto de HelloActivity. Clique na opção **Argumentos** na parte inferior do designer. Crie um novo argumento de `In` chamado `TextToWrite` de tipo `String`.  
  
4. Arraste uma atividade **WriteLine** da seção **Primitivos** da caixa de ferramentas para a superfície do designer. Atribuir o `TextToWrite` valor à propriedade **Texto** da atividade.  
  
5. Abra Program.cs. Adicione a seguinte diretiva para a parte superior do arquivo.  
  
    ```csharp  
    using System.Activities.XamlIntegration;  
    ```  
  
6. Substitua o conteúdo do método de `Main` com o código a seguir.  
  
    ```csharp  
    Activity act2 = ActivityXamlServices.Load(@"Workflow1.xaml");  
                    results = WorkflowInvoker.Invoke(act2, new Dictionary<string, object> { { "TextToWrite", "HelloWorld!" } });  
    Console.ReadLine();  
    ```  
  
7. Execute o aplicativo. Uma janela de console com o texto "Hello World!"  é exibido.  
  
8. Clique com o botão direito do mouse no arquivo Workflow1.xaml no **Solution Explorer** e selecione **'Exibir código '**. Observe que a classe da atividade é criada com `x:Class` e a propriedade é criada com `x:Property`.  
  
## <a name="see-also"></a>Confira também

- [Criando fluxos de trabalho, atividades e expressões de design usando o código obrigatório](authoring-workflows-activities-and-expressions-using-imperative-code.md)
