---
title: "Como gravar informa&#231;&#245;es de evento em um arquivo de texto (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
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
  - "logs de eventos [Visual Studio ], gravando informações de evento"
  - "eventos [Visual Basic], gravando informações de eventos em um arquivo de texto"
  - "arquivos de texto, gravando informações de eventos em um arquivo de texto"
ms.assetid: 9ca7cc03-bf99-4933-9e5e-61ee28e9a6b4
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como gravar informa&#231;&#245;es de evento em um arquivo de texto (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Você pode usar os objetos `My.Application.Log` e `My.Log` para criar um log de informações sobre eventos que ocorrem em seu aplicativo.  Este exemplo mostra como usar o método `My.Application.Log.WriteEntry` para registrar informações de rastreamento em um arquivo de log.  
  
### Para adicionar e configurar o ouvinte de log de arquivo  
  
1.  Clique com o botão direito do mouse em app.config no **Solution Explorer** e escolha **Open**.  
  
     \- ou \-  
  
     Se não houver nenhum arquivo app.config:  
  
    1.  No menu **Project**, escolha **Add New Item**.  
  
    2.  No caixa de diálogo **Add New Item** escolha **Application Configuration File**.  
  
    3.  Clique em **Adicionar**.  
  
2.  Localize a seção `<listeners>` em arquivo de configuração o aplicativo.  
  
     Você encontrará a seção \<listeners\> na seção \<source\> com o nome do atributo "DefaultSource", que está aninhada abaixo da seção \<system.diagnostics\>, que está aninhada sob a seção de nível superior \<configuration\>.  
  
3.  Adicione esse elemento à seção `<listeners>`.  
  
    ```  
    <add name="FileLogListener" />  
    ```  
  
4.  Localize a seção `<sharedListeners>` na seção `<system.diagnostics>`, aninhada sob a seção `<configuration>` de  nível superior.  
  
5.  Adicione esse elemento à seção `<sharedListeners>`.  
  
    ```  
    <add name="FileLogListener"   
        type="Microsoft.VisualBasic.Logging.FileLogTraceListener,   
              Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral,   
              PublicKeyToken=b03f5f7f11d50a3a"  
        initializeData="FileLogListenerWriter"  
        location="Custom"  
        customlocation="c:\temp\" />  
    ```  
  
     Altere o valor do atributo `customlocation` para o diretório de log.  
  
    > [!NOTE]
    >  Para definir o valor de uma propriedade ouvinte, use um atributo que tem o mesmo nome que a propriedade, com todas as letras do nome em minúsculas.  Por exemplo, os atributos `location` e `customlocation` definem os valores das propriedades <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.Location%2A> e <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.CustomLocation%2A>.  
  
### Para gravar informações de evento no log de arquivo  
  
-   Use o método `My.Application.Log.WriteEntry` ou `My.Application.Log.WriteException` para gravar informações sobre o log de eventos.  Para obter mais informações, consulte [Como gravar mensagens de log](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) e [Como registrar em log as exceções](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).  
  
     Depois que você configura o ouvinte de log de arquivo para um assembly, ele recebe todas as mensagens que `My.Application.Log` grava para esse assembly.  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=fullName>   
 <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>   
 <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>   
 [Trabalhando com logs de aplicativo](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)   
 [Como registrar em log as exceções](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)