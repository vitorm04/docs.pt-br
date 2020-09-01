---
description: -langversion (opções do compilador C#)
title: -langversion (opções do compilador C#)
ms.date: 05/20/2020
f1_keywords:
- /langversion
helpviewer_keywords:
- /langversion compiler option [C#]
- -langversion compiler option [C#]
- langversion compiler option [C#]
ms.custom: updateeachrelease
ms.assetid: 3fb00b05-a0ff-4782-b313-13a4c0f62d94
ms.openlocfilehash: b0e966bcc87303c0a7c2199fbfac743b22481424
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125469"
---
# <a name="-langversion-c-compiler-options"></a><span data-ttu-id="91455-103">-langversion (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="91455-103">-langversion (C# Compiler Options)</span></span>

<span data-ttu-id="91455-104">Faz com que o compilador aceite somente a sintaxe incluída na especificação de linguagem C# escolhida.</span><span class="sxs-lookup"><span data-stu-id="91455-104">Causes the compiler to accept only syntax that is included in the chosen C# language specification.</span></span>

## <a name="syntax"></a><span data-ttu-id="91455-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="91455-105">Syntax</span></span>

```console
-langversion:option
```

## <a name="arguments"></a><span data-ttu-id="91455-106">Argumentos</span><span class="sxs-lookup"><span data-stu-id="91455-106">Arguments</span></span>

`option`

<span data-ttu-id="91455-107">Os seguintes valores são válidos:</span><span class="sxs-lookup"><span data-stu-id="91455-107">The following values are valid:</span></span>

[!INCLUDE [lang-versions-table](../includes/langversion-table.md)]

<span data-ttu-id="91455-108">A versão da linguagem padrão depende da estrutura de destino do aplicativo e da versão do SDK ou do Visual Studio instalado.</span><span class="sxs-lookup"><span data-stu-id="91455-108">The default language version depends on the target framework for your application and the version of the SDK or Visual Studio installed.</span></span> <span data-ttu-id="91455-109">Essas regras são definidas no artigo [Configurando a versão do idioma](../configure-language-version.md#defaults) .</span><span class="sxs-lookup"><span data-stu-id="91455-109">Those rules are defined in the [configuring the language version](../configure-language-version.md#defaults) article.</span></span>

## <a name="remarks"></a><span data-ttu-id="91455-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="91455-110">Remarks</span></span>

<span data-ttu-id="91455-111">Os metadados referenciados pelo seu aplicativo de C# não estão sujeitos à opção do compilador **-langversion**.</span><span class="sxs-lookup"><span data-stu-id="91455-111">Metadata referenced by your C# application is not subject to **-langversion** compiler option.</span></span>

<span data-ttu-id="91455-112">Como cada versão do compilador do C# contém extensões para a especificação de linguagem, **-langversion** não dá a funcionalidade equivalente de uma versão anterior do compilador.</span><span class="sxs-lookup"><span data-stu-id="91455-112">Because each version of the C# compiler contains extensions to the language specification, **-langversion** does not give you the equivalent functionality of an earlier version of the compiler.</span></span>

<span data-ttu-id="91455-113">Além disso, embora as atualizações de versão do C# geralmente coincidam com as versões principais do .NET Framework, a nova sintaxe e as funcionalidades não estão necessariamente vinculadas a essa versão de estrutura específica.</span><span class="sxs-lookup"><span data-stu-id="91455-113">Additionally, while C# version updates generally coincide with major .NET Framework releases, the new syntax and features are not necessarily tied to that specific framework version.</span></span> <span data-ttu-id="91455-114">Embora as novas funcionalidades definitivamente exijam uma nova atualização do compilador que também é liberada junto com a revisão do C#, cada funcionalidade específica tem seus próprios requisitos mínimos de API ou do Common Language Runtime do .NET que podem permitir que ela seja executada em estruturas de nível inferior com a inclusão de pacotes NuGet ou de outras bibliotecas.</span><span class="sxs-lookup"><span data-stu-id="91455-114">While the new features definitely require a new compiler update that is also released alongside the C# revision, each specific feature has its own minimum .NET API or common language runtime requirements that may allow it to run on downlevel frameworks by including NuGet packages or other libraries.</span></span>

<span data-ttu-id="91455-115">Independentemente da configuração **-langversion** que você usar, use a versão atual do Common Language Runtime para criar seu. exe ou. dll.</span><span class="sxs-lookup"><span data-stu-id="91455-115">Regardless of which **-langversion** setting you use, use the current version of the common language runtime to create your .exe or .dll.</span></span> <span data-ttu-id="91455-116">Uma exceção são os assemblies Friend e [-moduleassemblyname (opção de compilador C#)](./moduleassemblyname-compiler-option.md), que funcionam em **-langversion: ISO-1**.</span><span class="sxs-lookup"><span data-stu-id="91455-116">One exception is friend assemblies and [-moduleassemblyname (C# Compiler Option)](./moduleassemblyname-compiler-option.md), which work under **-langversion:ISO-1**.</span></span>

<span data-ttu-id="91455-117">Para outras maneiras de especificar a versão da linguagem C#, consulte o artigo [selecionar a versão da linguagem c#](../configure-language-version.md) .</span><span class="sxs-lookup"><span data-stu-id="91455-117">For other ways to specify the C# language version, see the [Select the C# language version](../configure-language-version.md) article.</span></span>

<span data-ttu-id="91455-118">Para saber mais sobre como definir essa opção do compilador programaticamente, veja <xref:VSLangProj80.CSharpProjectConfigurationProperties3.LanguageVersion%2A>.</span><span class="sxs-lookup"><span data-stu-id="91455-118">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.LanguageVersion%2A>.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="91455-119">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="91455-119">C# language specification</span></span>

| <span data-ttu-id="91455-120">Versão</span><span class="sxs-lookup"><span data-stu-id="91455-120">Version</span></span>          | <span data-ttu-id="91455-121">Link</span><span class="sxs-lookup"><span data-stu-id="91455-121">Link</span></span>                       | <span data-ttu-id="91455-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="91455-122">Description</span></span>                                                             |
|------------------|----------------------------|-------------------------------------------------------------------------|
| <span data-ttu-id="91455-123">C# 7.0 e posterior</span><span class="sxs-lookup"><span data-stu-id="91455-123">C# 7.0 and later</span></span> |                            | <span data-ttu-id="91455-124">Não disponível no momento</span><span class="sxs-lookup"><span data-stu-id="91455-124">Not currently available</span></span>                                                 |
| <span data-ttu-id="91455-125">C# 6.0</span><span class="sxs-lookup"><span data-stu-id="91455-125">C# 6.0</span></span>           | <span data-ttu-id="91455-126">[Link][csharp-6]</span><span class="sxs-lookup"><span data-stu-id="91455-126">[Link][csharp-6]</span></span>           | <span data-ttu-id="91455-127">Especificação da Linguagem C# Versão 6 – Rascunho não oficial: .NET Foundation</span><span class="sxs-lookup"><span data-stu-id="91455-127">C# Language Specification Version 6 - Unofficial Draft: .NET Foundation</span></span> |
| <span data-ttu-id="91455-128">C# 5.0</span><span class="sxs-lookup"><span data-stu-id="91455-128">C# 5.0</span></span>           | <span data-ttu-id="91455-129">[Baixar PDF][csharp-5]</span><span class="sxs-lookup"><span data-stu-id="91455-129">[Download PDF][csharp-5]</span></span>   | <span data-ttu-id="91455-130">Padrão ECMA-334 – 5ª Edição</span><span class="sxs-lookup"><span data-stu-id="91455-130">Standard ECMA-334 5th Edition</span></span>                                           |
| <span data-ttu-id="91455-131">C# 3.0</span><span class="sxs-lookup"><span data-stu-id="91455-131">C# 3.0</span></span>           | <span data-ttu-id="91455-132">[Baixar DOC][csharp-3]</span><span class="sxs-lookup"><span data-stu-id="91455-132">[Download DOC][csharp-3]</span></span>   | <span data-ttu-id="91455-133">Especificação da Linguagem C# Versão 3.0: Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="91455-133">C# Language Specification Version 3.0: Microsoft Corporation</span></span>            |
| <span data-ttu-id="91455-134">C# 2.0</span><span class="sxs-lookup"><span data-stu-id="91455-134">C# 2.0</span></span>           | <span data-ttu-id="91455-135">[Baixar PDF][csharp-2]</span><span class="sxs-lookup"><span data-stu-id="91455-135">[Download PDF][csharp-2]</span></span>   | <span data-ttu-id="91455-136">Padrão ECMA-334 – 4ª Edição</span><span class="sxs-lookup"><span data-stu-id="91455-136">Standard ECMA-334 4th Edition</span></span>                                           |
| <span data-ttu-id="91455-137">C# 1.2</span><span class="sxs-lookup"><span data-stu-id="91455-137">C# 1.2</span></span>           | <span data-ttu-id="91455-138">[Baixar DOC][csharp-1.2]</span><span class="sxs-lookup"><span data-stu-id="91455-138">[Download DOC][csharp-1.2]</span></span> | <span data-ttu-id="91455-139">Especificação da Linguagem C# Versão 1.2: Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="91455-139">C# Language Specification Version 1.2: Microsoft Corporation</span></span>            |
| <span data-ttu-id="91455-140">C# 1.0</span><span class="sxs-lookup"><span data-stu-id="91455-140">C# 1.0</span></span>           | <span data-ttu-id="91455-141">[Baixar DOC][csharp-1]</span><span class="sxs-lookup"><span data-stu-id="91455-141">[Download DOC][csharp-1]</span></span>   | <span data-ttu-id="91455-142">Especificação da Linguagem C# Versão 1.0: Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="91455-142">C# Language Specification Version 1.0: Microsoft Corporation</span></span>            |

[csharp-6]: /dotnet/csharp/language-reference/language-specification/introduction
[csharp-5]: https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-334.pdf
[csharp-3]: https://download.microsoft.com/download/3/8/8/388e7205-bc10-4226-b2a8-75351c669b09/CSharp%20Language%20Specification.doc
[csharp-2]: https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%204th%20edition%20June%202006.pdf
[csharp-1.2]: https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%202nd%20edition%20December%202002.pdf
[csharp-1]: https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%201st%20edition%20December%202001.pdf

## <a name="minimum-sdk-version-needed-to-support-all-language-features"></a><span data-ttu-id="91455-143">Versão mínima do SDK necessária para dar suporte a todos os recursos de idioma</span><span class="sxs-lookup"><span data-stu-id="91455-143">Minimum SDK version needed to support all language features</span></span>

<span data-ttu-id="91455-144">A tabela a seguir lista as versões mínimas do SDK com o compilador C# que dá suporte à versão de idioma correspondente:</span><span class="sxs-lookup"><span data-stu-id="91455-144">The following table lists the minimum versions of the SDK with the C# compiler that supports the corresponding language version:</span></span>

| <span data-ttu-id="91455-145">Versão do C#</span><span class="sxs-lookup"><span data-stu-id="91455-145">C# version</span></span> | <span data-ttu-id="91455-146">Versão mínima do SDK</span><span class="sxs-lookup"><span data-stu-id="91455-146">Minimum SDK version</span></span>                                                                  |
|------------|--------------------------------------------------------------------------------------|
| <span data-ttu-id="91455-147">C# 8.0</span><span class="sxs-lookup"><span data-stu-id="91455-147">C# 8.0</span></span>     | <span data-ttu-id="91455-148">Ferramentas de Microsoft Visual Studio/Build 2019, versão 16,3 ou SDK do .NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="91455-148">Microsoft Visual Studio/Build Tools 2019, version 16.3, or .NET Core 3.0 SDK</span></span>         |
| <span data-ttu-id="91455-149">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="91455-149">C# 7.3</span></span>     | <span data-ttu-id="91455-150">Microsoft Visual Studio/Ferramentas de Build 2017, versão 15.7</span><span class="sxs-lookup"><span data-stu-id="91455-150">Microsoft Visual Studio/Build Tools 2017, version 15.7</span></span>                               |
| <span data-ttu-id="91455-151">C# 7.2</span><span class="sxs-lookup"><span data-stu-id="91455-151">C# 7.2</span></span>     | <span data-ttu-id="91455-152">Microsoft Visual Studio/Ferramentas de Build 2017, versão 15.5</span><span class="sxs-lookup"><span data-stu-id="91455-152">Microsoft Visual Studio/Build Tools 2017, version 15.5</span></span>                               |
| <span data-ttu-id="91455-153">C# 7.1</span><span class="sxs-lookup"><span data-stu-id="91455-153">C# 7.1</span></span>     | <span data-ttu-id="91455-154">Microsoft Visual Studio/Ferramentas de Build 2017, versão 15.3</span><span class="sxs-lookup"><span data-stu-id="91455-154">Microsoft Visual Studio/Build Tools 2017, version 15.3</span></span>                               |
| <span data-ttu-id="91455-155">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="91455-155">C# 7.0</span></span>     | <span data-ttu-id="91455-156">Microsoft Visual Studio/Ferramentas de Build 2017</span><span class="sxs-lookup"><span data-stu-id="91455-156">Microsoft Visual Studio/Build Tools 2017</span></span>                                             |
| <span data-ttu-id="91455-157">C# 6</span><span class="sxs-lookup"><span data-stu-id="91455-157">C# 6</span></span>       | <span data-ttu-id="91455-158">Microsoft Visual Studio/Ferramentas de Build 2015</span><span class="sxs-lookup"><span data-stu-id="91455-158">Microsoft Visual Studio/Build Tools 2015</span></span>                                             |
| <span data-ttu-id="91455-159">C# 5</span><span class="sxs-lookup"><span data-stu-id="91455-159">C# 5</span></span>       | <span data-ttu-id="91455-160">Microsoft Visual Studio/Ferramentas de Build 2012 ou compilador do .NET Framework 4.5 em pacote</span><span class="sxs-lookup"><span data-stu-id="91455-160">Microsoft Visual Studio/Build Tools 2012 or bundled .NET Framework 4.5 compiler</span></span>      |
| <span data-ttu-id="91455-161">C# 4</span><span class="sxs-lookup"><span data-stu-id="91455-161">C# 4</span></span>       | <span data-ttu-id="91455-162">Microsoft Visual Studio/Ferramentas de Build 2010 ou compilador do .NET Framework 4.0 em pacote</span><span class="sxs-lookup"><span data-stu-id="91455-162">Microsoft Visual Studio/Build Tools 2010 or bundled .NET Framework 4.0 compiler</span></span>      |
| <span data-ttu-id="91455-163">C# 3</span><span class="sxs-lookup"><span data-stu-id="91455-163">C# 3</span></span>       | <span data-ttu-id="91455-164">Microsoft Visual Studio/Ferramentas de Build 2008 ou compilador do .NET Framework 3.5 em pacote</span><span class="sxs-lookup"><span data-stu-id="91455-164">Microsoft Visual Studio/Build Tools 2008 or bundled .NET Framework 3.5 compiler</span></span>      |
| <span data-ttu-id="91455-165">C# 2</span><span class="sxs-lookup"><span data-stu-id="91455-165">C# 2</span></span>       | <span data-ttu-id="91455-166">Microsoft Visual Studio/Ferramentas de Build 2005 ou compilador do .NET Framework 2.0 em pacote</span><span class="sxs-lookup"><span data-stu-id="91455-166">Microsoft Visual Studio/Build Tools 2005 or bundled .NET Framework 2.0 compiler</span></span>      |
| <span data-ttu-id="91455-167">C# 1.0/1.2</span><span class="sxs-lookup"><span data-stu-id="91455-167">C# 1.0/1.2</span></span> | <span data-ttu-id="91455-168">Compilador de ferramentas Microsoft Visual Studio/Build .NET 2002 ou pacotes .NET Framework 1,0 em pacote</span><span class="sxs-lookup"><span data-stu-id="91455-168">Microsoft Visual Studio/Build Tools .NET 2002 or bundled .NET Framework 1.0 compiler</span></span> |

## <a name="see-also"></a><span data-ttu-id="91455-169">Confira também</span><span class="sxs-lookup"><span data-stu-id="91455-169">See also</span></span>

- [<span data-ttu-id="91455-170">Opções do compilador C#</span><span class="sxs-lookup"><span data-stu-id="91455-170">C# Compiler Options</span></span>](index.md)
- [<span data-ttu-id="91455-171">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="91455-171">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
