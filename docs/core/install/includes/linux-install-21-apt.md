---
ms.openlocfilehash: 188fef66444cd60f59a3cb9619c0d86efd155f99
ms.sourcegitcommit: b1442669f1982d3a1cb18ea35b5acfb0fc7d93e4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93135533"
---

### <a name="install-the-sdk"></a><span data-ttu-id="fae4c-101">Instalar o SDK</span><span class="sxs-lookup"><span data-stu-id="fae4c-101">Install the SDK</span></span>

<span data-ttu-id="fae4c-102">SDK do .NET Core permite que você desenvolva aplicativos com o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="fae4c-102">.NET Core SDK allows you to develop apps with .NET Core.</span></span> <span data-ttu-id="fae4c-103">Se você instalar SDK do .NET Core, não será necessário instalar o tempo de execução correspondente.</span><span class="sxs-lookup"><span data-stu-id="fae4c-103">If you install .NET Core SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="fae4c-104">Para instalar o SDK do .NET Core, execute os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="fae4c-104">To install .NET Core SDK, run the following commands:</span></span>

```bash
sudo apt-get update; \
  sudo apt-get install -y apt-transport-https && \
  sudo apt-get update && \
  sudo apt-get install -y dotnet-sdk-2.1
```

> [!IMPORTANT]
> <span data-ttu-id="fae4c-105">Se você receber uma mensagem de erro semelhante a **não é possível localizar o pacote dotnet-SDK-2,1** , consulte a seção [solução de problemas da apt](#apt-troubleshooting) .</span><span class="sxs-lookup"><span data-stu-id="fae4c-105">If you receive an error message similar to **Unable to locate package dotnet-sdk-2.1** , see the [APT troubleshooting](#apt-troubleshooting) section.</span></span>

### <a name="install-the-runtime"></a><span data-ttu-id="fae4c-106">Instalar o runtime</span><span class="sxs-lookup"><span data-stu-id="fae4c-106">Install the runtime</span></span>

<span data-ttu-id="fae4c-107">O tempo de execução do .NET Core permite executar aplicativos que foram feitos com o .NET Core que não incluiu o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="fae4c-107">The .NET Core Runtime allows you to run apps that were made with .NET Core that didn't include the runtime.</span></span> <span data-ttu-id="fae4c-108">Os comandos a seguir instalam o tempo de execução do ASP.NET Core, que é o tempo de execução mais compatível para o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="fae4c-108">The following commands install the ASP.NET Core Runtime, which is the most compatible runtime for .NET Core.</span></span> <span data-ttu-id="fae4c-109">Em seu terminal, execute os comandos a seguir.</span><span class="sxs-lookup"><span data-stu-id="fae4c-109">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update; \
  sudo apt-get install -y apt-transport-https && \
  sudo apt-get update && \
  sudo apt-get install -y aspnetcore-runtime-2.1
```

> [!IMPORTANT]
> <span data-ttu-id="fae4c-110">Se você receber uma mensagem de erro semelhante a **não é possível localizar o pacote aspnetcore-Runtime-2,1** , consulte a seção [solução de problemas da apt](#apt-troubleshooting) .</span><span class="sxs-lookup"><span data-stu-id="fae4c-110">If you receive an error message similar to **Unable to locate package aspnetcore-runtime-2.1** , see the [APT troubleshooting](#apt-troubleshooting) section.</span></span>

<span data-ttu-id="fae4c-111">Como alternativa ao tempo de execução de ASP.NET Core, você pode instalar o tempo de execução do .NET Core que não inclui suporte a ASP.NET Core: substitua `aspnetcore-runtime-2.1` no comando anterior por `dotnet-runtime-2.1` .</span><span class="sxs-lookup"><span data-stu-id="fae4c-111">As an alternative to the ASP.NET Core Runtime, you can install the .NET Core Runtime that doesn't include ASP.NET Core support: replace `aspnetcore-runtime-2.1` in the previous command with `dotnet-runtime-2.1`.</span></span>

```bash
sudo apt-get install -y dotnet-runtime-2.1
```
