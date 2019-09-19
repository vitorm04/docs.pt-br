---
title: Comando dotnet nuget push
description: O comando dotnet nuget push efetua push de um pacote no servidor e o publica.
author: karann-msft
ms.date: 06/26/2019
ms.openlocfilehash: 3299f79ec62aebdcdbef38f1e8b09a2dc5529ec4
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117494"
---
# <a name="dotnet-nuget-push"></a><span data-ttu-id="04763-103">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="04763-103">dotnet nuget push</span></span>

<span data-ttu-id="04763-104">**Este tópico aplica-se a: ✓** SDK do .NET Core 1.x e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="04763-104">**This topic applies to: ✓** .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="04763-105">Nome</span><span class="sxs-lookup"><span data-stu-id="04763-105">Name</span></span>

<span data-ttu-id="04763-106">`dotnet nuget push` – Envia um pacote ao servidor e os publica.</span><span class="sxs-lookup"><span data-stu-id="04763-106">`dotnet nuget push` - Pushes a package to the server and publishes it.</span></span>

## <a name="synopsis"></a><span data-ttu-id="04763-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="04763-107">Synopsis</span></span>

```dotnetcli
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output] [--interactive] [-k|--api-key] [-n|--no-symbols]
    [--no-service-endpoint] [-s|--source] [-sk|--symbol-api-key] [-ss|--symbol-source] [-t|--timeout]
dotnet nuget push [-h|--help]
```

## <a name="description"></a><span data-ttu-id="04763-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="04763-108">Description</span></span>

<span data-ttu-id="04763-109">O comando `dotnet nuget push` envia um pacote ao servidor e os publica.</span><span class="sxs-lookup"><span data-stu-id="04763-109">The `dotnet nuget push` command pushes a package to the server and publishes it.</span></span> <span data-ttu-id="04763-110">O comando push usa o servidor e detalhes de credencial encontradas no arquivo de configuração do sistema NuGet ou uma cadeia de arquivos de configuração.</span><span class="sxs-lookup"><span data-stu-id="04763-110">The push command uses server and credential details found in the system's NuGet config file or chain of config files.</span></span> <span data-ttu-id="04763-111">Para obter mais informações sobre arquivos de configuração, consulte [Configurando o comportamento do NuGet](/nuget/consume-packages/configuring-nuget-behavior).</span><span class="sxs-lookup"><span data-stu-id="04763-111">For more information on config files, see [Configuring NuGet Behavior](/nuget/consume-packages/configuring-nuget-behavior).</span></span> <span data-ttu-id="04763-112">A configuração de padrão do NuGet é obtida ao carregar *%AppData%\NuGet\NuGet.config* (Windows) ou *$HOME/.local/share* (Linux/macOS) e, em seguida, carregar qualquer *nuget.config* ou *.nuget\nuget.config* da raiz da unidade e terminar no diretório atual.</span><span class="sxs-lookup"><span data-stu-id="04763-112">NuGet's default configuration is obtained by loading *%AppData%\NuGet\NuGet.config* (Windows) or *$HOME/.local/share* (Linux/macOS), then loading any *nuget.config* or *.nuget\nuget.config* starting from the root of drive and ending in the current directory.</span></span>

## <a name="arguments"></a><span data-ttu-id="04763-113">Arguments</span><span class="sxs-lookup"><span data-stu-id="04763-113">Arguments</span></span>

* **`ROOT`**

  <span data-ttu-id="04763-114">Especifica o caminho do arquivo para o pacote a ser enviado por push.</span><span class="sxs-lookup"><span data-stu-id="04763-114">Specifies the file path to the package to be pushed.</span></span>

## <a name="options"></a><span data-ttu-id="04763-115">Opções</span><span class="sxs-lookup"><span data-stu-id="04763-115">Options</span></span>

* **`-d|--disable-buffering`**

  <span data-ttu-id="04763-116">Desabilita o buffer durante o push para um servidor HTTP(S) a fim de reduzir o uso de memória.</span><span class="sxs-lookup"><span data-stu-id="04763-116">Disables buffering when pushing to an HTTP(S) server to reduce memory usage.</span></span>

* **`--force-english-output`**

  <span data-ttu-id="04763-117">Força a execução do aplicativo usando uma cultura invariável com base em inglês.</span><span class="sxs-lookup"><span data-stu-id="04763-117">Forces the application to run using an invariant, English-based culture.</span></span>

* **`-h|--help`**

<span data-ttu-id="04763-118">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="04763-118">Prints out a short help for the command.</span></span>

* **`--interactive`**

  <span data-ttu-id="04763-119">Permite que o comando bloqueie e exija ação manual para operações como a autenticação.</span><span class="sxs-lookup"><span data-stu-id="04763-119">Allows the command to block and requires manual action for operations like authentication.</span></span> <span data-ttu-id="04763-120">Opção disponível desde o SDK 2.2 do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="04763-120">Option available since .NET Core 2.2 SDK.</span></span>

* **`-k|--api-key <API_KEY>`**

  <span data-ttu-id="04763-121">A chave da API para o servidor.</span><span class="sxs-lookup"><span data-stu-id="04763-121">The API key for the server.</span></span>

* **`-n|--no-symbols`**

  <span data-ttu-id="04763-122">Não envia símbolos por push (mesmo se estiver presente).</span><span class="sxs-lookup"><span data-stu-id="04763-122">Doesn't push symbols (even if present).</span></span>

* **`--no-service-endpoint`**

  <span data-ttu-id="04763-123">Não acrescenta "api/v2/package" à URL de origem.</span><span class="sxs-lookup"><span data-stu-id="04763-123">Doesn't append "api/v2/package" to the source URL.</span></span> <span data-ttu-id="04763-124">Opção disponível desde o SDK do .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="04763-124">Option available since .NET Core 2.1 SDK.</span></span>

* **`-s|--source <SOURCE>`**

  <span data-ttu-id="04763-125">Especifica a URL do servidor.</span><span class="sxs-lookup"><span data-stu-id="04763-125">Specifies the server URL.</span></span> <span data-ttu-id="04763-126">Essa opção será obrigatória, a menos que o valor de configuração `DefaultPushSource` seja definido no arquivo de configuração do NuGet.</span><span class="sxs-lookup"><span data-stu-id="04763-126">This option is required unless `DefaultPushSource` config value is set in the NuGet config file.</span></span>

* **`-sk|--symbol-api-key <API_KEY>`**

  <span data-ttu-id="04763-127">A chave da API para o servidor de símbolos.</span><span class="sxs-lookup"><span data-stu-id="04763-127">The API key for the symbol server.</span></span>

* **`-ss|--symbol-source <SOURCE>`**

  <span data-ttu-id="04763-128">Especifica a URL do servidor de símbolos.</span><span class="sxs-lookup"><span data-stu-id="04763-128">Specifies the symbol server URL.</span></span>

* **`-t|--timeout <TIMEOUT>`**

  <span data-ttu-id="04763-129">Especifica o tempo limite para enviar para um servidor em segundos.</span><span class="sxs-lookup"><span data-stu-id="04763-129">Specifies the timeout for pushing to a server in seconds.</span></span> <span data-ttu-id="04763-130">O padrão é 300 segundos (5 minutos).</span><span class="sxs-lookup"><span data-stu-id="04763-130">Defaults to 300 seconds (5 minutes).</span></span> <span data-ttu-id="04763-131">Especificar 0 (zero segundos) aplica o valor padrão.</span><span class="sxs-lookup"><span data-stu-id="04763-131">Specifying 0 (zero seconds) applies the default value.</span></span>

## <a name="examples"></a><span data-ttu-id="04763-132">Exemplos</span><span class="sxs-lookup"><span data-stu-id="04763-132">Examples</span></span>

* <span data-ttu-id="04763-133">Envia por push *foo.nupkg* à origem de push padrão, especificando uma chave de API:</span><span class="sxs-lookup"><span data-stu-id="04763-133">Pushes *foo.nupkg* to the default push source, specifying an API key:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a
  ```

* <span data-ttu-id="04763-134">Envia por push *foo.nupkg* à `https://customsource` de origem de push personalizada, especificando uma chave de API:</span><span class="sxs-lookup"><span data-stu-id="04763-134">Push *foo.nupkg* to the custom push source `https://customsource`, specifying an API key:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s https://customsource/
  ```

* <span data-ttu-id="04763-135">Envia por push *foo.nupkg* à origem de push padrão:</span><span class="sxs-lookup"><span data-stu-id="04763-135">Pushes *foo.nupkg* to the default push source:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg
  ```

* <span data-ttu-id="04763-136">Envia por push *foo.nupkg* à origem de símbolos padrão:</span><span class="sxs-lookup"><span data-stu-id="04763-136">Pushes *foo.symbols.nupkg* to the default symbols source:</span></span>

  ```dotnetcli
  dotnet nuget push foo.symbols.nupkg
  ```

* <span data-ttu-id="04763-137">Envia por push *foo.nupkg* à origem de push padrão, especificando um tempo limite de 360 segundos:</span><span class="sxs-lookup"><span data-stu-id="04763-137">Pushes *foo.nupkg* to the default push source, specifying a 360-second timeout:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg --timeout 360
  ```

* <span data-ttu-id="04763-138">Envia por push todos os arquivos *.nupkg* no diretório atual à origem de push padrão:</span><span class="sxs-lookup"><span data-stu-id="04763-138">Pushes all *.nupkg* files in the current directory to the default push source:</span></span>

  ```dotnetcli
  dotnet nuget push *.nupkg
  ```
  
  > [!NOTE]
  > <span data-ttu-id="04763-139">Se esse comando não funcionar, talvez seja devido a um bug que existia em versões mais antigas do SDK (SDK do .NET Core 2.1 e versões anteriores).</span><span class="sxs-lookup"><span data-stu-id="04763-139">If this command doesn't work, it might be due to a bug that existed in older versions of the SDK (.NET Core 2.1 SDK and earlier versions).</span></span>
  > <span data-ttu-id="04763-140">Para corrigir esse problema, atualize sua versão do SDK ou execute o seguinte comando em vez disso: `dotnet nuget push **/*.nupkg`</span><span class="sxs-lookup"><span data-stu-id="04763-140">To fix this, upgrade your SDK version or run the following command instead: `dotnet nuget push **/*.nupkg`</span></span>
