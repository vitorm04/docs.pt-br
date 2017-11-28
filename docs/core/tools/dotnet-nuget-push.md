---
title: "Comando dotnet nuget push – CLI do .NET Core"
description: O comando dotnet nuget push efetua push de um pacote no servidor e o publica.
author: karann-msft
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.openlocfilehash: 6721615e4df820ab50ea4f79fbba30daeffe8165
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="dotnet-nuget-push"></a><span data-ttu-id="3c251-103">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="3c251-103">dotnet nuget push</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="3c251-104">Nome</span><span class="sxs-lookup"><span data-stu-id="3c251-104">Name</span></span>

<span data-ttu-id="3c251-105">`dotnet nuget push` – Envia um pacote ao servidor e os publica.</span><span class="sxs-lookup"><span data-stu-id="3c251-105">`dotnet nuget push` - Pushes a package to the server and publishes it.</span></span>

## <a name="synopsis"></a><span data-ttu-id="3c251-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="3c251-106">Synopsis</span></span>

`dotnet nuget push [<ROOT>] [-s|--source] [-ss|--symbol-source] [-t|--timeout] [-k|--api-key] [-sk|--symbol-api-key] [-d|--disable-buffering] [-n|--no-symbols] [--force-english-output] [-h|--help]`

## <a name="description"></a><span data-ttu-id="3c251-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="3c251-107">Description</span></span>

<span data-ttu-id="3c251-108">O comando `dotnet nuget push` envia um pacote ao servidor e os publica.</span><span class="sxs-lookup"><span data-stu-id="3c251-108">The `dotnet nuget push` command pushes a package to the server and publishes it.</span></span> <span data-ttu-id="3c251-109">O comando push usa o servidor e detalhes de credencial encontradas no arquivo de configuração do sistema NuGet ou uma cadeia de arquivos de configuração.</span><span class="sxs-lookup"><span data-stu-id="3c251-109">The push command uses server and credential details found in the system's NuGet config file or chain of config files.</span></span> <span data-ttu-id="3c251-110">Para obter mais informações sobre arquivos de configuração, consulte [Configurando o comportamento do NuGet](/nuget/consume-packages/configuring-nuget-behavior).</span><span class="sxs-lookup"><span data-stu-id="3c251-110">For more information on config files, see [Configuring NuGet Behavior](/nuget/consume-packages/configuring-nuget-behavior).</span></span> <span data-ttu-id="3c251-111">A configuração de padrão do NuGet é obtida ao carregar *%AppData%\NuGet\NuGet.config* (Windows) ou *$HOME/.local/share* (Linux/macOS) e, em seguida, carregar qualquer *nuget.config* ou *.nuget\nuget.config* da raiz da unidade e terminar no diretório atual.</span><span class="sxs-lookup"><span data-stu-id="3c251-111">NuGet's default configuration is obtained by loading *%AppData%\NuGet\NuGet.config* (Windows) or *$HOME/.local/share* (Linux/macOS), then loading any *nuget.config* or *.nuget\nuget.config* starting from the root of drive and ending in the current directory.</span></span>

## <a name="arguments"></a><span data-ttu-id="3c251-112">Arguments</span><span class="sxs-lookup"><span data-stu-id="3c251-112">Arguments</span></span>

`ROOT`

<span data-ttu-id="3c251-113">Especifique o caminho até o pacote e sua chave de API para enviar o pacote por push para o servidor.</span><span class="sxs-lookup"><span data-stu-id="3c251-113">Specify the path to the package and your API key to push the package to the server.</span></span>

## <a name="options"></a><span data-ttu-id="3c251-114">Opções</span><span class="sxs-lookup"><span data-stu-id="3c251-114">Options</span></span>

`-h|--help`

<span data-ttu-id="3c251-115">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="3c251-115">Prints out a short help for the command.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="3c251-116">Especifica a URL do servidor.</span><span class="sxs-lookup"><span data-stu-id="3c251-116">Specifies the server URL.</span></span> <span data-ttu-id="3c251-117">Essa opção será obrigatória, a menos que o valor de configuração `DefaultPushSource` seja definido no arquivo de configuração do NuGet.</span><span class="sxs-lookup"><span data-stu-id="3c251-117">This option is required unless `DefaultPushSource` config value is set in the NuGet config file.</span></span>

`--symbols-source <SOURCE>`

<span data-ttu-id="3c251-118">Especifica a URL do servidor de símbolos.</span><span class="sxs-lookup"><span data-stu-id="3c251-118">Specifies the symbol server URL.</span></span>

`-t|--timeout <TIMEOUT>`

<span data-ttu-id="3c251-119">Especifica o tempo limite para enviar para um servidor em segundos.</span><span class="sxs-lookup"><span data-stu-id="3c251-119">Specifies the timeout for pushing to a server in seconds.</span></span> <span data-ttu-id="3c251-120">O padrão é 300 segundos (5 minutos).</span><span class="sxs-lookup"><span data-stu-id="3c251-120">Defaults to 300 seconds (5 minutes).</span></span> <span data-ttu-id="3c251-121">Especificar 0 (zero segundos) aplica o valor padrão.</span><span class="sxs-lookup"><span data-stu-id="3c251-121">Specifying 0 (zero seconds) applies the default value.</span></span>

`-k|--api-key <API_KEY>`

<span data-ttu-id="3c251-122">A chave da API para o servidor.</span><span class="sxs-lookup"><span data-stu-id="3c251-122">The API key for the server.</span></span>

`--symbol-api-key <API_KEY>`

<span data-ttu-id="3c251-123">A chave da API para o servidor de símbolos.</span><span class="sxs-lookup"><span data-stu-id="3c251-123">The API key for the symbol server.</span></span>

`-d|--disable-buffering`

<span data-ttu-id="3c251-124">Desabilita o armazenamento em buffer ao enviar a um servidor HTTP(S) para diminuir o uso de memória.</span><span class="sxs-lookup"><span data-stu-id="3c251-124">Disables buffering when pushing to an HTTP(S) server to decrease memory usage.</span></span>

`-n|--no-symbols`

<span data-ttu-id="3c251-125">Não envia símbolos por push (mesmo se estiver presente).</span><span class="sxs-lookup"><span data-stu-id="3c251-125">Doesn't push symbols (even if present).</span></span>

`--force-english-output`

<span data-ttu-id="3c251-126">Força todas as saídas registradas em inglês.</span><span class="sxs-lookup"><span data-stu-id="3c251-126">Forces all logged output in English.</span></span>

## <a name="examples"></a><span data-ttu-id="3c251-127">Exemplos</span><span class="sxs-lookup"><span data-stu-id="3c251-127">Examples</span></span>

<span data-ttu-id="3c251-128">Envia por push *foo.nupkg* à origem de push padrão, fornecendo uma chave de API:</span><span class="sxs-lookup"><span data-stu-id="3c251-128">Pushes *foo.nupkg* to the default push source, providing an API key:</span></span>

`dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a`

<span data-ttu-id="3c251-129">Envia por push *foo.nupkg* à origem de push personalizada `http://customsource`, fornecendo uma chave de API:</span><span class="sxs-lookup"><span data-stu-id="3c251-129">Push *foo.nupkg* to the custom push source `http://customsource`, providing an API key:</span></span>

`dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s http://customsource/`

<span data-ttu-id="3c251-130">Envia por push *foo.nupkg* à origem de push padrão:</span><span class="sxs-lookup"><span data-stu-id="3c251-130">Pushes *foo.nupkg* to the default push source:</span></span>

`dotnet nuget push foo.nupkg`

<span data-ttu-id="3c251-131">Envia por push *foo.nupkg* à origem de símbolos padrão:</span><span class="sxs-lookup"><span data-stu-id="3c251-131">Pushes *foo.symbols.nupkg* to the default symbols source:</span></span>

`dotnet nuget push foo.symbols.nupkg`

<span data-ttu-id="3c251-132">Envia por push *foo.nupkg* à origem de push padrão, especificando um tempo limite de 360 segundos:</span><span class="sxs-lookup"><span data-stu-id="3c251-132">Pushes *foo.nupkg* to the default push source, specifying a 360 second timeout:</span></span>

`dotnet nuget push foo.nupkg --timeout 360`

<span data-ttu-id="3c251-133">Envia por push todos os arquivos *.nupkg* no diretório atual à origem de push padrão:</span><span class="sxs-lookup"><span data-stu-id="3c251-133">Pushes all *.nupkg* files in the current directory to the default push source:</span></span>

`dotnet nuget push *.nupkg`

<span data-ttu-id="3c251-134">Envia por push todos os arquivos *.nupkg* no diretório atual à origem de push padrão, especificando um arquivo de configuração personalizado *./config/My.Config*:</span><span class="sxs-lookup"><span data-stu-id="3c251-134">Pushes all *.nupkg* files in the current directory to the default push source, specifying a custom config file *./config/My.Config*:</span></span>

`dotnet nuget push *.nupkg --config-file ./config/My.Config`

<span data-ttu-id="3c251-135">Envia por push todos os arquivos *.nupkg* no diretório atual à origem de push padrão, com detalhamento máximo:</span><span class="sxs-lookup"><span data-stu-id="3c251-135">Push all *.nupkg* files in the current directory to the default push source with maximum verbosity:</span></span>

`dotnet nuget push *.nupkg --verbosity detailed`
