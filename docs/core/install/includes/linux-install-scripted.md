---
ms.openlocfilehash: 0d29407896145bc3b2ed8284c839ae8f2f0521b2
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602946"
---

<span data-ttu-id="9cba4-101">Os [scripts dotnet-install](../../tools/dotnet-install-script.md) são usados para automação e instalações não administrativas do **SDK**.</span><span class="sxs-lookup"><span data-stu-id="9cba4-101">The [dotnet-install scripts](../../tools/dotnet-install-script.md) are used for automation and non-admin installs of the **SDK**.</span></span> <span data-ttu-id="9cba4-102">É possível baixar o script em <https://dot.net/v1/dotnet-install.sh>.</span><span class="sxs-lookup"><span data-stu-id="9cba4-102">You can download the script from <https://dot.net/v1/dotnet-install.sh>.</span></span>

<span data-ttu-id="9cba4-103">O script assume como padrão a instalação da versão mais recente do [LTS (suporte a longo prazo)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , que é o .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="9cba4-103">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="9cba4-104">Para instalar a versão atual, que pode não ser uma versão (LTS), use o `-c Current` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="9cba4-104">To install the current release, which may not be an (LTS) version, use the `-c Current` parameter.</span></span>

```bash
./dotnet-install.sh -c Current
```

<span data-ttu-id="9cba4-105">Para instalar o tempo de execução do .NET Core em vez do SDK, use o `--runtime` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="9cba4-105">To install .NET Core Runtime instead of the SDK, use the `--runtime` parameter.</span></span>

```bash
./dotnet-install.sh -c Current --runtime
```

<span data-ttu-id="9cba4-106">Você pode instalar uma versão específica alterando o `-c` parâmetro para indicar a versão específica.</span><span class="sxs-lookup"><span data-stu-id="9cba4-106">You can install a specific version by altering the `-c` parameter to indicate the specific version.</span></span> <span data-ttu-id="9cba4-107">O comando a seguir instala SDK do .NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="9cba4-107">The following command installs .NET Core SDK 3.1.</span></span>

```bash
./dotnet-install.sh -c 3.1
```

<span data-ttu-id="9cba4-108">Para obter mais informações, consulte [dotnet – referência de scripts de instalação](../../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="9cba4-108">For more information, see [dotnet-install scripts reference](../../tools/dotnet-install-script.md).</span></span>
