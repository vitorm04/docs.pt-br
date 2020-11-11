---
ms.openlocfilehash: aba7b473af7685aa45f7e093a2f75311687593df
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94506943"
---

<span data-ttu-id="cd095-101">Se você receber uma mensagem de erro semelhante a **não é possível localizar o pacote {dotnet-Package}** ou **não foi possível instalar alguns pacotes** , execute os comandos a seguir.</span><span class="sxs-lookup"><span data-stu-id="cd095-101">If you receive an error message similar to **Unable to locate package {dotnet-package}** or **Some packages could not be installed** , run the following commands.</span></span>

<span data-ttu-id="cd095-102">Há dois espaços reservados no seguinte conjunto de comandos.</span><span class="sxs-lookup"><span data-stu-id="cd095-102">There are two placeholders in the following set of commands.</span></span>

- `{dotnet-package}`\
<span data-ttu-id="cd095-103">Isso representa o pacote .NET que você está instalando, como `aspnetcore-runtime-3.1` .</span><span class="sxs-lookup"><span data-stu-id="cd095-103">This represents the .NET package you're installing, such as `aspnetcore-runtime-3.1`.</span></span> <span data-ttu-id="cd095-104">Isso é usado no comando a seguir `sudo apt-get install` .</span><span class="sxs-lookup"><span data-stu-id="cd095-104">This is used in the following `sudo apt-get install` command.</span></span>

- `{os-version}`\
<span data-ttu-id="cd095-105">Isso representa a versão do Linux em que você está.</span><span class="sxs-lookup"><span data-stu-id="cd095-105">This represents the Linux version you are on.</span></span> <span data-ttu-id="cd095-106">Isso é usado no `wget` comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="cd095-106">This is used in the `wget` command below.</span></span>

<span data-ttu-id="cd095-107">Primeiro, tente limpar a lista de pacotes:</span><span class="sxs-lookup"><span data-stu-id="cd095-107">First, try purging the package list:</span></span>

```bash
sudo dpkg --purge packages-microsoft-prod && sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update
```

<span data-ttu-id="cd095-108">Em seguida, tente instalar o .NET novamente.</span><span class="sxs-lookup"><span data-stu-id="cd095-108">Then, try to install .NET again.</span></span> <span data-ttu-id="cd095-109">Se isso não funcionar, você poderá executar uma instalação manual com os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="cd095-109">If that doesn't work, you can run a manual install with the following commands:</span></span>
