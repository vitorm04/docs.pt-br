---
title: "Alterar o local em que My.Application.Log grava informações (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- My.Application.Log object, walkthroughs
- event logs, changing output location
ms.assetid: ecc74f95-743c-450d-93f6-09a30db0fe4a
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c4cd2e675bf1be4f065ee116795a95dae64d13d9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-changing-where-myapplicationlog-writes-information-visual-basic"></a><span data-ttu-id="2d774-102">Instruções passo a passo: alterando onde My.Application.Log grava informações (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2d774-102">Walkthrough: Changing Where My.Application.Log Writes Information (Visual Basic)</span></span>
<span data-ttu-id="2d774-103">É possível usar os objetos `My.Application.Log` e `My.Log` para registrar em log as informações sobre eventos que ocorrem em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2d774-103">You can use the `My.Application.Log` and `My.Log` objects to log information about events that occur in your application.</span></span> <span data-ttu-id="2d774-104">Este passo a passo mostra como substituir as configurações padrão e fazer com que o objeto `Log` grave em outros ouvintes de log.</span><span class="sxs-lookup"><span data-stu-id="2d774-104">This walkthrough shows how to override the default settings and cause the `Log` object to write to other log listeners.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="2d774-105">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="2d774-105">Prerequisites</span></span>  
 <span data-ttu-id="2d774-106">O objeto `Log` pode gravar informações em vários ouvintes de log.</span><span class="sxs-lookup"><span data-stu-id="2d774-106">The `Log` object can write information to several log listeners.</span></span> <span data-ttu-id="2d774-107">Você precisa determinar a configuração atual dos ouvintes de log antes de alterar as configurações.</span><span class="sxs-lookup"><span data-stu-id="2d774-107">You need to determine the current configuration of the log listeners before changing the configurations.</span></span> <span data-ttu-id="2d774-108">Para obter mais informações, consulte [Instruções passo a passo: Determinando onde My.Application.Log grava informações](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).</span><span class="sxs-lookup"><span data-stu-id="2d774-108">For more information, see [Walkthrough: Determining Where My.Application.Log Writes Information](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).</span></span>  
  
 <span data-ttu-id="2d774-109">Talvez você queira examinar [Como gravar informações de evento em um arquivo de texto](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-event-information-to-a-text-file.md) ou [Como gravar em um log de eventos do aplicativo](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-to-an-application-event-log.md).</span><span class="sxs-lookup"><span data-stu-id="2d774-109">You may want to review [How to: Write Event Information to a Text File](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-event-information-to-a-text-file.md) or [How to: Write to an Application Event Log](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-to-an-application-event-log.md).</span></span>  
  
### <a name="to-add-listeners"></a><span data-ttu-id="2d774-110">Para adicionar ouvintes</span><span class="sxs-lookup"><span data-stu-id="2d774-110">To add listeners</span></span>  
  
1.  <span data-ttu-id="2d774-111">Clique com o botão direito do mouse em app.config no **Gerenciador de Soluções** e escolha **Abrir**.</span><span class="sxs-lookup"><span data-stu-id="2d774-111">Right-click app.config in **Solution Explorer** and choose **Open**.</span></span>  
  
     <span data-ttu-id="2d774-112">\- ou -</span><span class="sxs-lookup"><span data-stu-id="2d774-112">\- or -</span></span>  
  
     <span data-ttu-id="2d774-113">Se não houver nenhum arquivo app.config:</span><span class="sxs-lookup"><span data-stu-id="2d774-113">If there is no app.config file:</span></span>  
  
    1.  <span data-ttu-id="2d774-114">No menu **Projeto**, escolha **Adicionar Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="2d774-114">On the **Project** menu, choose **Add New Item**.</span></span>  
  
    2.  <span data-ttu-id="2d774-115">Na caixa de diálogo **Adicionar Novo Item**, selecione **Arquivo de Configuração de Aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="2d774-115">From the **Add New Item** dialog box, select **Application Configuration File**.</span></span>  
  
    3.  <span data-ttu-id="2d774-116">Clique em **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="2d774-116">Click **Add**.</span></span>  
  
2.  <span data-ttu-id="2d774-117">Localize a seção `<listeners>`, na seção `<source>` com o `name` atributo "DefaultSource", na seção `<sources>`.</span><span class="sxs-lookup"><span data-stu-id="2d774-117">Locate the `<listeners>` section, under the `<source>` section with the `name` attribute "DefaultSource", in the `<sources>` section.</span></span> <span data-ttu-id="2d774-118">A seção `<sources>` está na seção `<system.diagnostics>`, na seção `<configuration>` superior.</span><span class="sxs-lookup"><span data-stu-id="2d774-118">The `<sources>` section is in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
3.  <span data-ttu-id="2d774-119">Adicione esses elementos a essa seção `<listeners>`.</span><span class="sxs-lookup"><span data-stu-id="2d774-119">Add these elements to that `<listeners>` section.</span></span>  
  
    ```xml  
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
  
4.  <span data-ttu-id="2d774-120">Remova a marca de comentário dos ouvintes de log que você deseja receber mensagens de `Log`.</span><span class="sxs-lookup"><span data-stu-id="2d774-120">Uncomment the log listeners that you want to receive `Log` messages.</span></span>  
  
5.  <span data-ttu-id="2d774-121">Localize a seção `<sharedListeners>`, na seção `<system.diagnostics>`, na seção `<configuration>` superior.</span><span class="sxs-lookup"><span data-stu-id="2d774-121">Locate the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
6.  <span data-ttu-id="2d774-122">Adicione esses elementos a essa seção `<sharedListeners>`.</span><span class="sxs-lookup"><span data-stu-id="2d774-122">Add these elements to that `<sharedListeners>` section.</span></span>  
  
    ```xml  
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
  
7.  <span data-ttu-id="2d774-123">O conteúdo do arquivo app.config deve ser semelhante ao XML a seguir:</span><span class="sxs-lookup"><span data-stu-id="2d774-123">The content of the app.config file should be similar to the following XML:</span></span>  
  
    ```xml  
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
  
### <a name="to-reconfigure-a-listener"></a><span data-ttu-id="2d774-124">Para reconfigurar um ouvinte</span><span class="sxs-lookup"><span data-stu-id="2d774-124">To reconfigure a listener</span></span>  
  
1.  <span data-ttu-id="2d774-125">Localize o elemento `<add>` do ouvinte na seção `<sharedListeners>`.</span><span class="sxs-lookup"><span data-stu-id="2d774-125">Locate the listener's `<add>` element from the `<sharedListeners>` section.</span></span>  
  
2.  <span data-ttu-id="2d774-126">O atributo `type` fornece o nome do tipo de ouvinte.</span><span class="sxs-lookup"><span data-stu-id="2d774-126">The `type` attribute gives the name of the listener type.</span></span> <span data-ttu-id="2d774-127">Esse tipo deve herdar da classe <xref:System.Diagnostics.TraceListener>.</span><span class="sxs-lookup"><span data-stu-id="2d774-127">This type must inherit from the <xref:System.Diagnostics.TraceListener> class.</span></span> <span data-ttu-id="2d774-128">Use o nome de tipo de nome forte para garantir que o tipo correto seja usado.</span><span class="sxs-lookup"><span data-stu-id="2d774-128">Use the strongly named type name to ensure that the right type is used.</span></span> <span data-ttu-id="2d774-129">Para obter mais informações, consulte a seção “Para fazer referência a um tipo de nome forte”.</span><span class="sxs-lookup"><span data-stu-id="2d774-129">For more information, see the "To reference a strongly named type" section below.</span></span>  
  
     <span data-ttu-id="2d774-130">Alguns tipos que você pode usar são:</span><span class="sxs-lookup"><span data-stu-id="2d774-130">Some types that you can use are:</span></span>  
  
    -   <span data-ttu-id="2d774-131">Um ouvinte <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType>, que grava em um arquivo de log.</span><span class="sxs-lookup"><span data-stu-id="2d774-131">A <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> listener, which writes to a file log.</span></span>  
  
    -   <span data-ttu-id="2d774-132">O ouvinte <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> que grava informações no log de eventos do computador especificado pelo parâmetro `initializeData`.</span><span class="sxs-lookup"><span data-stu-id="2d774-132">A <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> listener, which writes information to the computer event log specified by the `initializeData` parameter.</span></span>  
  
    -   <span data-ttu-id="2d774-133">Os ouvintes <xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> e <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>, que gravam no arquivo especificado no parâmetro `initializeData`.</span><span class="sxs-lookup"><span data-stu-id="2d774-133">The <xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> and <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> listeners, which write to the file specified in the `initializeData` parameter.</span></span>  
  
    -   <span data-ttu-id="2d774-134">Um ouvinte <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>, que grava no console da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="2d774-134">A <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> listener, which writes to the command-line console.</span></span>  
  
     <span data-ttu-id="2d774-135">Para obter informações sobre onde outros tipos de ouvintes de log gravam informações, consulte a documentação daquele tipo.</span><span class="sxs-lookup"><span data-stu-id="2d774-135">For information about where other types of log listeners write information, consult that type's documentation.</span></span>  
  
3.  <span data-ttu-id="2d774-136">Quando o aplicativo cria o objeto de ouvinte de log, ele passa o atributo `initializeData` como o parâmetro de construtor.</span><span class="sxs-lookup"><span data-stu-id="2d774-136">When the application creates the log-listener object, it passes the `initializeData` attribute as the constructor parameter.</span></span> <span data-ttu-id="2d774-137">O significado do atributo `initializeData` depende o ouvinte de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="2d774-137">The meaning of the `initializeData` attribute depends on the trace listener.</span></span>  
  
4.  <span data-ttu-id="2d774-138">Depois de criar o ouvinte de log, o aplicativo define as propriedades do ouvinte.</span><span class="sxs-lookup"><span data-stu-id="2d774-138">After creating the log listener, the application sets the listener's properties.</span></span> <span data-ttu-id="2d774-139">Essas propriedades são definidas pelos outros atributos no elemento `<add>`.</span><span class="sxs-lookup"><span data-stu-id="2d774-139">These properties are defined by the other attributes in the `<add>` element.</span></span> <span data-ttu-id="2d774-140">Para obter mais informações sobre as propriedades de um ouvinte específico, consulte a documentação daquele tipo de ouvinte.</span><span class="sxs-lookup"><span data-stu-id="2d774-140">For more information on the properties for a particular listener, see the documentation for that listener's type.</span></span>  
  
### <a name="to-reference-a-strongly-named-type"></a><span data-ttu-id="2d774-141">Para fazer referência a um tipo de nome forte</span><span class="sxs-lookup"><span data-stu-id="2d774-141">To reference a strongly named type</span></span>  
  
1.  <span data-ttu-id="2d774-142">Para garantir que o tipo correto seja usado para seu ouvinte de log, certifique-se de usar o nome de tipo totalmente qualificado e o nome do assembly de nome forte.</span><span class="sxs-lookup"><span data-stu-id="2d774-142">To ensure that the right type is used for your log listener, make sure to use the fully qualified type name and the strongly named assembly name.</span></span> <span data-ttu-id="2d774-143">A sintaxe de um tipo de nome forte é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="2d774-143">The syntax of a strongly named type is as follows:</span></span>  
  
     <span data-ttu-id="2d774-144">\<*nome do tipo*>, \<*nome do assembly*>, \<*número de versão*>, \<*cultura*>, \<*nome forte*></span><span class="sxs-lookup"><span data-stu-id="2d774-144">\<*type name*>, \<*assembly name*>, \<*version number*>, \<*culture*>, \<*strong name*></span></span>  
  
2.  <span data-ttu-id="2d774-145">Este exemplo de código mostra como determinar o nome do tipo do nome forte para um tipo totalmente qualificado —"System.Diagnostics.FileLogTraceListener" nesse caso.</span><span class="sxs-lookup"><span data-stu-id="2d774-145">This code example shows how to determine the strongly named type name for a fully qualified type—"System.Diagnostics.FileLogTraceListener" in this case.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#15](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/walkthrough-changing-where-my-application-log-writes-information_1.vb)]  
  
     <span data-ttu-id="2d774-146">Esta é a saída e ela pode ser usada para fazer referência de forma única a um tipo de nome forte, como no procedimento "Para adicionar ouvintes" acima.</span><span class="sxs-lookup"><span data-stu-id="2d774-146">This is the output, and it can be used to uniquely reference a strongly named type, as in the "To add listeners" procedure above.</span></span>  
  
     `Microsoft.VisualBasic.Logging.FileLogTraceListener, Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a`  
  
## <a name="see-also"></a><span data-ttu-id="2d774-147">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2d774-147">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 <xref:System.Diagnostics.TraceListener>  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType>  
 <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>  
 [<span data-ttu-id="2d774-148">Como gravar informações de evento em um arquivo de texto</span><span class="sxs-lookup"><span data-stu-id="2d774-148">How to: Write Event Information to a Text File</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-event-information-to-a-text-file.md)  
 [<span data-ttu-id="2d774-149">Como gravar em um log de eventos do aplicativo</span><span class="sxs-lookup"><span data-stu-id="2d774-149">How to: Write to an Application Event Log</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-to-an-application-event-log.md)
