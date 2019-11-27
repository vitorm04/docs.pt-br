---
title: Linhas de Comando de Compilação de Exemplo
ms.date: 03/13/2018
helpviewer_keywords:
- command line [Visual Basic], compilers
- compilation [Visual Basic], command-line
- command-line compilers
- compiling source code [Visual Basic], from command line
- Visual Basic compiler, sample command lines
ms.assetid: 5bfbb487-5f47-4267-969a-39dfb917beeb
ms.openlocfilehash: 27a20a5a3525353ffbced729b8ac9c98b3e48fc1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350848"
---
# <a name="sample-compilation-command-lines-visual-basic"></a><span data-ttu-id="e8e02-102">Linhas de comando de compilação de exemplo (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e8e02-102">Sample compilation command lines (Visual Basic)</span></span>

<span data-ttu-id="e8e02-103">Como alternativa à compilação de Visual Basic programas de dentro do Visual Studio, você pode compilar a partir da linha de comando para produzir arquivos executáveis (. exe) ou arquivos. dll (biblioteca de vínculo dinâmico).</span><span class="sxs-lookup"><span data-stu-id="e8e02-103">As an alternative to compiling Visual Basic programs from within Visual Studio, you can compile from the command line to produce executable (.exe) files or dynamic-link library (.dll) files.</span></span>

<span data-ttu-id="e8e02-104">O compilador de linha de comando Visual Basic dá suporte a um conjunto completo de opções que controlam arquivos de entrada e saída, assemblies e opções de depuração e pré-processador.</span><span class="sxs-lookup"><span data-stu-id="e8e02-104">The Visual Basic command-line compiler supports a complete set of options that control input and output files, assemblies, and debug and preprocessor options.</span></span> <span data-ttu-id="e8e02-105">Cada opção está disponível em duas formas intercambiáveis: `-option` e `/option`.</span><span class="sxs-lookup"><span data-stu-id="e8e02-105">Each option is available in two interchangeable forms: `-option` and `/option`.</span></span> <span data-ttu-id="e8e02-106">Esta documentação mostra apenas o formulário `-option`.</span><span class="sxs-lookup"><span data-stu-id="e8e02-106">This documentation shows only the `-option` form.</span></span>

<span data-ttu-id="e8e02-107">A tabela a seguir lista algumas linhas de comando de exemplo que você pode modificar para seu próprio uso.</span><span class="sxs-lookup"><span data-stu-id="e8e02-107">The following table lists some sample command lines you can modify for your own use.</span></span>

|<span data-ttu-id="e8e02-108">{1&gt;Para&lt;1}</span><span class="sxs-lookup"><span data-stu-id="e8e02-108">To</span></span>|<span data-ttu-id="e8e02-109">Uso</span><span class="sxs-lookup"><span data-stu-id="e8e02-109">Use</span></span>|
|--------|---------|
|<span data-ttu-id="e8e02-110">Compilar File. vb e criar arquivo. exe</span><span class="sxs-lookup"><span data-stu-id="e8e02-110">Compile File.vb and create File.exe</span></span>|`vbc -reference:Microsoft.VisualBasic.dll File.vb`|
|<span data-ttu-id="e8e02-111">Compilar File. vb e criar File. dll</span><span class="sxs-lookup"><span data-stu-id="e8e02-111">Compile File.vb and create File.dll</span></span>|`vbc -target:library File.vb`|
|<span data-ttu-id="e8e02-112">Compilar File. vb e criar My. exe</span><span class="sxs-lookup"><span data-stu-id="e8e02-112">Compile File.vb and create My.exe</span></span>|`vbc -out:My.exe File.vb`|
|<span data-ttu-id="e8e02-113">Compile File. vb e crie uma biblioteca e um assembly de referência chamado file. dll</span><span class="sxs-lookup"><span data-stu-id="e8e02-113">Compile File.vb and create both a library and a reference assembly named File.dll</span></span>|`vbc -target:library -ref:.\debug\bin\ref\file.dll File.vb`|
|<span data-ttu-id="e8e02-114">Compilar todos os arquivos de Visual Basic no diretório atual, com otimizações no e o símbolo de `DEBUG` definido, produzindo file2. exe</span><span class="sxs-lookup"><span data-stu-id="e8e02-114">Compile all Visual Basic files in the current directory, with optimizations on and the `DEBUG` symbol defined, producing File2.exe</span></span>|`vbc -define:DEBUG=1 -optimize -out:File2.exe *.vb`|
|<span data-ttu-id="e8e02-115">Compilar todos os arquivos de Visual Basic no diretório atual, produzindo uma versão de depuração de arquivo2. dll sem exibir o logotipo ou avisos</span><span class="sxs-lookup"><span data-stu-id="e8e02-115">Compile all Visual Basic files in the current directory, producing a debug version of File2.dll without displaying the logo or warnings</span></span>|`vbc -target:library -out:File2.dll -nowarn -nologo -debug *.vb`|
|<span data-ttu-id="e8e02-116">Compilar todos os arquivos de Visual Basic no diretório atual para algo. dll</span><span class="sxs-lookup"><span data-stu-id="e8e02-116">Compile all Visual Basic files in the current directory to Something.dll</span></span>|`vbc -target:library -out:Something.dll *.vb`|

> [!TIP]
> <span data-ttu-id="e8e02-117">Ao criar um projeto usando o IDE do Visual Studio, você pode exibir informações sobre o comando **Vbc** associado com suas opções de compilador na janela de saída.</span><span class="sxs-lookup"><span data-stu-id="e8e02-117">When you build a project by using the Visual Studio IDE, you can display information about the associated **vbc** command with its compiler options in the output window.</span></span> <span data-ttu-id="e8e02-118">Para exibir essas informações, abra a [caixa de diálogo opções, projetos e soluções, compile e execute](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run)e defina o **detalhamento de saída de compilação do projeto MSBuild** como **normal** ou um nível mais alto de detalhamento.</span><span class="sxs-lookup"><span data-stu-id="e8e02-118">To display this information, open the [Options Dialog Box,  Projects and Solutions, Build and Run](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run), and then set the **MSBuild project build output verbosity** to **Normal** or a higher level of verbosity.</span></span>

## <a name="see-also"></a><span data-ttu-id="e8e02-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e8e02-119">See also</span></span>

- [<span data-ttu-id="e8e02-120">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e8e02-120">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="e8e02-121">Compilação Condicional</span><span class="sxs-lookup"><span data-stu-id="e8e02-121">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
