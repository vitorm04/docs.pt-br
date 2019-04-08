---
title: Filtrando a saída de My.Application.Log (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My.Log object, filtering output
- My.Application.Log object, filtering output
- application event logs, output filtering
ms.assetid: 2c0a457a-38a4-49e1-934d-a51320b7b4ca
ms.openlocfilehash: f38217a5385b9d736eaa744a73024f210eb8f553
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58829363"
---
# <a name="walkthrough-filtering-myapplicationlog-output-visual-basic"></a><span data-ttu-id="a30b1-102">Passo a passo: Filtrando a saída de My.Application.Log (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a30b1-102">Walkthrough: Filtering My.Application.Log Output (Visual Basic)</span></span>
<span data-ttu-id="a30b1-103">Este passo a passo demonstra como alterar a filtragem de log padrão do objeto `My.Application.Log` para controlar quais informações são passadas do objeto `Log` para os ouvintes e quais informações são gravadas pelos ouvintes.</span><span class="sxs-lookup"><span data-stu-id="a30b1-103">This walkthrough demonstrates how to change the default log filtering for the `My.Application.Log` object, to control what information is passed from the `Log` object to the listeners and what information is written by the listeners.</span></span> <span data-ttu-id="a30b1-104">Você pode alterar o comportamento de registro em log mesmo após ter compilado o aplicativo, porque as informações de configuração são armazenadas no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a30b1-104">You can change the logging behavior even after building the application, because the configuration information is stored in the application's configuration file.</span></span>  
  
## <a name="getting-started"></a><span data-ttu-id="a30b1-105">Guia de Introdução</span><span class="sxs-lookup"><span data-stu-id="a30b1-105">Getting Started</span></span>  
 <span data-ttu-id="a30b1-106">Cada mensagem que `My.Application.Log` grava tem um nível de gravidade associado, que os mecanismos de filtragem usam para controlar a saída de log.</span><span class="sxs-lookup"><span data-stu-id="a30b1-106">Each message that `My.Application.Log` writes has an associated severity level, which filtering mechanisms use to control the log output.</span></span> <span data-ttu-id="a30b1-107">Este aplicativo de exemplo usa métodos `My.Application.Log` para gravar diversas mensagens de log com diferentes níveis de gravidade.</span><span class="sxs-lookup"><span data-stu-id="a30b1-107">This sample application uses `My.Application.Log` methods to write several log messages with different severity levels.</span></span>  
  
#### <a name="to-build-the-sample-application"></a><span data-ttu-id="a30b1-108">Para compilar o aplicativo de exemplo</span><span class="sxs-lookup"><span data-stu-id="a30b1-108">To build the sample application</span></span>  
  
1.  <span data-ttu-id="a30b1-109">Abra um novo projeto de aplicativo do Windows Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="a30b1-109">Open a new Visual Basic Windows Application project.</span></span>  
  
2.  <span data-ttu-id="a30b1-110">Adicione um botão denominado Button1 a Form1.</span><span class="sxs-lookup"><span data-stu-id="a30b1-110">Add a button named Button1 to Form1.</span></span>  
  
3.  <span data-ttu-id="a30b1-111">No manipulador de eventos <xref:System.Windows.Forms.Control.Click> de Button1, adicione o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="a30b1-111">In the <xref:System.Windows.Forms.Control.Click> event handler for Button1, add the following code:</span></span>  
  
     [!code-vb[VbVbcnMyApplicationLogFiltering#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyApplicationLogFiltering/VB/Form1.vb#1)]  
  
4.  <span data-ttu-id="a30b1-112">Execute o aplicativo no depurador.</span><span class="sxs-lookup"><span data-stu-id="a30b1-112">Run the application in the debugger.</span></span>  
  
5.  <span data-ttu-id="a30b1-113">Pressione **Button1**.</span><span class="sxs-lookup"><span data-stu-id="a30b1-113">Press **Button1**.</span></span>  
  
     <span data-ttu-id="a30b1-114">O aplicativo grava as informações a seguir no arquivo de log e na saída da depuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a30b1-114">The application writes the following information to the application's debug output and log file.</span></span>  
  
     `DefaultSource Information: 0 : In Button1_Click`  
  
     `DefaultSource Error: 2 : Error in the application.`  
  
6.  <span data-ttu-id="a30b1-115">Feche o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a30b1-115">Close the application.</span></span>  
  
     <span data-ttu-id="a30b1-116">Para obter informações sobre como exibir a janela de saída de depuração do aplicativo, consulte [Janela de Saída](/visualstudio/ide/reference/output-window).</span><span class="sxs-lookup"><span data-stu-id="a30b1-116">For information on how to view the application's debug output window, see [Output Window](/visualstudio/ide/reference/output-window).</span></span> <span data-ttu-id="a30b1-117">Para obter informações sobre a localização do arquivo de log do aplicativo, confira [Passo a passo: Determinando o local em que My.Application.Log grava informações](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).</span><span class="sxs-lookup"><span data-stu-id="a30b1-117">For information on the location of the application's log file, see [Walkthrough: Determining Where My.Application.Log Writes Information](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a30b1-118">Por padrão, o aplicativo libera a saída do arquivo de log quando é fechado.</span><span class="sxs-lookup"><span data-stu-id="a30b1-118">By default, the application flushes the log-file output when the application closes.</span></span>  
  
     <span data-ttu-id="a30b1-119">No exemplo acima, a segunda chamada para o método <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A> e a chamada para o método <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A> produzem a saída de log, enquanto as primeira e última chamadas para o método `WriteEntry` não.</span><span class="sxs-lookup"><span data-stu-id="a30b1-119">In the example above, the second call to the <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A> method and the call to the <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A> method produces log output, while the first and last calls to the `WriteEntry` method do not.</span></span> <span data-ttu-id="a30b1-120">Isso ocorre porque os níveis de gravidade de `WriteEntry` e `WriteException` são "Information" e "Error", que são permitidos pela filtragem de log padrão do objeto `My.Application.Log`.</span><span class="sxs-lookup"><span data-stu-id="a30b1-120">This is because the severity levels of `WriteEntry` and `WriteException` are "Information" and "Error", both of which are allowed by the `My.Application.Log` object's default log filtering.</span></span> <span data-ttu-id="a30b1-121">No entanto, os eventos com os níveis de gravidade "Start" e "Stop" são impedidos de produzir a saída de log.</span><span class="sxs-lookup"><span data-stu-id="a30b1-121">However, events with "Start" and "Stop" severity levels are prevented from producing log output.</span></span>  
  
## <a name="filtering-for-all-myapplicationlog-listeners"></a><span data-ttu-id="a30b1-122">Filtragem de ouvintes de My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="a30b1-122">Filtering for All My.Application.Log Listeners</span></span>  
 <span data-ttu-id="a30b1-123">O objeto `My.Application.Log` usa um <xref:System.Diagnostics.SourceSwitch> chamado `DefaultSwitch` para controlar quais mensagens ele passa dos métodos `WriteEntry` e `WriteException` para os ouvintes de log.</span><span class="sxs-lookup"><span data-stu-id="a30b1-123">The `My.Application.Log` object uses a <xref:System.Diagnostics.SourceSwitch> named `DefaultSwitch` to control which messages it passes from the `WriteEntry` and `WriteException` methods to the log listeners.</span></span> <span data-ttu-id="a30b1-124">Você pode configurar `DefaultSwitch` no arquivo de configuração de aplicativo definindo seu valor como um dos valores de enumeração <xref:System.Diagnostics.SourceLevels>.</span><span class="sxs-lookup"><span data-stu-id="a30b1-124">You can configure `DefaultSwitch` in the application's configuration file by setting its value to one of the <xref:System.Diagnostics.SourceLevels> enumeration values.</span></span> <span data-ttu-id="a30b1-125">Por padrão, seu valor é “Information".</span><span class="sxs-lookup"><span data-stu-id="a30b1-125">By default, its value is "Information".</span></span>  
  
 <span data-ttu-id="a30b1-126">Esta tabela mostra o nível de gravidade necessário para o log gravar uma mensagem nos ouvintes, dada uma determinada configuração `DefaultSwitch`.</span><span class="sxs-lookup"><span data-stu-id="a30b1-126">This table shows the severity level required for Log to write a message to the listeners, given a particular `DefaultSwitch` setting.</span></span>  
  
|<span data-ttu-id="a30b1-127">Valor DefaultSwitch</span><span class="sxs-lookup"><span data-stu-id="a30b1-127">DefaultSwitch Value</span></span>|<span data-ttu-id="a30b1-128">Gravidade da mensagem necessária para a saída</span><span class="sxs-lookup"><span data-stu-id="a30b1-128">Message severity required for output</span></span>|  
|---|---| 
|`Critical`|`Critical`|  
|`Error`|<span data-ttu-id="a30b1-129">`Critical` ou `Error`</span><span class="sxs-lookup"><span data-stu-id="a30b1-129">`Critical` or `Error`</span></span>|  
|`Warning`|<span data-ttu-id="a30b1-130">`Critical`, `Error` ou `Warning`</span><span class="sxs-lookup"><span data-stu-id="a30b1-130">`Critical`, `Error`, or `Warning`</span></span>|  
|`Information`|<span data-ttu-id="a30b1-131">`Critical`, `Error`, `Warning` ou `Information`</span><span class="sxs-lookup"><span data-stu-id="a30b1-131">`Critical`, `Error`, `Warning`, or `Information`</span></span>|  
|`Verbose`|<span data-ttu-id="a30b1-132">`Critical`, `Error`, `Warning`, `Information` ou `Verbose`</span><span class="sxs-lookup"><span data-stu-id="a30b1-132">`Critical`, `Error`, `Warning`, `Information`, or `Verbose`</span></span>|  
|`ActivityTracing`|<span data-ttu-id="a30b1-133">`Start`, `Stop`, `Suspend`, `Resume` ou `Transfer`</span><span class="sxs-lookup"><span data-stu-id="a30b1-133">`Start`, `Stop`, `Suspend`, `Resume`, or `Transfer`</span></span>|  
|`All`|<span data-ttu-id="a30b1-134">Todas as mensagens são permitidas.</span><span class="sxs-lookup"><span data-stu-id="a30b1-134">All messages are allowed.</span></span>|  
|`Off`|<span data-ttu-id="a30b1-135">Todas as mensagens são bloqueadas.</span><span class="sxs-lookup"><span data-stu-id="a30b1-135">All messages are blocked.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="a30b1-136">Os métodos `WriteEntry` e `WriteException` têm uma sobrecarga que não especifica um nível de gravidade.</span><span class="sxs-lookup"><span data-stu-id="a30b1-136">The `WriteEntry` and `WriteException` methods each have an overload that does not specify a severity level.</span></span> <span data-ttu-id="a30b1-137">O nível de gravidade implícito para a sobrecarga `WriteEntry` é "Information" e o nível de gravidade implícito para a sobrecarga `WriteException` é "Error".</span><span class="sxs-lookup"><span data-stu-id="a30b1-137">The implicit severity level for the `WriteEntry` overload is "Information", and the implicit severity level for the `WriteException` overload is "Error".</span></span>  
  
 <span data-ttu-id="a30b1-138">Esta tabela explica a saída de log mostrada no exemplo anterior: com a configuração de `DefaultSwitch` padrão de "Information", apenas a segunda chamada para o método `WriteEntry` e a chamada para o método `WriteException` produzem a saída de log.</span><span class="sxs-lookup"><span data-stu-id="a30b1-138">This table explains the log output shown in the previous example: with the default `DefaultSwitch` setting of "Information", only the second call to the `WriteEntry` method and the call to the `WriteException` method produce log output.</span></span>  
  
#### <a name="to-log-only-activity-tracing-events"></a><span data-ttu-id="a30b1-139">Para registrar em log apenas eventos de rastreamento de atividade</span><span class="sxs-lookup"><span data-stu-id="a30b1-139">To log only activity tracing events</span></span>  
  
1.  <span data-ttu-id="a30b1-140">Clique com o botão direito do mouse em app.config no **Gerenciador de Soluções** e selecione **Abrir**.</span><span class="sxs-lookup"><span data-stu-id="a30b1-140">Right-click app.config in the **Solution Explorer** and select **Open**.</span></span>  
  
     <span data-ttu-id="a30b1-141">- ou -</span><span class="sxs-lookup"><span data-stu-id="a30b1-141">-or-</span></span>  
  
     <span data-ttu-id="a30b1-142">Se não houver nenhum arquivo app.config:</span><span class="sxs-lookup"><span data-stu-id="a30b1-142">If there is no app.config file:</span></span>  
  
    1.  <span data-ttu-id="a30b1-143">No menu **Projeto**, escolha **Adicionar Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="a30b1-143">On the **Project** menu, choose **Add New Item**.</span></span>  
  
    2.  <span data-ttu-id="a30b1-144">Na caixa de diálogo **Adicionar novo item**, escolha **Arquivo de configuração de aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="a30b1-144">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>  
  
    3.  <span data-ttu-id="a30b1-145">Clique em **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="a30b1-145">Click **Add**.</span></span>  
  
2.  <span data-ttu-id="a30b1-146">Localize a seção `<switches>`, que está na seção `<system.diagnostics>`, que está na seção `<configuration>` superior.</span><span class="sxs-lookup"><span data-stu-id="a30b1-146">Locate the `<switches>` section, which is in the `<system.diagnostics>` section, which is in the top-level `<configuration>` section.</span></span>  
  
3.  <span data-ttu-id="a30b1-147">Localize o elemento que adiciona `DefaultSwitch` à coleção de opções.</span><span class="sxs-lookup"><span data-stu-id="a30b1-147">Find the element that adds `DefaultSwitch` to the collection of switches.</span></span> <span data-ttu-id="a30b1-148">Ele deve ser semelhante a este:</span><span class="sxs-lookup"><span data-stu-id="a30b1-148">It should look similar to this element:</span></span>  
  
     `<add name="DefaultSwitch" value="Information" />`  
  
4.  <span data-ttu-id="a30b1-149">Altere o valor do atributo `value` para "ActivityTracing".</span><span class="sxs-lookup"><span data-stu-id="a30b1-149">Change the value of the `value` attribute to "ActivityTracing".</span></span>  
  
5.  <span data-ttu-id="a30b1-150">O conteúdo do arquivo app.config deve ser semelhante ao XML a seguir:</span><span class="sxs-lookup"><span data-stu-id="a30b1-150">The content of the app.config file should be similar to the following XML:</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.diagnostics>  
        <sources>  
          <!-- This section configures My.Application.Log -->  
          <source name="DefaultSource" switchName="DefaultSwitch">  
            <listeners>  
              <add name="FileLog"/>  
            </listeners>  
          </source>  
        </sources>  
        <switches>  
          <add name="DefaultSwitch" value="ActivityTracing" />  
        </switches>  
        <sharedListeners>  
          <add name="FileLog"  
               type="Microsoft.VisualBasic.Logging.FileLogTraceListener,   
                     Microsoft.VisualBasic, Version=8.0.0.0,   
                     Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a,   
                     processorArchitecture=MSIL"   
               initializeData="FileLogWriter"/>  
        </sharedListeners>  
      </system.diagnostics>  
    </configuration>  
    ```  
  
6.  <span data-ttu-id="a30b1-151">Execute o aplicativo no depurador.</span><span class="sxs-lookup"><span data-stu-id="a30b1-151">Run the application in the debugger.</span></span>  
  
7.  <span data-ttu-id="a30b1-152">Pressione **Button1**.</span><span class="sxs-lookup"><span data-stu-id="a30b1-152">Press **Button1**.</span></span>  
  
     <span data-ttu-id="a30b1-153">O aplicativo grava as informações a seguir no arquivo de log e na saída da depuração do aplicativo:</span><span class="sxs-lookup"><span data-stu-id="a30b1-153">The application writes the following information to the application's debug output and log file:</span></span>  
  
     `DefaultSource Start: 4 : Entering Button1_Click`  
  
     `DefaultSource Stop: 5 : Leaving Button1_Click`  
  
8.  <span data-ttu-id="a30b1-154">Feche o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a30b1-154">Close the application.</span></span>  
  
9. <span data-ttu-id="a30b1-155">Altere o valor do atributo `value` de volta para "Information".</span><span class="sxs-lookup"><span data-stu-id="a30b1-155">Change the value of the `value` attribute back to "Information".</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a30b1-156">A configuração da opção `DefaultSwitch` controla apenas `My.Application.Log`.</span><span class="sxs-lookup"><span data-stu-id="a30b1-156">The `DefaultSwitch` switch setting controls only `My.Application.Log`.</span></span> <span data-ttu-id="a30b1-157">Ele não altera como as classes [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.Diagnostics.Trace?displayProperty=nameWithType> e <xref:System.Diagnostics.Debug?displayProperty=nameWithType> se comportam.</span><span class="sxs-lookup"><span data-stu-id="a30b1-157">It does not change how the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.Diagnostics.Trace?displayProperty=nameWithType> and <xref:System.Diagnostics.Debug?displayProperty=nameWithType> classes behave.</span></span>  
  
## <a name="individual-filtering-for-myapplicationlog-listeners"></a><span data-ttu-id="a30b1-158">Filtragem individual de ouvintes de My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="a30b1-158">Individual Filtering For My.Application.Log Listeners</span></span>  
 <span data-ttu-id="a30b1-159">O exemplo anterior mostra como alterar a filtragem para toda a saída `My.Application.Log`.</span><span class="sxs-lookup"><span data-stu-id="a30b1-159">The previous example shows how to change the filtering for all `My.Application.Log` output.</span></span> <span data-ttu-id="a30b1-160">Este exemplo demonstra como filtrar um ouvinte de log individual.</span><span class="sxs-lookup"><span data-stu-id="a30b1-160">This example demonstrates how to filter an individual log listener.</span></span> <span data-ttu-id="a30b1-161">Por padrão, um aplicativo tem dois ouvintes que gravam na saída de depuração do aplicativo e no arquivo de log.</span><span class="sxs-lookup"><span data-stu-id="a30b1-161">By default, an application has two listeners that write to the application's debug output and the log file.</span></span>  
  
 <span data-ttu-id="a30b1-162">O arquivo de configuração controla o comportamento dos ouvintes de log, permitindo que cada um deles tenha um filtro, que é semelhante a uma opção para `My.Application.Log`.</span><span class="sxs-lookup"><span data-stu-id="a30b1-162">The configuration file controls the behavior of the log listeners by allowing each one to have a filter, which is similar to a switch for `My.Application.Log`.</span></span> <span data-ttu-id="a30b1-163">Um ouvinte de log produzirá uma mensagem somente se a gravidade da mensagem for permitida pelo `DefaultSwitch` do log e pelo filtro do ouvinte de log.</span><span class="sxs-lookup"><span data-stu-id="a30b1-163">A log listener will output a message only if the message's severity is allowed by both the log's `DefaultSwitch` and the log listener's filter.</span></span>  
  
 <span data-ttu-id="a30b1-164">Este exemplo demonstra como configurar a filtragem para um novo ouvinte de depuração e adicioná-lo ao objeto `Log`.</span><span class="sxs-lookup"><span data-stu-id="a30b1-164">This example demonstrates how to configure filtering for a new debug listener and add it to the `Log` object.</span></span> <span data-ttu-id="a30b1-165">O ouvinte de depuração padrão deve ser removido do objeto `Log`, de modo que seja claro que as mensagens de depuração são provenientes do novo ouvinte de depuração.</span><span class="sxs-lookup"><span data-stu-id="a30b1-165">The default debug listener should be removed from the `Log` object, so it is clear that the debug messages come from the new debug listener.</span></span>  
  
#### <a name="to-log-only-activity-tracing-events"></a><span data-ttu-id="a30b1-166">Para registrar em log apenas eventos de rastreamento de atividade</span><span class="sxs-lookup"><span data-stu-id="a30b1-166">To log only activity-tracing events</span></span>  
  
1.  <span data-ttu-id="a30b1-167">Clique com o botão direito do mouse em app.config no **Gerenciador de Soluções** e escolha **Abrir**.</span><span class="sxs-lookup"><span data-stu-id="a30b1-167">Right-click app.config in the **Solution Explorer** and choose **Open**.</span></span>  
  
     <span data-ttu-id="a30b1-168">- ou -</span><span class="sxs-lookup"><span data-stu-id="a30b1-168">-or-</span></span>  
  
     <span data-ttu-id="a30b1-169">Se não houver nenhum arquivo app.config:</span><span class="sxs-lookup"><span data-stu-id="a30b1-169">If there is no app.config file:</span></span>  
  
    1.  <span data-ttu-id="a30b1-170">No menu **Projeto**, escolha **Adicionar Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="a30b1-170">On the **Project** menu, choose **Add New Item**.</span></span>  
  
    2.  <span data-ttu-id="a30b1-171">Na caixa de diálogo **Adicionar novo item**, escolha **Arquivo de configuração de aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="a30b1-171">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>  
  
    3.  <span data-ttu-id="a30b1-172">Clique em **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="a30b1-172">Click **Add**.</span></span>  
  
2.  <span data-ttu-id="a30b1-173">Clique com o botão direito do mouse em app.config no **Gerenciador de Soluções**.</span><span class="sxs-lookup"><span data-stu-id="a30b1-173">Right-click app.config in **Solution Explorer**.</span></span> <span data-ttu-id="a30b1-174">Escolha **Abrir**.</span><span class="sxs-lookup"><span data-stu-id="a30b1-174">Choose **Open**.</span></span>  
  
3.  <span data-ttu-id="a30b1-175">Localize a seção `<listeners>`, na seção `<source>` com o atributo de `name` "DefaultSource", que está na seção `<sources>`.</span><span class="sxs-lookup"><span data-stu-id="a30b1-175">Locate the `<listeners>` section, in the `<source>` section with the `name` attribute "DefaultSource", which is under the `<sources>` section.</span></span> <span data-ttu-id="a30b1-176">A seção `<sources>` está na seção `<system.diagnostics>`, na seção `<configuration>` superior.</span><span class="sxs-lookup"><span data-stu-id="a30b1-176">The `<sources>` section is under the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
4.  <span data-ttu-id="a30b1-177">Adicione esse elemento à seção `<listeners>`:</span><span class="sxs-lookup"><span data-stu-id="a30b1-177">Add this element to the `<listeners>` section:</span></span>  
  
    ```xml  
    <!-- Remove the default debug listener. -->  
    <remove name="Default"/>  
    <!-- Add a filterable debug listener. -->  
    <add name="NewDefault"/>  
    ```  
  
5.  <span data-ttu-id="a30b1-178">Localize a seção `<sharedListeners>`, na seção `<system.diagnostics>`, na seção `<configuration>` superior.</span><span class="sxs-lookup"><span data-stu-id="a30b1-178">Locate the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
6.  <span data-ttu-id="a30b1-179">Adicione esse elemento a essa seção `<sharedListeners>`:</span><span class="sxs-lookup"><span data-stu-id="a30b1-179">Add this element to that `<sharedListeners>` section:</span></span>  
  
    ```xml  
    <add name="NewDefault"   
         type="System.Diagnostics.DefaultTraceListener,   
               System, Version=2.0.0.0, Culture=neutral,   
               PublicKeyToken=b77a5c561934e089,   
               processorArchitecture=MSIL">  
        <filter type="System.Diagnostics.EventTypeFilter"   
                initializeData="Error" />  
    </add>  
    ```  
  
     <span data-ttu-id="a30b1-180">O filtro <xref:System.Diagnostics.EventTypeFilter> escolhe um dos valores de enumeração <xref:System.Diagnostics.SourceLevels> como seu atributo `initializeData`.</span><span class="sxs-lookup"><span data-stu-id="a30b1-180">The <xref:System.Diagnostics.EventTypeFilter> filter takes one of the <xref:System.Diagnostics.SourceLevels> enumeration values as its `initializeData` attribute.</span></span>  
  
7.  <span data-ttu-id="a30b1-181">O conteúdo do arquivo app.config deve ser semelhante ao XML a seguir:</span><span class="sxs-lookup"><span data-stu-id="a30b1-181">The content of the app.config file should be similar to the following XML:</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.diagnostics>  
        <sources>  
          <!-- This section configures My.Application.Log -->  
          <source name="DefaultSource" switchName="DefaultSwitch">  
            <listeners>  
              <add name="FileLog"/>  
              <!-- Remove the default debug listener. -->  
              <remove name="Default"/>  
              <!-- Add a filterable debug listener. -->  
              <add name="NewDefault"/>  
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
                     Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a,   
                     processorArchitecture=MSIL"   
               initializeData="FileLogWriter"/>  
          <add name="NewDefault"   
               type="System.Diagnostics.DefaultTraceListener,   
                     System, Version=2.0.0.0, Culture=neutral,   
                     PublicKeyToken=b77a5c561934e089,   
                     processorArchitecture=MSIL">  
            <filter type="System.Diagnostics.EventTypeFilter"   
                    initializeData="Error" />  
          </add>  
        </sharedListeners>  
      </system.diagnostics>  
    </configuration>  
    ```  
  
8.  <span data-ttu-id="a30b1-182">Execute o aplicativo no depurador.</span><span class="sxs-lookup"><span data-stu-id="a30b1-182">Run the application in the debugger.</span></span>  
  
9. <span data-ttu-id="a30b1-183">Pressione **Button1**.</span><span class="sxs-lookup"><span data-stu-id="a30b1-183">Press **Button1**.</span></span>  
  
     <span data-ttu-id="a30b1-184">O aplicativo grava as informações a seguir no arquivo de log do aplicativo:</span><span class="sxs-lookup"><span data-stu-id="a30b1-184">The application writes the following information to the application's log file:</span></span>  
  
     `Default Information: 0 : In Button1_Click`  
  
     `Default Error: 2 : Error in the application.`  
  
     <span data-ttu-id="a30b1-185">O aplicativo grava menos informações na saída da depuração do aplicativo devido à filtragem mais restritiva.</span><span class="sxs-lookup"><span data-stu-id="a30b1-185">The application writes less information to the application's debug output because of the more restrictive filtering.</span></span>  
  
     `Default Error   2   Error`  
  
10. <span data-ttu-id="a30b1-186">Feche o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a30b1-186">Close the application.</span></span>  
  
 <span data-ttu-id="a30b1-187">Para obter mais informações sobre como alterar as configurações de log após a implantação, consulte [Trabalhando com logs de aplicativo](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).</span><span class="sxs-lookup"><span data-stu-id="a30b1-187">For more information about changing log settings after deployment, see [Working with Application Logs](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a30b1-188">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a30b1-188">See also</span></span>

- [<span data-ttu-id="a30b1-189">Passo a passo: determinando onde My.Application.Log grava informações</span><span class="sxs-lookup"><span data-stu-id="a30b1-189">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
- [<span data-ttu-id="a30b1-190">Passo a passo: alterando onde My.Application.Log grava informações</span><span class="sxs-lookup"><span data-stu-id="a30b1-190">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
- [<span data-ttu-id="a30b1-191">Passo a passo: criando ouvintes de log personalizados</span><span class="sxs-lookup"><span data-stu-id="a30b1-191">Walkthrough: Creating Custom Log Listeners</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-creating-custom-log-listeners.md)
- [<span data-ttu-id="a30b1-192">Como: gravar mensagens de log</span><span class="sxs-lookup"><span data-stu-id="a30b1-192">How to: Write Log Messages</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)
- [<span data-ttu-id="a30b1-193">Opções de rastreamento</span><span class="sxs-lookup"><span data-stu-id="a30b1-193">Trace Switches</span></span>](../../../../framework/debug-trace-profile/trace-switches.md)
- [<span data-ttu-id="a30b1-194">Registrando informações em log no aplicativo</span><span class="sxs-lookup"><span data-stu-id="a30b1-194">Logging Information from the Application</span></span>](../../../../visual-basic/developing-apps/programming/log-info/index.md)
