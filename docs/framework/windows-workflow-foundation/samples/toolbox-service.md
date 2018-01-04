---
title: "Serviço da caixa de ferramentas"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 742212d0-445e-41ed-9739-9ee848ce7f1b
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b800f2d250a918ea2b6c49b121c4ca9040b20631
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="toolbox-service"></a>Serviço da caixa de ferramentas
Este exemplo demonstra como atualizar as atividades da caixa de ferramentas de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] com base no contexto de fluxo de trabalho. O exemplo contém um fluxo de trabalho que modifica o conteúdo da caixa de ferramentas com base em se uma atividade personalizado está selecionada.  
  
## <a name="discussion"></a>Discussão  
 Durante a criação de fluxo de trabalho, os clientes desejam geralmente a caixa de ferramentas para ser contextuais. Por exemplo, o usuário pode querer para garantir que a caixa de ferramentas mostra algumas atividades adicionais quando uma atividade específica é adicionada ao fluxo de trabalho. Se as atividades são removidas de fluxo de trabalho, a caixa de ferramentas deve reagir adequadamente com base nos requisitos do domínio.  
  
 Em um designer novamente hospedado de fluxo de trabalho, você controla o controle de caixa de ferramentas e pode garantir que com base nas alterações no modelo fluxo de trabalho, o host que os disparadores exibe alterações no controle de caixa de ferramentas. No entanto, em [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], a caixa de ferramentas não é controlada pelo usuário e uma interface é necessária para modificar seu conteúdo. `IActivityToolboxService` é a interface.  
  
 API fornece os quatro métodos.  
  
```  
public interface IActivityToolboxService   
{   
        void AddCategory(string categoryName);   
        void RemoveCategory(string categoryName);   
        void AddItem(string qualifiedTypeName, string categoryName);   
        void RemoveItem(string qualifiedTypeName, string categoryName);   
        IList<string> EnumCategories();   
        IList<string> EnumItems(string categoryName);   
}  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Usando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], abra o arquivo de solução de WorkflowSimulator.sln.  
  
2.  Crie a solução. CTRL+SHIFT+B pressionando.  
  
3.  Abra o arquivo de Workflow.xaml.  
  
4.  Adicionar um **CustomActivity** arrastando e soltando-o na caixa de ferramentas. Observe que a chamada de uma categoria de caixa de ferramentas adicional: **nova categoria de WF** com uma atividade adicional **atribuir**.  
  
5.  Desmarque agora o **CustomActivity** arrastando outra atividade nela.  
  
6.  O item **atribuir** na categoria **nova categoria de WF** na caixa de ferramentas é removido. Além disso, porque não há mais item deixado na categoria, a categoria é removida também.  
  
7.  Selecione o **CustomActivity** novamente e a categoria e **atribuir** atividade é adicionada novamente.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\IActivityToolboxService`
