---
ms.openlocfilehash: f7cd60f02a51516b8e35cdb9014fa8b96a188ae2
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94506942"
---

### <a name="install-the-sdk"></a><span data-ttu-id="febe6-101">Instalar o SDK</span><span class="sxs-lookup"><span data-stu-id="febe6-101">Install the SDK</span></span>

<span data-ttu-id="febe6-102">O SDK do .NET Core permite que você desenvolva aplicativos com o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="febe6-102">The .NET Core SDK allows you to develop apps with .NET Core.</span></span> <span data-ttu-id="febe6-103">Se você instalar o SDK do .NET Core, não será necessário instalar o tempo de execução correspondente.</span><span class="sxs-lookup"><span data-stu-id="febe6-103">If you install the .NET Core SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="febe6-104">Para instalar o SDK do .NET Core, execute os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="febe6-104">To install the .NET Core SDK, run the following commands:</span></span>

```bash
sudo apt-get update; \
  sudo apt-get install -y apt-transport-https && \
  sudo apt-get update && \
  sudo apt-get install -y dotnet-sdk-2.1
```

> [!IMPORTANT]
> <span data-ttu-id="febe6-105">Se você receber uma mensagem de erro semelhante a **não é possível localizar o pacote dotnet-SDK-2,1** , consulte a seção [solução de problemas da apt](#apt-troubleshooting) .</span><span class="sxs-lookup"><span data-stu-id="febe6-105">If you receive an error message similar to **Unable to locate package dotnet-sdk-2.1** , see the [APT troubleshooting](#apt-troubleshooting) section.</span></span>

### <a name="install-the-runtime"></a><span data-ttu-id="febe6-106">Instalar o runtime</span><span class="sxs-lookup"><span data-stu-id="febe6-106">Install the runtime</span></span>

<span data-ttu-id="febe6-107">O tempo de execução do .NET Core permite executar aplicativos que foram feitos com o .NET Core que não incluiu o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="febe6-107">The .NET Core Runtime allows you to run apps that were made with .NET Core that didn't include the runtime.</span></span> <span data-ttu-id="febe6-108">Os comandos a seguir instalam o tempo de execução do ASP.NET Core, que é o tempo de execução mais compatível para o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="febe6-108">The following commands install the ASP.NET Core Runtime, which is the most compatible runtime for .NET Core.</span></span> <span data-ttu-id="febe6-109">Em seu terminal, execute os comandos a seguir.</span><span class="sxs-lookup"><span data-stu-id="febe6-109">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update; \
  sudo apt-get install -y apt-transport-https && \
  sudo apt-get update && \
  sudo apt-get install -y aspnetcore-runtime-2.1
```

> [!IMPORTANT]
> <span data-ttu-id="febe6-110">Se você receber uma mensagem de erro semelhante a **não é possível localizar o pacote aspnetcore-Runtime-2,1** , consulte a seção [solução de problemas da apt](#apt-troubleshooting) .</span><span class="sxs-lookup"><span data-stu-id="febe6-110">If you receive an error message similar to **Unable to locate package aspnetcore-runtime-2.1** , see the [APT troubleshooting](#apt-troubleshooting) section.</span></span>

<span data-ttu-id="febe6-111">Como alternativa ao tempo de execução de ASP.NET Core, você pode instalar o tempo de execução do .NET Core, que não inclui suporte a ASP.NET Core: substitua `aspnetcore-runtime-2.1` no comando anterior por `dotnet-runtime-2.1` .</span><span class="sxs-lookup"><span data-stu-id="febe6-111">As an alternative to the ASP.NET Core Runtime, you can install the .NET Core Runtime, which doesn't include ASP.NET Core support: replace `aspnetcore-runtime-2.1` in the previous command with `dotnet-runtime-2.1`.</span></span>

```bash
sudo apt-get install -y dotnet-runtime-2.1
```
