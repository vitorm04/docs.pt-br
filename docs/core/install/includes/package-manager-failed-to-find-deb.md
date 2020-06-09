---
ms.openlocfilehash: 7d398df060c031ae891218b82a2712d74f4c33b7
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602981"
---

<span data-ttu-id="adae4-101">Se você receber uma mensagem de erro semelhante a **não é possível localizar o pacote {NetCore-Package}**, execute os comandos a seguir.</span><span class="sxs-lookup"><span data-stu-id="adae4-101">If you receive an error message similar to **Unable to locate package {netcore-package}**, run the following commands.</span></span>

<span data-ttu-id="adae4-102">Há dois espaços reservados no seguinte conjunto de comandos.</span><span class="sxs-lookup"><span data-stu-id="adae4-102">There are two placeholders in the following set of commands.</span></span>

- `{dotnet-package}`\
<span data-ttu-id="adae4-103">Isso representa o pacote .NET Core que você está instalando, como `aspnetcore-runtime-3.1` .</span><span class="sxs-lookup"><span data-stu-id="adae4-103">This represents the .NET Core package you're installing, such as `aspnetcore-runtime-3.1`.</span></span> <span data-ttu-id="adae4-104">Isso é usado no `sudo apt-get install` comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="adae4-104">This is used in the `sudo apt-get install` command below.</span></span>

- `{os-version}`\
<span data-ttu-id="adae4-105">Isso representa a versão do Linux em que você está.</span><span class="sxs-lookup"><span data-stu-id="adae4-105">This represents the Linux version you are on.</span></span> <span data-ttu-id="adae4-106">Isso é usado no `wget` comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="adae4-106">This is used in the `wget` command below.</span></span>

<span data-ttu-id="adae4-107">Tente limpar a lista de pacotes:</span><span class="sxs-lookup"><span data-stu-id="adae4-107">Try purging the package list:</span></span>

```bash
sudo dpkg --purge packages-microsoft-prod && sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update
sudo apt-get install {dotnet-package}
```

<span data-ttu-id="adae4-108">Se isso não funcionar, você poderá executar uma instalação manual com os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="adae4-108">If that doesn't work, you can run a manual install with the following commands:</span></span>
