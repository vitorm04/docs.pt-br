---
title: "Como gravar em um log de eventos do aplicativo (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/13/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Elemento Computer.EventLog"
  - "Método WriteEntry"
  - "Elemento My.Computer.EventLog"
  - "logs de eventos, gravando em"
ms.assetid: cadbc8c1-87af-4746-934e-55b79a4f6e2b
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como gravar em um log de eventos do aplicativo (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Você pode usar o `My.Application.Log` e `My.Log` objetos para gravar informações sobre eventos que ocorrem em seu aplicativo. Este exemplo mostra como configurar um ouvinte de log de eventos isso `My.Application.Log` grava informações de rastreamento para o log de eventos do aplicativo.  
  
 Você não pode gravar no log de segurança. Para gravar no log do sistema, você deve ser um membro da conta LocalSystem ou administrador.  
  
 Para exibir um log de eventos, você pode usar **Server Explorer** ou **Visualizar eventos do Windows**. Para obter mais informações, consulte [Eventos ETW no .NET Framework](../Topic/ETW%20Events%20in%20the%20.NET%20Framework.md).  
  
> [!NOTE]
>  Logs de eventos não são suportados no Windows 95, Windows 98 ou Windows Millennium Edition.  
  
### Para adicionar e configurar o ouvinte de log de eventos  
  
1.  Clique com botão direito app. config em **Solution Explorer** e escolha **Abrir**.  
  
     \- ou \-  
  
     Se não houver nenhum arquivo App. config,  
  
    1.  Sobre o **projeto** menu, escolha **Add New Item**.  
  
    2.  Do **Add New Item** caixa de diálogo, escolha **arquivo de configuração do aplicativo**.  
  
    3.  Clique em **Adicionar**.  
  
2.  Localize o `<listeners>` seção no arquivo de configuração do aplicativo.  
  
     Você encontrará o `<listeners>` seção o `<source>` seção com o atributo name "DefaultSource", que está aninhada sob o `<system.diagnostics>` seção, que está aninhada em nível superior `<configuration>` seção.  
  
3.  Adicionar esse elemento a que `<listeners>` seção:  
  
    ```  
    <add name="EventLog"/>  
    ```  
  
4.  Localize o `<sharedListeners>` seção, o `<system.diagnostics>` seção superior `<configuration>` seção.  
  
5.  Adicionar esse elemento a que `<sharedListeners>` seção:  
  
    ```  
    <add name="EventLog"  
        type="System.Diagnostics.EventLogTraceListener, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
         initializeData="APPLICATION_NAME"/>  
    ```  
  
     Substitua `APPLICATION_NAME` com o nome do seu aplicativo.  
  
    > [!NOTE]
    >  Normalmente, um aplicativo grava somente erros no log de eventos. Para obter informações sobre filtragem de saída de log, consulte [Instruções passo a passo: filtrando a saída de My.Application.Log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).  
  
### Para gravar informações de evento no log de eventos  
  
-   Use o `My.Application.Log.WriteEntry` ou `My.Application.Log.WriteException` método para gravar informações no log de eventos. Para obter mais informações, consulte [Como gravar mensagens de log](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) e [Como registrar em log as exceções](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).  
  
     Depois de configurar o ouvinte de log de eventos para um assembly, ele recebe todas as mensagens que `My.Applcation.Log` grava desse assembly.  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=fullName>   
 <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>   
 <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>   
 [Trabalhando com logs de aplicativo](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)   
 [Como registrar em log as exceções](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)   
 [Instruções passo a passo: determinando onde My.Application.Log grava informações](../Topic/Walkthrough:%20Determining%20Where%20My.Application.Log%20Writes%20Information%20\(Visual%20Basic\).md)