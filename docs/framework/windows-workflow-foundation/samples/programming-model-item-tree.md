---
title: Árvore modelo de programação de item
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0229efde-19ac-4bdc-a187-c6227a7bd1a5
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 497aa75214bdbbefa7f09ef56fe96926c2461ed6
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="programming-model-item-tree"></a>Árvore modelo de programação de item
Este exemplo demonstra como navegar a <xref:System.Activities.Presentation.Model.ModelItem> árvore usando associação de dados declarativo do modo de exibição de árvore do Windows Presentation Foundation (WPF).  
  
## <a name="sample-details"></a>Detalhes de exemplo  
 A árvore de <xref:System.Activities.Presentation.Model.ModelItem> é a abstração que é usada pela infraestrutura de [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)] para expor os dados sobre a instância subjacente que está sendo editada. A ilustração a seguir é uma descrição das várias camadas de infraestrutura dentro de [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)].  
  
 ![Arquitetura de Designer de fluxo de trabalho](../../../../docs/framework/windows-workflow-foundation/samples/media/workflowdesignerarch.JPG "WorkflowDesignerArch")  
  
 <xref:System.Activities.Presentation.Model.ModelItem> consiste em um ponteiro para o valor subjacente, bem como uma coleção de objetos <xref:System.Activities.Presentation.Model.ModelProperty> . Um objeto de <xref:System.Activities.Presentation.Model.ModelProperty> por sua vez, consiste dados como nome e tipo da propriedade e então um ponteiro para o valor que, por sua vez, é outro <xref:System.Activities.Presentation.Model.ModelItem>. Um conversor de valor é usado para manipular qualquer um de <xref:System.Activities.Presentation.Model.ModelItem>s retornado de <xref:System.Activities.Presentation.Model.ModelProperty> para fazê-lo aparecer corretamente no modo de exibição de árvore. O exemplo demonstra como programar em imperativa contra a árvore de <xref:System.Activities.Presentation.Model.ModelItem> usando a sintaxe imperativa, como visto no exemplo a seguir.  
  
```csharp  
ModelItem mi = wd.Context.Services.GetService<ModelService>().Root;  
ModelProperty mp = mi.Properties["Activities"];  
mp.Collection.Add(new Persist());  
ModelItem justAdded = mp.Collection.Last();  
justAdded.Properties["DisplayName"].SetValue("new name");  
```  
  
#### <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1.  Abra a solução de ProgrammingModelItemTree.sln em [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Compile a solução selecionando **compilar solução** do **criar** menu.  
  
3.  Pressione F5 para executar o aplicativo. O formulário de [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] é exibido em seguida.  
  
4.  Clique o **WF carregar** botão carregar o <xref:System.Activities.Presentation.Model.ModelItem> e associá-lo para o modo de exibição de árvore.  
  
5.  Clicando o **árvore de modelo de Item de alteração** botão executa o código anterior para adicionar um item na árvore e definir uma propriedade.  
  
> [!IMPORTANT]
>  Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\ProgrammingModelItemTree`  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Data.IValueConverter>
