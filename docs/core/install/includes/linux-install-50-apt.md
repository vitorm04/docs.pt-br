---
ms.openlocfilehash: 87c7abf6a20dd8e9769f3b3b3cbe271d32fd62c3
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94506946"
---

### <a name="install-the-sdk"></a><span data-ttu-id="56e19-101">Instalar o SDK</span><span class="sxs-lookup"><span data-stu-id="56e19-101">Install the SDK</span></span>

<span data-ttu-id="56e19-102">O SDK do .NET permite que você desenvolva aplicativos com o .NET.</span><span class="sxs-lookup"><span data-stu-id="56e19-102">The .NET SDK allows you to develop apps with .NET.</span></span> <span data-ttu-id="56e19-103">Se você instalar o SDK do .NET, não precisará instalar o tempo de execução correspondente.</span><span class="sxs-lookup"><span data-stu-id="56e19-103">If you install the .NET SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="56e19-104">Para instalar o SDK do .NET, execute os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="56e19-104">To install the .NET SDK, run the following commands:</span></span>

```bash
sudo apt-get update; \
  sudo apt-get install -y apt-transport-https && \
  sudo apt-get update && \
  sudo apt-get install -y dotnet-sdk-5.0
```

> [!IMPORTANT]
> <span data-ttu-id="56e19-105">Se você receber uma mensagem de erro semelhante a **não é possível localizar o pacote dotnet-SDK-5,0** , consulte a seção [solução de problemas da apt](#apt-troubleshooting) .</span><span class="sxs-lookup"><span data-stu-id="56e19-105">If you receive an error message similar to **Unable to locate package dotnet-sdk-5.0** , see the [APT troubleshooting](#apt-troubleshooting) section.</span></span>

### <a name="install-the-runtime"></a><span data-ttu-id="56e19-106">Instalar o runtime</span><span class="sxs-lookup"><span data-stu-id="56e19-106">Install the runtime</span></span>

<span data-ttu-id="56e19-107">O tempo de execução de ASP.NET Core permite que você execute aplicativos que foram feitos com o .NET que não forneceu o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="56e19-107">The ASP.NET Core Runtime allows you to run apps that were made with .NET that didn't provide the runtime.</span></span> <span data-ttu-id="56e19-108">Os comandos a seguir instalam o tempo de execução do ASP.NET Core, que é o tempo de execução mais compatível para o .NET.</span><span class="sxs-lookup"><span data-stu-id="56e19-108">The following commands install the ASP.NET Core Runtime, which is the most compatible runtime for .NET.</span></span> <span data-ttu-id="56e19-109">Em seu terminal, execute os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="56e19-109">In your terminal, run the following commands:</span></span>

```bash
sudo apt-get update; \
  sudo apt-get install -y apt-transport-https && \
  sudo apt-get update && \
  sudo apt-get install -y aspnetcore-runtime-5.0
```

> [!IMPORTANT]
> <span data-ttu-id="56e19-110">Se você receber uma mensagem de erro semelhante a **não é possível localizar o pacote aspnetcore-Runtime-5,0** , consulte a seção [solução de problemas da apt](#apt-troubleshooting) .</span><span class="sxs-lookup"><span data-stu-id="56e19-110">If you receive an error message similar to **Unable to locate package aspnetcore-runtime-5.0** , see the [APT troubleshooting](#apt-troubleshooting) section.</span></span>

<span data-ttu-id="56e19-111">Como alternativa ao tempo de execução de ASP.NET Core, você pode instalar o tempo de execução do .NET, que não inclui suporte a ASP.NET Core: substitua `aspnetcore-runtime-5.0` no comando anterior por `dotnet-runtime-5.0` :</span><span class="sxs-lookup"><span data-stu-id="56e19-111">As an alternative to the ASP.NET Core Runtime, you can install the .NET Runtime, which doesn't include ASP.NET Core support: replace `aspnetcore-runtime-5.0` in the previous command with `dotnet-runtime-5.0`:</span></span>

```bash
sudo apt-get install -y dotnet-runtime-5.0
```
