---
title: Classe base de NativeActivity
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 254a4c50-425b-426d-a32f-0f7234925bac
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5f5a925aa9fc14c370c50ab0877742b207461c1d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="nativeactivity-base-class"></a>Classe base de NativeActivity
<xref:System.Activities.NativeActivity> é uma classe abstrata com um construtor protegido. Como <xref:System.Activities.CodeActivity>, <xref:System.Activities.NativeActivity> é usado para gravar o comportamento obrigatório implementando um método de <xref:System.Activities.NativeActivity.Execute%2A> . Ao contrário de <xref:System.Activities.CodeActivity>, <xref:System.Activities.NativeActivity> tem acesso a todos os recursos expostos em tempo de execução do fluxo de trabalho através do objeto de <xref:System.Activities.NativeActivityContext> passado para o método de <xref:System.Activities.NativeActivity.Execute%2A> .  
  
## <a name="using-nativeactivitycontext"></a>Usando NativeActivityContext  
 Recursos de tempo de execução de fluxo de trabalho podem ser acessados de dentro do método de <xref:System.Activities.NativeActivity.Execute%2A> usando membros de parâmetro de `context` , do tipo <xref:System.Activities.NativeActivityContext>. Os recursos <xref:System.Activities.NativeActivityContext> direto disponível incluem o seguinte:  
  
-   Obter e definir os argumentos e variáveis.  
  
-   Atividades filhos de programação com <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A>  
  
-   Anulando a execução da atividade usando <xref:System.Activities.NativeActivityContext.Abort%2A>.  
  
-   Cancelando a execução filho usando <xref:System.Activities.NativeActivityContext.CancelChild%2A> e <xref:System.Activities.NativeActivityContext.CancelChildren%2A>.  
  
-   Acesso aos indicadores de atividade usando métodos como <xref:System.Activities.NativeActivityContext.CreateBookmark%2A>, <xref:System.Activities.NativeActivityContext.RemoveBookmark%2A>, e <xref:System.Activities.NativeActivityContext.ResumeBookmark%2A>.  
  
-   Recursos personalizados de rastreamento que usam <xref:System.Activities.CodeActivityContext.Track%2A>.  
  
-   Acesso às propriedades de execução da atividade e propriedades de valor usando <xref:System.Activities.CodeActivityContext.GetProperty%2A> e <xref:System.Activities.NativeActivityContext.GetValue%2A>.  
  
-   Ações e funções de atividade de programação usando o <xref:System.Activities.NativeActivityContext.ScheduleAction%2A> e o <xref:System.Activities.NativeActivityContext.ScheduleFunc%2A>.  
  
#### <a name="to-create-a-custom-activity-that-inherits-from-nativeactivity"></a>Para criar uma atividade personalizado que herda de NativeActivity  
  
1.  Abra[!INCLUDE[vs2010](../../../includes/vs2010-md.md)].  
  
2.  Selecione **arquivo**, **novo**e, em seguida, **projeto**. Selecione **Workflow 4.0** em **Visual C#** no **tipos de projeto** janela e selecione o **v2010** nó. Selecione **biblioteca de atividades** no **modelos** janela. Nomeie o novo projeto HelloActivity.  
  
3.  Activity1 no projeto HelloActivity e selecione **excluir**.  
  
4.  O projeto HelloActivity e selecione **adicionar**e, em seguida, **classe**. Nomeie a nova classe HelloActivity.cs.  
  
5.  No arquivo de HelloActivity.cs, adicione as seguintes diretivas de `using` .  
  
    ```csharp  
    using System.Activities;  
    using System.Activities.Statements;  
    ```  
  
6.  Faça a nova classe herdar de <xref:System.Activities.NativeActivity> adicionando uma classe base para a declaração de classe.  
  
    ```csharp  
    class HelloActivity : NativeActivity  
    ```  
  
7.  Adicionar funcionalidade à classe adicionando um método de <xref:System.Activities.NativeActivity.Execute%2A> .  
  
    ```csharp  
    protected override void Execute(NativeActivityContext context)  
    {  
        Console.WriteLine("Hello World!");  
    }  
    ```  
  
8.  Substitua o método de <xref:System.Activities.NativeActivity.CacheMetadata%2A> e chamar o método apropriado no para permitir que o tempo de execução de fluxo de trabalho aprender sobre variáveis personalizados, os argumentos, os filhos, e os representantes de atividade. Para obter mais informações consulte a classe de <xref:System.Activities.NativeActivityMetadata> .  
  
9. Use o objeto de <xref:System.Activities.NativeActivityContext> para agendar um indexador. Consulte <xref:System.Activities.WorkflowApplicationIdleEventArgs.Bookmarks%2A> para obter detalhes sobre como criar, agendar, e retomar um indexador.  
  
    ```  
    protected override void Execute(NativeActivityContext context)  
        {  
            // Create a Bookmark and wait for it to be resumed.  
            context.CreateBookmark(BookmarkName.Get(context),   
                new BookmarkCallback(OnResumeBookmark));  
        }  
    ```
