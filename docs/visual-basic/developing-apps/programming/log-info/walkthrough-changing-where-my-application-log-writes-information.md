---
title: "Instru&#231;&#245;es passo a passo: alterando onde My.Application.Log grava informa&#231;&#245;es (Visual Basic) | Microsoft Docs"
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
  - "Objeto My.Application.Log, instruções passo a passo"
  - "logs de eventos, alterando o local de saída"
ms.assetid: ecc74f95-743c-450d-93f6-09a30db0fe4a
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Instru&#231;&#245;es passo a passo: alterando onde My.Application.Log grava informa&#231;&#245;es (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Você pode usar o `My.Application.Log` e `My.Log` objetos para registrar informações sobre eventos que ocorrem em seu aplicativo. Este passo a passo mostra como substituir as configurações padrão e fazer com que o `Log` objeto grave em outros ouvintes de log.  
  
## Pré-requisitos  
 O `Log` objeto pode gravar informações em vários ouvintes de log. Você precisa determinar a configuração atual dos ouvintes de log antes de alterar as configurações. Para obter mais informações, consulte [Instruções passo a passo: determinando onde My.Application.Log grava informações](../Topic/Walkthrough:%20Determining%20Where%20My.Application.Log%20Writes%20Information%20\(Visual%20Basic\).md).  
  
 Talvez você queira examinar [Como gravar informações de evento em um arquivo de texto](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-event-information-to-a-text-file.md) ou [Como gravar em um log de eventos do aplicativo](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-to-an-application-event-log.md).  
  
### Para adicionar ouvintes  
  
1.  Clique com botão direito app. config em **Solution Explorer** e escolha **Abrir**.  
  
     \- ou \-  
  
     Se não houver nenhum arquivo App. config:  
  
    1.  Sobre o **projeto** menu, escolha **Add New Item**.  
  
    2.  Do **Add New Item** caixa de diálogo, selecione **arquivo de configuração do aplicativo**.  
  
    3.  Clique em **Adicionar**.  
  
2.  Localize o `<listeners>` seção, no `<source>` seção com o `name` atributo "DefaultSource", o `<sources>` seção. O `<sources>` seção está no `<system.diagnostics>` seção superior `<configuration>` seção.  
  
3.  Adicione esses elementos que `<listeners>` seção.  
  
    ```  
    <!-- Uncomment to connect the application file log. -->  
    <!-- <add name="FileLog" /> -->  
    <!-- Uncomment to connect the event log. -->  
    <!-- <add name="EventLog" /> -->  
    <!-- Uncomment to connect the event log. -->  
    <!-- <add name="Delimited" /> -->  
    <!-- Uncomment to connect the XML log. -->  
    <!-- <add name="XmlWriter" /> -->  
    <!-- Uncomment to connect the console log. -->  
    <!-- <add name="Console" /> -->  
    ```  
  
4.  Remova os ouvintes de log que você deseja receber `Log` mensagens.  
  
5.  Localize o `<sharedListeners>` seção, o `<system.diagnostics>` seção superior `<configuration>` seção.  
  
6.  Adicione esses elementos que `<sharedListeners>` seção.  
  
    ```  
    <add name="FileLog"  
         type="Microsoft.VisualBasic.Logging.FileLogTraceListener,   
               Microsoft.VisualBasic, Version=8.0.0.0,   
               Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"  
         initializeData="FileLogWriter" />  
    <add name="EventLog"  
         type="System.Diagnostics.EventLogTraceListener,   
               System, Version=2.0.0.0,   
               Culture=neutral, PublicKeyToken=b77a5c561934e089"  
         initializeData="sample application"/>  
    <add name="Delimited"   
         type="System.Diagnostics.DelimitedListTraceListener,   
               System, Version=2.0.0.0,   
               Culture=neutral, PublicKeyToken=b77a5c561934e089"  
         initializeData="c:\temp\sampleDelimitedFile.txt"  
         traceOutputOptions="DateTime" />  
    <add name="XmlWriter"  
         type="System.Diagnostics.XmlWriterTraceListener,   
               System, Version=2.0.0.0,   
               Culture=neutral, PublicKeyToken=b77a5c561934e089"  
         initializeData="c:\temp\sampleLogFile.xml" />  
    <add name="Console"  
         type="System.Diagnostics.ConsoleTraceListener,   
               System, Version=2.0.0.0,   
               Culture=neutral, PublicKeyToken=b77a5c561934e089"  
         initializeData="true" />  
    ```  
  
7.  O conteúdo do arquivo App. config deve ser semelhante ao XML a seguir:  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.diagnostics>  
        <sources>  
          <!-- This section configures My.Application.Log -->  
          <source name="DefaultSource" switchName="DefaultSwitch">  
            <listeners>  
              <add name="FileLog"/>  
              <!-- Uncomment to connect the application file log. -->  
              <!-- <add name="FileLog" /> -->  
              <!-- Uncomment to connect the event log. -->  
              <!-- <add name="EventLog" /> -->  
              <!-- Uncomment to connect the event log. -->  
              <!-- <add name="Delimited" /> -->  
              <!-- Uncomment to connect the XML log. -->  
              <!-- <add name="XmlWriter" /> -->  
              <!-- Uncomment to connect the console log. -->  
              <!-- <add name="Console" /> -->  
            </listeners>  
          </source>  
        </sources>  
        <switches>  
          <add name="DefaultSwitch" value="Information" />  
        </switches>  
        <sharedListeners>  
          <add name="FileLog"  
               type="Microsoft.VisualBasic.Logging.FileLogTraceListener,   
                     Microsoft.VisualBasic, Version=8.0.0.0,   
                     Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"  
               initializeData="FileLogWriter" />  
          <add name="EventLog"  
               type="System.Diagnostics.EventLogTraceListener,   
                     System, Version=2.0.0.0,   
                     Culture=neutral, PublicKeyToken=b77a5c561934e089"  
               initializeData="sample application"/>  
          <add name="Delimited"   
               type="System.Diagnostics.DelimitedListTraceListener,   
                     System, Version=2.0.0.0,   
                     Culture=neutral, PublicKeyToken=b77a5c561934e089"  
               initializeData="c:\temp\sampleDelimitedFile.txt"  
               traceOutputOptions="DateTime" />  
          <add name="XmlWriter"  
               type="System.Diagnostics.XmlWriterTraceListener,   
                     System, Version=2.0.0.0,   
                     Culture=neutral, PublicKeyToken=b77a5c561934e089"  
               initializeData="c:\temp\sampleLogFile.xml" />  
          <add name="Console"  
               type="System.Diagnostics.ConsoleTraceListener,   
                     System, Version=2.0.0.0,   
                     Culture=neutral, PublicKeyToken=b77a5c561934e089"  
               initializeData="true" />  
        </sharedListeners>  
      </system.diagnostics>  
    </configuration>  
    ```  
  
### Para reconfigurar um ouvinte  
  
1.  Localize o ouvinte `<add>` elemento o `<sharedListeners>` seção.  
  
2.  O `type` atributo fornece o nome do tipo de ouvinte. Esse tipo deve herdar da <xref:System.Diagnostics.TraceListener> classe. Use o nome do tipo nomeado para garantir que o tipo correto é usado. Para obter mais informações, consulte a seção "para fazer referência a um tipo de nome forte" abaixo.  
  
     Alguns tipos que você pode usar são:  
  
    -   Um <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=fullName> ouvinte, que grava em um arquivo de log.  
  
    -   Um <xref:System.Diagnostics.EventLogTraceListener?displayProperty=fullName> ouvinte, que grava informações no log de eventos do computador especificado pelo `initializeData` parâmetro.  
  
    -   O <xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=fullName> e <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=fullName> ouvintes, que gravam no arquivo especificado no `initializeData` parâmetro.  
  
    -   Um <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=fullName> ouvinte, que grava no console de linha de comando.  
  
     Para obter informações sobre onde outros tipos de ouvintes de log gravam informações, consulte a documentação daquele tipo.  
  
3.  Quando o aplicativo cria o objeto de ouvinte de log, ele passa a `initializeData` atributo como o parâmetro de construtor. O significado de `initializeData` atributo depende o ouvinte de rastreamento.  
  
4.  Depois de criar o ouvinte de log, o aplicativo define as propriedades do ouvinte. Essas propriedades são definidas pelos outros atributos no `<add>` elemento. Para obter mais informações sobre as propriedades de um ouvinte específico, consulte a documentação para aquele tipo de ouvinte.  
  
### Para fazer referência a um tipo de nome forte  
  
1.  Para garantir que o tipo correto é usado para seu ouvinte de log, certifique\-se de usar o nome de tipo totalmente qualificado e o nome do assembly de nome forte. A sintaxe de um tipo de nome forte é da seguinte maneira:  
  
     \<*nome do tipo*\>, \<*nome do assembly*\>, \<*o número de versão*\>, \<*cultura*\>, \<*nome forte*\>  
  
2.  Este exemplo de código mostra como determinar o nome do tipo nomeado para um System.Diagnostics.FileLogTraceListener totalmente qualificado "neste caso.  
  
     [!code-vb[VbVbalrMyApplicationLog#15](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/walkthrough-changing-where-my-application-log-writes-information_1.vb)]  
  
     Esta é a saída, e ele pode ser usado para fazer referência única um tipo de nome forte, como no procedimento "para adicionar ouvintes" acima.  
  
     `Microsoft.VisualBasic.Logging.FileLogTraceListener, Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a`  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=fullName>   
 <xref:System.Diagnostics.TraceListener>   
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=fullName>   
 <xref:System.Diagnostics.EventLogTraceListener?displayProperty=fullName>   
 [Como gravar informações de evento em um arquivo de texto](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-event-information-to-a-text-file.md)   
 [Como gravar em um log de eventos do aplicativo](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-to-an-application-event-log.md)