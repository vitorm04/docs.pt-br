---
title: "Como gerenciar versões de dependência de pacote para o .NET Core 1.0"
description: "Saiba mais sobre o gerenciamento de versão de dependência de pacote para seus aplicativos e bibliotecas do .NET Core."
keywords: .NET, .NET Core
author: cartermp
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 4424a947-bdf9-4775-8d48-dc350a4e0aee
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 7f31aeb3c07a75059a4f8cd9392dcea31eb5bf41
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---

# <a name="how-to-manage-package-dependency-versions-for-net-core-10"></a><span data-ttu-id="5c92d-104">Como gerenciar versões de dependência de pacote para o .NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="5c92d-104">How to Manage Package Dependency Versions for .NET Core 1.0</span></span>

<span data-ttu-id="5c92d-105">Esse artigo aborda o que você precisa saber sobre as versões do pacote para seus aplicativos e bibliotecas .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5c92d-105">This article covers what you need to know about package versions for your .NET Core libraries and apps.</span></span>

## <a name="glossary"></a><span data-ttu-id="5c92d-106">Glossário</span><span class="sxs-lookup"><span data-stu-id="5c92d-106">Glossary</span></span>

<span data-ttu-id="5c92d-107">**Corrigir** – Corrigir as dependências significa que você está usando a mesma “família” de pacotes lançados em NuGet para .NET Core 1.0.</span><span class="sxs-lookup"><span data-stu-id="5c92d-107">**Fix** - Fixing dependencies means you are using the same "family" of packages released on NuGet for .NET Core 1.0.</span></span>

<span data-ttu-id="5c92d-108">**Metapacote** – Um pacote NuGet que representa um conjunto de pacotes NuGet.</span><span class="sxs-lookup"><span data-stu-id="5c92d-108">**Metapackage** - A NuGet package that represents a set of NuGet packages.</span></span>

<span data-ttu-id="5c92d-109">**Cortar** – O ato de remover de um metapacote os pacotes dos quais você não.</span><span class="sxs-lookup"><span data-stu-id="5c92d-109">**Trimming** - The act of removing the packages you do not depend on from a metapackage.</span></span>  <span data-ttu-id="5c92d-110">Isso é algo relevante para autores de pacotes NuGet.</span><span class="sxs-lookup"><span data-stu-id="5c92d-110">This is something relevant for NuGet package authors.</span></span>  <span data-ttu-id="5c92d-111">Consulte [Reduzindo as dependências de pacote com o project.json](../deploying/reducing-dependencies.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="5c92d-111">See [Reducing Package Dependencies with project.json](../deploying/reducing-dependencies.md) for more information.</span></span> 

## <a name="fix-your-dependencies-to-net-core-10"></a><span data-ttu-id="5c92d-112">Corrija suas dependências para o .NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="5c92d-112">Fix your dependencies to .NET Core 1.0</span></span>

<span data-ttu-id="5c92d-113">Para restaurar os pacotes de forma confiável e escrever código com segurança, é importante que você corrija suas dependências para as versões de pacotes enviados juntamente com o .NET Core 1.0.</span><span class="sxs-lookup"><span data-stu-id="5c92d-113">To reliably restore packages and write reliable code, it's important that you fix your dependencies to the versions of packages shipping alongside .NET Core 1.0.</span></span>  <span data-ttu-id="5c92d-114">Isso significa que todos os pacotes devem ter uma única versão sem nenhum qualificador adicional.</span><span class="sxs-lookup"><span data-stu-id="5c92d-114">This means every package should have a single version with no additional qualifiers.</span></span>

<span data-ttu-id="5c92d-115">**Exemplos de pacotes corrigidos para 1.0**</span><span class="sxs-lookup"><span data-stu-id="5c92d-115">**Examples of packages fixed to 1.0**</span></span>

`"System.Collections":"4.0.11"`

`"NETStandard.Library":"1.6.0"`

`"Microsoft.NETCore.App":"1.0.0"`

<span data-ttu-id="5c92d-116">**Exemplos de pacotes NÃO corrigidos para 1.0**</span><span class="sxs-lookup"><span data-stu-id="5c92d-116">**Examples of packages that are NOT fixed to 1.0**</span></span>

`"Microsoft.NETCore.App":"1.0.0-rc4-00454-00"`

`"System.Net.Http":"4.1.0-*"`

`"System.Text.RegularExpressions":"4.0.10-rc3-24021-00"`

### <a name="why-does-this-matter"></a><span data-ttu-id="5c92d-117">Por que isso importa?</span><span class="sxs-lookup"><span data-stu-id="5c92d-117">Why does this matter?</span></span>

<span data-ttu-id="5c92d-118">Asseguramos que, se você corrigir suas dependências para aquelas fornecidas junto com o .NET Core 1.0, os pacotes sempre funcionarão juntos.</span><span class="sxs-lookup"><span data-stu-id="5c92d-118">We guarantee that if you fixed your dependencies to what ships alongside .NET Core 1.0, those packages will all work together.</span></span>  <span data-ttu-id="5c92d-119">Essa garantia não existe se você usar pacotes que não são corrigidos dessa maneira.</span><span class="sxs-lookup"><span data-stu-id="5c92d-119">There is no such guarantee if you use packages which aren't fixed in this way.</span></span>

### <a name="scenarios"></a><span data-ttu-id="5c92d-120">Cenários</span><span class="sxs-lookup"><span data-stu-id="5c92d-120">Scenarios</span></span>

<span data-ttu-id="5c92d-121">Embora haja uma grande lista de todos os pacotes e suas versões lançadas com o .NET Core 1.0, você pode não precisar examiná-la se seu código estiver em determinados cenários.</span><span class="sxs-lookup"><span data-stu-id="5c92d-121">Although there is a big list of all packages and their versions released with .NET Core 1.0, you may not have to look through it if your code falls under certain scenarios.</span></span>

<span data-ttu-id="5c92d-122">**Você tem somente dependências de** `NETStandard.Library`**?**</span><span class="sxs-lookup"><span data-stu-id="5c92d-122">**Are you depending only on** `NETStandard.Library`**?**</span></span>

<span data-ttu-id="5c92d-123">Se assim, você deve corrigir o pacote `NETStandard.Library` para a versão `1.6`.</span><span class="sxs-lookup"><span data-stu-id="5c92d-123">If so, you should fixed your `NETStandard.Library` package to version `1.6`.</span></span>  <span data-ttu-id="5c92d-124">Como esse é um metapacote auxiliar, o fechamento do seu pacote também é corrigido para 1.0.</span><span class="sxs-lookup"><span data-stu-id="5c92d-124">Because this is a curated metapackage, its package closure is also fixed to 1.0.</span></span>

<span data-ttu-id="5c92d-125">**Você tem somente dependências de** `Microsoft.NETCore.App`**?**</span><span class="sxs-lookup"><span data-stu-id="5c92d-125">**Are you depending only on** `Microsoft.NETCore.App`**?**</span></span>

<span data-ttu-id="5c92d-126">Se assim, você deve corrigir o pacote `Microsoft.NETCore.App` para a versão `1.0.0`.</span><span class="sxs-lookup"><span data-stu-id="5c92d-126">If so, you should fixed your `Microsoft.NETCore.App` package to version `1.0.0`.</span></span>  <span data-ttu-id="5c92d-127">Como esse é um metapacote auxiliar, o fechamento do seu pacote também é corrigido para 1.0.</span><span class="sxs-lookup"><span data-stu-id="5c92d-127">Because this is a curated metapackage, its package closure is also fixed to 1.0.</span></span>

<span data-ttu-id="5c92d-128">**Você está [cortando](../deploying/reducing-dependencies.md) as dependências do seu metapacote**  `NETStandard.Library` **ou** `Microsoft.NETCore.App` **?**</span><span class="sxs-lookup"><span data-stu-id="5c92d-128">**Are you [trimming](../deploying/reducing-dependencies.md) your** `NETStandard.Library` **or** `Microsoft.NETCore.App` **metapackage dependencies?**</span></span>

<span data-ttu-id="5c92d-129">Nesse caso, você deve garantir que o metapacote de início seja corrigido para 1.0.</span><span class="sxs-lookup"><span data-stu-id="5c92d-129">If so, you should ensure that the metapackage you start with is fixed to 1.0.</span></span>  <span data-ttu-id="5c92d-130">Os pacotes individuais dos quais você depende após o corte também são corrigidos para 1.0.</span><span class="sxs-lookup"><span data-stu-id="5c92d-130">The individual packages you depend on after trimming are also fixed to 1.0.</span></span>

<span data-ttu-id="5c92d-131">**Você tem dependências de pacotes fora dos metapacotes** `NETStandard.Library` **ou** `Microsoft.NETCore.App` **?**</span><span class="sxs-lookup"><span data-stu-id="5c92d-131">**Are you depending on packages outside the** `NETStandard.Library` **or** `Microsoft.NETCore.App` **metapackages?**</span></span>

<span data-ttu-id="5c92d-132">Nesse caso, você precisa corrigir suas outras dependências para 1.0.</span><span class="sxs-lookup"><span data-stu-id="5c92d-132">If so, you need to fix your other dependencies to 1.0.</span></span>  <span data-ttu-id="5c92d-133">Consulte as versões do pacote correto e números de build no fim desse artigo.</span><span class="sxs-lookup"><span data-stu-id="5c92d-133">See the correct package versions and build numbers at the end of this article.</span></span>

### <a name="a-note-on-using-a-splat-string--when-versioning"></a><span data-ttu-id="5c92d-134">Uma observação sobre o uso de uma cadeia de caracteres splat (\*) durante o controle de versão</span><span class="sxs-lookup"><span data-stu-id="5c92d-134">A note on using a splat string (\*) when versioning</span></span>

<span data-ttu-id="5c92d-135">Você pode ter adotado um padrão de controle de versão que usa uma cadeia de caracteres splat (\*) como esta: `"System.Collections":"4.0.11-*"`.</span><span class="sxs-lookup"><span data-stu-id="5c92d-135">You may have adopted a versioning pattern which uses a splat (\*) string like this: `"System.Collections":"4.0.11-*"`.</span></span>

<span data-ttu-id="5c92d-136">**Você não deve fazer isso**.</span><span class="sxs-lookup"><span data-stu-id="5c92d-136">**You should not do this**.</span></span>  <span data-ttu-id="5c92d-137">Usar a cadeia de caracteres splat pode resultar na restauração de pacotes de diferentes versões, algumas muito mais avançadas que o .NET Core 1.0.</span><span class="sxs-lookup"><span data-stu-id="5c92d-137">Using the splat string could result in restoring packages from different builds, some of which may be further along than .NET Core 1.0.</span></span>  <span data-ttu-id="5c92d-138">Isso poderia deixar alguns pacotes incompatíveis.</span><span class="sxs-lookup"><span data-stu-id="5c92d-138">This could then result in some packages being incompatible.</span></span>

## <a name="packages-and-version-numbers-organized-by-metapackage"></a><span data-ttu-id="5c92d-139">Pacotes e os Números de Versão organizados por Metapacote</span><span class="sxs-lookup"><span data-stu-id="5c92d-139">Packages and Version Numbers organized by Metapackage</span></span>

<span data-ttu-id="5c92d-140">[Lista de todos os pacotes do .NET Standard e suas versões para 1.0](https://github.com/dotnet/versions/blob/master/build-info/dotnet/corefx/release/1.0.0/Latest_Packages.txt).</span><span class="sxs-lookup"><span data-stu-id="5c92d-140">[List of all .NET Standard packages and their versions for 1.0](https://github.com/dotnet/versions/blob/master/build-info/dotnet/corefx/release/1.0.0/Latest_Packages.txt).</span></span>

<span data-ttu-id="5c92d-141">[Lista de todos os pacotes de tempo de execução e suas versões para 1.0](https://github.com/dotnet/versions/blob/master/build-info/dotnet/coreclr/release/1.0.0/LKG_Packages.txt).</span><span class="sxs-lookup"><span data-stu-id="5c92d-141">[List of all runtime packages and their versions for 1.0](https://github.com/dotnet/versions/blob/master/build-info/dotnet/coreclr/release/1.0.0/LKG_Packages.txt).</span></span>

<span data-ttu-id="5c92d-142">[Lista de todos os pacotes de aplicativo do .NET Core e suas versões para 1.0](https://github.com/dotnet/versions/blob/master/build-info/dotnet/core-setup/release/1.0.0/Latest_Packages.txt).</span><span class="sxs-lookup"><span data-stu-id="5c92d-142">[List of all .NET Core application packages and their versions for 1.0](https://github.com/dotnet/versions/blob/master/build-info/dotnet/core-setup/release/1.0.0/Latest_Packages.txt).</span></span>

