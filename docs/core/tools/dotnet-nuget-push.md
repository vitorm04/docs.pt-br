---
title: Comando dotnet nuget push
description: O comando dotnet nuget push efetua push de um pacote no servidor e o publica.
author: karann-msft
ms.date: 02/14/2020
ms.openlocfilehash: 1e7831de4c041591b3602e405418f89f1d1d27d1
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895463"
---
# <a name="dotnet-nuget-push"></a><span data-ttu-id="74ec7-103">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="74ec7-103">dotnet nuget push</span></span>

<span data-ttu-id="74ec7-104">**Este artigo aplica-se a:** ✔️ SDK do .NET Core 2. x e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="74ec7-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="74ec7-105">Nome</span><span class="sxs-lookup"><span data-stu-id="74ec7-105">Name</span></span>

<span data-ttu-id="74ec7-106">`dotnet nuget push` – Envia um pacote ao servidor e os publica.</span><span class="sxs-lookup"><span data-stu-id="74ec7-106">`dotnet nuget push` - Pushes a package to the server and publishes it.</span></span>

## <a name="synopsis"></a><span data-ttu-id="74ec7-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="74ec7-107">Synopsis</span></span>

```dotnetcli
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output]
    [--interactive] [-k|--api-key <API_KEY>] [-n|--no-symbols]
    [--no-service-endpoint] [-s|--source <SOURCE>] [--skip-duplicate]
    [-sk|--symbol-api-key <API_KEY>] [-ss|--symbol-source <SOURCE>]
    [-t|--timeout <TIMEOUT>]

dotnet nuget push -h|--help
```

## <a name="description"></a><span data-ttu-id="74ec7-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="74ec7-108">Description</span></span>

<span data-ttu-id="74ec7-109">O comando `dotnet nuget push` envia um pacote ao servidor e os publica.</span><span class="sxs-lookup"><span data-stu-id="74ec7-109">The `dotnet nuget push` command pushes a package to the server and publishes it.</span></span> <span data-ttu-id="74ec7-110">O comando push usa o servidor e detalhes de credencial encontradas no arquivo de configuração do sistema NuGet ou uma cadeia de arquivos de configuração.</span><span class="sxs-lookup"><span data-stu-id="74ec7-110">The push command uses server and credential details found in the system's NuGet config file or chain of config files.</span></span> <span data-ttu-id="74ec7-111">Para obter mais informações sobre arquivos de configuração, consulte [Configurando o comportamento do NuGet](/nuget/consume-packages/configuring-nuget-behavior).</span><span class="sxs-lookup"><span data-stu-id="74ec7-111">For more information on config files, see [Configuring NuGet Behavior](/nuget/consume-packages/configuring-nuget-behavior).</span></span> <span data-ttu-id="74ec7-112">A configuração de padrão do NuGet é obtida ao carregar *%AppData%\NuGet\NuGet.config* (Windows) ou *$HOME/.local/share* (Linux/macOS) e, em seguida, carregar qualquer *nuget.config* ou *.nuget\nuget.config* da raiz da unidade e terminar no diretório atual.</span><span class="sxs-lookup"><span data-stu-id="74ec7-112">NuGet's default configuration is obtained by loading *%AppData%\NuGet\NuGet.config* (Windows) or *$HOME/.local/share* (Linux/macOS), then loading any *nuget.config* or *.nuget\nuget.config* starting from the root of drive and ending in the current directory.</span></span>

<span data-ttu-id="74ec7-113">O comando envia por push um pacote existente.</span><span class="sxs-lookup"><span data-stu-id="74ec7-113">The command pushes an existing package.</span></span> <span data-ttu-id="74ec7-114">Ele não cria um pacote.</span><span class="sxs-lookup"><span data-stu-id="74ec7-114">It doesn't create a package.</span></span> <span data-ttu-id="74ec7-115">Para criar um pacote, use [`dotnet pack`](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="74ec7-115">To create a package, use [`dotnet pack`](dotnet-pack.md).</span></span>

## <a name="arguments"></a><span data-ttu-id="74ec7-116">Argumentos</span><span class="sxs-lookup"><span data-stu-id="74ec7-116">Arguments</span></span>

- **`ROOT`**

  <span data-ttu-id="74ec7-117">Especifica o caminho do arquivo para o pacote a ser enviado por push.</span><span class="sxs-lookup"><span data-stu-id="74ec7-117">Specifies the file path to the package to be pushed.</span></span>

## <a name="options"></a><span data-ttu-id="74ec7-118">Opções</span><span class="sxs-lookup"><span data-stu-id="74ec7-118">Options</span></span>

- **`-d|--disable-buffering`**

  <span data-ttu-id="74ec7-119">Desabilita o buffer durante o push para um servidor HTTP(S) a fim de reduzir o uso de memória.</span><span class="sxs-lookup"><span data-stu-id="74ec7-119">Disables buffering when pushing to an HTTP(S) server to reduce memory usage.</span></span>

- **`--force-english-output`**

  <span data-ttu-id="74ec7-120">Força a execução do aplicativo usando uma cultura invariável com base em inglês.</span><span class="sxs-lookup"><span data-stu-id="74ec7-120">Forces the application to run using an invariant, English-based culture.</span></span>

- **`-h|--help`**

  <span data-ttu-id="74ec7-121">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="74ec7-121">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="74ec7-122">Permite que o comando bloqueie e exija ação manual para operações como a autenticação.</span><span class="sxs-lookup"><span data-stu-id="74ec7-122">Allows the command to block and requires manual action for operations like authentication.</span></span> <span data-ttu-id="74ec7-123">Opção disponível desde o SDK 2.2 do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="74ec7-123">Option available since .NET Core 2.2 SDK.</span></span>

- **`-k|--api-key <API_KEY>`**

  <span data-ttu-id="74ec7-124">A chave da API para o servidor.</span><span class="sxs-lookup"><span data-stu-id="74ec7-124">The API key for the server.</span></span>

- **`-n|--no-symbols`**

  <span data-ttu-id="74ec7-125">Não envia símbolos por push (mesmo se estiver presente).</span><span class="sxs-lookup"><span data-stu-id="74ec7-125">Doesn't push symbols (even if present).</span></span>

- **`--no-service-endpoint`**

  <span data-ttu-id="74ec7-126">Não acrescenta "api/v2/package" à URL de origem.</span><span class="sxs-lookup"><span data-stu-id="74ec7-126">Doesn't append "api/v2/package" to the source URL.</span></span> <span data-ttu-id="74ec7-127">Opção disponível desde o SDK do .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="74ec7-127">Option available since .NET Core 2.1 SDK.</span></span>

- **`-s|--source <SOURCE>`**

  <span data-ttu-id="74ec7-128">Especifica a URL do servidor.</span><span class="sxs-lookup"><span data-stu-id="74ec7-128">Specifies the server URL.</span></span> <span data-ttu-id="74ec7-129">Essa opção será obrigatória, a menos que o valor de configuração `DefaultPushSource` seja definido no arquivo de configuração do NuGet.</span><span class="sxs-lookup"><span data-stu-id="74ec7-129">This option is required unless `DefaultPushSource` config value is set in the NuGet config file.</span></span>

- **`--skip-duplicate`**

  <span data-ttu-id="74ec7-130">Ao enviar vários pacotes para um servidor HTTP (S), o trata qualquer resposta de conflito 409 como um aviso para que o envio por push possa continuar.</span><span class="sxs-lookup"><span data-stu-id="74ec7-130">When pushing multiple packages to an HTTP(S) server, treats any 409 Conflict response as a warning so that the push can continue.</span></span> <span data-ttu-id="74ec7-131">Disponível desde o SDK do .NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="74ec7-131">Available since .NET Core 3.1 SDK.</span></span>

- **`-sk|--symbol-api-key <API_KEY>`**

  <span data-ttu-id="74ec7-132">A chave da API para o servidor de símbolos.</span><span class="sxs-lookup"><span data-stu-id="74ec7-132">The API key for the symbol server.</span></span>

- **`-ss|--symbol-source <SOURCE>`**

  <span data-ttu-id="74ec7-133">Especifica a URL do servidor de símbolos.</span><span class="sxs-lookup"><span data-stu-id="74ec7-133">Specifies the symbol server URL.</span></span>

- **`-t|--timeout <TIMEOUT>`**

  <span data-ttu-id="74ec7-134">Especifica o tempo limite para enviar para um servidor em segundos.</span><span class="sxs-lookup"><span data-stu-id="74ec7-134">Specifies the timeout for pushing to a server in seconds.</span></span> <span data-ttu-id="74ec7-135">O padrão é 300 segundos (5 minutos).</span><span class="sxs-lookup"><span data-stu-id="74ec7-135">Defaults to 300 seconds (5 minutes).</span></span> <span data-ttu-id="74ec7-136">Especificar 0 (zero segundos) aplica o valor padrão.</span><span class="sxs-lookup"><span data-stu-id="74ec7-136">Specifying 0 (zero seconds) applies the default value.</span></span>

## <a name="examples"></a><span data-ttu-id="74ec7-137">Exemplos</span><span class="sxs-lookup"><span data-stu-id="74ec7-137">Examples</span></span>

- <span data-ttu-id="74ec7-138">Envie por push *foo. nupkg* para a fonte Push padrão, especificando uma chave de API:</span><span class="sxs-lookup"><span data-stu-id="74ec7-138">Push *foo.nupkg* to the default push source, specifying an API key:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a
  ```

- <span data-ttu-id="74ec7-139">Envie por push o *foo. nupkg* para o servidor do NuGet oficial, especificando uma chave de API:</span><span class="sxs-lookup"><span data-stu-id="74ec7-139">Push *foo.nupkg* to the official NuGet server, specifying an API key:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s https://api.nuget.org/v3/index.json
  ```
  
  * <span data-ttu-id="74ec7-140">Envia por push *foo.nupkg* à `https://customsource` de origem de push personalizada, especificando uma chave de API:</span><span class="sxs-lookup"><span data-stu-id="74ec7-140">Push *foo.nupkg* to the custom push source `https://customsource`, specifying an API key:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s https://customsource/
  ```

- <span data-ttu-id="74ec7-141">Envie por push *foo. nupkg* para a fonte Push padrão:</span><span class="sxs-lookup"><span data-stu-id="74ec7-141">Push *foo.nupkg* to the default push source:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg
  ```

- <span data-ttu-id="74ec7-142">Envie por push *foo. Symbols. nupkg* para a fonte de símbolos padrão:</span><span class="sxs-lookup"><span data-stu-id="74ec7-142">Push *foo.symbols.nupkg* to the default symbols source:</span></span>

  ```dotnetcli
  dotnet nuget push foo.symbols.nupkg
  ```

- <span data-ttu-id="74ec7-143">Envie por push *foo. nupkg* para a fonte Push padrão, especificando um tempo limite de 360 segundos:</span><span class="sxs-lookup"><span data-stu-id="74ec7-143">Push *foo.nupkg* to the default push source, specifying a 360-second timeout:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg --timeout 360
  ```

- <span data-ttu-id="74ec7-144">Envie por push todos os arquivos *. nupkg* no diretório atual para a fonte Push padrão:</span><span class="sxs-lookup"><span data-stu-id="74ec7-144">Push all *.nupkg* files in the current directory to the default push source:</span></span>

  ```dotnetcli
  dotnet nuget push *.nupkg
  ```

  > [!NOTE]
  > <span data-ttu-id="74ec7-145">Se esse comando não funcionar, talvez seja devido a um bug que existia em versões mais antigas do SDK (SDK do .NET Core 2.1 e versões anteriores).</span><span class="sxs-lookup"><span data-stu-id="74ec7-145">If this command doesn't work, it might be due to a bug that existed in older versions of the SDK (.NET Core 2.1 SDK and earlier versions).</span></span>
  > <span data-ttu-id="74ec7-146">Para corrigir esse problema, atualize sua versão do SDK ou execute o seguinte comando em vez disso: `dotnet nuget push **/*.nupkg`</span><span class="sxs-lookup"><span data-stu-id="74ec7-146">To fix this, upgrade your SDK version or run the following command instead: `dotnet nuget push **/*.nupkg`</span></span>

- <span data-ttu-id="74ec7-147">Envie todos os arquivos *. nupkg* mesmo se uma resposta de conflito 409 for retornada por um servidor http (S):</span><span class="sxs-lookup"><span data-stu-id="74ec7-147">Push all *.nupkg* files even if a 409 Conflict response is returned by an HTTP(S) server:</span></span>

  ```dotnetcli
  dotnet nuget push *.nupkg --skip-duplicate
  ```

- <span data-ttu-id="74ec7-148">Envie por push todos os arquivos *. nupkg* no diretório atual para um diretório de feed local:</span><span class="sxs-lookup"><span data-stu-id="74ec7-148">Push all *.nupkg* files in the current directory to a local feed directory:</span></span>

  ```dotnetcli
  dotnet nuget push *.nupkg -s c:\mydir
  ```

  <span data-ttu-id="74ec7-149">Esse comando não armazena pacotes em uma estrutura de pastas hierárquicas, o que é recomendado para otimizar o desempenho.</span><span class="sxs-lookup"><span data-stu-id="74ec7-149">This command doesn't store packages in a hierarchical folder structure, which is recommended to optimize performance.</span></span> <span data-ttu-id="74ec7-150">Para obter mais informações, consulte [feeds locais](/nuget/hosting-packages/local-feeds).</span><span class="sxs-lookup"><span data-stu-id="74ec7-150">For more information, see [Local feeds](/nuget/hosting-packages/local-feeds).</span></span>  
