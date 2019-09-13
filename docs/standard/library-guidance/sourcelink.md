---
title: Source Link e bibliotecas .NET
description: Recomendações de melhores práticas de uso do Source Link para melhorar a depuração de bibliotecas .NET.
author: jamesnk
ms.author: mairaw
ms.date: 01/15/2019
ms.openlocfilehash: 7530c984ce4bbe9e40362bd550bec57ac585a550
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928986"
---
# <a name="source-link"></a><span data-ttu-id="405ac-103">Source Link</span><span class="sxs-lookup"><span data-stu-id="405ac-103">Source Link</span></span>

<span data-ttu-id="405ac-104">O Source Link é uma tecnologia que permite a depuração de código-fonte dos assemblies .NET do NuGet por desenvolvedores.</span><span class="sxs-lookup"><span data-stu-id="405ac-104">Source Link is a technology that enables source code debugging of .NET assemblies from NuGet by developers.</span></span> <span data-ttu-id="405ac-105">O Source Link é executado durante a criação do pacote NuGet e insere os metadados de controle do código-fonte nos assemblies e no pacote.</span><span class="sxs-lookup"><span data-stu-id="405ac-105">Source Link executes when creating the NuGet package and embeds source control metadata inside assemblies and the package.</span></span> <span data-ttu-id="405ac-106">Os desenvolvedores que baixam o pacote e têm o Source Link habilitado no Visual Studio podem intervir no código-fonte.</span><span class="sxs-lookup"><span data-stu-id="405ac-106">Developers who download the package and have Source Link enabled in Visual Studio can step into its source code.</span></span> <span data-ttu-id="405ac-107">O Source Link fornece metadados de controle do código-fonte para criar uma ótima experiência de depuração.</span><span class="sxs-lookup"><span data-stu-id="405ac-107">Source Link provides source control metadata to create a great debugging experience.</span></span>

## <a name="source-link-demo"></a><span data-ttu-id="405ac-108">Demonstração do Source Link</span><span class="sxs-lookup"><span data-stu-id="405ac-108">Source Link demo</span></span>

> [!VIDEO https://www.youtube.com/embed/gyRGhCQPkB4?start=61]

## <a name="using-source-link"></a><span data-ttu-id="405ac-109">Usando o Source Link</span><span class="sxs-lookup"><span data-stu-id="405ac-109">Using Source Link</span></span>

<span data-ttu-id="405ac-110">Encontre instruções sobre como usar o Source Link no repositório GitHub [dotnet/sourcelink](https://github.com/dotnet/sourcelink/blob/master/README.md).</span><span class="sxs-lookup"><span data-stu-id="405ac-110">Instructions for using Source Link can be found on the [dotnet/sourcelink](https://github.com/dotnet/sourcelink/blob/master/README.md) GitHub repository.</span></span>

<span data-ttu-id="405ac-111">Use o [Explorador de Pacotes NuGet](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) para confirmar que os metadados do Source Link foram inseridos com êxito no pacote.</span><span class="sxs-lookup"><span data-stu-id="405ac-111">You can use [NuGet Package Explorer](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) to confirm that the Source Link metadata has been successfully embedded in the package.</span></span> <span data-ttu-id="405ac-112">Verifique se os metadados `Repository` estão presentes com um identificador de comentário e se os arquivos .pdb estão localizados com o .dll de cada destino.</span><span class="sxs-lookup"><span data-stu-id="405ac-112">Check the `Repository` metadata is present with a comment identifier and that .pdb files are located with each target's .dll.</span></span>

<span data-ttu-id="405ac-113">![Source Link no Explorador de Pacotes NuGet](./media/sourcelink/nuget-package-explorer-sourcelink.png "Source Link in NuGet Package Explorer")</span><span class="sxs-lookup"><span data-stu-id="405ac-113">![Source Link in NuGet Package Explorer](./media/sourcelink/nuget-package-explorer-sourcelink.png "Source Link in NuGet Package Explorer")</span></span>

<span data-ttu-id="405ac-114">**✔️ CONSIDERE** o uso do Source Link para adicionar metadados de controle do código-fonte aos assemblies e pacotes NuGet.</span><span class="sxs-lookup"><span data-stu-id="405ac-114">**✔️ CONSIDER** using Source Link to add source control metadata to your assemblies and NuGet packages.</span></span>

> [!TIP]
> <span data-ttu-id="405ac-115">Você ainda pode aprimorar a experiência de depuração do desenvolvedor com a adição de atributos do depurador aos seus tipos.</span><span class="sxs-lookup"><span data-stu-id="405ac-115">You can further enhance a developer's debugging experience by adding debugger attributes to your types.</span></span>
>
> * <span data-ttu-id="405ac-116"><xref:System.Diagnostics.DebuggerDisplayAttribute> pode personalizar como uma classe ou campo é exibido nas janelas de variáveis do depurador.</span><span class="sxs-lookup"><span data-stu-id="405ac-116"><xref:System.Diagnostics.DebuggerDisplayAttribute> can customize how a class or field is displayed in the debugger variable windows.</span></span>
> * <span data-ttu-id="405ac-117"><xref:System.Diagnostics.DebuggerStepThroughAttribute> instrui o depurador a depurar o código em vez de intervir nele.</span><span class="sxs-lookup"><span data-stu-id="405ac-117"><xref:System.Diagnostics.DebuggerStepThroughAttribute> instructs the debugger to step through the code instead of stepping into the code.</span></span>
> * <span data-ttu-id="405ac-118"><xref:System.Diagnostics.DebuggerBrowsableAttribute> controla se um membro é exibido nas janelas de variáveis do depurador.</span><span class="sxs-lookup"><span data-stu-id="405ac-118"><xref:System.Diagnostics.DebuggerBrowsableAttribute> controls whether a member is displayed in the debugger variable windows.</span></span>

<span data-ttu-id="405ac-119">**✔️ CONSIDERE** publicar arquivos de símbolo (`*.pdb`).</span><span class="sxs-lookup"><span data-stu-id="405ac-119">**✔️ CONSIDER** publishing symbol files (`*.pdb`).</span></span>

> <span data-ttu-id="405ac-120">Para proporcionar a melhor experiência de depuração, a biblioteca deverá publicar arquivos de símbolo, além de usar o Source Link.</span><span class="sxs-lookup"><span data-stu-id="405ac-120">For the best debugging experience your library should publish symbol files as well as use Source Link.</span></span> <span data-ttu-id="405ac-121">Para obter mais informações sobre arquivos de símbolo e pacotes de símbolos, confira [Pacotes de símbolos](./nuget.md#symbol-packages).</span><span class="sxs-lookup"><span data-stu-id="405ac-121">For more information about symbol files and symbol packages, see [Symbol packages](./nuget.md#symbol-packages).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="405ac-122">[Anterior](dependencies.md)
>[Próximo](publish-nuget-package.md)</span><span class="sxs-lookup"><span data-stu-id="405ac-122">[Previous](dependencies.md)
[Next](publish-nuget-package.md)</span></span>
