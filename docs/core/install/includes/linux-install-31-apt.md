---
ms.openlocfilehash: 56f5d27eb9be2f8eb3e335c5ec161dba1bcfdb1e
ms.sourcegitcommit: b1442669f1982d3a1cb18ea35b5acfb0fc7d93e4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93135695"
---

### <a name="install-the-sdk"></a><span data-ttu-id="940d2-101">Instalar o SDK</span><span class="sxs-lookup"><span data-stu-id="940d2-101">Install the SDK</span></span>

<span data-ttu-id="940d2-102">SDK do .NET Core permite que você desenvolva aplicativos com o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="940d2-102">.NET Core SDK allows you to develop apps with .NET Core.</span></span> <span data-ttu-id="940d2-103">Se você instalar SDK do .NET Core, não será necessário instalar o tempo de execução correspondente.</span><span class="sxs-lookup"><span data-stu-id="940d2-103">If you install .NET Core SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="940d2-104">Para instalar o SDK do .NET Core, execute os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="940d2-104">To install .NET Core SDK, run the following commands:</span></span>

```bash
sudo apt-get update; \
  sudo apt-get install -y apt-transport-https && \
  sudo apt-get update && \
  sudo apt-get install -y dotnet-sdk-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="940d2-105">Se você receber uma mensagem de erro semelhante a **não é possível localizar o pacote dotnet-SDK-3,1** , consulte a seção [solução de problemas da apt](#apt-troubleshooting) .</span><span class="sxs-lookup"><span data-stu-id="940d2-105">If you receive an error message similar to **Unable to locate package dotnet-sdk-3.1** , see the [APT troubleshooting](#apt-troubleshooting) section.</span></span>

### <a name="install-the-runtime"></a><span data-ttu-id="940d2-106">Instalar o runtime</span><span class="sxs-lookup"><span data-stu-id="940d2-106">Install the runtime</span></span>

<span data-ttu-id="940d2-107">O tempo de execução do .NET Core permite executar aplicativos que foram feitos com o .NET Core que não incluiu o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="940d2-107">The .NET Core Runtime allows you to run apps that were made with .NET Core that didn't include the runtime.</span></span> <span data-ttu-id="940d2-108">Os comandos a seguir instalam o tempo de execução do ASP.NET Core, que é o tempo de execução mais compatível para o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="940d2-108">The following commands install the ASP.NET Core Runtime, which is the most compatible runtime for .NET Core.</span></span> <span data-ttu-id="940d2-109">Em seu terminal, execute os comandos a seguir.</span><span class="sxs-lookup"><span data-stu-id="940d2-109">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update; \
  sudo apt-get install -y apt-transport-https && \
  sudo apt-get update && \
  sudo apt-get install -y aspnetcore-runtime-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="940d2-110">Se você receber uma mensagem de erro semelhante a **não é possível localizar o pacote aspnetcore-Runtime-3,1** , consulte a seção [solução de problemas da apt](#apt-troubleshooting) .</span><span class="sxs-lookup"><span data-stu-id="940d2-110">If you receive an error message similar to **Unable to locate package aspnetcore-runtime-3.1** , see the [APT troubleshooting](#apt-troubleshooting) section.</span></span>

<span data-ttu-id="940d2-111">Como alternativa ao tempo de execução de ASP.NET Core, você pode instalar o tempo de execução do .NET Core que não inclui suporte a ASP.NET Core: substitua `aspnetcore-runtime-3.1` no comando anterior por `dotnet-runtime-3.1` .</span><span class="sxs-lookup"><span data-stu-id="940d2-111">As an alternative to the ASP.NET Core Runtime, you can install the .NET Core Runtime that doesn't include ASP.NET Core support: replace `aspnetcore-runtime-3.1` in the previous command with `dotnet-runtime-3.1`.</span></span>

```bash
sudo apt-get install -y dotnet-runtime-3.1
```
