---
title: -langversion (opções do compilador C#)
ms.date: 05/20/2020
f1_keywords:
- /langversion
helpviewer_keywords:
- /langversion compiler option [C#]
- -langversion compiler option [C#]
- langversion compiler option [C#]
ms.assetid: 3fb00b05-a0ff-4782-b313-13a4c0f62d94
ms.openlocfilehash: 408b2fb1f19f872db675321601ebc1b0c921044b
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83802949"
---
# <a name="-langversion-c-compiler-options"></a><span data-ttu-id="5bb5b-102">-langversion (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="5bb5b-102">-langversion (C# Compiler Options)</span></span>

<span data-ttu-id="5bb5b-103">Faz com que o compilador aceite somente a sintaxe incluída na especificação de linguagem C# escolhida.</span><span class="sxs-lookup"><span data-stu-id="5bb5b-103">Causes the compiler to accept only syntax that is included in the chosen C# language specification.</span></span>

## <a name="syntax"></a><span data-ttu-id="5bb5b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5bb5b-104">Syntax</span></span>

```console
-langversion:option
```

## <a name="arguments"></a><span data-ttu-id="5bb5b-105">Argumentos</span><span class="sxs-lookup"><span data-stu-id="5bb5b-105">Arguments</span></span>

`option`

<span data-ttu-id="5bb5b-106">Os seguintes valores são válidos:</span><span class="sxs-lookup"><span data-stu-id="5bb5b-106">The following values are valid:</span></span>

[!INCLUDE [lang-versions-table](../includes/langversion-table.md)]

<span data-ttu-id="5bb5b-107">A versão da linguagem padrão depende da estrutura de destino do aplicativo e da versão do SDK ou do Visual Studio instalado.</span><span class="sxs-lookup"><span data-stu-id="5bb5b-107">The default language version depends on the target framework for your application and the version of the SDK or Visual Studio installed.</span></span> <span data-ttu-id="5bb5b-108">Essas regras são definidas no artigo [Configurando a versão do idioma](../configure-language-version.md#defaults) .</span><span class="sxs-lookup"><span data-stu-id="5bb5b-108">Those rules are defined in the [configuring the language version](../configure-language-version.md#defaults) article.</span></span>

## <a name="remarks"></a><span data-ttu-id="5bb5b-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="5bb5b-109">Remarks</span></span>

<span data-ttu-id="5bb5b-110">Os metadados referenciados pelo seu aplicativo de C# não estão sujeitos à opção do compilador **-langversion**.</span><span class="sxs-lookup"><span data-stu-id="5bb5b-110">Metadata referenced by your C# application is not subject to **-langversion** compiler option.</span></span>

<span data-ttu-id="5bb5b-111">Como cada versão do compilador do C# contém extensões para a especificação de linguagem, **-langversion** não dá a funcionalidade equivalente de uma versão anterior do compilador.</span><span class="sxs-lookup"><span data-stu-id="5bb5b-111">Because each version of the C# compiler contains extensions to the language specification, **-langversion** does not give you the equivalent functionality of an earlier version of the compiler.</span></span>

<span data-ttu-id="5bb5b-112">Além disso, embora as atualizações de versão do C# geralmente coincidam com as versões principais do .NET Framework, a nova sintaxe e as funcionalidades não estão necessariamente vinculadas a essa versão de estrutura específica.</span><span class="sxs-lookup"><span data-stu-id="5bb5b-112">Additionally, while C# version updates generally coincide with major .NET Framework releases, the new syntax and features are not necessarily tied to that specific framework version.</span></span> <span data-ttu-id="5bb5b-113">Embora as novas funcionalidades definitivamente exijam uma nova atualização do compilador que também é liberada junto com a revisão do C#, cada funcionalidade específica tem seus próprios requisitos mínimos de API ou do Common Language Runtime do .NET que podem permitir que ela seja executada em estruturas de nível inferior com a inclusão de pacotes NuGet ou de outras bibliotecas.</span><span class="sxs-lookup"><span data-stu-id="5bb5b-113">While the new features definitely require a new compiler update that is also released alongside the C# revision, each specific feature has its own minimum .NET API or common language runtime requirements that may allow it to run on downlevel frameworks by including NuGet packages or other libraries.</span></span>

<span data-ttu-id="5bb5b-114">Independentemente da configuração **-langversion** que você usar, use a versão atual do Common Language Runtime para criar seu. exe ou. dll.</span><span class="sxs-lookup"><span data-stu-id="5bb5b-114">Regardless of which **-langversion** setting you use, use the current version of the common language runtime to create your .exe or .dll.</span></span> <span data-ttu-id="5bb5b-115">Uma exceção são os assemblies Friend e [-moduleassemblyname (opção de compilador C#)](./moduleassemblyname-compiler-option.md), que funcionam em **-langversion: ISO-1**.</span><span class="sxs-lookup"><span data-stu-id="5bb5b-115">One exception is friend assemblies and [-moduleassemblyname (C# Compiler Option)](./moduleassemblyname-compiler-option.md), which work under **-langversion:ISO-1**.</span></span>

<span data-ttu-id="5bb5b-116">Para outras maneiras de especificar a versão da linguagem C#, consulte o artigo [selecionar a versão da linguagem c#](../configure-language-version.md) .</span><span class="sxs-lookup"><span data-stu-id="5bb5b-116">For other ways to specify the C# language version, see the [Select the C# language version](../configure-language-version.md) article.</span></span>

<span data-ttu-id="5bb5b-117">Para saber mais sobre como definir essa opção do compilador programaticamente, veja <xref:VSLangProj80.CSharpProjectConfigurationProperties3.LanguageVersion%2A>.</span><span class="sxs-lookup"><span data-stu-id="5bb5b-117">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.LanguageVersion%2A>.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="5bb5b-118">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="5bb5b-118">C# language specification</span></span>

| <span data-ttu-id="5bb5b-119">Versão</span><span class="sxs-lookup"><span data-stu-id="5bb5b-119">Version</span></span>          | <span data-ttu-id="5bb5b-120">Link</span><span class="sxs-lookup"><span data-stu-id="5bb5b-120">Link</span></span>                       | <span data-ttu-id="5bb5b-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="5bb5b-121">Description</span></span>                                                             |
|------------------|----------------------------|-------------------------------------------------------------------------|
| <span data-ttu-id="5bb5b-122">C# 7.0 e posterior</span><span class="sxs-lookup"><span data-stu-id="5bb5b-122">C# 7.0 and later</span></span> |                            | <span data-ttu-id="5bb5b-123">Não disponível no momento</span><span class="sxs-lookup"><span data-stu-id="5bb5b-123">Not currently available</span></span>                                                 |
| <span data-ttu-id="5bb5b-124">C# 6.0</span><span class="sxs-lookup"><span data-stu-id="5bb5b-124">C# 6.0</span></span>           | <span data-ttu-id="5bb5b-125">[Link][csharp-6]</span><span class="sxs-lookup"><span data-stu-id="5bb5b-125">[Link][csharp-6]</span></span>           | <span data-ttu-id="5bb5b-126">Especificação da Linguagem C# Versão 6 – Rascunho não oficial: .NET Foundation</span><span class="sxs-lookup"><span data-stu-id="5bb5b-126">C# Language Specification Version 6 - Unofficial Draft: .NET Foundation</span></span> |
| <span data-ttu-id="5bb5b-127">C# 5.0</span><span class="sxs-lookup"><span data-stu-id="5bb5b-127">C# 5.0</span></span>           | <span data-ttu-id="5bb5b-128">[Baixar PDF][csharp-5]</span><span class="sxs-lookup"><span data-stu-id="5bb5b-128">[Download PDF][csharp-5]</span></span>   | <span data-ttu-id="5bb5b-129">Padrão ECMA-334 – 5ª Edição</span><span class="sxs-lookup"><span data-stu-id="5bb5b-129">Standard ECMA-334 5th Edition</span></span>                                           |
| <span data-ttu-id="5bb5b-130">C# 3.0</span><span class="sxs-lookup"><span data-stu-id="5bb5b-130">C# 3.0</span></span>           | <span data-ttu-id="5bb5b-131">[Baixar DOC][csharp-3]</span><span class="sxs-lookup"><span data-stu-id="5bb5b-131">[Download DOC][csharp-3]</span></span>   | <span data-ttu-id="5bb5b-132">Especificação da Linguagem C# Versão 3.0: Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="5bb5b-132">C# Language Specification Version 3.0: Microsoft Corporation</span></span>            |
| <span data-ttu-id="5bb5b-133">C# 2.0</span><span class="sxs-lookup"><span data-stu-id="5bb5b-133">C# 2.0</span></span>           | <span data-ttu-id="5bb5b-134">[Baixar PDF][csharp-2]</span><span class="sxs-lookup"><span data-stu-id="5bb5b-134">[Download PDF][csharp-2]</span></span>   | <span data-ttu-id="5bb5b-135">Padrão ECMA-334 – 4ª Edição</span><span class="sxs-lookup"><span data-stu-id="5bb5b-135">Standard ECMA-334 4th Edition</span></span>                                           |
| <span data-ttu-id="5bb5b-136">C# 1.2</span><span class="sxs-lookup"><span data-stu-id="5bb5b-136">C# 1.2</span></span>           | <span data-ttu-id="5bb5b-137">[Baixar DOC][csharp-1.2]</span><span class="sxs-lookup"><span data-stu-id="5bb5b-137">[Download DOC][csharp-1.2]</span></span> | <span data-ttu-id="5bb5b-138">Especificação da Linguagem C# Versão 1.2: Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="5bb5b-138">C# Language Specification Version 1.2: Microsoft Corporation</span></span>            |
| <span data-ttu-id="5bb5b-139">C# 1.0</span><span class="sxs-lookup"><span data-stu-id="5bb5b-139">C# 1.0</span></span>           | <span data-ttu-id="5bb5b-140">[Baixar DOC][csharp-1]</span><span class="sxs-lookup"><span data-stu-id="5bb5b-140">[Download DOC][csharp-1]</span></span>   | <span data-ttu-id="5bb5b-141">Especificação da Linguagem C# Versão 1.0: Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="5bb5b-141">C# Language Specification Version 1.0: Microsoft Corporation</span></span>            |

[csharp-6]: /dotnet/csharp/language-reference/language-specification/introduction
[csharp-5]: https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-334.pdf
[csharp-3]: https://download.microsoft.com/download/3/8/8/388e7205-bc10-4226-b2a8-75351c669b09/CSharp%20Language%20Specification.doc
[csharp-2]: https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%204th%20edition%20June%202006.pdf
[csharp-1.2]: https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%202nd%20edition%20December%202002.pdf
[csharp-1]: https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%201st%20edition%20December%202001.pdf

## <a name="minimum-sdk-version-needed-to-support-all-language-features"></a><span data-ttu-id="5bb5b-142">Versão mínima do SDK necessária para dar suporte a todos os recursos de idioma</span><span class="sxs-lookup"><span data-stu-id="5bb5b-142">Minimum SDK version needed to support all language features</span></span>

<span data-ttu-id="5bb5b-143">A tabela a seguir lista as versões mínimas do SDK com o compilador C# que dá suporte à versão de idioma correspondente:</span><span class="sxs-lookup"><span data-stu-id="5bb5b-143">The following table lists the minimum versions of the SDK with the C# compiler that supports the corresponding language version:</span></span>

| <span data-ttu-id="5bb5b-144">Versão do C#</span><span class="sxs-lookup"><span data-stu-id="5bb5b-144">C# version</span></span> | <span data-ttu-id="5bb5b-145">Versão mínima do SDK</span><span class="sxs-lookup"><span data-stu-id="5bb5b-145">Minimum SDK version</span></span>                                                                  |
|------------|--------------------------------------------------------------------------------------|
| <span data-ttu-id="5bb5b-146">C# 8.0</span><span class="sxs-lookup"><span data-stu-id="5bb5b-146">C# 8.0</span></span>     | <span data-ttu-id="5bb5b-147">Ferramentas de Microsoft Visual Studio/Build 2019, versão 16,3 ou SDK do .NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="5bb5b-147">Microsoft Visual Studio/Build Tools 2019, version 16.3, or .NET Core 3.0 SDK</span></span>         |
| <span data-ttu-id="5bb5b-148">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="5bb5b-148">C# 7.3</span></span>     | <span data-ttu-id="5bb5b-149">Microsoft Visual Studio/Ferramentas de Build 2017, versão 15.7</span><span class="sxs-lookup"><span data-stu-id="5bb5b-149">Microsoft Visual Studio/Build Tools 2017, version 15.7</span></span>                               |
| <span data-ttu-id="5bb5b-150">C# 7.2</span><span class="sxs-lookup"><span data-stu-id="5bb5b-150">C# 7.2</span></span>     | <span data-ttu-id="5bb5b-151">Microsoft Visual Studio/Ferramentas de Build 2017, versão 15.5</span><span class="sxs-lookup"><span data-stu-id="5bb5b-151">Microsoft Visual Studio/Build Tools 2017, version 15.5</span></span>                               |
| <span data-ttu-id="5bb5b-152">C# 7.1</span><span class="sxs-lookup"><span data-stu-id="5bb5b-152">C# 7.1</span></span>     | <span data-ttu-id="5bb5b-153">Microsoft Visual Studio/Ferramentas de Build 2017, versão 15.3</span><span class="sxs-lookup"><span data-stu-id="5bb5b-153">Microsoft Visual Studio/Build Tools 2017, version 15.3</span></span>                               |
| <span data-ttu-id="5bb5b-154">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="5bb5b-154">C# 7.0</span></span>     | <span data-ttu-id="5bb5b-155">Microsoft Visual Studio/Ferramentas de Build 2017</span><span class="sxs-lookup"><span data-stu-id="5bb5b-155">Microsoft Visual Studio/Build Tools 2017</span></span>                                             |
| <span data-ttu-id="5bb5b-156">C# 6</span><span class="sxs-lookup"><span data-stu-id="5bb5b-156">C# 6</span></span>       | <span data-ttu-id="5bb5b-157">Microsoft Visual Studio/Ferramentas de Build 2015</span><span class="sxs-lookup"><span data-stu-id="5bb5b-157">Microsoft Visual Studio/Build Tools 2015</span></span>                                             |
| <span data-ttu-id="5bb5b-158">C# 5</span><span class="sxs-lookup"><span data-stu-id="5bb5b-158">C# 5</span></span>       | <span data-ttu-id="5bb5b-159">Microsoft Visual Studio/Ferramentas de Build 2012 ou compilador do .NET Framework 4.5 em pacote</span><span class="sxs-lookup"><span data-stu-id="5bb5b-159">Microsoft Visual Studio/Build Tools 2012 or bundled .NET Framework 4.5 compiler</span></span>      |
| <span data-ttu-id="5bb5b-160">C# 4</span><span class="sxs-lookup"><span data-stu-id="5bb5b-160">C# 4</span></span>       | <span data-ttu-id="5bb5b-161">Microsoft Visual Studio/Ferramentas de Build 2010 ou compilador do .NET Framework 4.0 em pacote</span><span class="sxs-lookup"><span data-stu-id="5bb5b-161">Microsoft Visual Studio/Build Tools 2010 or bundled .NET Framework 4.0 compiler</span></span>      |
| <span data-ttu-id="5bb5b-162">C# 3</span><span class="sxs-lookup"><span data-stu-id="5bb5b-162">C# 3</span></span>       | <span data-ttu-id="5bb5b-163">Microsoft Visual Studio/Ferramentas de Build 2008 ou compilador do .NET Framework 3.5 em pacote</span><span class="sxs-lookup"><span data-stu-id="5bb5b-163">Microsoft Visual Studio/Build Tools 2008 or bundled .NET Framework 3.5 compiler</span></span>      |
| <span data-ttu-id="5bb5b-164">C# 2</span><span class="sxs-lookup"><span data-stu-id="5bb5b-164">C# 2</span></span>       | <span data-ttu-id="5bb5b-165">Microsoft Visual Studio/Ferramentas de Build 2005 ou compilador do .NET Framework 2.0 em pacote</span><span class="sxs-lookup"><span data-stu-id="5bb5b-165">Microsoft Visual Studio/Build Tools 2005 or bundled .NET Framework 2.0 compiler</span></span>      |
| <span data-ttu-id="5bb5b-166">C# 1.0/1.2</span><span class="sxs-lookup"><span data-stu-id="5bb5b-166">C# 1.0/1.2</span></span> | <span data-ttu-id="5bb5b-167">Compilador de ferramentas Microsoft Visual Studio/Build .NET 2002 ou pacotes .NET Framework 1,0 em pacote</span><span class="sxs-lookup"><span data-stu-id="5bb5b-167">Microsoft Visual Studio/Build Tools .NET 2002 or bundled .NET Framework 1.0 compiler</span></span> |

## <a name="see-also"></a><span data-ttu-id="5bb5b-168">Confira também</span><span class="sxs-lookup"><span data-stu-id="5bb5b-168">See also</span></span>

- [<span data-ttu-id="5bb5b-169">Opções do compilador C#</span><span class="sxs-lookup"><span data-stu-id="5bb5b-169">C# Compiler Options</span></span>](index.md)
- [<span data-ttu-id="5bb5b-170">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="5bb5b-170">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
