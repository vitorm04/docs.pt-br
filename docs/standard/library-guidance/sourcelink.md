---
title: SourceLink e bibliotecas do .NET
description: Recomendações de melhores práticas para usar o SourceLink para melhorar a depuração para bibliotecas do .NET.
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: 3bc72e158a5773b656095f9ce58b442469f91e67
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53128915"
---
# <a name="sourcelink"></a><span data-ttu-id="d697d-103">SourceLink</span><span class="sxs-lookup"><span data-stu-id="d697d-103">SourceLink</span></span>

<span data-ttu-id="d697d-104">O SourceLink é uma tecnologia que permite a depuração de código-fonte dos assemblies do .NET do NuGet por desenvolvedores.</span><span class="sxs-lookup"><span data-stu-id="d697d-104">SourceLink is a technology that enables source code debugging of .NET assemblies from NuGet by developers.</span></span> <span data-ttu-id="d697d-105">O SourceLink é executado ao criar o pacote do NuGet e insere os metadados de controle do código-fonte dentro de assemblies e do pacote.</span><span class="sxs-lookup"><span data-stu-id="d697d-105">SourceLink executes when creating the NuGet package and embeds source control metadata inside assemblies and the package.</span></span> <span data-ttu-id="d697d-106">Os desenvolvedores que baixam o pacote e têm o SourceLink habilitado no Visual Studio podem intervir em seu código-fonte.</span><span class="sxs-lookup"><span data-stu-id="d697d-106">Developers who download the package and have SourceLink enabled in Visual Studio can step into its source code.</span></span> <span data-ttu-id="d697d-107">O SourceLink fornece metadados de controle do código-fonte para criar uma ótima experiência de depuração.</span><span class="sxs-lookup"><span data-stu-id="d697d-107">SourceLink provides source control metadata to create a great debugging experience.</span></span>

## <a name="sourcelink-demo"></a><span data-ttu-id="d697d-108">Demonstração do SourceLink</span><span class="sxs-lookup"><span data-stu-id="d697d-108">SourceLink demo</span></span>

> [!VIDEO https://www.youtube.com/embed/gyRGhCQPkB4?start=61]

## <a name="using-sourcelink"></a><span data-ttu-id="d697d-109">Usando o SourceLink</span><span class="sxs-lookup"><span data-stu-id="d697d-109">Using SourceLink</span></span>

<span data-ttu-id="d697d-110">É possível encontrar instruções sobre como usar o SourceLink no repositório GitHub [dotnet/sourceLink](https://github.com/dotnet/sourcelink/blob/master/README.md).</span><span class="sxs-lookup"><span data-stu-id="d697d-110">Instructions for using SourceLink can be found on the [dotnet/sourceLink](https://github.com/dotnet/sourcelink/blob/master/README.md) GitHub repository.</span></span>

<span data-ttu-id="d697d-111">Você pode usar o [Explorador de Pacotes do NuGet](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) para confirmar que os metadados do SourceLink foram inseridos com êxito no pacote.</span><span class="sxs-lookup"><span data-stu-id="d697d-111">You can use [NuGet Package Explorer](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) to confirm that the SourceLink metadata has been successfully embedded in the package.</span></span> <span data-ttu-id="d697d-112">Verifique se os metadados `Repository` estão presentes com um identificador de comentário e se os arquivos .pdb estão localizados com o .dll de cada destino.</span><span class="sxs-lookup"><span data-stu-id="d697d-112">Check the `Repository` metadata is present with a comment identifier and that .pdb files are located with each target's .dll.</span></span>

<span data-ttu-id="d697d-113">![SourceLink no Explorador de Pacotes do NuGet](./media/sourcelink/nuget-package-explorer-sourcelink.png "SourceLink no Explorador de Pacotes do NuGet")</span><span class="sxs-lookup"><span data-stu-id="d697d-113">![SourceLink in NuGet Package Explorer](./media/sourcelink/nuget-package-explorer-sourcelink.png "SourceLink in NuGet Package Explorer")</span></span>

<span data-ttu-id="d697d-114">**✔️ CONSIDERE** usar o SourceLink para adicionar metadados de controle do código-fonte aos seus assemblies e pacotes do NuGet.</span><span class="sxs-lookup"><span data-stu-id="d697d-114">**✔️ CONSIDER** using SourceLink to add source control metadata to your assemblies and NuGet packages.</span></span>

> [!TIP]
> <span data-ttu-id="d697d-115">Você ainda pode aprimorar a experiência de depuração do desenvolvedor com a adição de atributos do depurador aos seus tipos.</span><span class="sxs-lookup"><span data-stu-id="d697d-115">You can further enhance a developer's debugging experience by adding debugger attributes to your types.</span></span>
> * <span data-ttu-id="d697d-116"><xref:System.Diagnostics.DebuggerDisplayAttribute> pode personalizar como uma classe ou campo é exibido nas janelas de variáveis do depurador.</span><span class="sxs-lookup"><span data-stu-id="d697d-116"><xref:System.Diagnostics.DebuggerDisplayAttribute> can customize how a class or field is displayed in the debugger variable windows.</span></span>
> * <span data-ttu-id="d697d-117"><xref:System.Diagnostics.DebuggerStepThroughAttribute> instrui o depurador a depurar o código em vez de intervir nele.</span><span class="sxs-lookup"><span data-stu-id="d697d-117"><xref:System.Diagnostics.DebuggerStepThroughAttribute> instructs the debugger to step through the code instead of stepping into the code.</span></span>
> * <span data-ttu-id="d697d-118"><xref:System.Diagnostics.DebuggerBrowsableAttribute> controla se um membro é exibido nas janelas de variáveis do depurador.</span><span class="sxs-lookup"><span data-stu-id="d697d-118"><xref:System.Diagnostics.DebuggerBrowsableAttribute> controls whether a member is displayed in the debugger variable windows.</span></span>

<span data-ttu-id="d697d-119">**✔️ CONSIDERE** incluir arquivos de símbolo (`*.pdb`) no pacote do NuGet.</span><span class="sxs-lookup"><span data-stu-id="d697d-119">**✔️ CONSIDER** including symbol files (`*.pdb`) in the NuGet package.</span></span>

> <span data-ttu-id="d697d-120">Normalmente, você poderia publicar arquivos de símbolo em um [pacote de símbolos](./nuget.md#symbol-packages).</span><span class="sxs-lookup"><span data-stu-id="d697d-120">Ordinarily, you'd publish symbol files in a [symbol package](./nuget.md#symbol-packages).</span></span> <span data-ttu-id="d697d-121">No momento, o principal host público para pacotes de símbolos não é compatível com os arquivos de símbolo portáteis (`*.pdb`) criados por projetos no estilo de SDK e os pacotes de símbolos não são úteis.</span><span class="sxs-lookup"><span data-stu-id="d697d-121">Currently the main public host for symbol packages doesn't support the portable symbol files (`*.pdb`) created by SDK-style projects, and symbol packages aren't useful.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="d697d-122">[Anterior](dependencies.md)
>[Próximo](publish-nuget-package.md)</span><span class="sxs-lookup"><span data-stu-id="d697d-122">[Previous](dependencies.md)
[Next](publish-nuget-package.md)</span></span>