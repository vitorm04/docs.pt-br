---
title: Comando dotnet nuget push
description: O comando dotnet nuget push efetua push de um pacote no servidor e o publica.
author: karann-msft
ms.date: 12/04/2018
ms.openlocfilehash: 4f0d127d8b9f37b1c381d8981f54035a2fc3b0e5
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53169346"
---
# <a name="dotnet-nuget-push"></a><span data-ttu-id="5fb5e-103">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="5fb5e-103">dotnet nuget push</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="5fb5e-104">Nome</span><span class="sxs-lookup"><span data-stu-id="5fb5e-104">Name</span></span>

<span data-ttu-id="5fb5e-105">`dotnet nuget push` – Envia um pacote ao servidor e os publica.</span><span class="sxs-lookup"><span data-stu-id="5fb5e-105">`dotnet nuget push` - Pushes a package to the server and publishes it.</span></span>

## <a name="synopsis"></a><span data-ttu-id="5fb5e-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="5fb5e-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="5fb5e-107">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="5fb5e-107">.NET Core 2.x</span></span>](#tab/netcore2x)
```
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output] [--interactive] [-k|--api-key] [-n|--no-symbols]
    [--no-service-endpoint] [-s|--source] [-sk|--symbol-api-key] [-ss|--symbol-source] [-t|--timeout]
dotnet nuget push [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="5fb5e-108">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="5fb5e-108">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output] [-k|--api-key] [-n|--no-symbols]
    [-s|--source] [-sk|--symbol-api-key] [-ss|--symbol-source] [-t|--timeout]
dotnet nuget push [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="5fb5e-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="5fb5e-109">Description</span></span>

<span data-ttu-id="5fb5e-110">O comando `dotnet nuget push` envia um pacote ao servidor e os publica.</span><span class="sxs-lookup"><span data-stu-id="5fb5e-110">The `dotnet nuget push` command pushes a package to the server and publishes it.</span></span> <span data-ttu-id="5fb5e-111">O comando push usa o servidor e detalhes de credencial encontradas no arquivo de configuração do sistema NuGet ou uma cadeia de arquivos de configuração.</span><span class="sxs-lookup"><span data-stu-id="5fb5e-111">The push command uses server and credential details found in the system's NuGet config file or chain of config files.</span></span> <span data-ttu-id="5fb5e-112">Para obter mais informações sobre arquivos de configuração, consulte [Configurando o comportamento do NuGet](/nuget/consume-packages/configuring-nuget-behavior).</span><span class="sxs-lookup"><span data-stu-id="5fb5e-112">For more information on config files, see [Configuring NuGet Behavior](/nuget/consume-packages/configuring-nuget-behavior).</span></span> <span data-ttu-id="5fb5e-113">A configuração de padrão do NuGet é obtida ao carregar *%AppData%\NuGet\NuGet.config* (Windows) ou *$HOME/.local/share* (Linux/macOS) e, em seguida, carregar qualquer *nuget.config* ou *.nuget\nuget.config* da raiz da unidade e terminar no diretório atual.</span><span class="sxs-lookup"><span data-stu-id="5fb5e-113">NuGet's default configuration is obtained by loading *%AppData%\NuGet\NuGet.config* (Windows) or *$HOME/.local/share* (Linux/macOS), then loading any *nuget.config* or *.nuget\nuget.config* starting from the root of drive and ending in the current directory.</span></span>

## <a name="arguments"></a><span data-ttu-id="5fb5e-114">Arguments</span><span class="sxs-lookup"><span data-stu-id="5fb5e-114">Arguments</span></span>

* **`ROOT`**

  <span data-ttu-id="5fb5e-115">Especifica o caminho do arquivo para o pacote a ser enviado por push.</span><span class="sxs-lookup"><span data-stu-id="5fb5e-115">Specifies the file path to the package to be pushed.</span></span>

## <a name="options"></a><span data-ttu-id="5fb5e-116">Opções</span><span class="sxs-lookup"><span data-stu-id="5fb5e-116">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="5fb5e-117">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="5fb5e-117">.NET Core 2.x</span></span>](#tab/netcore2x)

* **`-d|--disable-buffering`**

  <span data-ttu-id="5fb5e-118">Desabilita o buffer durante o push para um servidor HTTP(S) a fim de reduzir o uso de memória.</span><span class="sxs-lookup"><span data-stu-id="5fb5e-118">Disables buffering when pushing to an HTTP(S) server to reduce memory usage.</span></span>

* **`--force-english-output`**

  <span data-ttu-id="5fb5e-119">Força a execução do aplicativo usando uma cultura invariável com base em inglês.</span><span class="sxs-lookup"><span data-stu-id="5fb5e-119">Forces the application to run using an invariant, English-based culture.</span></span>

* **`-h|--help`**

<span data-ttu-id="5fb5e-120">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="5fb5e-120">Prints out a short help for the command.</span></span>

* **`--interactive`**

  <span data-ttu-id="5fb5e-121">Permite que o comando bloqueie e exija ação manual para operações como a autenticação.</span><span class="sxs-lookup"><span data-stu-id="5fb5e-121">Allows the command to block and requires manual action for operations like authentication.</span></span> <span data-ttu-id="5fb5e-122">Opção disponível desde o SDK 2.2 do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5fb5e-122">Option available since .NET Core 2.2 SDK.</span></span>

* **`-k|--api-key <API_KEY>`**

  <span data-ttu-id="5fb5e-123">A chave da API para o servidor.</span><span class="sxs-lookup"><span data-stu-id="5fb5e-123">The API key for the server.</span></span>

* **`-n|--no-symbols`**

  <span data-ttu-id="5fb5e-124">Não envia símbolos por push (mesmo se estiver presente).</span><span class="sxs-lookup"><span data-stu-id="5fb5e-124">Doesn't push symbols (even if present).</span></span>

* **`--no-service-endpoint`**

  <span data-ttu-id="5fb5e-125">Não acrescenta "api/v2/package" à URL de origem.</span><span class="sxs-lookup"><span data-stu-id="5fb5e-125">Doesn't append "api/v2/package" to the source URL.</span></span> <span data-ttu-id="5fb5e-126">Opção disponível desde o SDK do .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="5fb5e-126">Option available since .NET Core 2.1 SDK.</span></span>

* **`-s|--source <SOURCE>`**

  <span data-ttu-id="5fb5e-127">Especifica a URL do servidor.</span><span class="sxs-lookup"><span data-stu-id="5fb5e-127">Specifies the server URL.</span></span> <span data-ttu-id="5fb5e-128">Essa opção será obrigatória, a menos que o valor de configuração `DefaultPushSource` seja definido no arquivo de configuração do NuGet.</span><span class="sxs-lookup"><span data-stu-id="5fb5e-128">This option is required unless `DefaultPushSource` config value is set in the NuGet config file.</span></span>

* **`-sk|--symbol-api-key <API_KEY>`**

  <span data-ttu-id="5fb5e-129">A chave da API para o servidor de símbolos.</span><span class="sxs-lookup"><span data-stu-id="5fb5e-129">The API key for the symbol server.</span></span>

* **`-ss|--symbol-source <SOURCE>`**

  <span data-ttu-id="5fb5e-130">Especifica a URL do servidor de símbolos.</span><span class="sxs-lookup"><span data-stu-id="5fb5e-130">Specifies the symbol server URL.</span></span>

* **`-t|--timeout <TIMEOUT>`**

  <span data-ttu-id="5fb5e-131">Especifica o tempo limite para enviar para um servidor em segundos.</span><span class="sxs-lookup"><span data-stu-id="5fb5e-131">Specifies the timeout for pushing to a server in seconds.</span></span> <span data-ttu-id="5fb5e-132">O padrão é 300 segundos (5 minutos).</span><span class="sxs-lookup"><span data-stu-id="5fb5e-132">Defaults to 300 seconds (5 minutes).</span></span> <span data-ttu-id="5fb5e-133">Especificar 0 (zero segundos) aplica o valor padrão.</span><span class="sxs-lookup"><span data-stu-id="5fb5e-133">Specifying 0 (zero seconds) applies the default value.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="5fb5e-134">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="5fb5e-134">.NET Core 1.x</span></span>](#tab/netcore1x)

* **`-d|--disable-buffering`**

  <span data-ttu-id="5fb5e-135">Desabilita o buffer durante o push para um servidor HTTP(S) a fim de reduzir o uso de memória.</span><span class="sxs-lookup"><span data-stu-id="5fb5e-135">Disables buffering when pushing to an HTTP(S) server to reduce memory usage.</span></span>

* **`--force-english-output`**

  <span data-ttu-id="5fb5e-136">Força a execução do aplicativo usando uma cultura invariável com base em inglês.</span><span class="sxs-lookup"><span data-stu-id="5fb5e-136">Forces the application to run using an invariant, English-based culture.</span></span>

* **`-h|--help`**

  <span data-ttu-id="5fb5e-137">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="5fb5e-137">Prints out a short help for the command.</span></span>

* **`-k|--api-key <API_KEY>`**

  <span data-ttu-id="5fb5e-138">A chave da API para o servidor.</span><span class="sxs-lookup"><span data-stu-id="5fb5e-138">The API key for the server.</span></span>

* **`-n|--no-symbols`**

  <span data-ttu-id="5fb5e-139">Não envia símbolos por push (mesmo se estiver presente).</span><span class="sxs-lookup"><span data-stu-id="5fb5e-139">Doesn't push symbols (even if present).</span></span>

* **`-s|--source <SOURCE>`**

  <span data-ttu-id="5fb5e-140">Especifica a URL do servidor.</span><span class="sxs-lookup"><span data-stu-id="5fb5e-140">Specifies the server URL.</span></span> <span data-ttu-id="5fb5e-141">Essa opção será obrigatória, a menos que o valor de configuração `DefaultPushSource` seja definido no arquivo de configuração do NuGet.</span><span class="sxs-lookup"><span data-stu-id="5fb5e-141">This option is required unless `DefaultPushSource` config value is set in the NuGet config file.</span></span>

* **`-sk|--symbol-api-key <API_KEY>`**

  <span data-ttu-id="5fb5e-142">A chave da API para o servidor de símbolos.</span><span class="sxs-lookup"><span data-stu-id="5fb5e-142">The API key for the symbol server.</span></span>

* **`-ss|--symbol-source <SOURCE>`**

  <span data-ttu-id="5fb5e-143">Especifica a URL do servidor de símbolos.</span><span class="sxs-lookup"><span data-stu-id="5fb5e-143">Specifies the symbol server URL.</span></span>

* **`-t|--timeout <TIMEOUT>`**

  <span data-ttu-id="5fb5e-144">Especifica o tempo limite para enviar para um servidor em segundos.</span><span class="sxs-lookup"><span data-stu-id="5fb5e-144">Specifies the timeout for pushing to a server in seconds.</span></span> <span data-ttu-id="5fb5e-145">O padrão é 300 segundos (5 minutos).</span><span class="sxs-lookup"><span data-stu-id="5fb5e-145">Defaults to 300 seconds (5 minutes).</span></span> <span data-ttu-id="5fb5e-146">Especificar 0 (zero segundos) aplica o valor padrão.</span><span class="sxs-lookup"><span data-stu-id="5fb5e-146">Specifying 0 (zero seconds) applies the default value.</span></span>

---

## <a name="examples"></a><span data-ttu-id="5fb5e-147">Exemplos</span><span class="sxs-lookup"><span data-stu-id="5fb5e-147">Examples</span></span>

* <span data-ttu-id="5fb5e-148">Envia por push *foo.nupkg* à origem de push padrão, especificando uma chave de API:</span><span class="sxs-lookup"><span data-stu-id="5fb5e-148">Pushes *foo.nupkg* to the default push source, specifying an API key:</span></span>

  ```console
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a
  ```

* <span data-ttu-id="5fb5e-149">Envia por push *foo.nupkg* à `https://customsource` de origem de push personalizada, especificando uma chave de API:</span><span class="sxs-lookup"><span data-stu-id="5fb5e-149">Push *foo.nupkg* to the custom push source `https://customsource`, specifying an API key:</span></span>

  ```console
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s https://customsource/
  ```

* <span data-ttu-id="5fb5e-150">Envia por push *foo.nupkg* à origem de push padrão:</span><span class="sxs-lookup"><span data-stu-id="5fb5e-150">Pushes *foo.nupkg* to the default push source:</span></span>

  ```console
  dotnet nuget push foo.nupkg
  ```

* <span data-ttu-id="5fb5e-151">Envia por push *foo.nupkg* à origem de símbolos padrão:</span><span class="sxs-lookup"><span data-stu-id="5fb5e-151">Pushes *foo.symbols.nupkg* to the default symbols source:</span></span>

  ```console
  dotnet nuget push foo.symbols.nupkg
  ```

* <span data-ttu-id="5fb5e-152">Envia por push *foo.nupkg* à origem de push padrão, especificando um tempo limite de 360 segundos:</span><span class="sxs-lookup"><span data-stu-id="5fb5e-152">Pushes *foo.nupkg* to the default push source, specifying a 360-second timeout:</span></span>

  ```console
  dotnet nuget push foo.nupkg --timeout 360
  ```

* <span data-ttu-id="5fb5e-153">Envia por push todos os arquivos *.nupkg* no diretório atual à origem de push padrão:</span><span class="sxs-lookup"><span data-stu-id="5fb5e-153">Pushes all *.nupkg* files in the current directory to the default push source:</span></span>

  ```console
  dotnet nuget push *.nupkg
  ```