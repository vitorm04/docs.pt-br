---
title: Determinar o local em que My.Application.Log grava informações (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My.Log object, output location
- output, application log location
- My.Application.Log object, outpout location
- event logs, determining output location
- application event logs, output location
- applications [Visual Basic], output location
ms.assetid: 5b70143a-7741-45f2-ae1d-03324a3a4189
ms.openlocfilehash: fa177fa1f07c52d900f57e5bf61c967f06203c4f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33590927"
---
# <a name="walkthrough-determining-where-myapplicationlog-writes-information-visual-basic"></a><span data-ttu-id="9db30-102">Instruções passo a passo: determinando onde My.Application.Log grava informações (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9db30-102">Walkthrough: Determining Where My.Application.Log Writes Information (Visual Basic)</span></span>
<span data-ttu-id="9db30-103">O objeto `My.Application.Log` pode gravar informações em vários ouvintes de log.</span><span class="sxs-lookup"><span data-stu-id="9db30-103">The `My.Application.Log` object can write information to several log listeners.</span></span> <span data-ttu-id="9db30-104">Os ouvintes de log são configurados pelo arquivo de configuração do computador e podem ser substituídos pelo arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9db30-104">The log listeners are configured by the computer's configuration file and can be overridden by an application's configuration file.</span></span> <span data-ttu-id="9db30-105">Este tópico descreve as configurações padrão e como determinar as configurações para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9db30-105">This topic describes the default settings and how to determine the settings for your application.</span></span>  
  
 <span data-ttu-id="9db30-106">Para obter mais informações sobre os locais de saída padrão, consulte [Trabalhando com logs de aplicativo](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).</span><span class="sxs-lookup"><span data-stu-id="9db30-106">For more information about the default output locations, see [Working with Application Logs](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).</span></span>  
  
### <a name="to-determine-the-listeners-for-myapplicationlog"></a><span data-ttu-id="9db30-107">Para determinar os ouvintes de My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="9db30-107">To determine the listeners for My.Application.Log</span></span>  
  
1.  <span data-ttu-id="9db30-108">Localize o arquivo de configuração do assembly.</span><span class="sxs-lookup"><span data-stu-id="9db30-108">Locate the assembly's configuration file.</span></span> <span data-ttu-id="9db30-109">Se você estiver desenvolvendo o assembly, poderá acessar o app.config em Visual Studio no **Gerenciador de Soluções**.</span><span class="sxs-lookup"><span data-stu-id="9db30-109">If you are developing the assembly, you can access the app.config in Visual Studio from the **Solution Explorer**.</span></span> <span data-ttu-id="9db30-110">Caso contrário, o nome do arquivo de configuração é o nome do assembly acrescentado com ".config" e ele está localizado no mesmo diretório do assembly.</span><span class="sxs-lookup"><span data-stu-id="9db30-110">Otherwise, the configuration file name is the assembly's name appended with ".config", and it is located in the same directory as the assembly.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9db30-111">Nem todo assembly tem um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="9db30-111">Not every assembly has a configuration file.</span></span>  
  
     <span data-ttu-id="9db30-112">O arquivo de configuração é um arquivo XML.</span><span class="sxs-lookup"><span data-stu-id="9db30-112">The configuration file is an XML file.</span></span>  
  
2.  <span data-ttu-id="9db30-113">Localize a seção `<listeners>`, na seção `<source>` com o `name` atributo "DefaultSource", localizado na seção `<sources>`.</span><span class="sxs-lookup"><span data-stu-id="9db30-113">Locate the `<listeners>` section, in the `<source>` section with the `name` attribute "DefaultSource", located in the `<sources>` section.</span></span> <span data-ttu-id="9db30-114">A seção `<sources>` está localizada na seção `<system.diagnostics>`, na seção `<configuration>` superior.</span><span class="sxs-lookup"><span data-stu-id="9db30-114">The `<sources>` section is located in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
     <span data-ttu-id="9db30-115">Se estas seções não existirem, o arquivo de configuração do computador poderá configurar os ouvintes de log `My.Application.Log`.</span><span class="sxs-lookup"><span data-stu-id="9db30-115">If these sections do not exist, then the computer's configuration file may configure the `My.Application.Log` log listeners.</span></span> <span data-ttu-id="9db30-116">As etapas a seguir descrevem como determinar o que define o arquivo de configuração do computador:</span><span class="sxs-lookup"><span data-stu-id="9db30-116">The following steps describe how to determine what the computer configuration file defines:</span></span>  
  
    1.  <span data-ttu-id="9db30-117">Localize o arquivo machine.config do computador.</span><span class="sxs-lookup"><span data-stu-id="9db30-117">Locate the computer's machine.config file.</span></span> <span data-ttu-id="9db30-118">Normalmente, ele está localizado no diretório *SystemRoot\Microsoft.NET\Framework\frameworkVersion\CONFIG*, em que `SystemRoot` é o diretório do sistema operacional e `frameworkVersion` é a versão do [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9db30-118">Typically, it is located in the *SystemRoot\Microsoft.NET\Framework\frameworkVersion\CONFIG* directory, where `SystemRoot` is the operating system directory, and `frameworkVersion` is the version of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span>  
  
         <span data-ttu-id="9db30-119">As configurações em machine.config podem ser substituídas por um arquivo de configuração de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9db30-119">The settings in machine.config can be overridden by an application's configuration file.</span></span>  
  
         <span data-ttu-id="9db30-120">Se os elementos opcionais listados abaixo não existirem, você poderá criá-los.</span><span class="sxs-lookup"><span data-stu-id="9db30-120">If the optional elements listed below do not exist, you can create them.</span></span>  
  
    2.  <span data-ttu-id="9db30-121">Localize a seção `<listeners>`, na seção `<source>` com o atributo `name` "DefaultSource", na seção `<sources>`, na seção `<system.diagnostics>`, na seção superior `<configuration>`.</span><span class="sxs-lookup"><span data-stu-id="9db30-121">Locate the `<listeners>` section, in the `<source>` section with the `name` attribute "DefaultSource", in the `<sources>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
         <span data-ttu-id="9db30-122">Se estas seções não existirem, o `My.Application.Log` terá apenas os ouvintes de log padrão.</span><span class="sxs-lookup"><span data-stu-id="9db30-122">If these sections do not exist, then the `My.Application.Log` has only the default log listeners.</span></span>  
  
3.  <span data-ttu-id="9db30-123">Localize os elementos <`add>` na seção <`listeners>`.</span><span class="sxs-lookup"><span data-stu-id="9db30-123">Locate the <`add>` elements in the <`listeners>` section.</span></span>  
  
     <span data-ttu-id="9db30-124">Esses elementos adicionam os ouvintes de log nomeados à origem `My.Application.Log`.</span><span class="sxs-lookup"><span data-stu-id="9db30-124">These elements add the named log listeners to `My.Application.Log` source.</span></span>  
  
4.  <span data-ttu-id="9db30-125">Localize os elementos `<add>` com os nomes dos ouvintes de log na seção `<sharedListeners>`, na seção `<system.diagnostics>`, na seção superior `<configuration>`.</span><span class="sxs-lookup"><span data-stu-id="9db30-125">Locate the `<add>` elements with the names of the log listeners in the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
5.  <span data-ttu-id="9db30-126">Para muitos tipos de ouvintes compartilhados, os dados de inicialização do ouvinte incluem uma descrição de onde o ouvinte direciona os dados:</span><span class="sxs-lookup"><span data-stu-id="9db30-126">For many types of shared listeners, the listener's initialization data includes a description of where the listener directs the data:</span></span>  
  
    -   <span data-ttu-id="9db30-127">Um ouvinte <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> grava em um arquivo de log, conforme descrito na introdução.</span><span class="sxs-lookup"><span data-stu-id="9db30-127">A <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> listener writes to a file log, as described in the introduction.</span></span>  
  
    -   <span data-ttu-id="9db30-128">O ouvinte <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> grava informações no log de eventos do computador especificado pelo parâmetro `initializeData`.</span><span class="sxs-lookup"><span data-stu-id="9db30-128">A <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> listener writes information to the computer event log specified by the `initializeData` parameter.</span></span> <span data-ttu-id="9db30-129">Para exibir um log de eventos, é possível usar o **Gerenciador de Servidores** ou o **Visualizador de Eventos do Windows**.</span><span class="sxs-lookup"><span data-stu-id="9db30-129">To view an event log, you can use **Server Explorer** or **Windows Event Viewer**.</span></span> <span data-ttu-id="9db30-130">Para obter mais informações, consulte [Eventos ETW no .NET Framework](../../../../framework/performance/etw-events.md).</span><span class="sxs-lookup"><span data-stu-id="9db30-130">For more information, see [ETW Events in the .NET Framework](../../../../framework/performance/etw-events.md).</span></span>  
  
    -   <span data-ttu-id="9db30-131">Os ouvintes <xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> e <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> gravam no arquivo especificado no parâmetro `initializeData`.</span><span class="sxs-lookup"><span data-stu-id="9db30-131">The <xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> and <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> listeners write to the file specified in the `initializeData` parameter.</span></span>  
  
    -   <span data-ttu-id="9db30-132">Um ouvinte <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> grava no console da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="9db30-132">A <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> listener writes to the command-line console.</span></span>  
  
    -   <span data-ttu-id="9db30-133">Para obter informações sobre onde outros tipos de ouvintes de log gravam informações, consulte a documentação daquele tipo.</span><span class="sxs-lookup"><span data-stu-id="9db30-133">For information about where other types of log listeners write information, consult that type's documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9db30-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9db30-134">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 <xref:System.Diagnostics.DefaultTraceListener>  
 <xref:System.Diagnostics.EventLogTraceListener>  
 <xref:System.Diagnostics.DelimitedListTraceListener>  
 <xref:System.Diagnostics.XmlWriterTraceListener>  
 <xref:System.Diagnostics.ConsoleTraceListener>  
 <xref:System.Diagnostics>  
 [<span data-ttu-id="9db30-135">Trabalhando com logs de aplicativo</span><span class="sxs-lookup"><span data-stu-id="9db30-135">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)  
 [<span data-ttu-id="9db30-136">Como registrar em log as exceções</span><span class="sxs-lookup"><span data-stu-id="9db30-136">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)  
 [<span data-ttu-id="9db30-137">Como gravar mensagens de log</span><span class="sxs-lookup"><span data-stu-id="9db30-137">How to: Write Log Messages</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)  
 [<span data-ttu-id="9db30-138">Instruções passo a passo: alterando onde My.Application.Log grava informações</span><span class="sxs-lookup"><span data-stu-id="9db30-138">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)  
 [<span data-ttu-id="9db30-139">Eventos ETW no .NET Framework</span><span class="sxs-lookup"><span data-stu-id="9db30-139">ETW Events in the .NET Framework</span></span>](../../../../framework/performance/etw-events.md)  
 [<span data-ttu-id="9db30-140">Solução de problemas: ouvintes de Log</span><span class="sxs-lookup"><span data-stu-id="9db30-140">Troubleshooting: Log Listeners</span></span>](../../../../visual-basic/developing-apps/programming/log-info/troubleshooting-log-listeners.md)
