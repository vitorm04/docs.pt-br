---
ms.openlocfilehash: 36f1ee26def82d426b6637ae96f382fc89791a2f
ms.sourcegitcommit: b1442669f1982d3a1cb18ea35b5acfb0fc7d93e4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93135589"
---

### <a name="install-the-sdk"></a><span data-ttu-id="6c63b-101">Instalar o SDK</span><span class="sxs-lookup"><span data-stu-id="6c63b-101">Install the SDK</span></span>

<span data-ttu-id="6c63b-102">O SDK do .NET Core permite que você desenvolva aplicativos com o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6c63b-102">The .NET Core SDK allows you to develop apps with .NET Core.</span></span> <span data-ttu-id="6c63b-103">Para instalar o SDK do .NET Core, execute os comandos a seguir.</span><span class="sxs-lookup"><span data-stu-id="6c63b-103">To install the .NET Core SDK, run the following commands.</span></span>

```bash
sudo zypper install dotnet-sdk-3.1
```

### <a name="install-the-runtime"></a><span data-ttu-id="6c63b-104">Instalar o runtime</span><span class="sxs-lookup"><span data-stu-id="6c63b-104">Install the runtime</span></span>

<span data-ttu-id="6c63b-105">O tempo de execução do .NET Core permite executar aplicativos que foram feitos com o .NET Core que não incluiu o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="6c63b-105">The .NET Core Runtime allows you to run apps that were made with .NET Core that didn't include the runtime.</span></span> <span data-ttu-id="6c63b-106">Os comandos a seguir instalam o tempo de execução do ASP.NET Core, que é o tempo de execução mais compatível para o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6c63b-106">The following commands install the ASP.NET Core Runtime, which is the most compatible runtime for .NET Core.</span></span> <span data-ttu-id="6c63b-107">Em seu terminal, execute os comandos a seguir.</span><span class="sxs-lookup"><span data-stu-id="6c63b-107">In your terminal, run the following commands.</span></span>

```bash
sudo zypper install aspnetcore-runtime-3.1
```

<span data-ttu-id="6c63b-108">Como alternativa ao tempo de execução de ASP.NET Core, você pode instalar o tempo de execução do .NET Core que não inclui suporte a ASP.NET Core: substitua `aspnetcore-runtime-2.1` no comando anterior por `dotnet-runtime-3.1` .</span><span class="sxs-lookup"><span data-stu-id="6c63b-108">As an alternative to the ASP.NET Core Runtime, you can install the .NET Core Runtime that doesn't include ASP.NET Core support: replace `aspnetcore-runtime-2.1` in the previous command with `dotnet-runtime-3.1`.</span></span>

```bash
sudo zypper install dotnet-runtime-3.1
```
