---
ms.openlocfilehash: db89539982c1afe0df374027d54826f3265f0fee
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84603009"
---

### <a name="install-the-sdk"></a><span data-ttu-id="fbcb7-101">Instalar o SDK</span><span class="sxs-lookup"><span data-stu-id="fbcb7-101">Install the SDK</span></span>

<span data-ttu-id="fbcb7-102">O SDK do .NET Core permite que você desenvolva aplicativos com o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="fbcb7-102">The .NET Core SDK allows you to develop apps with .NET Core.</span></span> <span data-ttu-id="fbcb7-103">Para instalar o SDK do .NET Core, execute os comandos a seguir.</span><span class="sxs-lookup"><span data-stu-id="fbcb7-103">To install the .NET Core SDK, run the following commands.</span></span>

```bash
sudo zypper install dotnet-sdk-3.1
```

### <a name="install-the-runtime"></a><span data-ttu-id="fbcb7-104">Instalar o runtime</span><span class="sxs-lookup"><span data-stu-id="fbcb7-104">Install the runtime</span></span>

<span data-ttu-id="fbcb7-105">O tempo de execução do .NET Core permite executar aplicativos que foram feitos com o .NET Core que não incluiu o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="fbcb7-105">The .NET Core Runtime allows you to run apps that were made with .NET Core that didn't include the runtime.</span></span> <span data-ttu-id="fbcb7-106">Os comandos a seguir instalam o tempo de execução de ASP.NET Core, que é o tempo de execução mais compatível para o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="fbcb7-106">The commands below install the ASP.NET Core Runtime, which is the most compatible runtime for .NET Core.</span></span> <span data-ttu-id="fbcb7-107">Em seu terminal, execute os comandos a seguir.</span><span class="sxs-lookup"><span data-stu-id="fbcb7-107">In your terminal, run the following commands.</span></span>

```bash
sudo zypper install aspnetcore-runtime-3.1
```

<span data-ttu-id="fbcb7-108">Como alternativa ao tempo de execução de ASP.NET Core, você pode instalar o tempo de execução do .NET Core que não inclui suporte a ASP.NET Core: substitua `aspnetcore-runtime-2.1` no comando acima por `dotnet-runtime-3.1` .</span><span class="sxs-lookup"><span data-stu-id="fbcb7-108">As an alternative to the ASP.NET Core Runtime, you can install the .NET Core Runtime that doesn't include ASP.NET Core support: replace `aspnetcore-runtime-2.1` in the command above with `dotnet-runtime-3.1`.</span></span>

```bash
sudo zypper install dotnet-runtime-3.1
```
