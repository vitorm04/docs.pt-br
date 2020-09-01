---
ms.openlocfilehash: 9d4c031eda291b0a8832c824789efdffe4084926
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89132932"
---

<span data-ttu-id="8cf6c-101">Se você receber uma mensagem de erro semelhante a **não é possível localizar o pacote {NetCore-Package}** ou **alguns pacotes não puderam ser instalados**, execute os comandos a seguir.</span><span class="sxs-lookup"><span data-stu-id="8cf6c-101">If you receive an error message similar to **Unable to locate package {netcore-package}** or **Some packages could not be installed**, run the following commands.</span></span>

<span data-ttu-id="8cf6c-102">Há dois espaços reservados no seguinte conjunto de comandos.</span><span class="sxs-lookup"><span data-stu-id="8cf6c-102">There are two placeholders in the following set of commands.</span></span>

- `{dotnet-package}`\
<span data-ttu-id="8cf6c-103">Isso representa o pacote .NET Core que você está instalando, como `aspnetcore-runtime-3.1` .</span><span class="sxs-lookup"><span data-stu-id="8cf6c-103">This represents the .NET Core package you're installing, such as `aspnetcore-runtime-3.1`.</span></span> <span data-ttu-id="8cf6c-104">Isso é usado no `sudo apt-get install` comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="8cf6c-104">This is used in the `sudo apt-get install` command below.</span></span>

- `{os-version}`\
<span data-ttu-id="8cf6c-105">Isso representa a versão do Linux em que você está.</span><span class="sxs-lookup"><span data-stu-id="8cf6c-105">This represents the Linux version you are on.</span></span> <span data-ttu-id="8cf6c-106">Isso é usado no `wget` comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="8cf6c-106">This is used in the `wget` command below.</span></span>

<span data-ttu-id="8cf6c-107">Primeiro, tente limpar a lista de pacotes:</span><span class="sxs-lookup"><span data-stu-id="8cf6c-107">First, try purging the package list:</span></span>

```bash
sudo dpkg --purge packages-microsoft-prod && sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update
```

<span data-ttu-id="8cf6c-108">Em seguida, tente instalar o .NET Core novamente.</span><span class="sxs-lookup"><span data-stu-id="8cf6c-108">Then, try to install .NET Core again.</span></span> <span data-ttu-id="8cf6c-109">Se isso não funcionar, você poderá executar uma instalação manual com os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="8cf6c-109">If that doesn't work, you can run a manual install with the following commands:</span></span>
