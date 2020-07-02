---
ms.openlocfilehash: 3d8179c5c0e84f8ff1197cce7790c80a5f5a4f6d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619437"
---

<span data-ttu-id="e1183-101">Quando você instala o com um Gerenciador de pacotes, essas bibliotecas são instaladas para você.</span><span class="sxs-lookup"><span data-stu-id="e1183-101">When you install with a package manager, these libraries are installed for you.</span></span> <span data-ttu-id="e1183-102">Mas, se você instalar manualmente o .NET Core ou publicar um aplicativo independente, precisará verificar se essas bibliotecas estão instaladas:</span><span class="sxs-lookup"><span data-stu-id="e1183-102">But, if you manually install .NET Core or you publish a self-contained app, you'll need to make sure these libraries are installed:</span></span>

- <span data-ttu-id="e1183-103">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="e1183-103">krb5-libs</span></span>
- <span data-ttu-id="e1183-104">libicu</span><span class="sxs-lookup"><span data-stu-id="e1183-104">libicu</span></span>
- <span data-ttu-id="e1183-105">openssl-libs</span><span class="sxs-lookup"><span data-stu-id="e1183-105">openssl-libs</span></span>

<span data-ttu-id="e1183-106">Se a versão do OpenSSL do ambiente de tempo de execução de destino for 1,1 ou mais recente, você precisará instalar o **compat-openssl10**.</span><span class="sxs-lookup"><span data-stu-id="e1183-106">If the target runtime environment's OpenSSL version is 1.1 or newer, you'll need to install **compat-openssl10**.</span></span>

<span data-ttu-id="e1183-107">Para obter mais informações sobre as dependências, consulte [aplicativos do Linux autocontidos](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span><span class="sxs-lookup"><span data-stu-id="e1183-107">For more information about the dependencies, see [Self-contained Linux apps](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

<span data-ttu-id="e1183-108">Para aplicativos .NET Core que usam o assembly *System. Drawing. Common* , você também precisará da seguinte dependência:</span><span class="sxs-lookup"><span data-stu-id="e1183-108">For .NET Core apps that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

- [<span data-ttu-id="e1183-109">libgdiplus (versão 6.0.1 ou posterior)</span><span class="sxs-lookup"><span data-stu-id="e1183-109">libgdiplus (version 6.0.1 or later)</span></span>](https://www.mono-project.com/docs/gui/libgdiplus/)

  > [!WARNING]
  > <span data-ttu-id="e1183-110">Você pode instalar uma versão recente do *libgdiplus* adicionando o repositório do mono ao seu sistema.</span><span class="sxs-lookup"><span data-stu-id="e1183-110">You can install a recent version of *libgdiplus* by adding the Mono repository to your system.</span></span> <span data-ttu-id="e1183-111">Para obter mais informações, consulte <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="e1183-111">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>
