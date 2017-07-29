---
title: Como gravar em um log de eventos do aplicativo (Visual Basic)
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- Computer.EventLog element
- WriteEntry method
- My.Computer.EventLog element
- event logs, writing to
ms.assetid: cadbc8c1-87af-4746-934e-55b79a4f6e2b
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 7cc73b0644003f8231a7792b0b62d143159da075
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-write-to-an-application-event-log-visual-basic"></a>Como gravar em um log de eventos do aplicativo (Visual Basic)
É possível usar os objetos `My.Application.Log` e `My.Log` para gravar informações sobre eventos que ocorrem em seu aplicativo. Este exemplo mostra como configurar um ouvinte de log de eventos. Assim, `My.Application.Log` grava informações de rastreamento no log de eventos do aplicativo.  
  
 Não é possível gravar no log de segurança. Para gravar no log do sistema, é necessário ser um membro do LocalSystem ou ter uma conta Administrador.  
  
 Para exibir um log de eventos, é possível usar o **Gerenciador de Servidores** ou o **Visualizador de Eventos do Windows**. Para obter mais informações, consulte [Eventos ETW no .NET Framework](http://msdn.microsoft.com/library/d186276f-6afb-4dfd-bf3c-4251edc2c299).  
  
> [!NOTE]
>  Não há suporte para logs de eventos no Windows 95, Windows 98 ou Windows Millennium Edition.  
  
### <a name="to-add-and-configure-the-event-log-listener"></a>Para adicionar e configurar o ouvinte de log de eventos  
  
1.  Clique com o botão direito do mouse em app.config no **Gerenciador de Soluções** e escolha **Abrir**.  
  
     \- ou -  
  
     Se não houver nenhum arquivo app.config,  
  
    1.  No menu **Projeto**, escolha **Adicionar Novo Item**.  
  
    2.  Na caixa de diálogo **Adicionar novo item**, escolha **Arquivo de configuração de aplicativo**.  
  
    3.  Clique em **Adicionar**.  
  
2.  Localize a seção `<listeners>` no arquivo de configuração de aplicativo.  
  
     Localize a seção `<listeners>` na seção `<source>` com o atributo de nome "DefaultSource", aninhado na seção `<system.diagnostics>`, aninhada na seção `<configuration>` superior.  
  
3.  Adicione esse elemento a essa seção `<listeners>`:  
  
    ```xml  
    <add name="EventLog"/>  
    ```  
  
4.  Localize a seção `<sharedListeners>`, na seção `<system.diagnostics>`, na seção `<configuration>` superior.  
  
5.  Adicione esse elemento a essa seção `<sharedListeners>`:  
  
    ```xml  
    <add name="EventLog"  
        type="System.Diagnostics.EventLogTraceListener, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
         initializeData="APPLICATION_NAME"/>  
    ```  
  
     Substitua `APPLICATION_NAME` pelo nome do aplicativo.  
  
    > [!NOTE]
    >  Normalmente, um aplicativo grava somente erros no log de eventos. Para obter informações sobre filtragem de saída de log, consulte [Instruções passo a passo: filtrando a saída de My.Application.Log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).  
  
### <a name="to-write-event-information-to-the-event-log"></a>Para gravar informações de evento em um log de eventos  
  
-   Use o método `My.Application.Log.WriteEntry` ou `My.Application.Log.WriteException` para gravar informações no log de eventos. Para obter mais informações, consulte [Como: Gravar mensagens de log](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) e [Como registrar em log as exceções](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).  
  
     Depois de configurar o ouvinte de log de eventos para um assembly, ele receberá todas as mensagens que `My.Applcation.Log` grava desse assembly.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=fullName>   
 <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>   
 <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>   
 [Trabalhando com Logs de Aplicativo](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)   
 [Como registrar as exceções em log](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)   
 [Instruções passo a passo: determinando onde My.Application.Log grava informações](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)

