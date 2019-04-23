---
title: 'Como: Gravar informações de evento em um arquivo de texto (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs [Visual Studio], writing event information
- text files [Visual Basic], writing event information to a text file
- events [Visual Basic], writing event information to a text file
ms.assetid: 9ca7cc03-bf99-4933-9e5e-61ee28e9a6b4
ms.openlocfilehash: e696ccb7327197c2f3a2468d30085dc6d390e034
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59312703"
---
# <a name="how-to-write-event-information-to-a-text-file-visual-basic"></a>Como: Gravar informações de evento em um arquivo de texto (Visual Basic)
É possível usar os objetos `My.Application.Log` e `My.Log` para registrar em log as informações sobre eventos que ocorrem em seu aplicativo. Este exemplo mostra como usar o método `My.Application.Log.WriteEntry` para registrar em log informações de rastreamento em um arquivo de log.  
  
### <a name="to-add-and-configure-the-file-log-listener"></a>Para adicionar e configurar o ouvinte de log de arquivo  
  
1. Clique com o botão direito do mouse em app.config no **Gerenciador de Soluções** e escolha **Abrir**.  
  
     \- ou -  
  
     Se não houver nenhum arquivo app.config:  
  
    1.  No menu **Projeto**, escolha **Adicionar Novo Item**.  
  
    2.  Na caixa de diálogo **Adicionar novo item**, escolha **Arquivo de configuração de aplicativo**.  
  
    3.  Clique em **Adicionar**.  
  
2. Localize a seção `<listeners>` no arquivo de configuração de aplicativo.  
  
     Você localizará a seção \<listeners> na seção \<source> com o atributo de nome "DefaultSource", aninhado na seção \<system.diagnostics>, aninhada na seção \<configuration> superior.  
  
3. Adicione esse elemento a essa seção `<listeners>`:  
  
    ```xml  
    <add name="FileLogListener" />  
    ```  
  
4. Localize a seção `<sharedListeners>` na seção `<system.diagnostics>`, aninhada na seção `<configuration>` superior.  
  
5. Adicione esse elemento a essa seção `<sharedListeners>`:  
  
    ```xml  
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
  
-   Use o método `My.Application.Log.WriteEntry` ou `My.Application.Log.WriteException` para gravar informações no log de arquivos. Para obter mais informações, confira [Como: Gravar mensagens de Log](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) e [Como: Registrar exceções em log](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).  
  
     Depois de configurar o ouvinte de log de arquivos para um assembly, ele receberá todas as mensagens que `My.Application.Log` grava desse assembly.  
  
## <a name="see-also"></a>Consulte também

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [Trabalhando com logs de aplicativo](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [Como: registrar exceções](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
