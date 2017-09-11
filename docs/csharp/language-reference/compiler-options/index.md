---
title: "Opções do compilador de C#"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- cs.build.options
dev_langs:
- CSharp
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
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 02cfb7708959057de593506db55e4f31f5ab4fd0
ms.openlocfilehash: 7c5f5274a5685e50fb7f1d06771b0340200d1c3f
ms.contentlocale: pt-br
ms.lasthandoff: 08/28/2017

---
# <a name="c-compiler-options"></a><span data-ttu-id="77f5a-102">Opções do compilador de C#</span><span class="sxs-lookup"><span data-stu-id="77f5a-102">C# Compiler Options</span></span>
<span data-ttu-id="77f5a-103">O compilador produz arquivos executáveis (.exe), bibliotecas de vínculo dinâmico (.dll) ou módulos de código (.netmodule).</span><span class="sxs-lookup"><span data-stu-id="77f5a-103">The compiler produces executable (.exe) files, dynamic-link libraries (.dll), or code modules (.netmodule).</span></span>  
  
 <span data-ttu-id="77f5a-104">Todas as opções do compilador estão disponíveis em duas formas: **-option** e **/option**.</span><span class="sxs-lookup"><span data-stu-id="77f5a-104">Every compiler option is available in two forms: **-option** and **/option**.</span></span> <span data-ttu-id="77f5a-105">A documentação mostra apenas o formulário **/option**.</span><span class="sxs-lookup"><span data-stu-id="77f5a-105">The documentation only shows the **/option** form.</span></span>  
  
 <span data-ttu-id="77f5a-106">No Visual Web Developer 2008, você pode definir opções do compilador no arquivo web.config.</span><span class="sxs-lookup"><span data-stu-id="77f5a-106">In Visual Web Developer 2008, you set compiler options in the web.config file.</span></span> <span data-ttu-id="77f5a-107">Para obter mais informações, consulte [\<compilador> Elemento](https://msdn.microsoft.com/library/y9x69bzw).</span><span class="sxs-lookup"><span data-stu-id="77f5a-107">For more information, see [\<compiler> Element](https://msdn.microsoft.com/library/y9x69bzw).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="77f5a-108">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="77f5a-108">In This Section</span></span>  
 [<span data-ttu-id="77f5a-109">Build pela linha de comando com csc.exe</span><span class="sxs-lookup"><span data-stu-id="77f5a-109">Command-line Building With csc.exe</span></span>](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)  
 <span data-ttu-id="77f5a-110">Informações sobre como compilar um aplicativo do Visual em C# na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="77f5a-110">Information about building a Visual C# application from the command line.</span></span>  
  
 [<span data-ttu-id="77f5a-111">Como configurar variáveis de ambiente para a linha de comando do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="77f5a-111">How to: Set Environment Variables for the Visual Studio Command Line</span></span>](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md)  
 <span data-ttu-id="77f5a-112">Fornece etapas para executar vsvars32.bat para habilitar compilações de linha de comando.</span><span class="sxs-lookup"><span data-stu-id="77f5a-112">Provides steps for running vsvars32.bat  to enable command-line builds.</span></span>  
  
 [<span data-ttu-id="77f5a-113">Opções do compilador de C# listadas por categoria</span><span class="sxs-lookup"><span data-stu-id="77f5a-113">C# Compiler Options Listed by Category</span></span>](../../../csharp/language-reference/compiler-options/listed-by-category.md)  
 <span data-ttu-id="77f5a-114">Uma lista categórica de opções do compilador.</span><span class="sxs-lookup"><span data-stu-id="77f5a-114">A categorical listing of the compiler options.</span></span>  
  
 [<span data-ttu-id="77f5a-115">Opções do compilador de C# listadas em ordem alfabética</span><span class="sxs-lookup"><span data-stu-id="77f5a-115">C# Compiler Options Listed Alphabetically</span></span>](../../../csharp/language-reference/compiler-options/listed-alphabetically.md)  
 <span data-ttu-id="77f5a-116">Uma lista alfabética de opções do compilador.</span><span class="sxs-lookup"><span data-stu-id="77f5a-116">An alphabetical listing of the compiler options.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="77f5a-117">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="77f5a-117">Related Sections</span></span>  
 [<span data-ttu-id="77f5a-118">Página de build, Designer de Projeto</span><span class="sxs-lookup"><span data-stu-id="77f5a-118">Build Page, Project Designer</span></span>](/visualstudio/ide/reference/build-page-project-designer-csharp)  
 <span data-ttu-id="77f5a-119">Definindo propriedades que controlam como o projeto é compilado, criado e depurado.</span><span class="sxs-lookup"><span data-stu-id="77f5a-119">Setting properties that govern how your project is compiled, built, and debugged.</span></span> <span data-ttu-id="77f5a-120">Inclui informações sobre as etapas de build personalizadas em projetos do Visual em C#.</span><span class="sxs-lookup"><span data-stu-id="77f5a-120">Includes information about custom build steps in Visual C# projects.</span></span>  
  
 [<span data-ttu-id="77f5a-121">Compilações personalizadas e padrão</span><span class="sxs-lookup"><span data-stu-id="77f5a-121">Default and Custom Builds</span></span>](/visualstudio/ide/compiling-and-building-in-visual-studio)  
 <span data-ttu-id="77f5a-122">Informações sobre tipos de build e configurações.</span><span class="sxs-lookup"><span data-stu-id="77f5a-122">Information on build types and configurations.</span></span>  
  
 [<span data-ttu-id="77f5a-123">Preparando e gerenciando compilações</span><span class="sxs-lookup"><span data-stu-id="77f5a-123">Preparing and Managing Builds</span></span>](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio)  
 <span data-ttu-id="77f5a-124">Procedimentos para compilação dentro do ambiente de desenvolvimento do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="77f5a-124">Procedures for building within the Visual Studio development environment.</span></span>

