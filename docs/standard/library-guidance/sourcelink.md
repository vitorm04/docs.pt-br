---
title: Bibliotecas SourceLink e .NET
description: Práticas recomendadas para usar SourceLink para melhorar a depuração para bibliotecas do .NET.
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: fa4af47eaa5dd1510640c2bf0ebb2187b56efae0
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49369675"
---
# <a name="sourcelink"></a><span data-ttu-id="2cf61-103">SourceLink</span><span class="sxs-lookup"><span data-stu-id="2cf61-103">SourceLink</span></span>

<span data-ttu-id="2cf61-104">SourceLink é uma tecnologia que permite a depuração de código fonte dos assemblies do .NET do NuGet por desenvolvedores.</span><span class="sxs-lookup"><span data-stu-id="2cf61-104">SourceLink is a technology that enables source code debugging of .NET assemblies from NuGet by developers.</span></span> <span data-ttu-id="2cf61-105">SourceLink executa ao criar o pacote do NuGet e insere os metadados de controle do código-fonte dentro de módulos (assemblies) e o pacote.</span><span class="sxs-lookup"><span data-stu-id="2cf61-105">SourceLink executes when creating the NuGet package and embeds source control metadata inside assemblies and the package.</span></span> <span data-ttu-id="2cf61-106">Os desenvolvedores que baixar o pacote e tem SourceLink habilitado no Visual Studio podem entrar em seu código-fonte.</span><span class="sxs-lookup"><span data-stu-id="2cf61-106">Developers who download the package and have SourceLink enabled in Visual Studio can step into its source code.</span></span> <span data-ttu-id="2cf61-107">SourceLink fornece metadados de controle do código-fonte para criar uma ótima experiência de depuração.</span><span class="sxs-lookup"><span data-stu-id="2cf61-107">SourceLink provides source control metadata to create a great debugging experience.</span></span>

## <a name="sourcelink-demo"></a><span data-ttu-id="2cf61-108">Demonstração de SourceLink</span><span class="sxs-lookup"><span data-stu-id="2cf61-108">SourceLink demo</span></span>

> [!VIDEO https://www.youtube.com/embed/gyRGhCQPkB4?start=61]

## <a name="using-sourcelink"></a><span data-ttu-id="2cf61-109">Usando SourceLink</span><span class="sxs-lookup"><span data-stu-id="2cf61-109">Using SourceLink</span></span>

<span data-ttu-id="2cf61-110">Instruções sobre como usar SourceLink pode ser encontrado na [dotnet/sourceLink](https://github.com/dotnet/sourcelink/blob/master/README.md) repositório do GitHub.</span><span class="sxs-lookup"><span data-stu-id="2cf61-110">Instructions for using SourceLink can be found on the [dotnet/sourceLink](https://github.com/dotnet/sourcelink/blob/master/README.md) GitHub repository.</span></span>

<span data-ttu-id="2cf61-111">Você pode usar [Explorador de pacotes NuGet](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) para confirmar que os metadados de SourceLink foi inserido com êxito no pacote.</span><span class="sxs-lookup"><span data-stu-id="2cf61-111">You can use [NuGet Package Explorer](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) to confirm that the SourceLink metadata has been successfully embedded in the package.</span></span> <span data-ttu-id="2cf61-112">Verifique o `Repository` metadados estão presente com um identificador de comentário e arquivos. PDB estão localizados com. dll de cada nome de destino.</span><span class="sxs-lookup"><span data-stu-id="2cf61-112">Check the `Repository` metadata is present with a comment identifier and that .pdb files are located with each target's .dll.</span></span>

<span data-ttu-id="2cf61-113">![SourceLink no Explorador de pacotes do NuGet](./media/sourcelink/nuget-package-explorer-sourcelink.png "SourceLink no Explorador de pacotes do NuGet")</span><span class="sxs-lookup"><span data-stu-id="2cf61-113">![SourceLink in NuGet Package Explorer](./media/sourcelink/nuget-package-explorer-sourcelink.png "SourceLink in NuGet Package Explorer")</span></span>

<span data-ttu-id="2cf61-114">**Considere a possibilidade de ✔️** usando SourceLink para adicionar metadados de controle do código-fonte para seus assemblies e o pacote do NuGet.</span><span class="sxs-lookup"><span data-stu-id="2cf61-114">**✔️ CONSIDER** using SourceLink to add source control metadata to your assemblies and NuGet package.</span></span>

<span data-ttu-id="2cf61-115">**Considere a possibilidade de ✔️** incluindo arquivos PDB no pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="2cf61-115">**✔️ CONSIDER** including PDB files in the NuGet package.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="2cf61-116">[Anterior](./dependencies.md)
[Próximo](./publish-nuget-package.md)</span><span class="sxs-lookup"><span data-stu-id="2cf61-116">[Previous](./dependencies.md)
[Next](./publish-nuget-package.md)</span></span>
