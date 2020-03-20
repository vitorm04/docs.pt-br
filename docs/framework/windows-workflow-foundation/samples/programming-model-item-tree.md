---
title: Árvore modelo de programação de item
ms.date: 03/30/2017
ms.assetid: 0229efde-19ac-4bdc-a187-c6227a7bd1a5
ms.openlocfilehash: f14b140fdac95f3763cc5625841a725793876fa4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142687"
---
# <a name="programming-model-item-tree"></a>Árvore modelo de programação de item
Esta amostra demonstra como <xref:System.Activities.Presentation.Model.ModelItem> navegar na árvore usando a vinculação de dados declarativos da Visualização de Árvore da Windows Presentation Foundation (WPF).

## <a name="sample-details"></a>Detalhes de exemplo
 A <xref:System.Activities.Presentation.Model.ModelItem> árvore é a abstração usada pela infra-estrutura do Windows Workflow Designer para expor os dados sobre a instância subjacente que está sendo editada. A ilustração a seguir é uma representação das várias camadas de infra-estrutura dentro do Workflow Designer.

 ![Diagrama que mostra a arquitetura Workflow Designer.](./media/programming-model-item-tree/workflow-designer-architecture.jpg)

 <xref:System.Activities.Presentation.Model.ModelItem> consiste em um ponteiro para o valor subjacente, bem como uma coleção de objetos <xref:System.Activities.Presentation.Model.ModelProperty> . Um objeto de <xref:System.Activities.Presentation.Model.ModelProperty> por sua vez, consiste dados como nome e tipo da propriedade e então um ponteiro para o valor que, por sua vez, é outro <xref:System.Activities.Presentation.Model.ModelItem>. Um conversor de valor é usado para manipular qualquer um de <xref:System.Activities.Presentation.Model.ModelItem>s retornado de <xref:System.Activities.Presentation.Model.ModelProperty> para fazê-lo aparecer corretamente no modo de exibição de árvore. O exemplo demonstra como programar em imperativa contra a árvore de <xref:System.Activities.Presentation.Model.ModelItem> usando a sintaxe imperativa, como visto no exemplo a seguir.

```csharp
ModelItem mi = wd.Context.Services.GetService<ModelService>().Root;
ModelProperty mp = mi.Properties["Activities"];
mp.Collection.Add(new Persist());
ModelItem justAdded = mp.Collection.Last();
justAdded.Properties["DisplayName"].SetValue("new name");
```

#### <a name="to-use-this-sample"></a>Para usar este exemplo

1. Abra a solução ProgrammingModelItemTree.sln no Visual Studio 2010.

2. Construa a solução selecionando **Build Solution** no menu **Build.**

3. Pressione F5 para executar o aplicativo. Em seguida, o formulário WPF é exibido.

4. Clique no botão **Load** <xref:System.Activities.Presentation.Model.ModelItem> WF para carregar o e amarrá-lo à exibição da árvore.

5. Clicar no botão **Alterar modelo árvore de itens** executa o código anterior para adicionar um item na árvore e definir uma propriedade.

> [!IMPORTANT]
> Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\ProgrammingModelItemTree`  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Data.IValueConverter>
