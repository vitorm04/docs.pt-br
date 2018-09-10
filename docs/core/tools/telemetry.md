---
title: Telemetria do SDK do .NET Core
description: Descubra os recursos de telemetria do SDK do .NET Core que coletam informações de uso para análise, quais dados são coletados e como desabilitá-los.
author: richlander
ms.author: mairaw
ms.date: 06/20/2018
ms.openlocfilehash: b60fc9d9d619334269343fd858a782cdfeb09ba4
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43513334"
---
# <a name="net-core-sdk-telemetry"></a><span data-ttu-id="88b4e-103">Telemetria do SDK do .NET Core</span><span class="sxs-lookup"><span data-stu-id="88b4e-103">.NET Core SDK telemetry</span></span>

<span data-ttu-id="88b4e-104">O [SDK do .NET Core](index.md) inclui um [recurso de telemetria](https://github.com/dotnet/cli/tree/master/src/dotnet/Telemetry) que coleta informações de uso.</span><span class="sxs-lookup"><span data-stu-id="88b4e-104">The [.NET Core SDK](index.md) includes a [telemetry feature](https://github.com/dotnet/cli/tree/master/src/dotnet/Telemetry) that collects usage information.</span></span> <span data-ttu-id="88b4e-105">É importante que a Equipe do .NET entenda como as ferramentas são usadas para que possa melhorá-las.</span><span class="sxs-lookup"><span data-stu-id="88b4e-105">It's important that the .NET Team understands how the tools are used so they can be improved.</span></span> <span data-ttu-id="88b4e-106">Para obter mais informações, consulte [What we've learned from .NET Core SDK Telemetry](https://blogs.msdn.microsoft.com/dotnet/2017/07/21/what-weve-learned-from-net-core-sdk-telemetry/) (O que aprendemos com a telemetria do SDK do .NET Core).</span><span class="sxs-lookup"><span data-stu-id="88b4e-106">For more information, see [What we've learned from .NET Core SDK Telemetry](https://blogs.msdn.microsoft.com/dotnet/2017/07/21/what-weve-learned-from-net-core-sdk-telemetry/).</span></span>

<span data-ttu-id="88b4e-107">Os dados coletados são anônimos e são publicados de forma agregada para serem usados pela Microsoft e pela comunidade sob a [Licença de Atribuição Creative Commons](https://creativecommons.org/licenses/by/4.0/).</span><span class="sxs-lookup"><span data-stu-id="88b4e-107">The collected data is anonymous and published in an aggregated form for use by both Microsoft and the community under the [Creative Commons Attribution License](https://creativecommons.org/licenses/by/4.0/).</span></span>

## <a name="scope"></a><span data-ttu-id="88b4e-108">Escopo</span><span class="sxs-lookup"><span data-stu-id="88b4e-108">Scope</span></span>

<span data-ttu-id="88b4e-109">O comando `dotnet` é usado para inicializar os aplicativos e a CLI do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="88b4e-109">The `dotnet` command is used to launch both apps and the .NET Core CLI.</span></span> <span data-ttu-id="88b4e-110">O comando `dotnet` em si não realiza coletas de telemetria.</span><span class="sxs-lookup"><span data-stu-id="88b4e-110">The `dotnet` command itself doesn't collect telemetry.</span></span> <span data-ttu-id="88b4e-111">Os comandos da CLI do .NET Core são executados pelo comando `dotnet` para realizar coletas de telemetria.</span><span class="sxs-lookup"><span data-stu-id="88b4e-111">The .NET Core CLI commands run by the `dotnet` command collect the telemetry.</span></span>

<span data-ttu-id="88b4e-112">A telemetria *não é habilitada* ao usar o comando `dotnet` em si sem nenhum comando anexado:</span><span class="sxs-lookup"><span data-stu-id="88b4e-112">Telemetry *isn't enabled* when using the `dotnet` command itself, with no command attached:</span></span>

- `dotnet`
- `dotnet [path-to-app]`

<span data-ttu-id="88b4e-113">A telemetria *é habilitada* ao usar os [comandos da CLI do .NET Core](index.md), como:</span><span class="sxs-lookup"><span data-stu-id="88b4e-113">Telemetry *is enabled* when using the [.NET Core CLI commands](index.md), such as:</span></span>

- `dotnet build`
- `dotnet pack`
- `dotnet restore`
- `dotnet run`

## <a name="how-to-opt-out"></a><span data-ttu-id="88b4e-114">Como recusar</span><span class="sxs-lookup"><span data-stu-id="88b4e-114">How to opt out</span></span>

<span data-ttu-id="88b4e-115">O recurso de telemetria do SDK do .NET Core é habilitado por padrão.</span><span class="sxs-lookup"><span data-stu-id="88b4e-115">The .NET Core SDK telemetry feature is enabled by default.</span></span> <span data-ttu-id="88b4e-116">Recuse o recurso de telemetria configurando a variável de ambiente `DOTNET_CLI_TELEMETRY_OPTOUT` como `1` ou `true`.</span><span class="sxs-lookup"><span data-stu-id="88b4e-116">Opt out of the telemetry feature by setting the `DOTNET_CLI_TELEMETRY_OPTOUT` environment variable to `1` or `true`.</span></span>

## <a name="data-points"></a><span data-ttu-id="88b4e-117">Pontos de dados</span><span class="sxs-lookup"><span data-stu-id="88b4e-117">Data points</span></span>

<span data-ttu-id="88b4e-118">O recurso coleta os seguintes dados:</span><span class="sxs-lookup"><span data-stu-id="88b4e-118">The feature collects the following data:</span></span>

- <span data-ttu-id="88b4e-119">Carimbo de data/hora da invocação&#8224;</span><span class="sxs-lookup"><span data-stu-id="88b4e-119">Timestamp of invocation&#8224;</span></span>
- <span data-ttu-id="88b4e-120">Comando invocado (por exemplo, "build")&#8224;</span><span class="sxs-lookup"><span data-stu-id="88b4e-120">Command invoked (for example, "build")&#8224;</span></span>
- <span data-ttu-id="88b4e-121">Três endereços IP octet usados para determinar a localização geográfica&#8224;</span><span class="sxs-lookup"><span data-stu-id="88b4e-121">Three octet IP address used to determine geographical location&#8224;</span></span>
- <span data-ttu-id="88b4e-122">`ExitCode` do comando</span><span class="sxs-lookup"><span data-stu-id="88b4e-122">`ExitCode` of the command</span></span>
- <span data-ttu-id="88b4e-123">Executor de teste (para projetos de teste)</span><span class="sxs-lookup"><span data-stu-id="88b4e-123">Test runner (for test projects)</span></span>
- <span data-ttu-id="88b4e-124">Sistema operacional e versão&#8224;</span><span class="sxs-lookup"><span data-stu-id="88b4e-124">Operating system and version&#8224;</span></span>
- <span data-ttu-id="88b4e-125">Se as IDs de tempo de execução estão presentes no nó de tempos de execução</span><span class="sxs-lookup"><span data-stu-id="88b4e-125">Whether runtime IDs are present in the runtimes node</span></span>
- <span data-ttu-id="88b4e-126">Versão do SDK do .NET Core&#8224;</span><span class="sxs-lookup"><span data-stu-id="88b4e-126">.NET Core SDK version&#8224;</span></span>

<span data-ttu-id="88b4e-127">&#8224;Essa métrica é publicada.</span><span class="sxs-lookup"><span data-stu-id="88b4e-127">&#8224;This metric is published.</span></span>

<span data-ttu-id="88b4e-128">A partir do SDK 2.0 do .NET Core, os novos pontos de dados são coletados:</span><span class="sxs-lookup"><span data-stu-id="88b4e-128">Starting with .NET Core SDK 2.0, new data points are collected:</span></span>

- <span data-ttu-id="88b4e-129">opções e argumentos de comando do `dotnet`: somente argumentos e opções conhecidos são coletados (não cadeias de caracteres arbitrárias).</span><span class="sxs-lookup"><span data-stu-id="88b4e-129">`dotnet` command arguments and options: only known arguments and options are collected (not arbitrary strings).</span></span>
- <span data-ttu-id="88b4e-130">Se o SDK está em execução em um contêiner.</span><span class="sxs-lookup"><span data-stu-id="88b4e-130">Whether the SDK is running in a container.</span></span>
- <span data-ttu-id="88b4e-131">Estruturas de destino.</span><span class="sxs-lookup"><span data-stu-id="88b4e-131">Target frameworks.</span></span>
- <span data-ttu-id="88b4e-132">Endereço MAC com hash: uma ID única e criptograficamente anônima (SHA256) para um computador.</span><span class="sxs-lookup"><span data-stu-id="88b4e-132">Hashed MAC address: a cryptographically (SHA256) anonymous and unique ID for a machine.</span></span> <span data-ttu-id="88b4e-133">Essa métrica não é publicada.</span><span class="sxs-lookup"><span data-stu-id="88b4e-133">This metric isn't published.</span></span>
- <span data-ttu-id="88b4e-134">Diretório de trabalho atual com hash.</span><span class="sxs-lookup"><span data-stu-id="88b4e-134">Hashed current working directory.</span></span>

<span data-ttu-id="88b4e-135">O recurso não coleta dados pessoais como nomes de usuário ou endereços de emails.</span><span class="sxs-lookup"><span data-stu-id="88b4e-135">The feature doesn't collect personal data, such as usernames or email addresses.</span></span> <span data-ttu-id="88b4e-136">Ele não examina seu código e não extrai dados de nível de projeto confidenciais, como nome, repositório ou autor.</span><span class="sxs-lookup"><span data-stu-id="88b4e-136">It doesn't scan your code and doesn't extract sensitive project-level data, such as name, repo, or author.</span></span> <span data-ttu-id="88b4e-137">Os dados são enviados com segurança para os servidores Microsoft usando a tecnologia [Microsoft Azure Application Insights](https://azure.microsoft.com/services/application-insights/), mantidos em acesso restrito e publicados sob controles de segurança rigorosos dos sistemas do [Armazenamento do Microsoft Azure](https://azure.microsoft.com/services/storage/) seguros.</span><span class="sxs-lookup"><span data-stu-id="88b4e-137">The data is sent securely to Microsoft servers using [Microsoft Azure Application Insights](https://azure.microsoft.com/services/application-insights/) technology, held under restricted access, and published under strict security controls from secure [Azure Storage](https://azure.microsoft.com/services/storage/) systems.</span></span>

<span data-ttu-id="88b4e-138">A equipe do .NET quer saber como as ferramentas são usadas e se elas estão funcionando bem, e não o que você está compilando com as ferramentas.</span><span class="sxs-lookup"><span data-stu-id="88b4e-138">The .NET team wants to know how the tools are used and if they're working well, not what you're building with the tools.</span></span> <span data-ttu-id="88b4e-139">Se você suspeita que a telemetria está coletando dados confidenciais ou que os dados estão sendo manipulados de modo inseguro ou inadequado, registre um problema no repositório [dotnet/cli](https://github.com/dotnet/cli/issues) para investigação.</span><span class="sxs-lookup"><span data-stu-id="88b4e-139">If you suspect that the telemetry is collecting sensitive data or that the data is being insecurely or inappropriately handled, file an issue in the [dotnet/cli](https://github.com/dotnet/cli/issues) repository for investigation.</span></span>

## <a name="published-data"></a><span data-ttu-id="88b4e-140">Dados publicados</span><span class="sxs-lookup"><span data-stu-id="88b4e-140">Published data</span></span>

<span data-ttu-id="88b4e-141">Os dados publicados estão disponíveis trimestralmente e são listados em [.NET Core SDK Usage Data](https://github.com/dotnet/core/blob/master/release-notes/cli-usage-data.md) (Dados de uso do SDK do .NET Core).</span><span class="sxs-lookup"><span data-stu-id="88b4e-141">Published data is available quarterly and are listed at [.NET Core SDK Usage Data](https://github.com/dotnet/core/blob/master/release-notes/cli-usage-data.md).</span></span> <span data-ttu-id="88b4e-142">As colunas de um arquivo de dados são:</span><span class="sxs-lookup"><span data-stu-id="88b4e-142">The columns of a data file are:</span></span>

- <span data-ttu-id="88b4e-143">Timestamp</span><span class="sxs-lookup"><span data-stu-id="88b4e-143">Timestamp</span></span>
- <span data-ttu-id="88b4e-144">Ocorrências&#8224;</span><span class="sxs-lookup"><span data-stu-id="88b4e-144">Occurrences&#8224;</span></span>
- <span data-ttu-id="88b4e-145">Comando</span><span class="sxs-lookup"><span data-stu-id="88b4e-145">Command</span></span>
- <span data-ttu-id="88b4e-146">Geografia&#8225;</span><span class="sxs-lookup"><span data-stu-id="88b4e-146">Geography&#8225;</span></span>
- <span data-ttu-id="88b4e-147">OSFamily</span><span class="sxs-lookup"><span data-stu-id="88b4e-147">OSFamily</span></span>
- <span data-ttu-id="88b4e-148">RuntimeID</span><span class="sxs-lookup"><span data-stu-id="88b4e-148">RuntimeID</span></span>
- <span data-ttu-id="88b4e-149">OSVersion</span><span class="sxs-lookup"><span data-stu-id="88b4e-149">OSVersion</span></span>
- <span data-ttu-id="88b4e-150">SDKVersion</span><span class="sxs-lookup"><span data-stu-id="88b4e-150">SDKVersion</span></span>

<span data-ttu-id="88b4e-151">&#8224;A coluna *Ocorrências* exibe uma contagem agregada do uso desse comando para as métricas dessa linha naquele dia.</span><span class="sxs-lookup"><span data-stu-id="88b4e-151">&#8224;The *Occurrences* column displays the aggregate count of that command's use for that row's metrics that day.</span></span>

<span data-ttu-id="88b4e-152">&#8225;Normalmente, a coluna *Geografia* exibe o nome de um país.</span><span class="sxs-lookup"><span data-stu-id="88b4e-152">&#8225;Typically, the *Geography* column displays the name of a country.</span></span> <span data-ttu-id="88b4e-153">Em alguns casos, continente da Antártida aparece na coluna, devido ao fato de os pesquisadores usarem o .NET Core na Antártida ou a dados de localização incorretos.</span><span class="sxs-lookup"><span data-stu-id="88b4e-153">In some cases, the continent of Antarctica appears in this column, either due to researchers using .NET Core in Antarctica or incorrect location data.</span></span>

### <a name="example"></a><span data-ttu-id="88b4e-154">Exemplo</span><span class="sxs-lookup"><span data-stu-id="88b4e-154">Example</span></span>

| <span data-ttu-id="88b4e-155">Timestamp</span><span class="sxs-lookup"><span data-stu-id="88b4e-155">Timestamp</span></span>      | <span data-ttu-id="88b4e-156">Ocorrências</span><span class="sxs-lookup"><span data-stu-id="88b4e-156">Occurrences</span></span> | <span data-ttu-id="88b4e-157">Comando</span><span class="sxs-lookup"><span data-stu-id="88b4e-157">Command</span></span> | <span data-ttu-id="88b4e-158">Geografia</span><span class="sxs-lookup"><span data-stu-id="88b4e-158">Geography</span></span> | <span data-ttu-id="88b4e-159">OSFamily</span><span class="sxs-lookup"><span data-stu-id="88b4e-159">OSFamily</span></span> | <span data-ttu-id="88b4e-160">RuntimeID</span><span class="sxs-lookup"><span data-stu-id="88b4e-160">RuntimeID</span></span>     | <span data-ttu-id="88b4e-161">OSVersion</span><span class="sxs-lookup"><span data-stu-id="88b4e-161">OSVersion</span></span> | <span data-ttu-id="88b4e-162">SDKVersion</span><span class="sxs-lookup"><span data-stu-id="88b4e-162">SDKVersion</span></span> |
| -------------- | ----------- | ------- | --------- | -------- | ------------- | --------- | ---------- |
| <span data-ttu-id="88b4e-163">4/16/2017 0:00</span><span class="sxs-lookup"><span data-stu-id="88b4e-163">4/16/2017 0:00</span></span> | <span data-ttu-id="88b4e-164">8</span><span class="sxs-lookup"><span data-stu-id="88b4e-164">8</span></span>           | <span data-ttu-id="88b4e-165">executar</span><span class="sxs-lookup"><span data-stu-id="88b4e-165">run</span></span>     | <span data-ttu-id="88b4e-166">Uganda</span><span class="sxs-lookup"><span data-stu-id="88b4e-166">Uganda</span></span>    | <span data-ttu-id="88b4e-167">Darwin</span><span class="sxs-lookup"><span data-stu-id="88b4e-167">Darwin</span></span>   | <span data-ttu-id="88b4e-168">osx.10.12-x64</span><span class="sxs-lookup"><span data-stu-id="88b4e-168">osx.10.12-x64</span></span> | <span data-ttu-id="88b4e-169">10.12</span><span class="sxs-lookup"><span data-stu-id="88b4e-169">10.12</span></span>     | <span data-ttu-id="88b4e-170">1.0.1</span><span class="sxs-lookup"><span data-stu-id="88b4e-170">1.0.1</span></span>      |

### <a name="datasets"></a><span data-ttu-id="88b4e-171">Conjuntos de dados</span><span class="sxs-lookup"><span data-stu-id="88b4e-171">Datasets</span></span>

[<span data-ttu-id="88b4e-172">2016 – T3</span><span class="sxs-lookup"><span data-stu-id="88b4e-172">2016 - Q3</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2016-q3.tsv)  
[<span data-ttu-id="88b4e-173">2016 – T4</span><span class="sxs-lookup"><span data-stu-id="88b4e-173">2016 - Q4</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2016-q4.tsv)  
[<span data-ttu-id="88b4e-174">2017 – T1</span><span class="sxs-lookup"><span data-stu-id="88b4e-174">2017 - Q1</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q1.tsv)  
[<span data-ttu-id="88b4e-175">2017 – T2</span><span class="sxs-lookup"><span data-stu-id="88b4e-175">2017 - Q2</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q2.tsv)  
[<span data-ttu-id="88b4e-176">2017 – T3</span><span class="sxs-lookup"><span data-stu-id="88b4e-176">2017 - Q3</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q3.tsv)  
[<span data-ttu-id="88b4e-177">2017 – T4</span><span class="sxs-lookup"><span data-stu-id="88b4e-177">2017 - Q4</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q4.tsv)  

<span data-ttu-id="88b4e-178">Outros conjuntos de dados são publicados usando um formato de URL padrão.</span><span class="sxs-lookup"><span data-stu-id="88b4e-178">Additional datasets are posted using a standard URL format.</span></span> <span data-ttu-id="88b4e-179">Substitua `<YEAR>` pelo ano e substitua `<QUARTER>` pelo trimestre do ano (use `1`, `2`, `3` ou `4`).</span><span class="sxs-lookup"><span data-stu-id="88b4e-179">Replace `<YEAR>` with the year and replace `<QUARTER>` with the quarter of the year (use `1`, `2`, `3`, or `4`).</span></span> <span data-ttu-id="88b4e-180">Os arquivos estão no formato *TSV* (valores separados por tabulação).</span><span class="sxs-lookup"><span data-stu-id="88b4e-180">The files are in tab-separated values (*TSV*) format.</span></span>

`https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-<YEAR>-q<QUARTER>.tsv`

## <a name="license"></a><span data-ttu-id="88b4e-181">Licença</span><span class="sxs-lookup"><span data-stu-id="88b4e-181">License</span></span>

<span data-ttu-id="88b4e-182">A distribuição da Microsoft do .NET Core é licenciada com o [EULA da MICROSOFT .NET LIBRARY](https://aka.ms/dotnet-core-eula).</span><span class="sxs-lookup"><span data-stu-id="88b4e-182">The Microsoft distribution of .NET Core is licensed with the [MICROSOFT .NET LIBRARY EULA](https://aka.ms/dotnet-core-eula).</span></span> <span data-ttu-id="88b4e-183">Esta licença inclui a seção “DADOS” para habilitar a telemetria (mostrada abaixo).</span><span class="sxs-lookup"><span data-stu-id="88b4e-183">This license includes the "DATA" section to enable telemetry (shown below).</span></span>

<span data-ttu-id="88b4e-184">Os [Pacotes NuGet do .NET](https://www.nuget.org/profiles/dotnetframework) usam essa mesma licença, mas não habilitam a telemetria (consulte o [Escopo](#scope)).</span><span class="sxs-lookup"><span data-stu-id="88b4e-184">[.NET NuGet packages](https://www.nuget.org/profiles/dotnetframework) use the same license but don't enable telemetry (see [Scope](#scope)).</span></span>

> 2. <span data-ttu-id="88b4e-185">DADOS.</span><span class="sxs-lookup"><span data-stu-id="88b4e-185">DATA.</span></span> <span data-ttu-id="88b4e-186">O software pode coletar informações sobre você e seu uso do software e enviá-las para a Microsoft.</span><span class="sxs-lookup"><span data-stu-id="88b4e-186">The software may collect information about you and your use of the software, and send that to Microsoft.</span></span> <span data-ttu-id="88b4e-187">A Microsoft pode usar essas informações para melhorar nossos produtos e serviços.</span><span class="sxs-lookup"><span data-stu-id="88b4e-187">Microsoft may use this information to improve our products and services.</span></span> <span data-ttu-id="88b4e-188">Você pode saber mais sobre coleta e uso de dados na documentação de ajuda e na política de privacidade em http://go.microsoft.com/fwlink/?LinkId=528096.</span><span class="sxs-lookup"><span data-stu-id="88b4e-188">You can learn more about data collection and use in the help documentation and the privacy statement at http://go.microsoft.com/fwlink/?LinkId=528096.</span></span> <span data-ttu-id="88b4e-189">O uso do software serve como consentimento para essas práticas.</span><span class="sxs-lookup"><span data-stu-id="88b4e-189">Your use of the software operates as your consent to these practices.</span></span>

## <a name="disclosure"></a><span data-ttu-id="88b4e-190">Divulgação</span><span class="sxs-lookup"><span data-stu-id="88b4e-190">Disclosure</span></span>

<span data-ttu-id="88b4e-191">O SDK do .NET Core exibe o texto a seguir quando você executa pela primeira vez um dos [comandos da CLI do .NET Core](index.md) (por exemplo, `dotnet restore`).</span><span class="sxs-lookup"><span data-stu-id="88b4e-191">The .NET Core SDK displays the following text when you first run one of the [.NET Core CLI commands](index.md) (for example, `dotnet restore`).</span></span> <span data-ttu-id="88b4e-192">O texto pode variar um pouco dependendo da versão do SDK que você está executando.</span><span class="sxs-lookup"><span data-stu-id="88b4e-192">Text may vary slightly depending on the version of the SDK you're running.</span></span> <span data-ttu-id="88b4e-193">Essa experiência de “primeira execução” é como a Microsoft notifica você sobre a coleta de dados.</span><span class="sxs-lookup"><span data-stu-id="88b4e-193">This "first run" experience is how Microsoft notifies you about data collection.</span></span>

```console
Welcome to .NET Core!
---------------------
Learn more about .NET Core: https://aka.ms/dotnet-docs
Use 'dotnet --help' to see available commands or visit: https://aka.ms/dotnet-cli-docs

Telemetry
---------
The .NET Core tools collect usage data in order to help us improve your experience.
The data is anonymous and doesn't include command-line arguments.
The data is collected by Microsoft and shared with the community.
You can opt-out of telemetry by setting the DOTNET_CLI_TELEMETRY_OPTOUT environment variable to '1' or 'true' using your favorite shell.

Read more about .NET Core CLI Tools telemetry: https://aka.ms/dotnet-cli-telemetry
```

## <a name="see-also"></a><span data-ttu-id="88b4e-194">Consulte também</span><span class="sxs-lookup"><span data-stu-id="88b4e-194">See also</span></span>

- [<span data-ttu-id="88b4e-195">O que aprendemos com a telemetria do SDK do .NET Core</span><span class="sxs-lookup"><span data-stu-id="88b4e-195">What we've learned from .NET Core SDK Telemetry</span></span>](https://blogs.msdn.microsoft.com/dotnet/2017/07/21/what-weve-learned-from-net-core-sdk-telemetry/)
- [<span data-ttu-id="88b4e-196">Fonte de referência de telemetria (repositório dotnet/cli)</span><span class="sxs-lookup"><span data-stu-id="88b4e-196">Telemetry reference source (dotnet/cli repo)</span></span>](https://github.com/dotnet/cli/tree/master/src/dotnet/Telemetry)
- [<span data-ttu-id="88b4e-197">Dados de uso do SDK do .NET Core</span><span class="sxs-lookup"><span data-stu-id="88b4e-197">.NET Core SDK Usage Data</span></span>](https://github.com/dotnet/core/blob/master/release-notes/cli-usage-data.md)
