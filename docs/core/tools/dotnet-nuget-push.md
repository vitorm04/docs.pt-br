---
title: Comando dotnet nuget push – CLI do .NET Core
description: O comando dotnet nuget push efetua push de um pacote no servidor e o publica.
author: karann-msft
ms.author: mairaw
ms.date: 09/04/2018
ms.openlocfilehash: 23d27cef29008955850f9ed9f4a8baed9e7ad982
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/16/2018
ms.locfileid: "45609972"
---
# <a name="dotnet-nuget-push"></a><span data-ttu-id="03ff2-103">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="03ff2-103">dotnet nuget push</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="03ff2-104">Nome</span><span class="sxs-lookup"><span data-stu-id="03ff2-104">Name</span></span>

<span data-ttu-id="03ff2-105">`dotnet nuget push` – Envia um pacote ao servidor e os publica.</span><span class="sxs-lookup"><span data-stu-id="03ff2-105">`dotnet nuget push` - Pushes a package to the server and publishes it.</span></span>

## <a name="synopsis"></a><span data-ttu-id="03ff2-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="03ff2-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="03ff2-107">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="03ff2-107">.NET Core 2.1</span></span>](#tab/netcore21)
```
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output] [-k|--api-key] [-n|--no-symbols]
    [--no-service-endpoint] [-s|--source] [-sk|--symbol-api-key] [-ss|--symbol-source] [-t|--timeout]
dotnet nuget push [-h|--help]
```
# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="03ff2-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="03ff2-108">.NET Core 2.0</span></span>](#tab/netcore20)
```
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output] [-k|--api-key] [-n|--no-symbols]
    [-s|--source] [-sk|--symbol-api-key] [-ss|--symbol-source] [-t|--timeout]
dotnet nuget push [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="03ff2-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="03ff2-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output] [-k|--api-key] [-n|--no-symbols]
    [-s|--source] [-sk|--symbol-api-key] [-ss|--symbol-source] [-t|--timeout]
dotnet nuget push [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="03ff2-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="03ff2-110">Description</span></span>

<span data-ttu-id="03ff2-111">O comando `dotnet nuget push` envia um pacote ao servidor e os publica.</span><span class="sxs-lookup"><span data-stu-id="03ff2-111">The `dotnet nuget push` command pushes a package to the server and publishes it.</span></span> <span data-ttu-id="03ff2-112">O comando push usa o servidor e detalhes de credencial encontradas no arquivo de configuração do sistema NuGet ou uma cadeia de arquivos de configuração.</span><span class="sxs-lookup"><span data-stu-id="03ff2-112">The push command uses server and credential details found in the system's NuGet config file or chain of config files.</span></span> <span data-ttu-id="03ff2-113">Para obter mais informações sobre arquivos de configuração, consulte [Configurando o comportamento do NuGet](/nuget/consume-packages/configuring-nuget-behavior).</span><span class="sxs-lookup"><span data-stu-id="03ff2-113">For more information on config files, see [Configuring NuGet Behavior](/nuget/consume-packages/configuring-nuget-behavior).</span></span> <span data-ttu-id="03ff2-114">A configuração de padrão do NuGet é obtida ao carregar *%AppData%\NuGet\NuGet.config* (Windows) ou *$HOME/.local/share* (Linux/macOS) e, em seguida, carregar qualquer *nuget.config* ou *.nuget\nuget.config* da raiz da unidade e terminar no diretório atual.</span><span class="sxs-lookup"><span data-stu-id="03ff2-114">NuGet's default configuration is obtained by loading *%AppData%\NuGet\NuGet.config* (Windows) or *$HOME/.local/share* (Linux/macOS), then loading any *nuget.config* or *.nuget\nuget.config* starting from the root of drive and ending in the current directory.</span></span>

## <a name="arguments"></a><span data-ttu-id="03ff2-115">Arguments</span><span class="sxs-lookup"><span data-stu-id="03ff2-115">Arguments</span></span>

`ROOT`

<span data-ttu-id="03ff2-116">Especifica o caminho do arquivo para o pacote a ser enviado por push.</span><span class="sxs-lookup"><span data-stu-id="03ff2-116">Specifies the file path to the package to be pushed.</span></span>

## <a name="options"></a><span data-ttu-id="03ff2-117">Opções</span><span class="sxs-lookup"><span data-stu-id="03ff2-117">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="03ff2-118">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="03ff2-118">.NET Core 2.1</span></span>](#tab/netcore21)

`-d|--disable-buffering`

<span data-ttu-id="03ff2-119">Desabilita o buffer durante o push para um servidor HTTP(S) a fim de reduzir o uso de memória.</span><span class="sxs-lookup"><span data-stu-id="03ff2-119">Disables buffering when pushing to an HTTP(S) server to reduce memory usage.</span></span>

`--force-english-output`

<span data-ttu-id="03ff2-120">Força a execução do aplicativo usando uma cultura invariável com base em inglês.</span><span class="sxs-lookup"><span data-stu-id="03ff2-120">Forces the application to run using an invariant, English-based culture.</span></span>

`-h|--help`

<span data-ttu-id="03ff2-121">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="03ff2-121">Prints out a short help for the command.</span></span>

`-k|--api-key <API_KEY>`

<span data-ttu-id="03ff2-122">A chave da API para o servidor.</span><span class="sxs-lookup"><span data-stu-id="03ff2-122">The API key for the server.</span></span>

`-n|--no-symbols`

<span data-ttu-id="03ff2-123">Não envia símbolos por push (mesmo se estiver presente).</span><span class="sxs-lookup"><span data-stu-id="03ff2-123">Doesn't push symbols (even if present).</span></span>

`--no-service-endpoint`

<span data-ttu-id="03ff2-124">Não acrescenta "api/v2/package" à URL de origem.</span><span class="sxs-lookup"><span data-stu-id="03ff2-124">Doesn't append "api/v2/package" to the source URL.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="03ff2-125">Especifica a URL do servidor.</span><span class="sxs-lookup"><span data-stu-id="03ff2-125">Specifies the server URL.</span></span> <span data-ttu-id="03ff2-126">Essa opção será obrigatória, a menos que o valor de configuração `DefaultPushSource` seja definido no arquivo de configuração do NuGet.</span><span class="sxs-lookup"><span data-stu-id="03ff2-126">This option is required unless `DefaultPushSource` config value is set in the NuGet config file.</span></span>

`-sk|--symbol-api-key <API_KEY>`

<span data-ttu-id="03ff2-127">A chave da API para o servidor de símbolos.</span><span class="sxs-lookup"><span data-stu-id="03ff2-127">The API key for the symbol server.</span></span>

`-ss|--symbol-source <SOURCE>`

<span data-ttu-id="03ff2-128">Especifica a URL do servidor de símbolos.</span><span class="sxs-lookup"><span data-stu-id="03ff2-128">Specifies the symbol server URL.</span></span>

`-t|--timeout <TIMEOUT>`

<span data-ttu-id="03ff2-129">Especifica o tempo limite para enviar para um servidor em segundos.</span><span class="sxs-lookup"><span data-stu-id="03ff2-129">Specifies the timeout for pushing to a server in seconds.</span></span> <span data-ttu-id="03ff2-130">O padrão é 300 segundos (5 minutos).</span><span class="sxs-lookup"><span data-stu-id="03ff2-130">Defaults to 300 seconds (5 minutes).</span></span> <span data-ttu-id="03ff2-131">Especificar 0 (zero segundos) aplica o valor padrão.</span><span class="sxs-lookup"><span data-stu-id="03ff2-131">Specifying 0 (zero seconds) applies the default value.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="03ff2-132">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="03ff2-132">.NET Core 2.0</span></span>](#tab/netcore20)

`-d|--disable-buffering`

<span data-ttu-id="03ff2-133">Desabilita o buffer durante o push para um servidor HTTP(S) a fim de reduzir o uso de memória.</span><span class="sxs-lookup"><span data-stu-id="03ff2-133">Disables buffering when pushing to an HTTP(S) server to reduce memory usage.</span></span>

`--force-english-output`

<span data-ttu-id="03ff2-134">Força a execução do aplicativo usando uma cultura invariável com base em inglês.</span><span class="sxs-lookup"><span data-stu-id="03ff2-134">Forces the application to run using an invariant, English-based culture.</span></span>

`-h|--help`

<span data-ttu-id="03ff2-135">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="03ff2-135">Prints out a short help for the command.</span></span>

`-k|--api-key <API_KEY>`

<span data-ttu-id="03ff2-136">A chave da API para o servidor.</span><span class="sxs-lookup"><span data-stu-id="03ff2-136">The API key for the server.</span></span>

`-n|--no-symbols`

<span data-ttu-id="03ff2-137">Não envia símbolos por push (mesmo se estiver presente).</span><span class="sxs-lookup"><span data-stu-id="03ff2-137">Doesn't push symbols (even if present).</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="03ff2-138">Especifica a URL do servidor.</span><span class="sxs-lookup"><span data-stu-id="03ff2-138">Specifies the server URL.</span></span> <span data-ttu-id="03ff2-139">Essa opção será obrigatória, a menos que o valor de configuração `DefaultPushSource` seja definido no arquivo de configuração do NuGet.</span><span class="sxs-lookup"><span data-stu-id="03ff2-139">This option is required unless `DefaultPushSource` config value is set in the NuGet config file.</span></span>

`-sk|--symbol-api-key <API_KEY>`

<span data-ttu-id="03ff2-140">A chave da API para o servidor de símbolos.</span><span class="sxs-lookup"><span data-stu-id="03ff2-140">The API key for the symbol server.</span></span>

`-ss|--symbol-source <SOURCE>`

<span data-ttu-id="03ff2-141">Especifica a URL do servidor de símbolos.</span><span class="sxs-lookup"><span data-stu-id="03ff2-141">Specifies the symbol server URL.</span></span>

`-t|--timeout <TIMEOUT>`

<span data-ttu-id="03ff2-142">Especifica o tempo limite para enviar para um servidor em segundos.</span><span class="sxs-lookup"><span data-stu-id="03ff2-142">Specifies the timeout for pushing to a server in seconds.</span></span> <span data-ttu-id="03ff2-143">O padrão é 300 segundos (5 minutos).</span><span class="sxs-lookup"><span data-stu-id="03ff2-143">Defaults to 300 seconds (5 minutes).</span></span> <span data-ttu-id="03ff2-144">Especificar 0 (zero segundos) aplica o valor padrão.</span><span class="sxs-lookup"><span data-stu-id="03ff2-144">Specifying 0 (zero seconds) applies the default value.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="03ff2-145">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="03ff2-145">.NET Core 1.x</span></span>](#tab/netcore1x)

`-d|--disable-buffering`

<span data-ttu-id="03ff2-146">Desabilita o buffer durante o push para um servidor HTTP(S) a fim de reduzir o uso de memória.</span><span class="sxs-lookup"><span data-stu-id="03ff2-146">Disables buffering when pushing to an HTTP(S) server to reduce memory usage.</span></span>

`--force-english-output`

<span data-ttu-id="03ff2-147">Força a execução do aplicativo usando uma cultura invariável com base em inglês.</span><span class="sxs-lookup"><span data-stu-id="03ff2-147">Forces the application to run using an invariant, English-based culture.</span></span>

`-h|--help`

<span data-ttu-id="03ff2-148">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="03ff2-148">Prints out a short help for the command.</span></span>

`-k|--api-key <API_KEY>`

<span data-ttu-id="03ff2-149">A chave da API para o servidor.</span><span class="sxs-lookup"><span data-stu-id="03ff2-149">The API key for the server.</span></span>

`-n|--no-symbols`

<span data-ttu-id="03ff2-150">Não envia símbolos por push (mesmo se estiver presente).</span><span class="sxs-lookup"><span data-stu-id="03ff2-150">Doesn't push symbols (even if present).</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="03ff2-151">Especifica a URL do servidor.</span><span class="sxs-lookup"><span data-stu-id="03ff2-151">Specifies the server URL.</span></span> <span data-ttu-id="03ff2-152">Essa opção será obrigatória, a menos que o valor de configuração `DefaultPushSource` seja definido no arquivo de configuração do NuGet.</span><span class="sxs-lookup"><span data-stu-id="03ff2-152">This option is required unless `DefaultPushSource` config value is set in the NuGet config file.</span></span>

`-sk|--symbol-api-key <API_KEY>`

<span data-ttu-id="03ff2-153">A chave da API para o servidor de símbolos.</span><span class="sxs-lookup"><span data-stu-id="03ff2-153">The API key for the symbol server.</span></span>

`-ss|--symbol-source <SOURCE>`

<span data-ttu-id="03ff2-154">Especifica a URL do servidor de símbolos.</span><span class="sxs-lookup"><span data-stu-id="03ff2-154">Specifies the symbol server URL.</span></span>

`-t|--timeout <TIMEOUT>`

<span data-ttu-id="03ff2-155">Especifica o tempo limite para enviar para um servidor em segundos.</span><span class="sxs-lookup"><span data-stu-id="03ff2-155">Specifies the timeout for pushing to a server in seconds.</span></span> <span data-ttu-id="03ff2-156">O padrão é 300 segundos (5 minutos).</span><span class="sxs-lookup"><span data-stu-id="03ff2-156">Defaults to 300 seconds (5 minutes).</span></span> <span data-ttu-id="03ff2-157">Especificar 0 (zero segundos) aplica o valor padrão.</span><span class="sxs-lookup"><span data-stu-id="03ff2-157">Specifying 0 (zero seconds) applies the default value.</span></span>

---

## <a name="examples"></a><span data-ttu-id="03ff2-158">Exemplos</span><span class="sxs-lookup"><span data-stu-id="03ff2-158">Examples</span></span>

<span data-ttu-id="03ff2-159">Envia por push *foo.nupkg* à origem de push padrão, especificando uma chave de API:</span><span class="sxs-lookup"><span data-stu-id="03ff2-159">Pushes *foo.nupkg* to the default push source, specifying an API key:</span></span>

`dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a`

<span data-ttu-id="03ff2-160">Envia por push *foo.nupkg* à `http://customsource` de origem de push personalizada, especificando uma chave de API:</span><span class="sxs-lookup"><span data-stu-id="03ff2-160">Push *foo.nupkg* to the custom push source `http://customsource`, specifying an API key:</span></span>

`dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s http://customsource/`

<span data-ttu-id="03ff2-161">Envia por push *foo.nupkg* à origem de push padrão:</span><span class="sxs-lookup"><span data-stu-id="03ff2-161">Pushes *foo.nupkg* to the default push source:</span></span>

`dotnet nuget push foo.nupkg`

<span data-ttu-id="03ff2-162">Envia por push *foo.nupkg* à origem de símbolos padrão:</span><span class="sxs-lookup"><span data-stu-id="03ff2-162">Pushes *foo.symbols.nupkg* to the default symbols source:</span></span>

`dotnet nuget push foo.symbols.nupkg`

<span data-ttu-id="03ff2-163">Envia por push *foo.nupkg* à origem de push padrão, especificando um tempo limite de 360 segundos:</span><span class="sxs-lookup"><span data-stu-id="03ff2-163">Pushes *foo.nupkg* to the default push source, specifying a 360-second timeout:</span></span>

`dotnet nuget push foo.nupkg --timeout 360`

<span data-ttu-id="03ff2-164">Envia por push todos os arquivos *.nupkg* no diretório atual à origem de push padrão:</span><span class="sxs-lookup"><span data-stu-id="03ff2-164">Pushes all *.nupkg* files in the current directory to the default push source:</span></span>

`dotnet nuget push *.nupkg`
