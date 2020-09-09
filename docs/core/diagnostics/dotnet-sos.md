---
title: dotnet-SOS-.NET Core
description: Instalando e usando a ferramenta de linha de comando dotnet-SOS.
ms.date: 08/26/2020
ms.openlocfilehash: 3ce7ca79bbc2c72958d395e9d312e3001ec9fbf8
ms.sourcegitcommit: 43d5aca3fda42bad8843f6c4e72f6bd52daa55f1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/09/2020
ms.locfileid: "89598322"
---
# <a name="sos-installer-dotnet-sos"></a><span data-ttu-id="67990-103">Instalador do SOS (dotNet-SOS)</span><span class="sxs-lookup"><span data-stu-id="67990-103">SOS installer (dotnet-sos)</span></span>

<span data-ttu-id="67990-104">**Este artigo aplica-se a:** ✔️ SDK do .net Core 2,1 e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="67990-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="install-dotnet-sos"></a><span data-ttu-id="67990-105">Instalar dotnet-SOS</span><span class="sxs-lookup"><span data-stu-id="67990-105">Install dotnet-sos</span></span>

<span data-ttu-id="67990-106">Para instalar a versão de lançamento mais recente do `dotnet-sos` [pacote NuGet](https://www.nuget.org/packages/dotnet-sos), use o comando de [instalação da ferramenta dotnet](../tools/dotnet-tool-install.md) :</span><span class="sxs-lookup"><span data-stu-id="67990-106">To install the latest release version of the `dotnet-sos` [NuGet package](https://www.nuget.org/packages/dotnet-sos), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

```dotnetcli
dotnet tool install -g dotnet-sos
```

## <a name="synopsis"></a><span data-ttu-id="67990-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="67990-107">Synopsis</span></span>

```console
dotnet-sos [-h|--help] [options] [command]]
```

## <a name="description"></a><span data-ttu-id="67990-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="67990-108">Description</span></span>

<span data-ttu-id="67990-109">A `dotnet-sos` ferramenta global instala a [extensão do depurador SOS](https://docs.microsoft.com/dotnet/framework/tools/sos-dll-sos-debugging-extension) , permitindo a [inspeção do estado do .NET Core gerenciado](https://github.com/dotnet/diagnostics/blob/master/documentation/sos-debugging-extension.md) por meio de depuradores nativos como WinDbg/CDB no Windows e Lldb no Linux e no MacOS.</span><span class="sxs-lookup"><span data-stu-id="67990-109">The `dotnet-sos` global tool installs the [SOS debugger extension](https://docs.microsoft.com/dotnet/framework/tools/sos-dll-sos-debugging-extension) allowing [inspection of managed .NET Core state](https://github.com/dotnet/diagnostics/blob/master/documentation/sos-debugging-extension.md) from native debuggers like WinDbg/cdb on Windows and lldb on Linux and MacOS.</span></span> <span data-ttu-id="67990-110">Observe que as versões recentes do depurador do Windows (>= versão 10.0.18317.1001 do WinDbg ou do CDB) carregarão o SOS automaticamente da Galeria de extensões da Microsoft, portanto, instalar o SOS por meio da `dotnet-sos` ferramenta só será necessário no Linux e no MacOS ou no Windows se estiver usando ferramentas de depuração mais antigas.</span><span class="sxs-lookup"><span data-stu-id="67990-110">Note that recent versions of the Windows Debugger (>= version 10.0.18317.1001 of WinDbg or cdb) will load SOS automatically from the Microsoft extension gallery, so installing SOS via the `dotnet-sos` tool is only needed on Linux and MacOS or on Windows if using older debugging tools.</span></span>

## <a name="options"></a><span data-ttu-id="67990-111">Opções</span><span class="sxs-lookup"><span data-stu-id="67990-111">Options</span></span>

- **`--version`**

  <span data-ttu-id="67990-112">Exibe informações de versão.</span><span class="sxs-lookup"><span data-stu-id="67990-112">Displays version information.</span></span>

- **`-h|--help`**

  <span data-ttu-id="67990-113">Mostra a ajuda da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="67990-113">Shows command-line help.</span></span>

## <a name="dotnet-sos-install"></a><span data-ttu-id="67990-114">dotnet – instalação do SOS</span><span class="sxs-lookup"><span data-stu-id="67990-114">dotnet-sos install</span></span>

<span data-ttu-id="67990-115">Instala a [extensão SOS localmente](https://docs.microsoft.com/dotnet/framework/tools/sos-dll-sos-debugging-extension) para usar a depuração de processos do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="67990-115">Installs the [SOS extension locally](https://docs.microsoft.com/dotnet/framework/tools/sos-dll-sos-debugging-extension) for use debugging .NET Core processes.</span></span> <span data-ttu-id="67990-116">No MacOS e Linux, o arquivo. lldbinit será atualizado para que a extensão seja carregada automaticamente na inicialização do lldb.</span><span class="sxs-lookup"><span data-stu-id="67990-116">On MacOS and Linux, the .lldbinit file will be updated so that the extension automatically loads at lldb startup.</span></span> <span data-ttu-id="67990-117">Se estiver instalando o SOS no Windows com as ferramentas de depuração mais antigas (< versão 10.0.18317.1001), será necessário carregar manualmente a extensão no WinDbg ou no CDB executando `.load %USERPROFILE%\.dotnet\sos\sos.dll` no depurador.</span><span class="sxs-lookup"><span data-stu-id="67990-117">If installing SOS on Windows with older debugging tools (< version 10.0.18317.1001), you will need to manually load the extension in WinDbg or cdb by running `.load %USERPROFILE%\.dotnet\sos\sos.dll` in the debugger.</span></span>

### <a name="synopsis"></a><span data-ttu-id="67990-118">Sinopse</span><span class="sxs-lookup"><span data-stu-id="67990-118">Synopsis</span></span>

```console
dotnet-sos install
```

## <a name="dotnet-sos-uninstall"></a><span data-ttu-id="67990-119">dotnet – desinstalação do SOS</span><span class="sxs-lookup"><span data-stu-id="67990-119">dotnet-sos uninstall</span></span>

<span data-ttu-id="67990-120">Desinstala a [extensão SOS](https://docs.microsoft.com/dotnet/framework/tools/sos-dll-sos-debugging-extension) e, se estiver no Linux ou no MacOS, o removerá da configuração do lldb.</span><span class="sxs-lookup"><span data-stu-id="67990-120">Uninstalls the [SOS extension](https://docs.microsoft.com/dotnet/framework/tools/sos-dll-sos-debugging-extension) and, if on Linux or MacOS, removes it from lldb configuration.</span></span>

### <a name="synopsis"></a><span data-ttu-id="67990-121">Sinopse</span><span class="sxs-lookup"><span data-stu-id="67990-121">Synopsis</span></span>

```console
dotnet-sos uninstall
```
