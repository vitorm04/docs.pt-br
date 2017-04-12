---
title: "Como gravar informações de evento em um arquivo de texto (Visual Basic) | Microsoft Docs"
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
- event logs [Visual Studio], writing event information
- text files, writing event information to a text file
- events [Visual Basic], writing event information to a text file
ms.assetid: 9ca7cc03-bf99-4933-9e5e-61ee28e9a6b4
caps.latest.revision: 20
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 52c8739c0493275fc84274a295c2464a6cf9a580
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-write-event-information-to-a-text-file-visual-basic"></a>Como gravar informações de evento em um arquivo de texto (Visual Basic)
É possível usar os objetos `My.Application.Log` e `My.Log` para registrar em log as informações sobre eventos que ocorrem em seu aplicativo. Este exemplo mostra como usar o método `My.Application.Log.WriteEntry` para registrar em log informações de rastreamento em um arquivo de log.  
  
### <a name="to-add-and-configure-the-file-log-listener"></a>Para adicionar e configurar o ouvinte de log de arquivo  
  
1.  Clique com o botão direito do mouse em app.config no **Gerenciador de Soluções** e escolha **Abrir**.  
  
     \- ou -  
  
     Se não houver nenhum arquivo app.config:  
  
    1.  No menu **Projeto**, escolha **Adicionar Novo Item**.  
  
    2.  Na caixa de diálogo **Adicionar novo item**, escolha **Arquivo de configuração de aplicativo**.  
  
    3.  Clique em **Adicionar**.  
  
2.  Localize a seção `<listeners>` no arquivo de configuração de aplicativo.  
  
     Você localizará a seção \<listeners> na seção \<source> com o atributo de nome "DefaultSource", aninhado na seção \<system.diagnostics>, aninhada na seção \<configuration> superior.  
  
3.  Adicione esse elemento a essa seção `<listeners>`:  
  
    ```  
    <add name="FileLogListener" />  
    ```  
  
4.  Localize a seção `<sharedListeners>` na seção `<system.diagnostics>`, aninhada na seção `<configuration>` superior.  
  
5.  Adicione esse elemento a essa seção `<sharedListeners>`:  
  
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
    >  Para definir o valor de uma propriedade ouvinte, use um atributo com o mesmo nome da propriedade, com todas as letras do nome em minúsculas. Por exemplo, os atributos `location` e `customlocation` definem os valores das propriedades <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.Location%2A> e <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.CustomLocation%2A>.  
  
### <a name="to-write-event-information-to-the-file-log"></a>Para gravar informações de evento no log de arquivos  
  
-   Use o método `My.Application.Log.WriteEntry` ou `My.Application.Log.WriteException` para gravar informações no log de arquivos. Para obter mais informações, consulte [Como: Gravar mensagens de log](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) e [Como registrar em log as exceções](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).  
  
     Depois de configurar o ouvinte de log de arquivos para um assembly, ele receberá todas as mensagens que `My.Application.Log` grava desse assembly.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=fullName>   
 <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>   
 <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>   
 [Trabalhando com Logs de Aplicativo](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)   
 [Como registrar em log as exceções](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
