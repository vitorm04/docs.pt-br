---
ms.openlocfilehash: b371525c9f4e57c6a09e5bb9232884e5c5e707e0
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84603002"
---

<span data-ttu-id="004d4-101">Quando você instala o com um Gerenciador de pacotes, essas bibliotecas são instaladas para você.</span><span class="sxs-lookup"><span data-stu-id="004d4-101">When you install with a package manager, these libraries are installed for you.</span></span> <span data-ttu-id="004d4-102">Mas, se você instalar manualmente o .NET Core ou publicar um aplicativo independente, precisará verificar se essas bibliotecas estão instaladas:</span><span class="sxs-lookup"><span data-stu-id="004d4-102">But, if you manually install .NET Core or you publish a self-contained app, you'll need to make sure these libraries are installed:</span></span>

- <span data-ttu-id="004d4-103">lttng-ust</span><span class="sxs-lookup"><span data-stu-id="004d4-103">lttng-ust</span></span>
- <span data-ttu-id="004d4-104">libcurl</span><span class="sxs-lookup"><span data-stu-id="004d4-104">libcurl</span></span>
- <span data-ttu-id="004d4-105">openssl-libs</span><span class="sxs-lookup"><span data-stu-id="004d4-105">openssl-libs</span></span>
- <span data-ttu-id="004d4-106">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="004d4-106">krb5-libs</span></span>
- <span data-ttu-id="004d4-107">libicu</span><span class="sxs-lookup"><span data-stu-id="004d4-107">libicu</span></span>
- <span data-ttu-id="004d4-108">zlib</span><span class="sxs-lookup"><span data-stu-id="004d4-108">zlib</span></span>
- <span data-ttu-id="004d4-109">libunwind</span><span class="sxs-lookup"><span data-stu-id="004d4-109">libunwind</span></span>
- <span data-ttu-id="004d4-110">libuuid</span><span class="sxs-lookup"><span data-stu-id="004d4-110">libuuid</span></span>

<span data-ttu-id="004d4-111">Se a versão do OpenSSL do ambiente de tempo de execução de destino for 1,1 ou mais recente, você precisará instalar o **compat-openssl10**.</span><span class="sxs-lookup"><span data-stu-id="004d4-111">If the target runtime environment's OpenSSL version is 1.1 or newer, you'll need to install **compat-openssl10**.</span></span>

<span data-ttu-id="004d4-112">Para obter mais informações sobre as dependências, consulte [aplicativos do Linux autocontidos](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span><span class="sxs-lookup"><span data-stu-id="004d4-112">For more information about the dependencies, see [Self-contained Linux apps](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

<span data-ttu-id="004d4-113">Para aplicativos .NET Core que usam o assembly *System. Drawing. Common* , você também precisará da seguinte dependência:</span><span class="sxs-lookup"><span data-stu-id="004d4-113">For .NET Core apps that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

- [<span data-ttu-id="004d4-114">libgdiplus (versão 6.0.1 ou posterior)</span><span class="sxs-lookup"><span data-stu-id="004d4-114">libgdiplus (version 6.0.1 or later)</span></span>](https://www.mono-project.com/docs/gui/libgdiplus/)

  > [!WARNING]
  > <span data-ttu-id="004d4-115">Você pode instalar uma versão recente do *libgdiplus* adicionando o repositório do mono ao seu sistema.</span><span class="sxs-lookup"><span data-stu-id="004d4-115">You can install a recent version of *libgdiplus* by adding the Mono repository to your system.</span></span> <span data-ttu-id="004d4-116">Para obter mais informações, consulte <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="004d4-116">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>
