---
title: "Criação de atividade de fluxo de trabalho usando a classe de CodeActivity"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cfe315c1-f86d-43ec-b9ce-2f8c469b1106
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2daec260c1224cd81280c6bf699b70efc2072588
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="workflow-activity-authoring-using-the-codeactivity-class"></a>Criação de atividade de fluxo de trabalho usando a classe de CodeActivity
As atividades criadas por herança de <xref:System.Activities.CodeActivity> podem implementar o comportamento básico obrigatório substituindo o método de <xref:System.Activities.CodeActivity.Execute%2A> .  
  
## <a name="using-codeactivitycontext"></a>Usando CodeActivityContext  
 Recursos de tempo de execução de fluxo de trabalho podem ser acessados de dentro do método de <xref:System.Activities.CodeActivity.Execute%2A> usando membros de parâmetro de `context` , do tipo <xref:System.Activities.CodeActivityContext>. Os recursos <xref:System.Activities.CodeActivityContext> direto disponível incluem o seguinte:  
  
-   Definindo e obtendo os valores das variáveis e os argumentos.  
  
-   Recursos personalizados de rastreamento que usam <xref:System.Activities.CodeActivityContext.Track%2A>.  
  
-   Acesso às propriedades de execução da atividade usando <xref:System.Activities.CodeActivityContext.GetProperty%2A>.  
  
#### <a name="to-create-a-custom-activity-that-inherits-from-codeactivity"></a>Para criar uma atividade personalizado que herda de CodeActivity  
  
1.  Abra[!INCLUDE[vs2010](../../../includes/vs2010-md.md)].  
  
2.  Selecione **arquivo**, **novo**e, em seguida, **projeto**. Selecione **Workflow 4.0** em **Visual C#** no **tipos de projeto** janela e selecione o **v2010** nó. Selecione **biblioteca de atividades** no **modelos** janela. Nomeie o novo projeto HelloActivity.  
  
3.  Activity1 no projeto HelloActivity e selecione **excluir**.  
  
4.  O projeto HelloActivity e selecione **adicionar** e, em seguida, **classe**. Nomeie a nova classe HelloActivity.cs.  
  
5.  No arquivo de HelloActivity.cs, adicione as seguintes diretivas de `using` .  
  
    ```csharp  
    using System.Activities;  
    using System.Activities.Statements;  
    ```  
  
6.  Faça a nova classe herdar de <xref:System.Activities.CodeActivity> adicionando uma classe base para a declaração de classe.  
  
    ```csharp  
    class HelloActivity : CodeActivity  
    ```  
  
7.  Adicionar funcionalidade à classe adicionando um método de <xref:System.Activities.CodeActivity.Execute%2A> .  
  
    ```csharp  
    protected override void Execute(CodeActivityContext context)  
    {  
        Console.WriteLine("Hello World!");  
    }  
    ```  
  
8.  Use <xref:System.Activities.CodeActivityContext> para criar um registro de rastreamento.  
  
    ```csharp  
    protected override void Execute(CodeActivityContext context)  
    {  
        Console.WriteLine("Hello World!");  
        CustomTrackingRecord record = new CustomTrackingRecord("MyRecord");  
        record.Data.Add(new KeyValuePair<String, Object>("ExecutionTime", DateTime.Now));  
        context.Track(record);  
    }  
    ```
