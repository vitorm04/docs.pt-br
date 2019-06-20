---
title: Selecione a versão da linguagem Visual Basic
description: Configure o compilador para executar a validação de sintaxe usando uma versão específica do compilador.
ms.date: 05/24/2018
ms.openlocfilehash: 4768d59a37d168b2883396f1dea4d0c1a0ff4ca7
ms.sourcegitcommit: 4c41ec195caf03d98b7900007c3c8e24eba20d34
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/20/2019
ms.locfileid: "67268271"
---
# <a name="select-the-visual-basic-language-version"></a><span data-ttu-id="e4624-103">Selecione a versão da linguagem Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e4624-103">Select the Visual Basic language version</span></span>

<span data-ttu-id="e4624-104">O compilador do Visual Basic usa como padrão para a versão principal mais recente da linguagem que foi lançada.</span><span class="sxs-lookup"><span data-stu-id="e4624-104">The Visual Basic compiler defaults to the latest major version of the language that has been released.</span></span> <span data-ttu-id="e4624-105">Você pode optar por compilar qualquer projeto usando uma nova versão de ponto da linguagem.</span><span class="sxs-lookup"><span data-stu-id="e4624-105">You may choose to compile any project using a new point release of the language.</span></span> <span data-ttu-id="e4624-106">A escolha de uma versão mais recente da linguagem permite que o projeto use as últimas funcionalidades da linguagem.</span><span class="sxs-lookup"><span data-stu-id="e4624-106">Choosing a newer version of the language enables your project to make use of the latest language features.</span></span> <span data-ttu-id="e4624-107">Em outros cenários, talvez você precise validar se um projeto é compilado por completo ao usar uma versão mais antiga da linguagem.</span><span class="sxs-lookup"><span data-stu-id="e4624-107">In other scenarios, you may need to validate that a project compiles cleanly when using an older version of the language.</span></span>

<span data-ttu-id="e4624-108">Essa funcionalidade separa a decisão de instalar novas versões do SDK e das ferramentas no ambiente de desenvolvimento da decisão de incorporar novas funcionalidades da linguagem em um projeto.</span><span class="sxs-lookup"><span data-stu-id="e4624-108">This capability decouples the decision to install new versions of the SDK and tools in your development environment from the decision to incorporate new language features in a project.</span></span> <span data-ttu-id="e4624-109">Instale o último SDK e as últimas ferramentas no computador de build.</span><span class="sxs-lookup"><span data-stu-id="e4624-109">You can install the latest SDK and tools on your build machine.</span></span> <span data-ttu-id="e4624-110">Cada projeto pode ser configurado para usar uma versão específica da linguagem de seu build.</span><span class="sxs-lookup"><span data-stu-id="e4624-110">Each project can be configured to use a specific version of the language for its build.</span></span>

<span data-ttu-id="e4624-111">Há três maneiras de definir a versão de idioma:</span><span class="sxs-lookup"><span data-stu-id="e4624-111">There are three ways to set the language version:</span></span>

- <span data-ttu-id="e4624-112">Editar manualmente sua [ **. vbproj** arquivo](#edit-the-vbproj-file)</span><span class="sxs-lookup"><span data-stu-id="e4624-112">Manually edit your [**.vbproj** file](#edit-the-vbproj-file)</span></span>
- <span data-ttu-id="e4624-113">Defina a versão de idioma [para vários projetos em um subdiretório](#configure-multiple-projects)</span><span class="sxs-lookup"><span data-stu-id="e4624-113">Set the language version [for multiple projects in a subdirectory](#configure-multiple-projects)</span></span>
- <span data-ttu-id="e4624-114">Configurar o [ `-langversion` opção de compilador](#set-the-langversion-compiler-option)</span><span class="sxs-lookup"><span data-stu-id="e4624-114">Configure the [`-langversion` compiler option](#set-the-langversion-compiler-option)</span></span>

## <a name="edit-the-vbproj-file"></a><span data-ttu-id="e4624-115">Edite o arquivo vbproj</span><span class="sxs-lookup"><span data-stu-id="e4624-115">Edit the vbproj file</span></span>

<span data-ttu-id="e4624-116">Você pode definir a versão de idioma no seu **. vbproj** arquivo.</span><span class="sxs-lookup"><span data-stu-id="e4624-116">You can set the language version in your **.vbproj** file.</span></span> <span data-ttu-id="e4624-117">Adicione o seguinte elemento:</span><span class="sxs-lookup"><span data-stu-id="e4624-117">Add the following element:</span></span>

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="e4624-118">O valor `latest` usa a versão secundária mais recente da linguagem Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="e4624-118">The value `latest` uses the latest minor version of the Visual Basic language.</span></span> <span data-ttu-id="e4624-119">Os valores válidos são:</span><span class="sxs-lookup"><span data-stu-id="e4624-119">Valid values are:</span></span>

|<span data-ttu-id="e4624-120">Valor</span><span class="sxs-lookup"><span data-stu-id="e4624-120">Value</span></span>|<span data-ttu-id="e4624-121">Significado</span><span class="sxs-lookup"><span data-stu-id="e4624-121">Meaning</span></span>|
|------------|-------------|
|<span data-ttu-id="e4624-122">default</span><span class="sxs-lookup"><span data-stu-id="e4624-122">default</span></span>|<span data-ttu-id="e4624-123">O compilador aceita toda a sintaxe de linguagem válida da versão principal mais recente à qual dá suporte.</span><span class="sxs-lookup"><span data-stu-id="e4624-123">The compiler accepts all valid language syntax from the latest major version that it can support.</span></span>|
|<span data-ttu-id="e4624-124">9</span><span class="sxs-lookup"><span data-stu-id="e4624-124">9</span></span>|<span data-ttu-id="e4624-125">O compilador aceita somente a sintaxe incluída no Visual Basic 9.0 ou inferior.</span><span class="sxs-lookup"><span data-stu-id="e4624-125">The compiler accepts only syntax that is included in Visual Basic 9.0 or lower.</span></span>|
|<span data-ttu-id="e4624-126">10</span><span class="sxs-lookup"><span data-stu-id="e4624-126">10</span></span>|<span data-ttu-id="e4624-127">O compilador aceita somente a sintaxe incluída no Visual Basic 10.0 ou inferior.</span><span class="sxs-lookup"><span data-stu-id="e4624-127">The compiler accepts only syntax that is included in Visual Basic 10.0 or lower.</span></span>|
|<span data-ttu-id="e4624-128">11</span><span class="sxs-lookup"><span data-stu-id="e4624-128">11</span></span>|<span data-ttu-id="e4624-129">O compilador aceita somente a sintaxe incluída no Visual Basic 11.0 ou inferior.</span><span class="sxs-lookup"><span data-stu-id="e4624-129">The compiler accepts only syntax that is included in Visual Basic 11.0 or lower.</span></span>|
|<span data-ttu-id="e4624-130">12</span><span class="sxs-lookup"><span data-stu-id="e4624-130">12</span></span>|<span data-ttu-id="e4624-131">O compilador aceita somente a sintaxe incluída no Visual Basic 12.0 ou inferior.</span><span class="sxs-lookup"><span data-stu-id="e4624-131">The compiler accepts only syntax that is included in Visual Basic 12.0 or lower.</span></span>|
|<span data-ttu-id="e4624-132">14</span><span class="sxs-lookup"><span data-stu-id="e4624-132">14</span></span>|<span data-ttu-id="e4624-133">O compilador aceita somente a sintaxe incluída no Visual Basic 14.0 ou inferior.</span><span class="sxs-lookup"><span data-stu-id="e4624-133">The compiler accepts only syntax that is included in Visual Basic 14.0 or lower.</span></span>|
|<span data-ttu-id="e4624-134">15</span><span class="sxs-lookup"><span data-stu-id="e4624-134">15</span></span>|<span data-ttu-id="e4624-135">O compilador aceita somente a sintaxe incluída em 15.0 do Visual Basic ou inferior.</span><span class="sxs-lookup"><span data-stu-id="e4624-135">The compiler accepts only syntax that is included in Visual Basic 15.0 or lower.</span></span>|
|<span data-ttu-id="e4624-136">15.3</span><span class="sxs-lookup"><span data-stu-id="e4624-136">15.3</span></span>|<span data-ttu-id="e4624-137">O compilador aceita somente a sintaxe incluída na versão 15.3 do Visual Basic ou inferior.</span><span class="sxs-lookup"><span data-stu-id="e4624-137">The compiler accepts only syntax that is included in Visual Basic 15.3 or lower.</span></span>|
|<span data-ttu-id="e4624-138">15.5</span><span class="sxs-lookup"><span data-stu-id="e4624-138">15.5</span></span>|<span data-ttu-id="e4624-139">O compilador aceita somente a sintaxe incluída na versão 15.5 do Visual Basic ou inferior.</span><span class="sxs-lookup"><span data-stu-id="e4624-139">The compiler accepts only syntax that is included in Visual Basic 15.5 or lower.</span></span>|
|<span data-ttu-id="e4624-140">15.8</span><span class="sxs-lookup"><span data-stu-id="e4624-140">15.8</span></span>|<span data-ttu-id="e4624-141">O compilador aceita somente a sintaxe incluída no Visual Basic 15,8 ou inferior.</span><span class="sxs-lookup"><span data-stu-id="e4624-141">The compiler accepts only syntax that is included in Visual Basic 15.8 or lower.</span></span>|
|<span data-ttu-id="e4624-142">mais recente</span><span class="sxs-lookup"><span data-stu-id="e4624-142">latest</span></span>|<span data-ttu-id="e4624-143">O compilador aceita toda a sintaxe de linguagem à qual dá suporte.</span><span class="sxs-lookup"><span data-stu-id="e4624-143">The compiler accepts all valid language syntax that it can support.</span></span>|

<span data-ttu-id="e4624-144">As cadeias de caracteres especiais `default` e `latest` são resolvidas nas últimas versões da linguagem principal e secundária instaladas no computador de build, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="e4624-144">The special strings `default` and `latest` resolve to the latest major and minor language versions installed on the build machine, respectively.</span></span>

## <a name="configure-multiple-projects"></a><span data-ttu-id="e4624-145">Configurar vários projetos</span><span class="sxs-lookup"><span data-stu-id="e4624-145">Configure multiple projects</span></span>

<span data-ttu-id="e4624-146">Crie um arquivo **Directory.build.props** que contém o elemento `<LangVersion>` para configurar vários diretórios.</span><span class="sxs-lookup"><span data-stu-id="e4624-146">You can create a **Directory.build.props** file that contains the `<LangVersion>` element to configure multiple directories.</span></span> <span data-ttu-id="e4624-147">Normalmente, você faz isso no diretório da solução.</span><span class="sxs-lookup"><span data-stu-id="e4624-147">You typically do that in your solution directory.</span></span> <span data-ttu-id="e4624-148">Adicione o seguinte a um arquivo **Directory.build.props** no diretório de solução:</span><span class="sxs-lookup"><span data-stu-id="e4624-148">Add the following to a **Directory.build.props** file in your solution directory:</span></span>

```xml
<Project>
 <PropertyGroup>
   <LangVersion>15.5</LangVersion>
 </PropertyGroup>
</Project>
```

<span data-ttu-id="e4624-149">Agora, compilações em cada subdiretório do diretório que contém esse arquivo serão usar sintaxe de versão 15.5 do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="e4624-149">Now, builds in every subdirectory of the directory containing that file will use Visual Basic version 15.5 syntax.</span></span> <span data-ttu-id="e4624-150">Para obter mais informações, confira o artigo sobre como [personalizar o build](/visualstudio/msbuild/customize-your-build).</span><span class="sxs-lookup"><span data-stu-id="e4624-150">For more information, see the article on [Customize your build](/visualstudio/msbuild/customize-your-build).</span></span>

## <a name="set-the-langversion-compiler-option"></a><span data-ttu-id="e4624-151">Definir a opção langversion do compilador</span><span class="sxs-lookup"><span data-stu-id="e4624-151">Set the langversion compiler option</span></span>

<span data-ttu-id="e4624-152">Você pode usar a opção `-langversion` da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="e4624-152">You can use the `-langversion` command-line option.</span></span> <span data-ttu-id="e4624-153">Para obter mais informações, confira o artigo sobre a opção [-langversion](../reference/command-line-compiler/langversion.md) do compilador.</span><span class="sxs-lookup"><span data-stu-id="e4624-153">For more information, see the article on the [-langversion](../reference/command-line-compiler/langversion.md) compiler option.</span></span> <span data-ttu-id="e4624-154">Você pode ver uma lista dos valores válidos, digitando `vbc -langversion:?` .</span><span class="sxs-lookup"><span data-stu-id="e4624-154">You can see a list of the valid values by typing  `vbc -langversion:?` .</span></span>
