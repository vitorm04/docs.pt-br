---
title: Controle de versão da linguagem C# – Guia de C#
description: Saiba mais como a versão da linguagem C# é determinada com base em seu projeto e os diferentes valores para os quais você pode ajustá-la manualmente.
ms.date: 07/10/2019
ms.openlocfilehash: e35fdf2bcdb1a31b752c760f3f6df59232e498a4
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68236092"
---
# <a name="c-language-versioning"></a><span data-ttu-id="1d996-103">Controle de versão da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="1d996-103">C# language versioning</span></span>

<span data-ttu-id="1d996-104">O compilador C# determina uma versão da linguagem padrão com base na estrutura de destino ou nas estruturas de seu projeto.</span><span class="sxs-lookup"><span data-stu-id="1d996-104">The C# compiler determines a default language version based on your project's target framework or frameworks.</span></span> <span data-ttu-id="1d996-105">Isso ocorre porque a linguagem C# pode ter recursos que dependem de tipos ou de componentes de tempo de execução que não estão disponíveis em todas as implementações do .NET.</span><span class="sxs-lookup"><span data-stu-id="1d996-105">This is because the C# language may have features that rely on types or runtime components that are not available in every .NET implementation.</span></span> <span data-ttu-id="1d996-106">Com isso, independentemente do destino no qual seu projeto é criado, você obtém a versão da linguagem mais compatível por padrão.</span><span class="sxs-lookup"><span data-stu-id="1d996-106">This also ensures that for whatever target your project is built against, you get the highest compatible language version by default.</span></span>

## <a name="defaults"></a><span data-ttu-id="1d996-107">Padrão</span><span class="sxs-lookup"><span data-stu-id="1d996-107">Defaults</span></span>

<span data-ttu-id="1d996-108">O compilador determina um padrão com base nestas regras:</span><span class="sxs-lookup"><span data-stu-id="1d996-108">The compiler determines a default based on these rules:</span></span>

|<span data-ttu-id="1d996-109">Estrutura de destino</span><span class="sxs-lookup"><span data-stu-id="1d996-109">Target framework</span></span>|<span data-ttu-id="1d996-110">version</span><span class="sxs-lookup"><span data-stu-id="1d996-110">version</span></span>|<span data-ttu-id="1d996-111">Padrão da versão da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="1d996-111">C# language version default</span></span>|
|----------------|-------|---------------------------|
|<span data-ttu-id="1d996-112">.NET Core</span><span class="sxs-lookup"><span data-stu-id="1d996-112">.NET Core</span></span>|<span data-ttu-id="1d996-113">3.x</span><span class="sxs-lookup"><span data-stu-id="1d996-113">3.x</span></span>|<span data-ttu-id="1d996-114">C# 8.0</span><span class="sxs-lookup"><span data-stu-id="1d996-114">C# 8.0</span></span>|
|<span data-ttu-id="1d996-115">.NET Core</span><span class="sxs-lookup"><span data-stu-id="1d996-115">.NET Core</span></span>|<span data-ttu-id="1d996-116">2.x</span><span class="sxs-lookup"><span data-stu-id="1d996-116">2.x</span></span>|<span data-ttu-id="1d996-117">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="1d996-117">C# 7.3</span></span>|
|<span data-ttu-id="1d996-118">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="1d996-118">.NET Standard</span></span>|<span data-ttu-id="1d996-119">all</span><span class="sxs-lookup"><span data-stu-id="1d996-119">all</span></span>|<span data-ttu-id="1d996-120">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="1d996-120">C# 7.3</span></span>|
|<span data-ttu-id="1d996-121">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="1d996-121">.NET Framework</span></span>|<span data-ttu-id="1d996-122">all</span><span class="sxs-lookup"><span data-stu-id="1d996-122">all</span></span>|<span data-ttu-id="1d996-123">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="1d996-123">C# 7.3</span></span>|

## <a name="default-for-previews"></a><span data-ttu-id="1d996-124">Padrão para versões prévias</span><span class="sxs-lookup"><span data-stu-id="1d996-124">Default for previews</span></span>

<span data-ttu-id="1d996-125">Quando seu projeto se destina a uma estrutura de visualização que tem uma versão da linguagem correspondente da visualização, a versão de linguagem usada é a de visualização.</span><span class="sxs-lookup"><span data-stu-id="1d996-125">When your project targets a preview framework that has a corresponding preview language version, the language version used is the preview language version.</span></span> <span data-ttu-id="1d996-126">Com isso, é possível usar os recursos mais recentes que são garantidos para trabalhar com essa versão prévia em qualquer ambiente sem afetar seus projetos que direcionam uma versão lançada do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1d996-126">This ensures that you can use the latest features that are guaranteed to work with that preview in any environment without affecting your projects that target a released .NET Core version.</span></span>

## <a name="overriding-a-default"></a><span data-ttu-id="1d996-127">Substituir um padrão</span><span class="sxs-lookup"><span data-stu-id="1d996-127">Overriding a default</span></span>

<span data-ttu-id="1d996-128">Se precisar especificar sua versão do C# explicitamente, poderá fazer isso de várias maneiras:</span><span class="sxs-lookup"><span data-stu-id="1d996-128">If you must specify your C# version explicitly, you can do so in several ways:</span></span>

- <span data-ttu-id="1d996-129">Edite manualmente o [arquivo de projeto](#edit-the-project-file).</span><span class="sxs-lookup"><span data-stu-id="1d996-129">Manually edit your [project file](#edit-the-project-file).</span></span>
- <span data-ttu-id="1d996-130">Definir a versão da linguagem [para vários projetos em um subdiretório](#configure-multiple-projects).</span><span class="sxs-lookup"><span data-stu-id="1d996-130">Set the language version [for multiple projects in a subdirectory](#configure-multiple-projects).</span></span>
- <span data-ttu-id="1d996-131">Configurar a opção [`-langversion` do compilador](compiler-options/langversion-compiler-option.md)</span><span class="sxs-lookup"><span data-stu-id="1d996-131">Configure the [`-langversion` compiler option](compiler-options/langversion-compiler-option.md)</span></span>

### <a name="edit-the-project-file"></a><span data-ttu-id="1d996-132">Editar o arquivo de projeto</span><span class="sxs-lookup"><span data-stu-id="1d996-132">Edit the project file</span></span>

<span data-ttu-id="1d996-133">É possível definir a versão da linguagem em seu arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="1d996-133">You can set the language version in your project file.</span></span> <span data-ttu-id="1d996-134">Por exemplo, se você quisesse explicitamente acesso às versões prévias do recurso, poderia adicionar um elemento como este:</span><span class="sxs-lookup"><span data-stu-id="1d996-134">For example, if you explicitly wanted access to preview features, you could do add an element like this:</span></span>

```xml
<PropertyGroup>
   <LangVersion>preview</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="1d996-135">O valor `preview` usa a versão prévia mais recente da linguagem C# compatível com seu compilador.</span><span class="sxs-lookup"><span data-stu-id="1d996-135">The value `preview` uses the latest available preview C# language that your compiler supports.</span></span>

### <a name="configure-multiple-projects"></a><span data-ttu-id="1d996-136">Configurar vários projetos</span><span class="sxs-lookup"><span data-stu-id="1d996-136">Configure multiple projects</span></span>

<span data-ttu-id="1d996-137">Crie um arquivo **Directory.Build.props** que contém o elemento `<LangVersion>` para configurar vários diretórios.</span><span class="sxs-lookup"><span data-stu-id="1d996-137">You can create a **Directory.Build.props** file that contains the `<LangVersion>` element to configure multiple directories.</span></span> <span data-ttu-id="1d996-138">Normalmente, você faz isso no diretório da solução.</span><span class="sxs-lookup"><span data-stu-id="1d996-138">You typically do that in your solution directory.</span></span> <span data-ttu-id="1d996-139">Adicione o seguinte a um arquivo **Directory.Build.props** no diretório de solução:</span><span class="sxs-lookup"><span data-stu-id="1d996-139">Add the following to a **Directory.Build.props** file in your solution directory:</span></span>

```xml
<Project>
 <PropertyGroup>
   <LangVersion>preview</LangVersion>
 </PropertyGroup>
</Project>
```

<span data-ttu-id="1d996-140">Agora, os builds de todo subdiretório do diretório que contém esse arquivo usarão a versão do C# da versão prévia.</span><span class="sxs-lookup"><span data-stu-id="1d996-140">Now, builds in every subdirectory of the directory containing that file will use the preview C# version.</span></span> <span data-ttu-id="1d996-141">Para obter mais informações, confira o artigo sobre como [personalizar o build](/visualstudio/msbuild/customize-your-build).</span><span class="sxs-lookup"><span data-stu-id="1d996-141">For more information, see the article on [Customize your build](/visualstudio/msbuild/customize-your-build).</span></span>

## <a name="c-language-version-reference"></a><span data-ttu-id="1d996-142">Referência à versão da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="1d996-142">C# language version reference</span></span>

<span data-ttu-id="1d996-143">A tabela a seguir mostra todas as versões atuais da linguagem C#.</span><span class="sxs-lookup"><span data-stu-id="1d996-143">The following table shows all current C# language versions.</span></span> <span data-ttu-id="1d996-144">Seu compilador talvez não entenda necessariamente todo valor se for mais antigo.</span><span class="sxs-lookup"><span data-stu-id="1d996-144">Your compiler may not necessarily understand every value if it is older.</span></span> <span data-ttu-id="1d996-145">Se instalar o .NET Core 3.0, você terá acesso a tudo que está listado.</span><span class="sxs-lookup"><span data-stu-id="1d996-145">If you install .NET Core 3.0, then you will have access to everything listed.</span></span>

|<span data-ttu-id="1d996-146">Valor</span><span class="sxs-lookup"><span data-stu-id="1d996-146">Value</span></span>|<span data-ttu-id="1d996-147">Significado</span><span class="sxs-lookup"><span data-stu-id="1d996-147">Meaning</span></span>|
|------------|-------------|
|<span data-ttu-id="1d996-148">versão prévia</span><span class="sxs-lookup"><span data-stu-id="1d996-148">preview</span></span>|<span data-ttu-id="1d996-149">O compilador aceita todas as sintaxes de linguagem válidas da versão prévia mais recente.</span><span class="sxs-lookup"><span data-stu-id="1d996-149">The compiler accepts all valid language syntax from the latest preview version.</span></span>|
|<span data-ttu-id="1d996-150">mais recente</span><span class="sxs-lookup"><span data-stu-id="1d996-150">latest</span></span>|<span data-ttu-id="1d996-151">O compilador aceita a sintaxe da versão lançada mais recente do compilador (incluindo a versão secundária).</span><span class="sxs-lookup"><span data-stu-id="1d996-151">The compiler accepts syntax from the latest released version of the compiler (including minor version).</span></span>|
|<span data-ttu-id="1d996-152">latestMajor</span><span class="sxs-lookup"><span data-stu-id="1d996-152">latestMajor</span></span>|<span data-ttu-id="1d996-153">O compilador aceita a sintaxe da versão principal mais recente lançada do compilador.</span><span class="sxs-lookup"><span data-stu-id="1d996-153">The compiler accepts syntax from the latest released major version of the compiler.</span></span>|
|<span data-ttu-id="1d996-154">8.0</span><span class="sxs-lookup"><span data-stu-id="1d996-154">8.0</span></span>|<span data-ttu-id="1d996-155">O compilador aceita somente a sintaxe incluída no C# 8.0 ou inferior.</span><span class="sxs-lookup"><span data-stu-id="1d996-155">The compiler accepts only syntax that is included in C# 8.0 or lower.</span></span>|
|<span data-ttu-id="1d996-156">7.3</span><span class="sxs-lookup"><span data-stu-id="1d996-156">7.3</span></span>|<span data-ttu-id="1d996-157">O compilador aceita somente a sintaxe incluída no C# 7.3 ou inferior.</span><span class="sxs-lookup"><span data-stu-id="1d996-157">The compiler accepts only syntax that is included in C# 7.3 or lower.</span></span>|
|<span data-ttu-id="1d996-158">7.2</span><span class="sxs-lookup"><span data-stu-id="1d996-158">7.2</span></span>|<span data-ttu-id="1d996-159">O compilador aceita somente a sintaxe incluída no C# 7.2 ou inferior.</span><span class="sxs-lookup"><span data-stu-id="1d996-159">The compiler accepts only syntax that is included in C# 7.2 or lower.</span></span>|
|<span data-ttu-id="1d996-160">7.1</span><span class="sxs-lookup"><span data-stu-id="1d996-160">7.1</span></span>|<span data-ttu-id="1d996-161">O compilador aceita somente a sintaxe incluída no C# 7.1 ou inferior.</span><span class="sxs-lookup"><span data-stu-id="1d996-161">The compiler accepts only syntax that is included in C# 7.1 or lower.</span></span>|
|<span data-ttu-id="1d996-162">7</span><span class="sxs-lookup"><span data-stu-id="1d996-162">7</span></span>|<span data-ttu-id="1d996-163">O compilador aceita somente a sintaxe incluída no C# 7.0 ou inferior.</span><span class="sxs-lookup"><span data-stu-id="1d996-163">The compiler accepts only syntax that is included in C# 7.0 or lower.</span></span>|
|<span data-ttu-id="1d996-164">6</span><span class="sxs-lookup"><span data-stu-id="1d996-164">6</span></span>|<span data-ttu-id="1d996-165">O compilador aceita somente a sintaxe incluída no C# 6.0 ou inferior.</span><span class="sxs-lookup"><span data-stu-id="1d996-165">The compiler accepts only syntax that is included in C# 6.0 or lower.</span></span>|
|<span data-ttu-id="1d996-166">5</span><span class="sxs-lookup"><span data-stu-id="1d996-166">5</span></span>|<span data-ttu-id="1d996-167">O compilador aceita somente a sintaxe incluída no C# 5.0 ou inferior.</span><span class="sxs-lookup"><span data-stu-id="1d996-167">The compiler accepts only syntax that is included in C# 5.0 or lower.</span></span>|
|<span data-ttu-id="1d996-168">4</span><span class="sxs-lookup"><span data-stu-id="1d996-168">4</span></span>|<span data-ttu-id="1d996-169">O compilador aceita somente a sintaxe incluída no C# 4.0 ou inferior.</span><span class="sxs-lookup"><span data-stu-id="1d996-169">The compiler accepts only syntax that is included in C# 4.0 or lower.</span></span>|
|<span data-ttu-id="1d996-170">3</span><span class="sxs-lookup"><span data-stu-id="1d996-170">3</span></span>|<span data-ttu-id="1d996-171">O compilador aceita somente a sintaxe incluída no C# 3.0 ou inferior.</span><span class="sxs-lookup"><span data-stu-id="1d996-171">The compiler accepts only syntax that is included in C# 3.0 or lower.</span></span>|
|<span data-ttu-id="1d996-172">ISO-2</span><span class="sxs-lookup"><span data-stu-id="1d996-172">ISO-2</span></span>|<span data-ttu-id="1d996-173">O compilador aceita somente a sintaxe incluída no ISO/IEC 23270:2006 C# (2.0)</span><span class="sxs-lookup"><span data-stu-id="1d996-173">The compiler accepts only syntax that is included in ISO/IEC 23270:2006 C# (2.0)</span></span> |
|<span data-ttu-id="1d996-174">ISO-1</span><span class="sxs-lookup"><span data-stu-id="1d996-174">ISO-1</span></span>|<span data-ttu-id="1d996-175">O compilador aceita somente a sintaxe incluída no ISO/IEC 23270:2003 C# (1.0/1.2)</span><span class="sxs-lookup"><span data-stu-id="1d996-175">The compiler accepts only syntax that is included in ISO/IEC 23270:2003 C# (1.0/1.2)</span></span> |
