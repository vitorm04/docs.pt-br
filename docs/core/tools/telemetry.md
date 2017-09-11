---
title: Telemetria de Ferramentas da CLI do .NET Core
description: "Descubra os recursos de telemetria das ferramentas do .NET Core que coletam informações de uso para análise, quais dados são coletados e como desabilitá-la."
keywords: .NET,.NET Core,telemetria
author: richlander
ms.author: mairaw
ms.date: 08/04/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 480df976-7568-4df4-9d26-9911357b5a31
ms.translationtype: HT
ms.sourcegitcommit: c58ed1b3c09f1e358d0b66f6cf7186821601fd69
ms.openlocfilehash: 8ea8ee44a58c6aabfd09afbc7ef53239a9029c57
ms.contentlocale: pt-br
ms.lasthandoff: 08/12/2017

---

# <a name="net-core-cli-tools-telemetry"></a><span data-ttu-id="317b6-104">Telemetria de Ferramentas da CLI do .NET Core</span><span class="sxs-lookup"><span data-stu-id="317b6-104">.NET Core CLI Tools telemetry</span></span>

<span data-ttu-id="317b6-105">O [SDK do .NET Core](index.md) inclui um [recurso de telemetria](https://github.com/dotnet/cli/pull/2145) que coleta informações de uso.</span><span class="sxs-lookup"><span data-stu-id="317b6-105">The [.NET Core SDK](index.md) includes a [telemetry feature](https://github.com/dotnet/cli/pull/2145) that collects usage information.</span></span> <span data-ttu-id="317b6-106">É importante que a Equipe do .NET compreenda como as ferramentas são usadas para que possamos melhorá-las.</span><span class="sxs-lookup"><span data-stu-id="317b6-106">It's important that the .NET Team understands how the tools are used so that we can improve them.</span></span> <span data-ttu-id="317b6-107">Para obter mais informações, consulte [What we've learned from .NET Core SDK Telemetry](https://blogs.msdn.microsoft.com/dotnet/2017/07/21/what-weve-learned-from-net-core-sdk-telemetry/) (O que aprendemos com a telemetria do SDK do .NET Core).</span><span class="sxs-lookup"><span data-stu-id="317b6-107">For more information, see [What we've learned from .NET Core SDK Telemetry](https://blogs.msdn.microsoft.com/dotnet/2017/07/21/what-weve-learned-from-net-core-sdk-telemetry/).</span></span>

<span data-ttu-id="317b6-108">Os dados coletados são anônimos e são publicados de forma agregada para serem usados pela Microsoft e pela comunidade sob a [Licença de Atribuição Creative Commons](https://creativecommons.org/licenses/by/4.0/).</span><span class="sxs-lookup"><span data-stu-id="317b6-108">The collected data is anonymous and published in an aggregated form for use by both Microsoft and the community under the [Creative Commons Attribution License](https://creativecommons.org/licenses/by/4.0/).</span></span> 

## <a name="scope"></a><span data-ttu-id="317b6-109">Escopo</span><span class="sxs-lookup"><span data-stu-id="317b6-109">Scope</span></span>

<span data-ttu-id="317b6-110">O comando `dotnet` é usado para inicializar os aplicativos e a CLI do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="317b6-110">The `dotnet` command is used to launch both apps and the .NET Core CLI.</span></span> <span data-ttu-id="317b6-111">O comando `dotnet` em si não realiza coletas de telemetria.</span><span class="sxs-lookup"><span data-stu-id="317b6-111">The `dotnet` command itself doesn't collect telemetry.</span></span> <span data-ttu-id="317b6-112">Os comandos da CLI do .NET Core são executados pelo comando `dotnet` para realizar coletas de telemetria.</span><span class="sxs-lookup"><span data-stu-id="317b6-112">The .NET Core CLI commands run by the `dotnet` command collect the telemetry.</span></span>

<span data-ttu-id="317b6-113">A telemetria *não é habilitada* ao usar o comando `dotnet` em si sem nenhum comando anexado:</span><span class="sxs-lookup"><span data-stu-id="317b6-113">Telemetry *isn't enabled* when using the `dotnet` command itself, with no command attached:</span></span>

- `dotnet`
- `dotnet [path-to-app]`

<span data-ttu-id="317b6-114">A telemetria *é habilitada* ao usar os [comandos da CLI do .NET Core](index.md), como:</span><span class="sxs-lookup"><span data-stu-id="317b6-114">Telemetry *is enabled* when using the [.NET Core CLI commands](index.md), such as:</span></span>

- `dotnet build`
- `dotnet pack`
- `dotnet restore`
- `dotnet run`

## <a name="behavior"></a><span data-ttu-id="317b6-115">Comportamento</span><span class="sxs-lookup"><span data-stu-id="317b6-115">Behavior</span></span>

<span data-ttu-id="317b6-116">O recurso de telemetria das Ferramentas da CLI do .NET Core é habilitado por padrão.</span><span class="sxs-lookup"><span data-stu-id="317b6-116">The .NET Core CLI Tools telemetry feature is enabled by default.</span></span> <span data-ttu-id="317b6-117">Recuse o recurso de telemetria definindo a variável de ambiente `DOTNET_CLI_TELEMETRY_OPTOUT` como `1` ou `true`.</span><span class="sxs-lookup"><span data-stu-id="317b6-117">Opt-out of the telemetry feature by setting the `DOTNET_CLI_TELEMETRY_OPTOUT` environment variable to `1` or `true`.</span></span>

## <a name="data-points"></a><span data-ttu-id="317b6-118">Pontos de dados</span><span class="sxs-lookup"><span data-stu-id="317b6-118">Data points</span></span>

<span data-ttu-id="317b6-119">O recurso coleta os seguintes dados:</span><span class="sxs-lookup"><span data-stu-id="317b6-119">The feature collects the following data:</span></span>

- <span data-ttu-id="317b6-120">Carimbo de data/hora da invocação&#8224;</span><span class="sxs-lookup"><span data-stu-id="317b6-120">Timestamp of invocation&#8224;</span></span>
- <span data-ttu-id="317b6-121">Comando invocado (por exemplo, "build")&#8224;</span><span class="sxs-lookup"><span data-stu-id="317b6-121">Command invoked (for example, "build")&#8224;</span></span>
- <span data-ttu-id="317b6-122">Três endereços IP octet usados para determinar a localização geográfica&#8224;</span><span class="sxs-lookup"><span data-stu-id="317b6-122">Three octet IP address used to determine geographical location&#8224;</span></span>
- <span data-ttu-id="317b6-123">`ExitCode` do comando</span><span class="sxs-lookup"><span data-stu-id="317b6-123">`ExitCode` of the command</span></span>
- <span data-ttu-id="317b6-124">Executor de teste (para projetos de teste)</span><span class="sxs-lookup"><span data-stu-id="317b6-124">Test runner (for test projects)</span></span>
- <span data-ttu-id="317b6-125">Sistema operacional e versão&#8224;</span><span class="sxs-lookup"><span data-stu-id="317b6-125">Operating system and version&#8224;</span></span>
- <span data-ttu-id="317b6-126">Se as IDs de tempo de execução estão presentes no nó de tempos de execução</span><span class="sxs-lookup"><span data-stu-id="317b6-126">Whether runtime IDs are present in the runtimes node</span></span>
- <span data-ttu-id="317b6-127">Versão do SDK do .NET Core&#8224;</span><span class="sxs-lookup"><span data-stu-id="317b6-127">.NET Core SDK version&#8224;</span></span>

<span data-ttu-id="317b6-128">&#8224;Essa métrica é publicada.</span><span class="sxs-lookup"><span data-stu-id="317b6-128">&#8224;This metric is published.</span></span>

<span data-ttu-id="317b6-129">A partir do SDK 2.0 do .NET Core, os novos pontos de dados são coletados:</span><span class="sxs-lookup"><span data-stu-id="317b6-129">Starting with .NET Core SDK 2.0, new data points are collected:</span></span>

- <span data-ttu-id="317b6-130">opções e argumentos de comando do `dotnet`: somente argumentos e opções conhecidos são coletados (não cadeias de caracteres arbitrárias).</span><span class="sxs-lookup"><span data-stu-id="317b6-130">`dotnet` command arguments and options: only known arguments and options are collected (not arbitrary strings).</span></span>
- <span data-ttu-id="317b6-131">Se o SDK está em execução em um contêiner.</span><span class="sxs-lookup"><span data-stu-id="317b6-131">Whether the SDK is running in a container.</span></span>
- <span data-ttu-id="317b6-132">Estruturas de destino.</span><span class="sxs-lookup"><span data-stu-id="317b6-132">Target frameworks.</span></span>
- <span data-ttu-id="317b6-133">Endereço MAC com hash: uma ID única e criptograficamente anônima (SHA256) para um computador.</span><span class="sxs-lookup"><span data-stu-id="317b6-133">Hashed MAC address: a cryptographically (SHA256) anonymous and unique ID for a machine.</span></span> <span data-ttu-id="317b6-134">Essa métrica não é publicada.</span><span class="sxs-lookup"><span data-stu-id="317b6-134">This metric is not published.</span></span>
- <span data-ttu-id="317b6-135">Diretório de trabalho atual com hash.</span><span class="sxs-lookup"><span data-stu-id="317b6-135">Hashed current working directory.</span></span>

<span data-ttu-id="317b6-136">O recurso não coleta dados pessoais como nomes de usuário ou endereços de emails.</span><span class="sxs-lookup"><span data-stu-id="317b6-136">The feature doesn't collect personal data, such as usernames or email addresses.</span></span> <span data-ttu-id="317b6-137">Ele não examina seu código e não extrai dados de nível de projeto confidenciais, como nome, repositório ou autor.</span><span class="sxs-lookup"><span data-stu-id="317b6-137">It doesn't scan your code and doesn't extract sensitive project-level data, such as name, repo, or author.</span></span> <span data-ttu-id="317b6-138">Os dados são enviados com segurança para os servidores Microsoft usando a tecnologia [Microsoft Azure Application Insights](https://azure.microsoft.com/services/application-insights/), mantidos em acesso restrito e publicados sob controles de segurança rigorosos dos sistemas do [Armazenamento do Microsoft Azure](https://azure.microsoft.com/services/storage/) seguros.</span><span class="sxs-lookup"><span data-stu-id="317b6-138">The data is sent securely to Microsoft servers using [Microsoft Azure Application Insights](https://azure.microsoft.com/services/application-insights/) technology, held under restricted access, and published under strict security controls from secure [Azure Storage](https://azure.microsoft.com/services/storage/) systems.</span></span>

<span data-ttu-id="317b6-139">Desejamos saber como as ferramentas são usadas e se elas estão funcionando bem, não o que você está compilando com elas.</span><span class="sxs-lookup"><span data-stu-id="317b6-139">We want to know how the tools are used and if they're working well, not what you're building with the tools.</span></span> <span data-ttu-id="317b6-140">Se você suspeitar que a telemetria está coletando dados confidenciais ou que nós estamos tratando dados de maneira insegura ou inadequada, [registre um problema nos problemas do repositório dotnet/cli](https://github.com/dotnet/cli/issues) para investigação.</span><span class="sxs-lookup"><span data-stu-id="317b6-140">If you suspect that the telemetry is collecting sensitive data or that we're insecurely or inappropriately handling data, [file an issue in the dotnet/cli repo issues](https://github.com/dotnet/cli/issues) for investigation.</span></span>

## <a name="published-data"></a><span data-ttu-id="317b6-141">Dados publicados</span><span class="sxs-lookup"><span data-stu-id="317b6-141">Published data</span></span>

<span data-ttu-id="317b6-142">Os dados publicados estão disponíveis trimestralmente e são listados em [.NET Core SDK Usage Data](https://github.com/dotnet/core/blob/master/release-notes/cli-usage-data.md) (Dados de uso do SDK do .NET Core).</span><span class="sxs-lookup"><span data-stu-id="317b6-142">Published data is available quarterly and are listed at [.NET Core SDK Usage Data](https://github.com/dotnet/core/blob/master/release-notes/cli-usage-data.md).</span></span> <span data-ttu-id="317b6-143">As colunas de um arquivo de dados são:</span><span class="sxs-lookup"><span data-stu-id="317b6-143">The columns of a data file are:</span></span>
- <span data-ttu-id="317b6-144">Timestamp</span><span class="sxs-lookup"><span data-stu-id="317b6-144">Timestamp</span></span>
- <span data-ttu-id="317b6-145">Ocorrências&#8224;</span><span class="sxs-lookup"><span data-stu-id="317b6-145">Occurrences&#8224;</span></span>
- <span data-ttu-id="317b6-146">Comando</span><span class="sxs-lookup"><span data-stu-id="317b6-146">Command</span></span>
- <span data-ttu-id="317b6-147">Geografia&#8225;</span><span class="sxs-lookup"><span data-stu-id="317b6-147">Geography&#8225;</span></span>
- <span data-ttu-id="317b6-148">OSFamily</span><span class="sxs-lookup"><span data-stu-id="317b6-148">OSFamily</span></span>
- <span data-ttu-id="317b6-149">RuntimeID</span><span class="sxs-lookup"><span data-stu-id="317b6-149">RuntimeID</span></span>
- <span data-ttu-id="317b6-150">OSVersion</span><span class="sxs-lookup"><span data-stu-id="317b6-150">OSVersion</span></span>
- <span data-ttu-id="317b6-151">SDKVersion</span><span class="sxs-lookup"><span data-stu-id="317b6-151">SDKVersion</span></span>

<span data-ttu-id="317b6-152">&#8224;A coluna *Ocorrências* exibe uma contagem agregada do uso desse comando para as métricas dessa linha naquele dia.</span><span class="sxs-lookup"><span data-stu-id="317b6-152">&#8224;The *Occurrences* column displays the aggregate count of that command's use for that row's metrics that day.</span></span> 

<span data-ttu-id="317b6-153">&#8225;Normalmente, a coluna *Geografia* exibe o nome de um país.</span><span class="sxs-lookup"><span data-stu-id="317b6-153">&#8225;Typically, the *Geography* column displays the name of a country.</span></span> <span data-ttu-id="317b6-154">Em alguns casos, continente da Antártida aparece na coluna, devido ao fato de os pesquisadores usarem o .NET Core na Antártida ou a dados de localização incorretos.</span><span class="sxs-lookup"><span data-stu-id="317b6-154">In some cases, the continent of Antarctica appears in this column, either due to researchers using .NET Core in Antarctica or incorrect location data.</span></span>

### <a name="example"></a><span data-ttu-id="317b6-155">Exemplo</span><span class="sxs-lookup"><span data-stu-id="317b6-155">Example</span></span>

| <span data-ttu-id="317b6-156">Timestamp</span><span class="sxs-lookup"><span data-stu-id="317b6-156">Timestamp</span></span>      | <span data-ttu-id="317b6-157">Ocorrências</span><span class="sxs-lookup"><span data-stu-id="317b6-157">Occurrences</span></span> | <span data-ttu-id="317b6-158">Comando</span><span class="sxs-lookup"><span data-stu-id="317b6-158">Command</span></span> | <span data-ttu-id="317b6-159">Geografia</span><span class="sxs-lookup"><span data-stu-id="317b6-159">Geography</span></span> | <span data-ttu-id="317b6-160">OSFamily</span><span class="sxs-lookup"><span data-stu-id="317b6-160">OSFamily</span></span> | <span data-ttu-id="317b6-161">RuntimeID</span><span class="sxs-lookup"><span data-stu-id="317b6-161">RuntimeID</span></span>     | <span data-ttu-id="317b6-162">OSVersion</span><span class="sxs-lookup"><span data-stu-id="317b6-162">OSVersion</span></span> | <span data-ttu-id="317b6-163">SDKVersion</span><span class="sxs-lookup"><span data-stu-id="317b6-163">SDKVersion</span></span> |
| -------------- | ----------- | ------- | --------- | -------- | ------------- | --------- | ---------- |
| <span data-ttu-id="317b6-164">4/16/2017 0:00</span><span class="sxs-lookup"><span data-stu-id="317b6-164">4/16/2017 0:00</span></span> | <span data-ttu-id="317b6-165">8</span><span class="sxs-lookup"><span data-stu-id="317b6-165">8</span></span>           | <span data-ttu-id="317b6-166">executar</span><span class="sxs-lookup"><span data-stu-id="317b6-166">run</span></span>     | <span data-ttu-id="317b6-167">Uganda</span><span class="sxs-lookup"><span data-stu-id="317b6-167">Uganda</span></span>    | <span data-ttu-id="317b6-168">Darwin</span><span class="sxs-lookup"><span data-stu-id="317b6-168">Darwin</span></span>   | <span data-ttu-id="317b6-169">osx.10.12-x64</span><span class="sxs-lookup"><span data-stu-id="317b6-169">osx.10.12-x64</span></span> | <span data-ttu-id="317b6-170">10.12</span><span class="sxs-lookup"><span data-stu-id="317b6-170">10.12</span></span>     | <span data-ttu-id="317b6-171">1.0.1</span><span class="sxs-lookup"><span data-stu-id="317b6-171">1.0.1</span></span>      |

### <a name="datasets"></a><span data-ttu-id="317b6-172">Conjuntos de dados</span><span class="sxs-lookup"><span data-stu-id="317b6-172">Datasets</span></span>

[<span data-ttu-id="317b6-173">2016 – T3</span><span class="sxs-lookup"><span data-stu-id="317b6-173">2016 - Q3</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2016-q3.tsv)  
[<span data-ttu-id="317b6-174">2016 – T4</span><span class="sxs-lookup"><span data-stu-id="317b6-174">2016 - Q4</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2016-q4.tsv)  
[<span data-ttu-id="317b6-175">2017 – T1</span><span class="sxs-lookup"><span data-stu-id="317b6-175">2017 - Q1</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q1.tsv)  
[<span data-ttu-id="317b6-176">2017 – T2</span><span class="sxs-lookup"><span data-stu-id="317b6-176">2017 - Q2</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q2.tsv)

<span data-ttu-id="317b6-177">Outros conjuntos de dados são publicados usando um formato de URL padrão.</span><span class="sxs-lookup"><span data-stu-id="317b6-177">Additional datasets are posted using a standard URL format.</span></span> <span data-ttu-id="317b6-178">Substitua `<YEAR>` pelo ano e substitua `<QUARTER>` pelo trimestre do ano (use `1`, `2`, `3` ou `4`).</span><span class="sxs-lookup"><span data-stu-id="317b6-178">Replace `<YEAR>` with the year and replace `<QUARTER>` with the quarter of the year (use `1`, `2`, `3`, or `4`).</span></span> <span data-ttu-id="317b6-179">Os arquivos estão no formato *TSV* (valores separados por tabulação).</span><span class="sxs-lookup"><span data-stu-id="317b6-179">The files are in tab-separated values (*TSV*) format.</span></span> 

```
https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-<YEAR>-q<QUARTER>.tsv
```

## <a name="license"></a><span data-ttu-id="317b6-180">Licença</span><span class="sxs-lookup"><span data-stu-id="317b6-180">License</span></span>

<span data-ttu-id="317b6-181">A distribuição da Microsoft do .NET Core é licenciada com o [EULA da MICROSOFT .NET LIBRARY](https://aka.ms/dotnet-core-eula).</span><span class="sxs-lookup"><span data-stu-id="317b6-181">The Microsoft distribution of .NET Core is licensed with the [MICROSOFT .NET LIBRARY EULA](https://aka.ms/dotnet-core-eula).</span></span> <span data-ttu-id="317b6-182">Esta licença inclui a seção “DADOS” para habilitar a telemetria (mostrada abaixo).</span><span class="sxs-lookup"><span data-stu-id="317b6-182">This license includes the "DATA" section to enable telemetry (shown below).</span></span>

<span data-ttu-id="317b6-183">Os [Pacotes NuGet do .NET](https://www.nuget.org/profiles/dotnetframework) usam essa mesma licença, mas não habilitam a telemetria (consulte o [Escopo](#scope)).</span><span class="sxs-lookup"><span data-stu-id="317b6-183">[.NET NuGet packages](https://www.nuget.org/profiles/dotnetframework) use the same license but don't enable telemetry (see [Scope](#scope)).</span></span>

> 2. <span data-ttu-id="317b6-184">DADOS.</span><span class="sxs-lookup"><span data-stu-id="317b6-184">DATA.</span></span> <span data-ttu-id="317b6-185">O software pode coletar informações sobre você e seu uso do software e enviá-las para a Microsoft.</span><span class="sxs-lookup"><span data-stu-id="317b6-185">The software may collect information about you and your use of the software, and send that to Microsoft.</span></span> <span data-ttu-id="317b6-186">A Microsoft pode usar essas informações para melhorar nossos produtos e serviços.</span><span class="sxs-lookup"><span data-stu-id="317b6-186">Microsoft may use this information to improve our products and services.</span></span> <span data-ttu-id="317b6-187">Você pode saber mais sobre coleta e uso de dados na Documentação de Ajuda e na política de privacidade em http://go.microsoft.com/fwlink/?LinkId=528096.</span><span class="sxs-lookup"><span data-stu-id="317b6-187">You can learn more about data collection and use in the help documentation and the privacy statement at http://go.microsoft.com/fwlink/?LinkId=528096.</span></span> <span data-ttu-id="317b6-188">O uso do software serve como consentimento para essas práticas.</span><span class="sxs-lookup"><span data-stu-id="317b6-188">Your use of the software operates as your consent to these practices.</span></span>

## <a name="disclosure"></a><span data-ttu-id="317b6-189">Divulgação</span><span class="sxs-lookup"><span data-stu-id="317b6-189">Disclosure</span></span>

<span data-ttu-id="317b6-190">As Ferramentas da CLI do .NET Core exibem o texto a seguir quando você executa um dos comandos pela primeira vez (por exemplo, `dotnet restore`).</span><span class="sxs-lookup"><span data-stu-id="317b6-190">The .NET Core CLI Tools display the following text when you first run one of the commands (for example, `dotnet restore`).</span></span> <span data-ttu-id="317b6-191">O texto pode variar um pouco dependendo da versão do SDK que você está executando.</span><span class="sxs-lookup"><span data-stu-id="317b6-191">Text may vary slightly depending on the version of the SDK you're running.</span></span> <span data-ttu-id="317b6-192">Essa experiência de “primeira execução” é como a Microsoft notifica você sobre a coleta de dados.</span><span class="sxs-lookup"><span data-stu-id="317b6-192">This "first run" experience is how Microsoft notifies you about data collection.</span></span>

```console
Welcome to .NET Core!
---------------------
Learn more about .NET Core @ https://aka.ms/dotnet-docs. Use dotnet --help to see available commands or go to https://aka.ms/dotnet-cli-docs.
 
Telemetry
--------------
The .NET Core tools collect usage data in order to improve your experience. The data is anonymous and does not include command-line arguments. The data is collected by Microsoft and shared with the community.
You can opt out of telemetry by setting a DOTNET_CLI_TELEMETRY_OPTOUT environment variable to 1 using your favorite shell.
You can read more about .NET Core tools telemetry @ https://aka.ms/dotnet-cli-telemetry.
```

## <a name="see-also"></a><span data-ttu-id="317b6-193">Consulte também</span><span class="sxs-lookup"><span data-stu-id="317b6-193">See also</span></span>

[<span data-ttu-id="317b6-194">O que aprendemos com a telemetria do SDK do .NET Core</span><span class="sxs-lookup"><span data-stu-id="317b6-194">What we've learned from .NET Core SDK Telemetry</span></span>](https://blogs.msdn.microsoft.com/dotnet/2017/07/21/what-weve-learned-from-net-core-sdk-telemetry/)  
<span data-ttu-id="317b6-195">[Fonte de referência de telemetria (repositório dotnet/da cli; versão/branch 2.0.0)](https://github.com/dotnet/cli/blob/release/2.0.0/src/dotnet/Telemetry.cs) </span><span class="sxs-lookup"><span data-stu-id="317b6-195">[Telemetry reference source (dotnet/cli repo; release/2.0.0 branch)](https://github.com/dotnet/cli/blob/release/2.0.0/src/dotnet/Telemetry.cs) </span></span>  
[<span data-ttu-id="317b6-196">Dados de uso do SDK do .NET Core</span><span class="sxs-lookup"><span data-stu-id="317b6-196">.NET Core SDK Usage Data</span></span>](https://github.com/dotnet/core/blob/master/release-notes/cli-usage-data.md)

