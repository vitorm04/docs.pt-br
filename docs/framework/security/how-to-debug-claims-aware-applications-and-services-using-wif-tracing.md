---
title: Como depurar serviços e aplicativos baseados em declarações usando o rastreamento do WIF
ms.date: 03/30/2017
ms.assetid: 3d51ba59-3adb-4ca4-bd33-5027531af687
author: BrucePerlerMS
ms.openlocfilehash: e10d8d2ea869b03586b4680ad8320aeb2de90620
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47088120"
---
# <a name="how-to-debug-claims-aware-applications-and-services-using-wif-tracing"></a><span data-ttu-id="1e39b-102">Como depurar serviços e aplicativos baseados em declarações usando o rastreamento do WIF</span><span class="sxs-lookup"><span data-stu-id="1e39b-102">How To: Debug Claims-Aware Applications And Services Using WIF Tracing</span></span>
## <a name="applies-to"></a><span data-ttu-id="1e39b-103">Aplica-se a</span><span class="sxs-lookup"><span data-stu-id="1e39b-103">Applies To</span></span>  
  
-   <span data-ttu-id="1e39b-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="1e39b-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>  
  
-   <span data-ttu-id="1e39b-105">Ferramenta Visualizador de Rastreamento de Serviço (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="1e39b-105">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>  
  
-   <span data-ttu-id="1e39b-106">Solução de problemas e depuração de aplicativos do WIF</span><span class="sxs-lookup"><span data-stu-id="1e39b-106">Troubleshooting and Debugging WIF Applications</span></span>  
  
## <a name="summary"></a><span data-ttu-id="1e39b-107">Resumo</span><span class="sxs-lookup"><span data-stu-id="1e39b-107">Summary</span></span>  
 <span data-ttu-id="1e39b-108">Estas Instruções descrevem as etapas necessárias para configurar o rastreamento do WIF, coletar logs de rastreamento e analisar os logs de rastreamento usando a ferramenta Visualizador de Rastreamento.</span><span class="sxs-lookup"><span data-stu-id="1e39b-108">This How-To describes required steps for how to configure WIF tracing, collect trace logs, and how to analyze the trace logs using Trace Viewer tool.</span></span> <span data-ttu-id="1e39b-109">Fornecem um mapeamento geral para entradas de rastreamento para as ações necessárias para solucionar problemas relacionados ao WIF.</span><span class="sxs-lookup"><span data-stu-id="1e39b-109">It provides general mapping for trace entries to actions needed to troubleshoot issues related to WIF.</span></span>  
  
## <a name="contents"></a><span data-ttu-id="1e39b-110">Conteúdo</span><span class="sxs-lookup"><span data-stu-id="1e39b-110">Contents</span></span>  
  
-   <span data-ttu-id="1e39b-111">Objetivos</span><span class="sxs-lookup"><span data-stu-id="1e39b-111">Objectives</span></span>  
  
-   <span data-ttu-id="1e39b-112">Resumo das etapas</span><span class="sxs-lookup"><span data-stu-id="1e39b-112">Summary of Steps</span></span>  
  
-   <span data-ttu-id="1e39b-113">Etapa 1 – Configurar o rastreamento do WIF usando o arquivo de configuração Web.config</span><span class="sxs-lookup"><span data-stu-id="1e39b-113">Step 1 – Configure WIF Tracing Using Web.config Configuration File</span></span>  
  
-   <span data-ttu-id="1e39b-114">Etapa 2 – Analisar arquivos de rastreamento do WIF usando a ferramenta Visualizador de Rastreamento</span><span class="sxs-lookup"><span data-stu-id="1e39b-114">Step 2 – Analyze WIF Trace Files Using Trace Viewer Tool</span></span>  
  
-   <span data-ttu-id="1e39b-115">Etapa 3 – Identificar soluções para corrigir problemas relacionados ao WIF</span><span class="sxs-lookup"><span data-stu-id="1e39b-115">Step 3 – Identify Solutions to Fix WIF Related Issues</span></span>  
  
-   <span data-ttu-id="1e39b-116">Itens relacionados</span><span class="sxs-lookup"><span data-stu-id="1e39b-116">Related Items</span></span>  
  
## <a name="objectives"></a><span data-ttu-id="1e39b-117">Objetivos</span><span class="sxs-lookup"><span data-stu-id="1e39b-117">Objectives</span></span>  
  
-   <span data-ttu-id="1e39b-118">Configure o rastreamento do WIF.</span><span class="sxs-lookup"><span data-stu-id="1e39b-118">Configure WIF tracing.</span></span>  
  
-   <span data-ttu-id="1e39b-119">Exiba os logs de rastreamento na ferramenta Visualizador de Rastreamento.</span><span class="sxs-lookup"><span data-stu-id="1e39b-119">View trace logs in the Trace Viewer tool.</span></span>  
  
-   <span data-ttu-id="1e39b-120">Identifique problemas relacionados ao WIF nos logs de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="1e39b-120">Identify WIF related issues in the trace logs.</span></span>  
  
-   <span data-ttu-id="1e39b-121">Aplique ações corretivas aos problemas relacionados ao WIF encontrados nos logs de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="1e39b-121">Apply corrective actions to WIF related issues found in the trace logs.</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="1e39b-122">Resumo das etapas</span><span class="sxs-lookup"><span data-stu-id="1e39b-122">Summary of Steps</span></span>  
  
-   <span data-ttu-id="1e39b-123">Etapa 1 – Configurar o rastreamento do WIF usando o arquivo de configuração Web.config</span><span class="sxs-lookup"><span data-stu-id="1e39b-123">Step 1 – Configure WIF Tracing Using Web.config Configuration File</span></span>  
  
-   <span data-ttu-id="1e39b-124">Etapa 2 – Analisar arquivos de rastreamento do WIF usando a ferramenta Visualizador de Rastreamento</span><span class="sxs-lookup"><span data-stu-id="1e39b-124">Step 2 – Analyze WIF Trace Files Using Trace Viewer Tool</span></span>  
  
-   <span data-ttu-id="1e39b-125">Etapa 3 – Identificar soluções para corrigir problemas relacionados ao WIF</span><span class="sxs-lookup"><span data-stu-id="1e39b-125">Step 3 – Identify Solutions to Fix WIF Related Issues</span></span>  
  
## <a name="step-1--configure-wif-tracing-using-webconfig-configuration-file"></a><span data-ttu-id="1e39b-126">Etapa 1 – Configurar o rastreamento do WIF usando o arquivo de configuração Web.config</span><span class="sxs-lookup"><span data-stu-id="1e39b-126">Step 1 – Configure WIF Tracing Using Web.config Configuration File</span></span>  
 <span data-ttu-id="1e39b-127">Nesta etapa, você adicionará alterações às seções de configuração no arquivo *Web.config* que permitem que o WIF rastreie seus eventos e armazene-os em um log de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="1e39b-127">In this step, you will add changes to configuration sections in the *Web.config* file that enable WIF to trace its events and store them in a trace log.</span></span>  
  
#### <a name="to-configure-wif-tracing-using-webconfig-configuration-file"></a><span data-ttu-id="1e39b-128">Para configurar o rastreamento do WIF usando o arquivo de configuração Web.config</span><span class="sxs-lookup"><span data-stu-id="1e39b-128">To configure WIF tracing using Web.config configuration file</span></span>  
  
1.  <span data-ttu-id="1e39b-129">Abra o arquivo de configuração **Web.config** ou **App.config** raiz no editor do Visual Studio clicando duas vezes nele no **Gerenciador de Soluções**.</span><span class="sxs-lookup"><span data-stu-id="1e39b-129">Open the root **Web.config** or **App.config** configuration file in the Visual Studio editor by double clicking on it in **Solution Explorer**.</span></span> <span data-ttu-id="1e39b-130">Se a solução não tiver o arquivo de configuração **Web.config** ou **App.config**, adicione-o clicando com o botão direito do mouse na solução no **Gerenciador de Soluções**, clicando em **Adicionar** e, em seguida, clicando em **Novo Item...**.</span><span class="sxs-lookup"><span data-stu-id="1e39b-130">If your solution does not have **Web.config** or **App.config** configuration file, add it by right clicking on the solution in the **Solution Explorer** and clicking **Add**, then clicking **New Item…**.</span></span> <span data-ttu-id="1e39b-131">Na caixa de diálogo **Novo Item**, selecione **Arquivo de Configuração de Aplicativo** para **App.config** ou **Arquivo de Configuração da Web** para **Web.config** na lista e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="1e39b-131">On the **New Item** dialog, Select **Application Configuration File** for **App.config** or **Web Configuration File** for **Web.config** from the list and click **OK**.</span></span>  
  
2.  <span data-ttu-id="1e39b-132">Adicione as entradas de configuração semelhantes à seguinte ao arquivo de configuração dentro do nó **\<configuration>** no final do arquivo de configuração:</span><span class="sxs-lookup"><span data-stu-id="1e39b-132">Add the configuration entries similar to the following to the configuration file inside **\<configuration>** node at the end of the configuration file:</span></span>  
  
    ```xml  
    <system.diagnostics>  
        <sources>  
            <source name="System.IdentityModel" switchValue="Verbose">  
                <listeners>  
                    <add name="xml" type="System.Diagnostics.XmlWriterTraceListener" initializeData="WIFTrace.e2e"/>  
                </listeners>  
            </source>  
        </sources>  
        <trace autoflush="true"/>  
    </system.diagnostics>  
    ```  
  
3.  <span data-ttu-id="1e39b-133">A configuração acima instrui o WIF a gerar eventos de rastreamento detalhados e registrá-los no arquivo *WIFTrace.e2e*.</span><span class="sxs-lookup"><span data-stu-id="1e39b-133">The above configuration instructs WIF to generate verbose trace events and log them into *WIFTrace.e2e* file.</span></span> <span data-ttu-id="1e39b-134">Para obter uma lista completa de valores para a opção **switchValue**, consulte a tabela Nível de rastreamento encontrada no seguinte tópico: [Configurando o rastreamento](../wcf/diagnostics/tracing/configuring-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="1e39b-134">For a complete list of values for the **switchValue** switch, refer to the Trace Level table found in the following topic: [Configuring Tracing](../wcf/diagnostics/tracing/configuring-tracing.md).</span></span>  
  
## <a name="step-2--analyze-wif-trace-files-using-trace-viewer-tool"></a><span data-ttu-id="1e39b-135">Etapa 2 – Analisar arquivos de rastreamento do WIF usando a ferramenta Visualizador de Rastreamento</span><span class="sxs-lookup"><span data-stu-id="1e39b-135">Step 2 – Analyze WIF Trace Files Using Trace Viewer Tool</span></span>  
 <span data-ttu-id="1e39b-136">Nesta etapa, você usará a ferramenta Visualizador de Rastreamento (SvcTraceViewer.exe) para analisar os logs de rastreamento do WIF.</span><span class="sxs-lookup"><span data-stu-id="1e39b-136">In this step, you will use the Trace Viewer Tool (SvcTraceViewer.exe) to analyze WIF trace logs.</span></span>  
  
#### <a name="to-analyze-wif-trace-logs-using-trace-viewer-tool-svctraceviewerexe"></a><span data-ttu-id="1e39b-137">Para analisar os logs de rastreamento do WIF usando a ferramenta Visualizador de Rastreamento (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="1e39b-137">To analyze WIF trace logs using Trace Viewer tool (SvcTraceViewer.exe)</span></span>  
  
1.  <span data-ttu-id="1e39b-138">A ferramenta Visualizador de Rastreamento (SvcTraceViewer.exe) é fornecida como parte do SDK do Windows.</span><span class="sxs-lookup"><span data-stu-id="1e39b-138">Trace Viewer tool (SvcTraceViewer.exe) ships as part of the Windows SDK.</span></span> <span data-ttu-id="1e39b-139">Se você ainda não instalou o SDK do Windows, baixe-o aqui: [SDK do Windows](https://www.microsoft.com/download/en/details.aspx?id=8279).</span><span class="sxs-lookup"><span data-stu-id="1e39b-139">If you haven’t already installed the Windows SDK, you can download it here: [Windows SDK](https://www.microsoft.com/download/en/details.aspx?id=8279).</span></span>  
  
2.  <span data-ttu-id="1e39b-140">Execute a ferramenta Visualizador de Rastreamento (SvcTraceViewer.exe).</span><span class="sxs-lookup"><span data-stu-id="1e39b-140">Run the Trace Viewer tool (SvcTraceViewer.exe).</span></span> <span data-ttu-id="1e39b-141">Normalmente, ele está disponível na pasta **Bin** do caminho de instalação.</span><span class="sxs-lookup"><span data-stu-id="1e39b-141">It is typically available in the **Bin** folder of the installation path.</span></span>  
  
3.  <span data-ttu-id="1e39b-142">Abra o arquivo de log de rastreamento do WIF, por exemplo, WIFTrace.e2e, selecionando a opção **Arquivo**, **Abrir...**</span><span class="sxs-lookup"><span data-stu-id="1e39b-142">Open the WIF trace log file, for example, WIFTrace.e2e by selecting **File**, **Open…**</span></span> <span data-ttu-id="1e39b-143">no menu ou usando o atalho **Ctrl+O**.</span><span class="sxs-lookup"><span data-stu-id="1e39b-143">option in the menu or using the **Ctrl+O** shortcut.</span></span> <span data-ttu-id="1e39b-144">O arquivo de log de rastreamento é aberto na ferramenta Visualizador de Rastreamento.</span><span class="sxs-lookup"><span data-stu-id="1e39b-144">The trace log file opens in the Trace Viewer tool.</span></span>  
  
4.  <span data-ttu-id="1e39b-145">Examine as entradas na guia **Atividade**. Cada entrada deve conter um número de atividade, o número de rastreamentos registrados, a duração da atividade e seus carimbos de data/hora de início e término.</span><span class="sxs-lookup"><span data-stu-id="1e39b-145">Review entries in the **Activity** tab. Each entry should contain an activity number, the number of traces that were logged, duration of the activity and its start and end timestamps.</span></span>  
  
5.  <span data-ttu-id="1e39b-146">Clique na guia **Atividade**. Você deverá ver entradas de rastreamento detalhadas na área principal da ferramenta.</span><span class="sxs-lookup"><span data-stu-id="1e39b-146">Click on the **Activity** tab. You should see detailed trace entries in the main area of the tool.</span></span> <span data-ttu-id="1e39b-147">Use a lista suspensa **Nível** no menu para filtrar um nível específico de rastreamentos, por exemplo: **Todos**, **Aviso**, **Erros**, **Informações**, etc.</span><span class="sxs-lookup"><span data-stu-id="1e39b-147">Use the **Level** dropdown list on the menu to filter specific level of traces, for example: **All**, **Warning**, **Errors**, **Information**, etc.</span></span>  
  
6.  <span data-ttu-id="1e39b-148">Clique nas entradas de rastreamento específicas para examinar os detalhes na área inferior da ferramenta.</span><span class="sxs-lookup"><span data-stu-id="1e39b-148">Click on specific trace entries to review the details in the lower area of the tool.</span></span> <span data-ttu-id="1e39b-149">Os detalhes podem ser exibidos usando a exibição **Formatado** e **XML**, escolhendo as guias correspondentes.</span><span class="sxs-lookup"><span data-stu-id="1e39b-149">The details can be viewed using **Formatted** and **XML** view by choosing corresponding tabs.</span></span>  
  
## <a name="step-3--identify-solutions-to-fix-wif-related-issues"></a><span data-ttu-id="1e39b-150">Etapa 3 – Identificar soluções para corrigir problemas relacionados ao WIF</span><span class="sxs-lookup"><span data-stu-id="1e39b-150">Step 3 – Identify Solutions to Fix WIF Related Issues</span></span>  
 <span data-ttu-id="1e39b-151">Nesta etapa, você pode identificar soluções para problemas relacionados ao WIF identificados usando o log de rastreamento do WIF e a ferramenta Visualizador de Rastreamento.</span><span class="sxs-lookup"><span data-stu-id="1e39b-151">In this step, you can identify solutions for WIF-related issues identified by using the WIF trace log and Trace Viewer tool.</span></span> <span data-ttu-id="1e39b-152">Elas descreve o mapeamento geral de exceções relacionadas ao WIF para possíveis soluções ou as ações necessárias para solucionar o problema.</span><span class="sxs-lookup"><span data-stu-id="1e39b-152">It outlines general mapping of WIF related exceptions to potential solutions or required actions to troubleshoot the issue.</span></span>  
  
#### <a name="to-identify-solutions-to-fix-wif-related-issues"></a><span data-ttu-id="1e39b-153">Para identificar soluções para corrigir problemas relacionados ao WIF</span><span class="sxs-lookup"><span data-stu-id="1e39b-153">To identify solutions to fix WIF related issues</span></span>  
  
1.  <span data-ttu-id="1e39b-154">Examine a tabela a seguir de exceções do WIF e as ações necessárias para corrigir os problemas.</span><span class="sxs-lookup"><span data-stu-id="1e39b-154">Review the following table of WIF exceptions and the required actions to correct the issues.</span></span>  
  
|<span data-ttu-id="1e39b-155">**ID de erro**</span><span class="sxs-lookup"><span data-stu-id="1e39b-155">**Error ID**</span></span>|<span data-ttu-id="1e39b-156">**Mensagem de erro**</span><span class="sxs-lookup"><span data-stu-id="1e39b-156">**Error Message**</span></span>|<span data-ttu-id="1e39b-157">**Ação necessária para corrigir o erro**</span><span class="sxs-lookup"><span data-stu-id="1e39b-157">**Action needed to fix the error**</span></span>|  
|-|-|-|  
|<span data-ttu-id="1e39b-158">ID4175</span><span class="sxs-lookup"><span data-stu-id="1e39b-158">ID4175</span></span>|<span data-ttu-id="1e39b-159">O emissor do token de segurança não foi reconhecido pelo IssuerNameRegistry.</span><span class="sxs-lookup"><span data-stu-id="1e39b-159">The issuer of the security token was not recognized by the IssuerNameRegistry.</span></span>  <span data-ttu-id="1e39b-160">Para aceitar tokens de segurança desse emissor, configure o IssuerNameRegistry para retornar um nome válido para esse emissor.</span><span class="sxs-lookup"><span data-stu-id="1e39b-160">To accept security tokens from this issuer, configure the IssuerNameRegistry to return a valid name for this issuer.</span></span>|<span data-ttu-id="1e39b-161">Esse erro pode ser causado pela ação de copiar uma impressão digital do snap-in do MMC e colá-la no arquivo *Web.config*.</span><span class="sxs-lookup"><span data-stu-id="1e39b-161">This error can be caused by copying a thumbprint from the MMC snap-in and pasting it into the *Web.config* file.</span></span> <span data-ttu-id="1e39b-162">Especificamente, você pode obter um caractere extra não imprimível na cadeia de texto ao copiar da janela de propriedades do certificado.</span><span class="sxs-lookup"><span data-stu-id="1e39b-162">Specifically, you can get an extra non-printable character in the text string when copying from the certificate properties window.</span></span> <span data-ttu-id="1e39b-163">Esse caractere extra faz com que a correspondência da impressão digital falhe. O procedimento para copiar corretamente a impressão digital pode ser encontrado aqui: [http://msdn.microsoft.com/library/ff359102.aspx](https://msdn.microsoft.com/library/ff359102.aspx)</span><span class="sxs-lookup"><span data-stu-id="1e39b-163">This extra character causes the thumbprint match to fail.The procedure for correctly copying the thumbprint can be found here: [http://msdn.microsoft.com/library/ff359102.aspx](https://msdn.microsoft.com/library/ff359102.aspx)</span></span>|  
  
## <a name="related-items"></a><span data-ttu-id="1e39b-164">Itens relacionados</span><span class="sxs-lookup"><span data-stu-id="1e39b-164">Related Items</span></span>  
  
-   [<span data-ttu-id="1e39b-165">Usando o Visualizador de Rastreamento de Serviço para exibir rastreamentos correlacionados e solucionar problemas</span><span class="sxs-lookup"><span data-stu-id="1e39b-165">Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting</span></span>](../wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
