---
title: Opções do compilador de C#
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- cs.build.options
helpviewer_keywords:
- compiler options [C#]
- csc.exe
- cl.exe compiler, C# options
- Visual C# compiler
- Visual C#, compiler options
ms.assetid: d3403556-1816-4546-a782-e8223a772e44
caps.latest.revision: 21
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 59000f60acdc8ada11bc5abb9e91b5f53d42b9ae
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="c-compiler-options"></a><span data-ttu-id="ab4f0-102">Opções do compilador de C#</span><span class="sxs-lookup"><span data-stu-id="ab4f0-102">C# Compiler Options</span></span>
<span data-ttu-id="ab4f0-103">O compilador produz arquivos executáveis (.exe), bibliotecas de vínculo dinâmico (.dll) ou módulos de código (.netmodule).</span><span class="sxs-lookup"><span data-stu-id="ab4f0-103">The compiler produces executable (.exe) files, dynamic-link libraries (.dll), or code modules (.netmodule).</span></span>  
  
 <span data-ttu-id="ab4f0-104">Todas as opções do compilador estão disponíveis em duas formas: **-option** e **/option**.</span><span class="sxs-lookup"><span data-stu-id="ab4f0-104">Every compiler option is available in two forms: **-option** and **/option**.</span></span> <span data-ttu-id="ab4f0-105">A documentação mostra apenas o formulário **-option**.</span><span class="sxs-lookup"><span data-stu-id="ab4f0-105">The documentation only shows the **-option** form.</span></span>  
  
 <span data-ttu-id="ab4f0-106">No Visual Studio, é possível definir opções do compilador no arquivo web.config.</span><span class="sxs-lookup"><span data-stu-id="ab4f0-106">In Visual Studio, you set compiler options in the web.config file.</span></span> <span data-ttu-id="ab4f0-107">Para obter mais informações, consulte [\<compilador> Elemento](../../../framework/configure-apps/file-schema/compiler/compiler-element.md).</span><span class="sxs-lookup"><span data-stu-id="ab4f0-107">For more information, see [\<compiler> Element](../../../framework/configure-apps/file-schema/compiler/compiler-element.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ab4f0-108">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="ab4f0-108">In This Section</span></span>  
 [<span data-ttu-id="ab4f0-109">Build pela linha de comando com csc.exe</span><span class="sxs-lookup"><span data-stu-id="ab4f0-109">Command-line Building With csc.exe</span></span>](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)  
 <span data-ttu-id="ab4f0-110">Informações sobre como compilar um aplicativo do Visual em C# na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="ab4f0-110">Information about building a Visual C# application from the command line.</span></span>  
  
 [<span data-ttu-id="ab4f0-111">Como configurar variáveis de ambiente para a linha de comando do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ab4f0-111">How to: Set Environment Variables for the Visual Studio Command Line</span></span>](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md)  
 <span data-ttu-id="ab4f0-112">Fornece etapas para executar vsvars32.bat para habilitar compilações de linha de comando.</span><span class="sxs-lookup"><span data-stu-id="ab4f0-112">Provides steps for running vsvars32.bat  to enable command-line builds.</span></span>  
  
 [<span data-ttu-id="ab4f0-113">Opções do compilador de C# listadas por categoria</span><span class="sxs-lookup"><span data-stu-id="ab4f0-113">C# Compiler Options Listed by Category</span></span>](../../../csharp/language-reference/compiler-options/listed-by-category.md)  
 <span data-ttu-id="ab4f0-114">Uma lista categórica de opções do compilador.</span><span class="sxs-lookup"><span data-stu-id="ab4f0-114">A categorical listing of the compiler options.</span></span>  
  
 [<span data-ttu-id="ab4f0-115">Opções do compilador de C# listadas em ordem alfabética</span><span class="sxs-lookup"><span data-stu-id="ab4f0-115">C# Compiler Options Listed Alphabetically</span></span>](../../../csharp/language-reference/compiler-options/listed-alphabetically.md)  
 <span data-ttu-id="ab4f0-116">Uma lista alfabética de opções do compilador.</span><span class="sxs-lookup"><span data-stu-id="ab4f0-116">An alphabetical listing of the compiler options.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ab4f0-117">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="ab4f0-117">Related Sections</span></span>  
 [<span data-ttu-id="ab4f0-118">Página de build, Designer de Projeto</span><span class="sxs-lookup"><span data-stu-id="ab4f0-118">Build Page, Project Designer</span></span>](/visualstudio/ide/reference/build-page-project-designer-csharp)  
 <span data-ttu-id="ab4f0-119">Definindo propriedades que controlam como o projeto é compilado, criado e depurado.</span><span class="sxs-lookup"><span data-stu-id="ab4f0-119">Setting properties that govern how your project is compiled, built, and debugged.</span></span> <span data-ttu-id="ab4f0-120">Inclui informações sobre as etapas de build personalizadas em projetos do Visual em C#.</span><span class="sxs-lookup"><span data-stu-id="ab4f0-120">Includes information about custom build steps in Visual C# projects.</span></span>  
  
 [<span data-ttu-id="ab4f0-121">Compilações personalizadas e padrão</span><span class="sxs-lookup"><span data-stu-id="ab4f0-121">Default and Custom Builds</span></span>](/visualstudio/ide/compiling-and-building-in-visual-studio)  
 <span data-ttu-id="ab4f0-122">Informações sobre tipos de build e configurações.</span><span class="sxs-lookup"><span data-stu-id="ab4f0-122">Information on build types and configurations.</span></span>  
  
 [<span data-ttu-id="ab4f0-123">Preparando e gerenciando compilações</span><span class="sxs-lookup"><span data-stu-id="ab4f0-123">Preparing and Managing Builds</span></span>](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio)  
 <span data-ttu-id="ab4f0-124">Procedimentos para compilação dentro do ambiente de desenvolvimento do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ab4f0-124">Procedures for building within the Visual Studio development environment.</span></span>
