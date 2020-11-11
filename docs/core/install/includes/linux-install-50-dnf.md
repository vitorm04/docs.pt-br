---
ms.openlocfilehash: 2cd5459ab7f2c8c96638bf27dd30980282036925
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94506917"
---

### <a name="install-the-sdk"></a><span data-ttu-id="400bc-101">Instalar o SDK</span><span class="sxs-lookup"><span data-stu-id="400bc-101">Install the SDK</span></span>

<span data-ttu-id="400bc-102">O SDK do .NET permite que você desenvolva aplicativos com o .NET.</span><span class="sxs-lookup"><span data-stu-id="400bc-102">The .NET SDK allows you to develop apps with .NET.</span></span> <span data-ttu-id="400bc-103">Se você instalar o SDK do .NET, não precisará instalar o tempo de execução correspondente.</span><span class="sxs-lookup"><span data-stu-id="400bc-103">If you install the .NET SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="400bc-104">Para instalar o SDK do .NET, execute os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="400bc-104">To install the .NET SDK, run the following commands:</span></span>

```bash
sudo dnf install dotnet-sdk-5.0
```

### <a name="install-the-runtime"></a><span data-ttu-id="400bc-105">Instalar o runtime</span><span class="sxs-lookup"><span data-stu-id="400bc-105">Install the runtime</span></span>

<span data-ttu-id="400bc-106">O tempo de execução de ASP.NET Core permite que você execute aplicativos que foram feitos com o .NET que não forneceu o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="400bc-106">The ASP.NET Core Runtime allows you to run apps that were made with .NET that didn't provide the runtime.</span></span> <span data-ttu-id="400bc-107">Os comandos a seguir instalam o tempo de execução do ASP.NET Core, que é o tempo de execução mais compatível para o .NET.</span><span class="sxs-lookup"><span data-stu-id="400bc-107">The following commands install the ASP.NET Core Runtime, which is the most compatible runtime for .NET.</span></span> <span data-ttu-id="400bc-108">Em seu terminal, execute os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="400bc-108">In your terminal, run the following commands:</span></span>

```bash
sudo dnf install aspnetcore-runtime-5.0
```

<span data-ttu-id="400bc-109">Como alternativa ao tempo de execução de ASP.NET Core, você pode instalar o tempo de execução do .NET, que não inclui suporte a ASP.NET Core: substitua `aspnetcore-runtime-5.0` no comando anterior por `dotnet-runtime-5.0` :</span><span class="sxs-lookup"><span data-stu-id="400bc-109">As an alternative to the ASP.NET Core Runtime, you can install the .NET Runtime, which doesn't include ASP.NET Core support: replace `aspnetcore-runtime-5.0` in the previous command with `dotnet-runtime-5.0`:</span></span>

```bash
sudo dnf install dotnet-runtime-5.0
```
