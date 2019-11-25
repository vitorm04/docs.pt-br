---
title: Trabalhando com logs de aplicativo
ms.date: 07/20/2015
helpviewer_keywords:
- logs, application
- application event logs, Visual Basic
- application event logs
ms.assetid: 2581afd1-5791-4bc4-86b2-46244e9fe468
ms.openlocfilehash: 617b940d2cf15779ae3c10e4663b63c9771d44b6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345895"
---
# <a name="working-with-application-logs-in-visual-basic"></a><span data-ttu-id="caa1a-102">Trabalhando com logs de aplicativo no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="caa1a-102">Working with Application Logs in Visual Basic</span></span>

<span data-ttu-id="caa1a-103">Os objetos `My.Application.Log` e `My.Log` facilitam a gravação de informações de registro em log e rastreamento em logs.</span><span class="sxs-lookup"><span data-stu-id="caa1a-103">The `My.Application.Log` and `My.Log` objects make it easy to write logging and tracing information to logs.</span></span>

## <a name="how-messages-are-logged"></a><span data-ttu-id="caa1a-104">Como as mensagens são registradas em log</span><span class="sxs-lookup"><span data-stu-id="caa1a-104">How Messages are Logged</span></span>

<span data-ttu-id="caa1a-105">Primeiro, a gravidade da mensagem é verificada com a propriedade <xref:System.Diagnostics.TraceSource.Switch%2A> da propriedade <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A> do log.</span><span class="sxs-lookup"><span data-stu-id="caa1a-105">First, the severity of the message is checked with the <xref:System.Diagnostics.TraceSource.Switch%2A> property of the log's <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A> property.</span></span> <span data-ttu-id="caa1a-106">Por padrão, somente mensagens com gravidade "Information" e superior são passadas para os ouvintes de rastreamento, especificados na coleção `TraceListener` do log.</span><span class="sxs-lookup"><span data-stu-id="caa1a-106">By default, only messages of severity "Information" and higher are passed on to the trace listeners, specified in the log's `TraceListener` collection.</span></span> <span data-ttu-id="caa1a-107">Em seguida, cada ouvinte compara a gravidade da mensagem com a propriedade <xref:System.Diagnostics.TraceSource.Switch%2A> do ouvinte.</span><span class="sxs-lookup"><span data-stu-id="caa1a-107">Then, each listener compares the severity of the message to the listener's <xref:System.Diagnostics.TraceSource.Switch%2A> property.</span></span> <span data-ttu-id="caa1a-108">Se a gravidade da mensagem for alta o suficiente, o ouvinte gravará a mensagem.</span><span class="sxs-lookup"><span data-stu-id="caa1a-108">If the message's severity is high enough, the listener writes out the message.</span></span>

<span data-ttu-id="caa1a-109">O diagrama a seguir mostra como uma mensagem gravada no método `WriteEntry` é passada para os métodos `WriteLine` dos ouvintes de rastreamento do log:</span><span class="sxs-lookup"><span data-stu-id="caa1a-109">The following diagram shows how a message written to the `WriteEntry` method gets passed to the `WriteLine` methods of the log's trace listeners:</span></span>

![Diagrama que mostra a chamada Meu log.](./media/working-with-application-logs/my-log-call-messages.png)

<span data-ttu-id="caa1a-111">É possível alterar o comportamento do log e dos ouvintes de rastreamento alterando o arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="caa1a-111">You can change the behavior of the log and the trace listeners by changing the application's configuration file.</span></span> <span data-ttu-id="caa1a-112">O diagrama a seguir mostra a correspondência entre as partes do log e o arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="caa1a-112">The following diagram shows the correspondence between the parts of the log and the configuration file.</span></span>

![Diagrama que mostra a configuração Meu log.](./media/working-with-application-logs/my-log-configuration.png)

## <a name="where-messages-are-logged"></a><span data-ttu-id="caa1a-114">Onde as mensagens são registradas em log</span><span class="sxs-lookup"><span data-stu-id="caa1a-114">Where Messages are Logged</span></span>

<span data-ttu-id="caa1a-115">Se o assembly não tiver nenhum arquivo de configuração, os objetos `My.Application.Log` e `My.Log` serão gravados na saída de depuração do aplicativo (por meio da classe <xref:System.Diagnostics.DefaultTraceListener>).</span><span class="sxs-lookup"><span data-stu-id="caa1a-115">If the assembly has no configuration file, the `My.Application.Log` and `My.Log` objects write to the application's debug output (through the <xref:System.Diagnostics.DefaultTraceListener> class).</span></span> <span data-ttu-id="caa1a-116">Além disso, o objeto `My.Application.Log` é gravado no arquivo de log do assembly (por meio da classe <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>), enquanto o objeto `My.Log` é gravado na saída da página da Web do ASP.NET (por meio da classe <xref:System.Web.WebPageTraceListener>).</span><span class="sxs-lookup"><span data-stu-id="caa1a-116">In addition, the `My.Application.Log` object writes to the assembly's log file (through the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class), while the `My.Log` object writes to the ASP.NET Web page's output (through the <xref:System.Web.WebPageTraceListener> class).</span></span>

<span data-ttu-id="caa1a-117">A saída de depuração pode ser vista na janela **Saída** do Visual Studio ao executar o aplicativo no modo de depuração.</span><span class="sxs-lookup"><span data-stu-id="caa1a-117">The debug output can be viewed in the Visual Studio **Output** window when running your application in debug mode.</span></span> <span data-ttu-id="caa1a-118">Para abrir a janela **Saída**, clique no item de menu **Depuração**, aponte para **Janelas** e, em seguida, clique em **Saída**.</span><span class="sxs-lookup"><span data-stu-id="caa1a-118">To open the **Output** window, click the **Debug** menu item, point to **Windows**, and then click **Output**.</span></span> <span data-ttu-id="caa1a-119">Na janela **Saída**, selecione **Depuração** na caixa **Mostrar saída de**.</span><span class="sxs-lookup"><span data-stu-id="caa1a-119">In the **Output** window, select **Debug** from the **Show output from** box.</span></span>

<span data-ttu-id="caa1a-120">Por padrão, `My.Application.Log` grava o arquivo de log no caminho para os dados de aplicativo do usuário.</span><span class="sxs-lookup"><span data-stu-id="caa1a-120">By default, `My.Application.Log` writes the log file in the path for the user's application data.</span></span> <span data-ttu-id="caa1a-121">Você pode obter o caminho pela propriedade <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.FullLogFileName%2A> do objeto <xref:Microsoft.VisualBasic.Logging.Log.DefaultFileLogWriter%2A>.</span><span class="sxs-lookup"><span data-stu-id="caa1a-121">You can get the path from the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.FullLogFileName%2A> property of the <xref:Microsoft.VisualBasic.Logging.Log.DefaultFileLogWriter%2A> object.</span></span> <span data-ttu-id="caa1a-122">O formato do caminho é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="caa1a-122">The format of that path is as follows:</span></span>

`BasePath`\\`CompanyName`\\`ProductName`\\`ProductVersion`

<span data-ttu-id="caa1a-123">Um valor típico para `BasePath` é o seguinte.</span><span class="sxs-lookup"><span data-stu-id="caa1a-123">A typical value for `BasePath` is as follows.</span></span>

<span data-ttu-id="caa1a-124">C:\Documents and Settings\\`username`\Application Data</span><span class="sxs-lookup"><span data-stu-id="caa1a-124">C:\Documents and Settings\\`username`\Application Data</span></span>

<span data-ttu-id="caa1a-125">Os valores de `CompanyName`, `ProductName` e `ProductVersion` vêm das informações do assembly do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="caa1a-125">The values of `CompanyName`, `ProductName`, and `ProductVersion` come from the application's assembly information.</span></span> <span data-ttu-id="caa1a-126">O formato do nome do arquivo de log é *AssemblyName*.log, em que *AssemblyName* é o nome do arquivo do assembly sem a extensão.</span><span class="sxs-lookup"><span data-stu-id="caa1a-126">The form of the log file name is *AssemblyName*.log, where *AssemblyName* is the file name of the assembly without the extension.</span></span> <span data-ttu-id="caa1a-127">Se mais de um arquivo de log for necessário, como quando o log original não está disponível quando o aplicativo tenta gravar no log, o formato do nome do arquivo de log será *AssemblyName*-*iteration*.log, em que `iteration` é um `Integer` positivo.</span><span class="sxs-lookup"><span data-stu-id="caa1a-127">If more than one log file is needed, such as when the original log is unavailable when the application attempts to write to the log, the form for the log file name is *AssemblyName*-*iteration*.log, where `iteration` is a positive `Integer`.</span></span>

<span data-ttu-id="caa1a-128">Você pode substituir o comportamento padrão adicionando ou alterando os arquivos de configuração de aplicativo e do computador.</span><span class="sxs-lookup"><span data-stu-id="caa1a-128">You can override the default behavior by adding or changing the computer's and the application's configuration files.</span></span> <span data-ttu-id="caa1a-129">Para obter mais informações, consulte [Instruções passo a passo: Alterando onde My.Application.Log grava informações](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md).</span><span class="sxs-lookup"><span data-stu-id="caa1a-129">For more information, see [Walkthrough: Changing Where My.Application.Log Writes Information](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md).</span></span>

## <a name="configuring-log-settings"></a><span data-ttu-id="caa1a-130">Definindo configurações de log</span><span class="sxs-lookup"><span data-stu-id="caa1a-130">Configuring Log Settings</span></span>

<span data-ttu-id="caa1a-131">The `Log` object has a default implementation that works without an application configuration file, app.config. To change the defaults, you must add a configuration file with the new settings.</span><span class="sxs-lookup"><span data-stu-id="caa1a-131">The `Log` object has a default implementation that works without an application configuration file, app.config. To change the defaults, you must add a configuration file with the new settings.</span></span> <span data-ttu-id="caa1a-132">Para obter mais informações, consulte [Instruções passo a passo: filtrando a saída de My.Application.Log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).</span><span class="sxs-lookup"><span data-stu-id="caa1a-132">For more information, see [Walkthrough: Filtering My.Application.Log Output](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).</span></span>

<span data-ttu-id="caa1a-133">As seções de configuração de log ficam localizadas no nó `<system.diagnostics>` no nó `<configuration>` principal do arquivo app.config.</span><span class="sxs-lookup"><span data-stu-id="caa1a-133">The log configuration sections are located in the `<system.diagnostics>` node in the main `<configuration>` node of the app.config file.</span></span> <span data-ttu-id="caa1a-134">As informações de log são definidas em vários nós:</span><span class="sxs-lookup"><span data-stu-id="caa1a-134">Log information is defined in several nodes:</span></span>

- <span data-ttu-id="caa1a-135">Os ouvintes para o objeto `Log` são definidos no nó `<sources>` chamado DefaultSource.</span><span class="sxs-lookup"><span data-stu-id="caa1a-135">The listeners for the `Log` object are defined in the `<sources>` node named DefaultSource.</span></span>

- <span data-ttu-id="caa1a-136">O filtro de gravidade para o objeto `Log` é definido no nó `<switches>` chamado DefaultSwitch.</span><span class="sxs-lookup"><span data-stu-id="caa1a-136">The severity filter for the `Log` object is defined in the `<switches>` node named DefaultSwitch.</span></span>

- <span data-ttu-id="caa1a-137">Os ouvintes de log são definidos no nó `<sharedListeners>`.</span><span class="sxs-lookup"><span data-stu-id="caa1a-137">The log listeners are defined in the `<sharedListeners>` node.</span></span>

 <span data-ttu-id="caa1a-138">Exemplos dos nós `<sources>`, `<switches>` e `<sharedListeners>` são mostrados no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="caa1a-138">Examples of `<sources>`, `<switches>`, and `<sharedListeners>` nodes are shown in the following code:</span></span>

```xml
<configuration>
  <system.diagnostics>
    <sources>
      <source name="DefaultSource" switchName="DefaultSwitch">
        <listeners>
          <add name="FileLog"/>
        </listeners>
      </source>
    </sources>
    <switches>
      <add name="DefaultSwitch" value="Information" />
    </switches>
    <sharedListeners>
      <add name="FileLog"
        type="Microsoft.VisualBasic.Logging.FileLogTraceListener,
          Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral,
          PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL"
        initializeData="FileLogWriter"
      />
    </sharedListeners>
  </system.diagnostics>
</configuration>
```

## <a name="changing-log-settings-after-deployment"></a><span data-ttu-id="caa1a-139">Alterando configurações de log após a implantação</span><span class="sxs-lookup"><span data-stu-id="caa1a-139">Changing Log Settings after Deployment</span></span>

<span data-ttu-id="caa1a-140">Quando você desenvolve um aplicativo, suas configurações são armazenadas no arquivo app.config, conforme mostrado nos exemplos acima.</span><span class="sxs-lookup"><span data-stu-id="caa1a-140">When you develop an application, its configuration settings are stored in the app.config file, as shown in the examples above.</span></span> <span data-ttu-id="caa1a-141">Após implantar o aplicativo, você ainda pode configurar o log editando o arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="caa1a-141">After you deploy your application, you can still configure the log by editing the configuration file.</span></span> <span data-ttu-id="caa1a-142">Em um aplicativo baseado no Windows, o nome do arquivo é *applicationName*.exe.config e ele deve residir na mesma pasta que o arquivo executável.</span><span class="sxs-lookup"><span data-stu-id="caa1a-142">In a Windows-based application, this file's name is *applicationName*.exe.config, and it must reside in the same folder as the executable file.</span></span> <span data-ttu-id="caa1a-143">Para um aplicativo Web, este é o arquivo Web.config associado ao projeto.</span><span class="sxs-lookup"><span data-stu-id="caa1a-143">For a Web application, this is the Web.config file associated with the project.</span></span>

<span data-ttu-id="caa1a-144">Quando seu aplicativo executa o código que cria uma instância de uma classe pela primeira vez, ele verifica o arquivo de configuração para obter informações sobre o objeto.</span><span class="sxs-lookup"><span data-stu-id="caa1a-144">When your application executes the code that creates an instance of a class for the first time, it checks the configuration file for information about the object.</span></span> <span data-ttu-id="caa1a-145">Para o objeto `Log`, isso ocorre na primeira vez em que o objeto `Log` é acessado.</span><span class="sxs-lookup"><span data-stu-id="caa1a-145">For the `Log` object, this happens the first time the `Log` object is accessed.</span></span> <span data-ttu-id="caa1a-146">O sistema examina o arquivo de configuração apenas uma vez para qualquer objeto em particular – na primeira vez em que seu aplicativo cria o objeto.</span><span class="sxs-lookup"><span data-stu-id="caa1a-146">The system examines the configuration file only once for any particular object—the first time your application creates the object.</span></span> <span data-ttu-id="caa1a-147">Portanto, talvez seja necessário reiniciar o aplicativo para que as alterações entrem em vigor.</span><span class="sxs-lookup"><span data-stu-id="caa1a-147">Therefore, you may need to restart the application for the changes to take effect.</span></span>

<span data-ttu-id="caa1a-148">Em um aplicativo implantado, você habilita o código de rastreamento reconfigurando objetos de opção antes de iniciar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="caa1a-148">In a deployed application, you enable trace code by reconfiguring switch objects before your application starts.</span></span> <span data-ttu-id="caa1a-149">Normalmente, isso envolve ativar e desativar os objetos de opção ou alterar os níveis de rastreamento e, então, reiniciar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="caa1a-149">Typically, this involves turning the switch objects on and off or by changing the tracing levels, and then restarting your application.</span></span>

## <a name="security-considerations"></a><span data-ttu-id="caa1a-150">Considerações sobre segurança</span><span class="sxs-lookup"><span data-stu-id="caa1a-150">Security Considerations</span></span>

<span data-ttu-id="caa1a-151">Considere o seguinte ao gravar dados no log:</span><span class="sxs-lookup"><span data-stu-id="caa1a-151">Consider the following when writing data to the log:</span></span>

- <span data-ttu-id="caa1a-152">**Evite vazar informações do usuário.**</span><span class="sxs-lookup"><span data-stu-id="caa1a-152">**Avoid leaking user information.**</span></span> <span data-ttu-id="caa1a-153">Certifique-se de que seu aplicativo grave somente informações aprovadas no log.</span><span class="sxs-lookup"><span data-stu-id="caa1a-153">Ensure that your application writes only approved information to the log.</span></span> <span data-ttu-id="caa1a-154">Por exemplo, pode ser aceitável que o log do aplicativo contenha nomes de usuário, mas não senhas.</span><span class="sxs-lookup"><span data-stu-id="caa1a-154">For example, it may be acceptable for the application log to contain user names, but not user passwords.</span></span>

- <span data-ttu-id="caa1a-155">**Proteja os locais do log.**</span><span class="sxs-lookup"><span data-stu-id="caa1a-155">**Make log locations secure.**</span></span> <span data-ttu-id="caa1a-156">Qualquer log que contiver informações possivelmente confidenciais deve ser armazenado em um local seguro.</span><span class="sxs-lookup"><span data-stu-id="caa1a-156">Any log that contains potentially sensitive information should be stored in a secure location.</span></span>

- <span data-ttu-id="caa1a-157">**Evite informações enganosas.**</span><span class="sxs-lookup"><span data-stu-id="caa1a-157">**Avoid misleading information.**</span></span> <span data-ttu-id="caa1a-158">Em geral, seu aplicativo deve validar todos os dados inseridos por um usuário antes de usar esses dados.</span><span class="sxs-lookup"><span data-stu-id="caa1a-158">In general, your application should validate all data entered by a user before using that data.</span></span> <span data-ttu-id="caa1a-159">Isso inclui gravar dados no log do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="caa1a-159">This includes writing data to the application log.</span></span>

- <span data-ttu-id="caa1a-160">**Evite situações de negação de serviço.**</span><span class="sxs-lookup"><span data-stu-id="caa1a-160">**Avoid denial of service.**</span></span> <span data-ttu-id="caa1a-161">Se seu aplicativo gravar muitas informações no log, ele poderá encher o log ou tornar difícil de encontrar informações importantes.</span><span class="sxs-lookup"><span data-stu-id="caa1a-161">If your application writes too much information to the log, it could fill the log or make finding important information difficult.</span></span>

## <a name="see-also"></a><span data-ttu-id="caa1a-162">Consulte também</span><span class="sxs-lookup"><span data-stu-id="caa1a-162">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [<span data-ttu-id="caa1a-163">Registrando informações em log no aplicativo</span><span class="sxs-lookup"><span data-stu-id="caa1a-163">Logging Information from the Application</span></span>](../../../../visual-basic/developing-apps/programming/log-info/index.md)
