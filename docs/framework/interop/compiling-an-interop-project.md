---
title: Compilando um projeto de interoperabilidade
ms.date: 03/30/2017
helpviewer_keywords:
- interoperation with unmanaged code, compiling
- COM interop, compiling
- exposing COM components to .NET Framework
- compiling interop projects
- interoperation with unmanaged code, exposing COM components
- COM interop, exposing COM components
ms.assetid: 6fcf6588-5e25-41af-b4ae-780974f2c3df
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5bc92eb9d4b7b0ae5db56303f3fbfa991c58e06a
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72523836"
---
# <a name="compiling-an-interop-project"></a><span data-ttu-id="97473-102">Compilando um projeto de interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="97473-102">Compiling an Interop Project</span></span>

<span data-ttu-id="97473-103">Os projetos de interoperabilidade COM que referenciam um ou mais assemblies que contêm tipos COM importados são compilados como qualquer outro projeto gerenciado.</span><span class="sxs-lookup"><span data-stu-id="97473-103">COM interop projects that reference one or more assemblies containing imported COM types are compiled like any other managed project.</span></span> <span data-ttu-id="97473-104">É possível referenciar assemblies de interoperabilidade em um ambiente de desenvolvimento como o Visual Studio ou referenciá-los ao usar um compilador de linha de comando.</span><span class="sxs-lookup"><span data-stu-id="97473-104">You can reference interop assemblies in a development environment such as Visual Studio, or you can reference them when you use a command-line compiler.</span></span> <span data-ttu-id="97473-105">Em ambos os casos, para ser compilado corretamente, o assembly de interoperabilidade deve estar no mesmo diretório dos outros arquivos de projeto.</span><span class="sxs-lookup"><span data-stu-id="97473-105">In either case, to compile properly, the interop assembly must be in the same directory as the other project files.</span></span>

 <span data-ttu-id="97473-106">Há duas maneiras de referenciar assemblies de interoperabilidade:</span><span class="sxs-lookup"><span data-stu-id="97473-106">There are two ways to reference interop assemblies:</span></span>

- <span data-ttu-id="97473-107">Tipos de interoperabilidade inseridos: a partir do .NET Framework 4 e do Visual Studio 2010, você pode instruir o compilador a inserir informações de tipo de um assembly de interoperabilidade em seu executável.</span><span class="sxs-lookup"><span data-stu-id="97473-107">Embedded interop types: Beginning with the .NET Framework 4 and Visual Studio 2010, you can instruct the compiler to embed type information from an interop assembly into your executable.</span></span> <span data-ttu-id="97473-108">Esta é a técnica recomendada.</span><span class="sxs-lookup"><span data-stu-id="97473-108">This is the recommended technique.</span></span>

- <span data-ttu-id="97473-109">Implantando assemblies de interoperabilidade: é possível criar uma referência padrão a um assembly de interoperabilidade.</span><span class="sxs-lookup"><span data-stu-id="97473-109">Deploying interop assemblies: You can create a standard reference to an interop assembly.</span></span> <span data-ttu-id="97473-110">Nesse caso, o assembly de interoperabilidade deve ser implantado com o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="97473-110">In this case, the interop assembly must be deployed with your application.</span></span>

 <span data-ttu-id="97473-111">As diferenças entre essas duas técnicas são abordadas mais detalhadamente em [Usando tipos COM em um código gerenciado](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="97473-111">The differences between these two techniques are discussed in greater detail in [Using COM Types in Managed Code](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100)).</span></span>

 <span data-ttu-id="97473-112">A incorporação de tipos de interoperabilidade com o Visual Studio é demonstrada em [instruções: incorporando tipos de assemblies gerenciados no Visual Studio](../../standard/assembly/embed-types-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="97473-112">Embedding interop types with Visual Studio is demonstrated in [Walkthrough: Embedding Types from Managed Assemblies in Visual Studio](../../standard/assembly/embed-types-visual-studio.md).</span></span>

 <span data-ttu-id="97473-113">Para fazer referência a um assembly de interoperabilidade com um compilador de linha de comando e inserir informações de tipo em seus executáveis, use a opção [-link (C# opções do compilador)](../../csharp/language-reference/compiler-options/link-compiler-option.md) ou o conjunto de compiladores [-link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) e especifique o nome do assembly de interoperabilidade.</span><span class="sxs-lookup"><span data-stu-id="97473-113">To reference an interop assembly with a command-line compiler and embed type information in your executables, use the [-link (C# Compiler Options)](../../csharp/language-reference/compiler-options/link-compiler-option.md) or the [-link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) compiler switch and specify the name of the interop assembly.</span></span>

> [!NOTE]
> <span data-ttu-id="97473-114">Os aplicativos do Visual C++ não podem inserir informações de tipo, mas podem interoperar com aplicativos ou suplementos que têm essa capacidade.</span><span class="sxs-lookup"><span data-stu-id="97473-114">Visual C++ applications cannot embed type information, but they can interoperate with applications or add-ins that do.</span></span>

 <span data-ttu-id="97473-115">Para compilar um aplicativo que inclui um assembly de interoperabilidade primário quando ele é implantado, use a opção do compilador **/reference** e especifique o nome do assembly de interoperabilidade.</span><span class="sxs-lookup"><span data-stu-id="97473-115">To compile an application that includes a primary interop assembly when it is deployed, use the **/reference** compiler switch and specify the name of the interop assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="97473-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="97473-116">See also</span></span>

- [<span data-ttu-id="97473-117">Expondo componentes do COM ao .NET Framework</span><span class="sxs-lookup"><span data-stu-id="97473-117">Exposing COM Components to the .NET Framework</span></span>](exposing-com-components.md)
- [<span data-ttu-id="97473-118">Componentes de independência de linguagem e componentes independentes da linguagem</span><span class="sxs-lookup"><span data-stu-id="97473-118">Language Independence and Language-Independent Components</span></span>](../../standard/language-independence-and-language-independent-components.md)
- <span data-ttu-id="97473-119">[Usando tipos COM no código gerenciado](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="97473-119">[Using COM Types in Managed Code](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))</span></span>
- [<span data-ttu-id="97473-120">Passo a passo: inserindo tipos de assemblies gerenciados no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="97473-120">Walkthrough: Embedding Types from Managed Assemblies in Visual Studio</span></span>](../../standard/assembly/embed-types-visual-studio.md)
- [<span data-ttu-id="97473-121">Importando uma biblioteca de tipos como um assembly</span><span class="sxs-lookup"><span data-stu-id="97473-121">Importing a Type Library as an Assembly</span></span>](importing-a-type-library-as-an-assembly.md)
