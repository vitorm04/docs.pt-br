---
description: Opções do compilador de C#
title: Opções do compilador de C#
ms.date: 07/20/2015
f1_keywords:
- cs.build.options
helpviewer_keywords:
- compiler options [C#]
- csc.exe
- cl.exe compiler, C# options
- Visual C# compiler
- Visual C#, compiler options
ms.assetid: d3403556-1816-4546-a782-e8223a772e44
ms.openlocfilehash: bcb246055ecb553bbefad2a0d5c95bf6a083ee6f
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125521"
---
# <a name="c-compiler-options"></a><span data-ttu-id="7d038-103">Opções do compilador de C#</span><span class="sxs-lookup"><span data-stu-id="7d038-103">C# Compiler Options</span></span>

<span data-ttu-id="7d038-104">O compilador produz arquivos executáveis (.exe), bibliotecas de vínculo dinâmico (.dll) ou módulos de código (.netmodule).</span><span class="sxs-lookup"><span data-stu-id="7d038-104">The compiler produces executable (.exe) files, dynamic-link libraries (.dll), or code modules (.netmodule).</span></span>

<span data-ttu-id="7d038-105">Todas as opções do compilador estão disponíveis em duas formas: **-option** e **/option**.</span><span class="sxs-lookup"><span data-stu-id="7d038-105">Every compiler option is available in two forms: **-option** and **/option**.</span></span> <span data-ttu-id="7d038-106">A documentação mostra apenas o formulário **-option**.</span><span class="sxs-lookup"><span data-stu-id="7d038-106">The documentation only shows the **-option** form.</span></span>

<span data-ttu-id="7d038-107">No Visual Studio, você define as opções do compilador no arquivo *web.config* .</span><span class="sxs-lookup"><span data-stu-id="7d038-107">In Visual Studio, you set compiler options in the *web.config* file.</span></span> <span data-ttu-id="7d038-108">Para obter mais informações, consulte [ \<compiler> elemento](../../../framework/configure-apps/file-schema/compiler/compiler-element.md).</span><span class="sxs-lookup"><span data-stu-id="7d038-108">For more information, see [\<compiler> Element](../../../framework/configure-apps/file-schema/compiler/compiler-element.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="7d038-109">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="7d038-109">In this section</span></span>

- <span data-ttu-id="7d038-110">[Criação de linha de comando com csc.exe](command-line-building-with-csc-exe.md) Informações sobre como criar um aplicativo Visual C# na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="7d038-110">[Command-line Building With csc.exe](command-line-building-with-csc-exe.md) Information about building a Visual C# application from the command line.</span></span>

- <span data-ttu-id="7d038-111">[Como definir variáveis de ambiente para a linha de comando do Visual Studio](how-to-set-environment-variables-for-the-visual-studio-command-line.md) Fornece as etapas para executar o *vsvars32.bat* para habilitar as compilações de linha de comando.</span><span class="sxs-lookup"><span data-stu-id="7d038-111">[How to set environment variables for the Visual Studio Command Line](how-to-set-environment-variables-for-the-visual-studio-command-line.md) Provides steps for running *vsvars32.bat* to enable command-line builds.</span></span>

- <span data-ttu-id="7d038-112">[Opções do compilador C# listadas por categoria](listed-by-category.md) Uma listagem categórica das opções do compilador.</span><span class="sxs-lookup"><span data-stu-id="7d038-112">[C# Compiler Options Listed by Category](listed-by-category.md) A categorical listing of the compiler options.</span></span>

- <span data-ttu-id="7d038-113">[Opções do compilador C# listadas em ordem alfabética](listed-alphabetically.md) Uma listagem alfabética das opções do compilador.</span><span class="sxs-lookup"><span data-stu-id="7d038-113">[C# Compiler Options Listed Alphabetically](listed-alphabetically.md) An alphabetical listing of the compiler options.</span></span>

## <a name="related-sections"></a><span data-ttu-id="7d038-114">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="7d038-114">Related sections</span></span>

- <span data-ttu-id="7d038-115">[Página de compilação, designer de projeto](/visualstudio/ide/reference/build-page-project-designer-csharp) Definir propriedades que regem como o projeto é compilado, compilado e depurado.</span><span class="sxs-lookup"><span data-stu-id="7d038-115">[Build Page, Project Designer](/visualstudio/ide/reference/build-page-project-designer-csharp) Setting properties that govern how your project is compiled, built, and debugged.</span></span> <span data-ttu-id="7d038-116">Inclui informações sobre as etapas de build personalizadas em projetos do Visual em C#.</span><span class="sxs-lookup"><span data-stu-id="7d038-116">Includes information about custom build steps in Visual C# projects.</span></span>

- <span data-ttu-id="7d038-117">[Compilações padrão e personalizadas](/visualstudio/ide/compiling-and-building-in-visual-studio) Informações sobre tipos de compilação e configurações.</span><span class="sxs-lookup"><span data-stu-id="7d038-117">[Default and Custom Builds](/visualstudio/ide/compiling-and-building-in-visual-studio) Information on build types and configurations.</span></span>

- <span data-ttu-id="7d038-118">[Preparando e gerenciando compilações](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio) Procedimentos para a criação dentro do ambiente de desenvolvimento do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7d038-118">[Preparing and Managing Builds](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio) Procedures for building within the Visual Studio development environment.</span></span>
