---
ms.openlocfilehash: fb78e1439a680a8dbb9fc0eb8afdeee3efef7ead
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/15/2020
ms.locfileid: "84768385"
---

<span data-ttu-id="a2188-101">Os [scripts dotnet-install](../../tools/dotnet-install-script.md) são usados para instalações de automação e não administrativas do **SDK** e do **tempo de execução**.</span><span class="sxs-lookup"><span data-stu-id="a2188-101">The [dotnet-install scripts](../../tools/dotnet-install-script.md) are used for automation and non-admin installs of the **SDK** and **Runtime**.</span></span> <span data-ttu-id="a2188-102">É possível baixar o script em <https://dot.net/v1/dotnet-install.sh>.</span><span class="sxs-lookup"><span data-stu-id="a2188-102">You can download the script from <https://dot.net/v1/dotnet-install.sh>.</span></span>

<span data-ttu-id="a2188-103">O script assume como padrão a instalação da versão mais recente do [LTS (suporte a longo prazo)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) do SDK, que é o .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="a2188-103">The script defaults to installing the latest SDK [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="a2188-104">Para instalar a versão atual, que pode não ser uma versão (LTS), use o `-c Current` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="a2188-104">To install the current release, which may not be an (LTS) version, use the `-c Current` parameter.</span></span>

```bash
./dotnet-install.sh -c Current
```

<span data-ttu-id="a2188-105">Para instalar o tempo de execução do .NET Core em vez do SDK, use o `--runtime` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="a2188-105">To install .NET Core Runtime instead of the SDK, use the `--runtime` parameter.</span></span>

```bash
./dotnet-install.sh -c Current --runtime aspnetcore
```

<span data-ttu-id="a2188-106">Você pode instalar uma versão específica alterando o `-c` parâmetro para indicar a versão específica.</span><span class="sxs-lookup"><span data-stu-id="a2188-106">You can install a specific version by altering the `-c` parameter to indicate the specific version.</span></span> <span data-ttu-id="a2188-107">O comando a seguir instala SDK do .NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="a2188-107">The following command installs .NET Core SDK 3.1.</span></span>

```bash
./dotnet-install.sh -c 3.1
```

<span data-ttu-id="a2188-108">Para obter mais informações, consulte [dotnet – referência de scripts de instalação](../../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="a2188-108">For more information, see [dotnet-install scripts reference](../../tools/dotnet-install-script.md).</span></span>
