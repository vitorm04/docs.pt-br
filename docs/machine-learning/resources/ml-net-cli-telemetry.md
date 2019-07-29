---
title: Coleta de telemetria pela CLI do ML.NET
description: Conheça os recursos de telemetria da CLI do ML.NET que coletam informações de uso para análise, quais dados são coletados e como desabilitá-los. Além disso, encontre links para o contrato de licença do .NET e informações sobre a conformidade com o RGPD da Microsoft.
ms.topic: conceptual
ms.date: 05/05/2019
ms.custom: ''
ms.openlocfilehash: eab1e37d7d0d47251c4f92422730b105cf2db265
ms.sourcegitcommit: 1e7ac70be1b4d89708c0d9552897515f2cbf52c4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68433790"
---
# <a name="telemetry-collection-by-the-mlnet-cli"></a><span data-ttu-id="06546-104">Coleta de telemetria pela CLI do ML.NET</span><span class="sxs-lookup"><span data-stu-id="06546-104">Telemetry collection by the ML.NET CLI</span></span>

<span data-ttu-id="06546-105">A [CLI do ML.NET](https://aka.ms/mlnet-cli) inclui um recurso de telemetria que coleta dados anônimos de uso que são agregados para uso pela Microsoft.</span><span class="sxs-lookup"><span data-stu-id="06546-105">The [ML.NET CLI](https://aka.ms/mlnet-cli) includes a telemetry feature that collects anonymous usage data that is aggregated for use by Microsoft.</span></span>

## <a name="how-microsoft-uses-the-data"></a><span data-ttu-id="06546-106">Como a Microsoft usa os dados</span><span class="sxs-lookup"><span data-stu-id="06546-106">How Microsoft uses the data</span></span>

<span data-ttu-id="06546-107">A equipe de produto usa dados de telemetria do ML.NET CLI para ajudar a entender como melhorar as ferramentas.</span><span class="sxs-lookup"><span data-stu-id="06546-107">The product team uses ML.NET CLI telemetry data to help understand how to improve the tools.</span></span> <span data-ttu-id="06546-108">Por exemplo, se os clientes usarem com pouca frequência uma determinada tarefa de aprendizado de máquina, a equipe de produto investigará por que e usará as descobertas para priorizar o desenvolvimento de recursos.</span><span class="sxs-lookup"><span data-stu-id="06546-108">For example, if customers infrequently use a particular machine learning task, the product team investigates why and uses findings to prioritize feature development.</span></span> <span data-ttu-id="06546-109">A telemetria da CLI do ML.NET também ajuda com a depuração de problemas, como falhas e anomalias de código.</span><span class="sxs-lookup"><span data-stu-id="06546-109">ML.NET CLI telemetry also helps with debugging of issues such as crashes and code anomalies.</span></span> 

<span data-ttu-id="06546-110">Embora a equipe de produto aprecia essas informações, ela também sabe que nem todo mundo deseja enviá-las.</span><span class="sxs-lookup"><span data-stu-id="06546-110">While the product team appreciates this insight, we also know that not everyone wants to send this data.</span></span> [<span data-ttu-id="06546-111">Saiba como desabilitar a telemetria.</span><span class="sxs-lookup"><span data-stu-id="06546-111">Find out how to disable telemetry.</span></span>](#opt-out-of-data-collection)

## <a name="scope"></a><span data-ttu-id="06546-112">Escopo</span><span class="sxs-lookup"><span data-stu-id="06546-112">Scope</span></span>

<span data-ttu-id="06546-113">O comando `mlnet` inicia a CLI do ML.NET, mas o comando em si não coleta telemetria.</span><span class="sxs-lookup"><span data-stu-id="06546-113">The `mlnet` command launches the ML.NET CLI, but the command itself doesn't collect telemetry.</span></span>

<span data-ttu-id="06546-114">A telemetria *não está habilitada* quando você executa o `mlnet` sem outro comando anexado.</span><span class="sxs-lookup"><span data-stu-id="06546-114">Telemetry *isn't enabled* when you run the `mlnet` command with no other command attached.</span></span> <span data-ttu-id="06546-115">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="06546-115">For example:</span></span>

- `mlnet`
- `mlnet --help`

<span data-ttu-id="06546-116">A telemetria *está habilitado* quando você executa um [comando da CLI do ML.NET](../reference/ml-net-cli-reference.md), como `mlnet auto-train`.</span><span class="sxs-lookup"><span data-stu-id="06546-116">Telemetry *is enabled* when you run an [ML.NET CLI command](../reference/ml-net-cli-reference.md), such as `mlnet auto-train`.</span></span>

## <a name="opt-out-of-data-collection"></a><span data-ttu-id="06546-117">Recusar a coleta de dados</span><span class="sxs-lookup"><span data-stu-id="06546-117">Opt out of data collection</span></span>

<span data-ttu-id="06546-118">O recurso de telemetria da CLI do ML.NET Core está habilitado por padrão.</span><span class="sxs-lookup"><span data-stu-id="06546-118">The ML.NET CLI telemetry feature is enabled by default.</span></span>

<span data-ttu-id="06546-119">Recuse o recurso de telemetria configurando a variável de ambiente `DOTNET_CLI_TELEMETRY_OPTOUT` como `1` ou `true`.</span><span class="sxs-lookup"><span data-stu-id="06546-119">Opt out of the telemetry feature by setting the `DOTNET_CLI_TELEMETRY_OPTOUT` environment variable to `1` or `true`.</span></span> <span data-ttu-id="06546-120">Essa variável de ambiente se aplica globalmente à ferramenta de CLI do .NET.</span><span class="sxs-lookup"><span data-stu-id="06546-120">This environment variable applies globally to the .NET CLI tool.</span></span>

## <a name="data-points-collected"></a><span data-ttu-id="06546-121">Pontos de dados coletados</span><span class="sxs-lookup"><span data-stu-id="06546-121">Data points collected</span></span>

<span data-ttu-id="06546-122">O recurso coleta os seguintes dados:</span><span class="sxs-lookup"><span data-stu-id="06546-122">The feature collects the following data:</span></span>

- <span data-ttu-id="06546-123">Qual comando foi invocado, como `auto-train`</span><span class="sxs-lookup"><span data-stu-id="06546-123">What command was invoked, such as `auto-train`</span></span>
- <span data-ttu-id="06546-124">Nomes de parâmetro de linha de comando usados (por ex., “dataset-name, label-column-name, ml-task, output-path, max-exploration-time, verbosity”)</span><span class="sxs-lookup"><span data-stu-id="06546-124">Command-line parameter names used (i.e. "dataset-name, label-column-name, ml-task, output-path, max-exploration-time, verbosity")</span></span>
- <span data-ttu-id="06546-125">Endereço MAC com hash: uma ID única e criptograficamente anônima (SHA256) para um computador</span><span class="sxs-lookup"><span data-stu-id="06546-125">Hashed MAC address: a cryptographically (SHA256) anonymous and unique ID for a machine</span></span>
- <span data-ttu-id="06546-126">Carimbo de data/hora de uma invocação</span><span class="sxs-lookup"><span data-stu-id="06546-126">Timestamp of an invocation</span></span>
- <span data-ttu-id="06546-127">Três endereços IP de octeto (não um endereço IP completo) usados apenas para determinar a localização geográfica</span><span class="sxs-lookup"><span data-stu-id="06546-127">Three octet IP address (not full IP address) used only to determine geographical location</span></span>
- <span data-ttu-id="06546-128">Nome de todos os argumentos/parâmetros usados.</span><span class="sxs-lookup"><span data-stu-id="06546-128">Name of all arguments/parameters used.</span></span> <span data-ttu-id="06546-129">Não valores do cliente, como cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="06546-129">Not the customer's values, such as strings</span></span>
- <span data-ttu-id="06546-130">Nome do arquivo de conjunto de dados com hash</span><span class="sxs-lookup"><span data-stu-id="06546-130">Hashed dataset filename</span></span>
- <span data-ttu-id="06546-131">Bucket do tamanho do arquivo de conjunto de dados</span><span class="sxs-lookup"><span data-stu-id="06546-131">Dataset file-size bucket</span></span>
- <span data-ttu-id="06546-132">Sistema operacional e versão</span><span class="sxs-lookup"><span data-stu-id="06546-132">Operating system and version</span></span>
- <span data-ttu-id="06546-133">Valor do parâmetro --task: Valores categóricos, como `regression`, `binary-classification` e `multiclass-classification`</span><span class="sxs-lookup"><span data-stu-id="06546-133">Value of --task parameter: Categorical values, such as `regression`, `binary-classification`, and `multiclass-classification`</span></span>
- <span data-ttu-id="06546-134">Versão da CLI do ML.NET (por ex., 0.3.27703.4)</span><span class="sxs-lookup"><span data-stu-id="06546-134">ML.NET CLI version (i.e. 0.3.27703.4)</span></span>

<span data-ttu-id="06546-135">Os dados são enviados com segurança para os servidores Microsoft usando a tecnologia [Azure Application Insights](https://azure.microsoft.com/services/application-insights/), mantidos em acesso restrito e usados sob controles de segurança rigorosos dos sistemas do [Armazenamento do Microsoft Azure](https://azure.microsoft.com/services/storage/) seguros.</span><span class="sxs-lookup"><span data-stu-id="06546-135">The data is sent securely to Microsoft servers using [Azure Application Insights](https://azure.microsoft.com/services/application-insights/) technology, held under restricted access, and used under strict security controls from secure [Azure Storage](https://azure.microsoft.com/services/storage/) systems.</span></span>

### <a name="data-points-not-collected"></a><span data-ttu-id="06546-136">Pontos de dados não coletados</span><span class="sxs-lookup"><span data-stu-id="06546-136">Data points not collected</span></span>
<span data-ttu-id="06546-137">O recurso de telemetria *não* coleta:</span><span class="sxs-lookup"><span data-stu-id="06546-137">The telemetry feature *doesn't* collect:</span></span>
- <span data-ttu-id="06546-138">dados pessoais, como nomes de usuário</span><span class="sxs-lookup"><span data-stu-id="06546-138">personal data, such as usernames</span></span>
- <span data-ttu-id="06546-139">nomes de arquivo de conjunto de dados</span><span class="sxs-lookup"><span data-stu-id="06546-139">dataset filenames</span></span>
- <span data-ttu-id="06546-140">dados de arquivos de conjunto de dados</span><span class="sxs-lookup"><span data-stu-id="06546-140">data from dataset files</span></span>

<span data-ttu-id="06546-141">Se você suspeita que a telemetria da CLI do ML.NET está coletando dados confidenciais ou que os dados estão sendo manipulados de modo inseguro ou inadequado, registre um problema no repositório [ML.NET](https://github.com/dotnet/machinelearning) para investigação.</span><span class="sxs-lookup"><span data-stu-id="06546-141">If you suspect that the ML.NET CLI telemetry is collecting sensitive data or that the data is being insecurely or inappropriately handled, file an issue in the [ML.NET](https://github.com/dotnet/machinelearning) repository for investigation.</span></span>

## <a name="license"></a><span data-ttu-id="06546-142">Licença</span><span class="sxs-lookup"><span data-stu-id="06546-142">License</span></span>

<span data-ttu-id="06546-143">A distribuição da Microsoft da CLI do ML.NET é licenciada com os [Termos de licença de software da Microsoft: Biblioteca do Microsoft .NET](https://aka.ms/dotnet-core-eula).</span><span class="sxs-lookup"><span data-stu-id="06546-143">The Microsoft distribution of ML.NET CLI is licensed with the [Microsoft Software License Terms: Microsoft .NET Library](https://aka.ms/dotnet-core-eula).</span></span> <span data-ttu-id="06546-144">Para obter detalhes sobre a coleta e o processamento de dados, veja a seção intitulada "Dados".</span><span class="sxs-lookup"><span data-stu-id="06546-144">For details on data collection and processing, see the section entitled "Data."</span></span>

## <a name="disclosure"></a><span data-ttu-id="06546-145">Divulgação</span><span class="sxs-lookup"><span data-stu-id="06546-145">Disclosure</span></span>

<span data-ttu-id="06546-146">Quando você executar pela primeira vez um [comando da CLI do ML.NET](../reference/ml-net-cli-reference.md), como `mlnet auto-train`, a ferramenta da CLI do ML.NET exibe o texto de divulgação que informa como recusar a telemetria.</span><span class="sxs-lookup"><span data-stu-id="06546-146">When you first run a [ML.NET CLI command](../reference/ml-net-cli-reference.md) such as `mlnet auto-train`, the ML.NET CLI tool displays disclosure text that tells you how to opt out of telemetry.</span></span> <span data-ttu-id="06546-147">O texto pode variar um pouco dependendo da versão da CLI que você está executando.</span><span class="sxs-lookup"><span data-stu-id="06546-147">Text may vary slightly depending on the version of the CLI you're running.</span></span>

## <a name="see-also"></a><span data-ttu-id="06546-148">Consulte também</span><span class="sxs-lookup"><span data-stu-id="06546-148">See also</span></span>
- [<span data-ttu-id="06546-149">Referência da CLI do ML.NET</span><span class="sxs-lookup"><span data-stu-id="06546-149">ML.NET CLI reference</span></span>](../reference/ml-net-cli-reference.md)
- [<span data-ttu-id="06546-150">Termos de licença de software da Microsoft: Microsoft do Microsoft .NET</span><span class="sxs-lookup"><span data-stu-id="06546-150">Microsoft Software License Terms: Microsoft .NET Library</span></span>](https://aka.ms/dotnet-core-eula)
- [<span data-ttu-id="06546-151">Privacidade na Microsoft</span><span class="sxs-lookup"><span data-stu-id="06546-151">Privacy at Microsoft</span></span>](https://www.microsoft.com/trustcenter/privacy/)
- [<span data-ttu-id="06546-152">Política de privacidade da Microsoft</span><span class="sxs-lookup"><span data-stu-id="06546-152">Microsoft Privacy Statement</span></span>](https://privacy.microsoft.com/privacystatement)
