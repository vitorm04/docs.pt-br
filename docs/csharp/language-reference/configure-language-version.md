---
title: Controle de versão da linguagem C# – Guia de C#
description: Saiba mais como a versão da linguagem C# é determinada com base em seu projeto e os diferentes valores para os quais você pode ajustá-la manualmente.
ms.date: 07/10/2019
ms.openlocfilehash: aa4f16d91b38fec7f5d4cd0b2632e62552b64eb7
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698802"
---
# <a name="c-language-versioning"></a><span data-ttu-id="aa68b-103">Controle de versão da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="aa68b-103">C# language versioning</span></span>

<span data-ttu-id="aa68b-104">O compilador do C# mais recente determina uma versão da linguagem padrão com base nas estruturas de destino do projeto.</span><span class="sxs-lookup"><span data-stu-id="aa68b-104">The latest C# compiler determines a default language version based on your project's target framework or frameworks.</span></span> <span data-ttu-id="aa68b-105">Isso ocorre porque a linguagem C# pode ter recursos que dependem de tipos ou de componentes de tempo de execução que não estão disponíveis em todas as implementações do .NET.</span><span class="sxs-lookup"><span data-stu-id="aa68b-105">This is because the C# language may have features that rely on types or runtime components that are not available in every .NET implementation.</span></span> <span data-ttu-id="aa68b-106">Com isso, independentemente do destino no qual seu projeto é criado, você obtém a versão da linguagem mais compatível por padrão.</span><span class="sxs-lookup"><span data-stu-id="aa68b-106">This also ensures that for whatever target your project is built against, you get the highest compatible language version by default.</span></span>

<span data-ttu-id="aa68b-107">As regras deste artigo se aplicam ao compilador fornecido com o Visual Studio 2019 ou o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="aa68b-107">The rules in this article apply to the compiler delivered with Visual Studio 2019, or the .NET Core 3.0 SDK.</span></span> <span data-ttu-id="aa68b-108">Os compiladores do C# que fazem parte da instalação do Visual Studio 2017 ou de versões anteriores do SDK do .NET Core são direcionados ao C# 7.0 por padrão.</span><span class="sxs-lookup"><span data-stu-id="aa68b-108">The C# compilers that are part of the Visual Studio 2017 installation or earlier .NET Core SDK versions target C# 7.0 by default.</span></span> 

## <a name="defaults"></a><span data-ttu-id="aa68b-109">Padrão</span><span class="sxs-lookup"><span data-stu-id="aa68b-109">Defaults</span></span>

<span data-ttu-id="aa68b-110">O compilador determina um padrão com base nestas regras:</span><span class="sxs-lookup"><span data-stu-id="aa68b-110">The compiler determines a default based on these rules:</span></span>

|<span data-ttu-id="aa68b-111">Estrutura de destino</span><span class="sxs-lookup"><span data-stu-id="aa68b-111">Target framework</span></span>|<span data-ttu-id="aa68b-112">version</span><span class="sxs-lookup"><span data-stu-id="aa68b-112">version</span></span>|<span data-ttu-id="aa68b-113">Padrão da versão da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="aa68b-113">C# language version default</span></span>|
|----------------|-------|---------------------------|
|<span data-ttu-id="aa68b-114">.NET Core</span><span class="sxs-lookup"><span data-stu-id="aa68b-114">.NET Core</span></span>|<span data-ttu-id="aa68b-115">Win</span><span class="sxs-lookup"><span data-stu-id="aa68b-115">3.x</span></span>|<span data-ttu-id="aa68b-116">C# 8.0</span><span class="sxs-lookup"><span data-stu-id="aa68b-116">C# 8.0</span></span>|
|<span data-ttu-id="aa68b-117">.NET Core</span><span class="sxs-lookup"><span data-stu-id="aa68b-117">.NET Core</span></span>|<span data-ttu-id="aa68b-118">2.x</span><span class="sxs-lookup"><span data-stu-id="aa68b-118">2.x</span></span>|<span data-ttu-id="aa68b-119">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="aa68b-119">C# 7.3</span></span>|
|<span data-ttu-id="aa68b-120">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="aa68b-120">.NET Standard</span></span>|<span data-ttu-id="aa68b-121">2.1</span><span class="sxs-lookup"><span data-stu-id="aa68b-121">2.1</span></span>|<span data-ttu-id="aa68b-122">C# 8.0</span><span class="sxs-lookup"><span data-stu-id="aa68b-122">C# 8.0</span></span>|
|<span data-ttu-id="aa68b-123">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="aa68b-123">.NET Standard</span></span>|<span data-ttu-id="aa68b-124">2.0</span><span class="sxs-lookup"><span data-stu-id="aa68b-124">2.0</span></span>|<span data-ttu-id="aa68b-125">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="aa68b-125">C# 7.3</span></span>|
|<span data-ttu-id="aa68b-126">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="aa68b-126">.NET Standard</span></span>|<span data-ttu-id="aa68b-127">1.x</span><span class="sxs-lookup"><span data-stu-id="aa68b-127">1.x</span></span>|<span data-ttu-id="aa68b-128">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="aa68b-128">C# 7.3</span></span>|
|<span data-ttu-id="aa68b-129">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="aa68b-129">.NET Framework</span></span>|<span data-ttu-id="aa68b-130">all</span><span class="sxs-lookup"><span data-stu-id="aa68b-130">all</span></span>|<span data-ttu-id="aa68b-131">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="aa68b-131">C# 7.3</span></span>|

## <a name="default-for-previews"></a><span data-ttu-id="aa68b-132">Padrão para versões prévias</span><span class="sxs-lookup"><span data-stu-id="aa68b-132">Default for previews</span></span>

<span data-ttu-id="aa68b-133">Quando seu projeto se destina a uma estrutura de visualização que tem uma versão da linguagem correspondente da visualização, a versão de linguagem usada é a de visualização.</span><span class="sxs-lookup"><span data-stu-id="aa68b-133">When your project targets a preview framework that has a corresponding preview language version, the language version used is the preview language version.</span></span> <span data-ttu-id="aa68b-134">Com isso, é possível usar os recursos mais recentes que são garantidos para trabalhar com essa versão prévia em qualquer ambiente sem afetar seus projetos que direcionam uma versão lançada do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="aa68b-134">This ensures that you can use the latest features that are guaranteed to work with that preview in any environment without affecting your projects that target a released .NET Core version.</span></span>

## <a name="override-a-default"></a><span data-ttu-id="aa68b-135">Substituir um padrão</span><span class="sxs-lookup"><span data-stu-id="aa68b-135">Override a default</span></span>

<span data-ttu-id="aa68b-136">Se precisar especificar sua versão do C# explicitamente, poderá fazer isso de várias maneiras:</span><span class="sxs-lookup"><span data-stu-id="aa68b-136">If you must specify your C# version explicitly, you can do so in several ways:</span></span>

- <span data-ttu-id="aa68b-137">Edite manualmente o [arquivo de projeto](#edit-the-project-file).</span><span class="sxs-lookup"><span data-stu-id="aa68b-137">Manually edit your [project file](#edit-the-project-file).</span></span>
- <span data-ttu-id="aa68b-138">Definir a versão da linguagem [para vários projetos em um subdiretório](#configure-multiple-projects).</span><span class="sxs-lookup"><span data-stu-id="aa68b-138">Set the language version [for multiple projects in a subdirectory](#configure-multiple-projects).</span></span>
- <span data-ttu-id="aa68b-139">Configurar a opção [`-langversion` do compilador](compiler-options/langversion-compiler-option.md)</span><span class="sxs-lookup"><span data-stu-id="aa68b-139">Configure the [`-langversion` compiler option](compiler-options/langversion-compiler-option.md)</span></span>

### <a name="edit-the-project-file"></a><span data-ttu-id="aa68b-140">Editar o arquivo de projeto</span><span class="sxs-lookup"><span data-stu-id="aa68b-140">Edit the project file</span></span>

<span data-ttu-id="aa68b-141">É possível definir a versão da linguagem em seu arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="aa68b-141">You can set the language version in your project file.</span></span> <span data-ttu-id="aa68b-142">Por exemplo, se você quiser explicitamente acesso às versões prévias dos recursos, adicione um elemento como este:</span><span class="sxs-lookup"><span data-stu-id="aa68b-142">For example, if you explicitly want access to preview features, add an element like this:</span></span>

```xml
<PropertyGroup>
   <LangVersion>preview</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="aa68b-143">O valor `preview` usa a versão prévia mais recente da linguagem C# compatível com seu compilador.</span><span class="sxs-lookup"><span data-stu-id="aa68b-143">The value `preview` uses the latest available preview C# language version that your compiler supports.</span></span>

### <a name="configure-multiple-projects"></a><span data-ttu-id="aa68b-144">Configurar vários projetos</span><span class="sxs-lookup"><span data-stu-id="aa68b-144">Configure multiple projects</span></span>

<span data-ttu-id="aa68b-145">Crie um arquivo **Directory.Build.props** que contém o elemento `<LangVersion>` para configurar vários diretórios.</span><span class="sxs-lookup"><span data-stu-id="aa68b-145">You can create a **Directory.Build.props** file that contains the `<LangVersion>` element to configure multiple directories.</span></span> <span data-ttu-id="aa68b-146">Normalmente, você faz isso no diretório da solução.</span><span class="sxs-lookup"><span data-stu-id="aa68b-146">You typically do that in your solution directory.</span></span> <span data-ttu-id="aa68b-147">Adicione o seguinte a um arquivo **Directory.Build.props** no diretório de solução:</span><span class="sxs-lookup"><span data-stu-id="aa68b-147">Add the following to a **Directory.Build.props** file in your solution directory:</span></span>

```xml
<Project>
 <PropertyGroup>
   <LangVersion>preview</LangVersion>
 </PropertyGroup>
</Project>
```

<span data-ttu-id="aa68b-148">Agora, os builds de todo subdiretório do diretório que contém esse arquivo usarão a versão do C# da versão prévia.</span><span class="sxs-lookup"><span data-stu-id="aa68b-148">Now, builds in every subdirectory of the directory containing that file will use the preview C# version.</span></span> <span data-ttu-id="aa68b-149">Para obter mais informações, confira o artigo sobre como [personalizar o build](/visualstudio/msbuild/customize-your-build).</span><span class="sxs-lookup"><span data-stu-id="aa68b-149">For more information, see the article on [Customize your build](/visualstudio/msbuild/customize-your-build).</span></span>

## <a name="c-language-version-reference"></a><span data-ttu-id="aa68b-150">Referência à versão da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="aa68b-150">C# language version reference</span></span>

<span data-ttu-id="aa68b-151">A tabela a seguir mostra todas as versões atuais da linguagem C#.</span><span class="sxs-lookup"><span data-stu-id="aa68b-151">The following table shows all current C# language versions.</span></span> <span data-ttu-id="aa68b-152">Seu compilador talvez não entenda necessariamente todo valor se for mais antigo.</span><span class="sxs-lookup"><span data-stu-id="aa68b-152">Your compiler may not necessarily understand every value if it is older.</span></span> <span data-ttu-id="aa68b-153">Se instalar o .NET Core 3.0, você terá acesso a tudo que está listado.</span><span class="sxs-lookup"><span data-stu-id="aa68b-153">If you install .NET Core 3.0, then you will have access to everything listed.</span></span>

|<span data-ttu-id="aa68b-154">Valor</span><span class="sxs-lookup"><span data-stu-id="aa68b-154">Value</span></span>|<span data-ttu-id="aa68b-155">Significado</span><span class="sxs-lookup"><span data-stu-id="aa68b-155">Meaning</span></span>|
|------------|-------------|
|<span data-ttu-id="aa68b-156">versão prévia</span><span class="sxs-lookup"><span data-stu-id="aa68b-156">preview</span></span>|<span data-ttu-id="aa68b-157">O compilador aceita todas as sintaxes de linguagem válidas da versão prévia mais recente.</span><span class="sxs-lookup"><span data-stu-id="aa68b-157">The compiler accepts all valid language syntax from the latest preview version.</span></span>|
|<span data-ttu-id="aa68b-158">latest</span><span class="sxs-lookup"><span data-stu-id="aa68b-158">latest</span></span>|<span data-ttu-id="aa68b-159">O compilador aceita a sintaxe da versão lançada mais recente do compilador (incluindo a versão secundária).</span><span class="sxs-lookup"><span data-stu-id="aa68b-159">The compiler accepts syntax from the latest released version of the compiler (including minor version).</span></span>|
|<span data-ttu-id="aa68b-160">latestMajor</span><span class="sxs-lookup"><span data-stu-id="aa68b-160">latestMajor</span></span>|<span data-ttu-id="aa68b-161">O compilador aceita a sintaxe da versão principal mais recente lançada do compilador.</span><span class="sxs-lookup"><span data-stu-id="aa68b-161">The compiler accepts syntax from the latest released major version of the compiler.</span></span>|
|<span data-ttu-id="aa68b-162">8.0</span><span class="sxs-lookup"><span data-stu-id="aa68b-162">8.0</span></span>|<span data-ttu-id="aa68b-163">O compilador aceita somente a sintaxe incluída no C# 8.0 ou inferior.</span><span class="sxs-lookup"><span data-stu-id="aa68b-163">The compiler accepts only syntax that is included in C# 8.0 or lower.</span></span>|
|<span data-ttu-id="aa68b-164">7.3</span><span class="sxs-lookup"><span data-stu-id="aa68b-164">7.3</span></span>|<span data-ttu-id="aa68b-165">O compilador aceita somente a sintaxe incluída no C# 7.3 ou inferior.</span><span class="sxs-lookup"><span data-stu-id="aa68b-165">The compiler accepts only syntax that is included in C# 7.3 or lower.</span></span>|
|<span data-ttu-id="aa68b-166">7.2</span><span class="sxs-lookup"><span data-stu-id="aa68b-166">7.2</span></span>|<span data-ttu-id="aa68b-167">O compilador aceita somente a sintaxe incluída no C# 7.2 ou inferior.</span><span class="sxs-lookup"><span data-stu-id="aa68b-167">The compiler accepts only syntax that is included in C# 7.2 or lower.</span></span>|
|<span data-ttu-id="aa68b-168">7.1</span><span class="sxs-lookup"><span data-stu-id="aa68b-168">7.1</span></span>|<span data-ttu-id="aa68b-169">O compilador aceita somente a sintaxe incluída no C# 7.1 ou inferior.</span><span class="sxs-lookup"><span data-stu-id="aa68b-169">The compiler accepts only syntax that is included in C# 7.1 or lower.</span></span>|
|<span data-ttu-id="aa68b-170">7</span><span class="sxs-lookup"><span data-stu-id="aa68b-170">7</span></span>|<span data-ttu-id="aa68b-171">O compilador aceita somente a sintaxe incluída no C# 7.0 ou inferior.</span><span class="sxs-lookup"><span data-stu-id="aa68b-171">The compiler accepts only syntax that is included in C# 7.0 or lower.</span></span>|
|<span data-ttu-id="aa68b-172">6</span><span class="sxs-lookup"><span data-stu-id="aa68b-172">6</span></span>|<span data-ttu-id="aa68b-173">O compilador aceita somente a sintaxe incluída no C# 6.0 ou inferior.</span><span class="sxs-lookup"><span data-stu-id="aa68b-173">The compiler accepts only syntax that is included in C# 6.0 or lower.</span></span>|
|<span data-ttu-id="aa68b-174">5</span><span class="sxs-lookup"><span data-stu-id="aa68b-174">5</span></span>|<span data-ttu-id="aa68b-175">O compilador aceita somente a sintaxe incluída no C# 5.0 ou inferior.</span><span class="sxs-lookup"><span data-stu-id="aa68b-175">The compiler accepts only syntax that is included in C# 5.0 or lower.</span></span>|
|<span data-ttu-id="aa68b-176">4</span><span class="sxs-lookup"><span data-stu-id="aa68b-176">4</span></span>|<span data-ttu-id="aa68b-177">O compilador aceita somente a sintaxe incluída no C# 4.0 ou inferior.</span><span class="sxs-lookup"><span data-stu-id="aa68b-177">The compiler accepts only syntax that is included in C# 4.0 or lower.</span></span>|
|<span data-ttu-id="aa68b-178">3</span><span class="sxs-lookup"><span data-stu-id="aa68b-178">3</span></span>|<span data-ttu-id="aa68b-179">O compilador aceita somente a sintaxe incluída no C# 3.0 ou inferior.</span><span class="sxs-lookup"><span data-stu-id="aa68b-179">The compiler accepts only syntax that is included in C# 3.0 or lower.</span></span>|
|<span data-ttu-id="aa68b-180">ISO-2</span><span class="sxs-lookup"><span data-stu-id="aa68b-180">ISO-2</span></span>|<span data-ttu-id="aa68b-181">O compilador aceita somente a sintaxe incluída no ISO/IEC 23270:2006 C# (2.0)</span><span class="sxs-lookup"><span data-stu-id="aa68b-181">The compiler accepts only syntax that is included in ISO/IEC 23270:2006 C# (2.0)</span></span> |
|<span data-ttu-id="aa68b-182">ISO-1</span><span class="sxs-lookup"><span data-stu-id="aa68b-182">ISO-1</span></span>|<span data-ttu-id="aa68b-183">O compilador aceita somente a sintaxe incluída no ISO/IEC 23270:2003 C# (1.0/1.2)</span><span class="sxs-lookup"><span data-stu-id="aa68b-183">The compiler accepts only syntax that is included in ISO/IEC 23270:2003 C# (1.0/1.2)</span></span> |
