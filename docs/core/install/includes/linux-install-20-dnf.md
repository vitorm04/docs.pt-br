---
ms.openlocfilehash: bd0953697ee3a9e928d09c1f270a4af5606ee0d9
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94507035"
---

### <a name="install-the-sdk"></a><span data-ttu-id="cedbc-101">Instalar o SDK</span><span class="sxs-lookup"><span data-stu-id="cedbc-101">Install the SDK</span></span>

<span data-ttu-id="cedbc-102">O SDK do .NET Core permite que você desenvolva aplicativos com o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="cedbc-102">The .NET Core SDK allows you to develop apps with .NET Core.</span></span> <span data-ttu-id="cedbc-103">Se você instalar o SDK do .NET Core, não será necessário instalar o tempo de execução correspondente.</span><span class="sxs-lookup"><span data-stu-id="cedbc-103">If you install the .NET Core SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="cedbc-104">Para instalar o SDK do .NET Core, execute os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="cedbc-104">To install the .NET Core SDK, run the following commands:</span></span>

```bash
sudo dnf install dotnet-sdk-2.0
```

### <a name="install-the-runtime"></a><span data-ttu-id="cedbc-105">Instalar o runtime</span><span class="sxs-lookup"><span data-stu-id="cedbc-105">Install the runtime</span></span>

<span data-ttu-id="cedbc-106">O tempo de execução do .NET Core permite executar aplicativos que foram feitos com o .NET Core que não incluiu o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="cedbc-106">The .NET Core Runtime allows you to run apps that were made with .NET Core that didn't include the runtime.</span></span> <span data-ttu-id="cedbc-107">Os comandos a seguir instalam o tempo de execução do ASP.NET Core, que é o tempo de execução mais compatível para o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="cedbc-107">The following commands install the ASP.NET Core Runtime, which is the most compatible runtime for .NET Core.</span></span> <span data-ttu-id="cedbc-108">Em seu terminal, execute os comandos a seguir.</span><span class="sxs-lookup"><span data-stu-id="cedbc-108">In your terminal, run the following commands.</span></span>

```bash
sudo dnf install aspnetcore-runtime-2.0
```

<span data-ttu-id="cedbc-109">Como alternativa ao tempo de execução de ASP.NET Core, você pode instalar o tempo de execução do .NET Core, que não inclui suporte a ASP.NET Core: substitua `aspnetcore-runtime-2.0` no comando anterior por `dotnet-runtime-2.0` .</span><span class="sxs-lookup"><span data-stu-id="cedbc-109">As an alternative to the ASP.NET Core Runtime, you can install the .NET Core Runtime, which doesn't include ASP.NET Core support: replace `aspnetcore-runtime-2.0` in the previous command with `dotnet-runtime-2.0`.</span></span>

```bash
sudo dnf install dotnet-runtime-2.0
```
