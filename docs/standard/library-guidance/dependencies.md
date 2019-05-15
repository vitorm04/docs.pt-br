---
title: Dependências e bibliotecas do .NET
description: Melhores práticas para gerenciar as dependências do NuGet em bibliotecas do .NET.
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: 5566ab83040ce5dc23520401e3fc4bb619af4ec4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61909907"
---
# <a name="dependencies"></a><span data-ttu-id="01e51-103">Dependências</span><span class="sxs-lookup"><span data-stu-id="01e51-103">Dependencies</span></span>

<span data-ttu-id="01e51-104">A principal maneira de adicionar as dependências em uma biblioteca do .NET fazer referência a pacotes do NuGet.</span><span class="sxs-lookup"><span data-stu-id="01e51-104">The primary way of adding dependencies to a .NET library is referencing NuGet packages.</span></span> <span data-ttu-id="01e51-105">Referências de pacote do NuGet permitem que você rapidamente reutilize e aproveite a funcionalidade já escrita, mas são uma fonte comum de atrito para desenvolvedores do .NET.</span><span class="sxs-lookup"><span data-stu-id="01e51-105">NuGet package references allow you to quickly reuse and leverage already written functionality, but they're a common source of friction for .NET developers.</span></span> <span data-ttu-id="01e51-106">Gerenciar dependências corretamente é importante para evitar que alterações em outras bibliotecas .NET provoquem falhas na sua biblioteca do .NET e vice-versa.</span><span class="sxs-lookup"><span data-stu-id="01e51-106">Correctly managing dependencies is important to prevent changes in other .NET libraries from breaking your .NET library, and vice versa!</span></span>

## <a name="diamond-dependencies"></a><span data-ttu-id="01e51-107">Dependências de losango</span><span class="sxs-lookup"><span data-stu-id="01e51-107">Diamond dependencies</span></span>

<span data-ttu-id="01e51-108">É uma situação comum um projeto do .NET ter várias versões de um pacote em sua árvore de dependência.</span><span class="sxs-lookup"><span data-stu-id="01e51-108">It's a common situation for a .NET project to have multiple versions of a package in its dependency tree.</span></span> <span data-ttu-id="01e51-109">Por exemplo, um aplicativo depende de dois pacotes do NuGet e cada um dos quais depende de versões diferentes do mesmo pacote.</span><span class="sxs-lookup"><span data-stu-id="01e51-109">For example, an app depends on two NuGet packages, each of which depends on different versions of the same package.</span></span> <span data-ttu-id="01e51-110">Agora existe uma dependência de losango no grafo de dependência do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="01e51-110">A diamond dependency now exists in the app's dependency graph.</span></span>

<span data-ttu-id="01e51-111">![Dependência de losango](./media/dependencies/diamond-dependency.png "Dependência de losango")</span><span class="sxs-lookup"><span data-stu-id="01e51-111">![Diamond dependency](./media/dependencies/diamond-dependency.png "Diamond dependency")</span></span>

<span data-ttu-id="01e51-112">No momento da compilação, o NuGet analisa todos os pacotes de que um projeto depende, incluindo as dependências das dependências.</span><span class="sxs-lookup"><span data-stu-id="01e51-112">At build time, NuGet analyzes all the packages that a project depends on, including the dependencies of dependencies.</span></span> <span data-ttu-id="01e51-113">Quando várias versões de um pacote são detectadas, as regras são avaliadas para escolher uma.</span><span class="sxs-lookup"><span data-stu-id="01e51-113">When multiple versions of a package are detected, rules are evaluated to pick one.</span></span> <span data-ttu-id="01e51-114">Unificar pacotes é necessário porque executar versões lado a lado de um assembly no mesmo aplicativo é um problema no .NET.</span><span class="sxs-lookup"><span data-stu-id="01e51-114">Unifying packages is necessary because running side-by-side versions of an assembly in the same application is problematic in .NET.</span></span>

<span data-ttu-id="01e51-115">A maioria das dependências de losangos é facilmente resolvida. No entanto, podem criar problemas em determinadas circunstâncias:</span><span class="sxs-lookup"><span data-stu-id="01e51-115">Most diamond dependencies are easily resolved; however, they can create issues in certain circumstances:</span></span>

1. <span data-ttu-id="01e51-116">**Referências de pacote do NuGet conflitantes** impedem que uma versão seja resolvida durante a restauração de pacote.</span><span class="sxs-lookup"><span data-stu-id="01e51-116">**Conflicting NuGet package references** prevent a version from being resolved during package restore.</span></span>
2. <span data-ttu-id="01e51-117">**Alterações da falha entre as versões** causam erros e exceções em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="01e51-117">**Breaking changes between the versions** cause bugs and exceptions at runtime.</span></span>
3. <span data-ttu-id="01e51-118">**O assembly do pacote tem um nome forte**, a versão do assembly é alterada e o aplicativo está em execução no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="01e51-118">**The package assembly is strong named**, the assembly version changed, and the app is running on the .NET Framework.</span></span> <span data-ttu-id="01e51-119">Redirecionamentos de associação de assembly são necessários.</span><span class="sxs-lookup"><span data-stu-id="01e51-119">Assembly binding redirects are required.</span></span>

<span data-ttu-id="01e51-120">Não é possível saber quais pacotes serão usados junto com o seu.</span><span class="sxs-lookup"><span data-stu-id="01e51-120">It's not possible to know what packages will be used alongside your own.</span></span> <span data-ttu-id="01e51-121">Uma boa maneira de reduzir a probabilidade de uma dependência de losango provocar falha na sua biblioteca é minimizar o número de pacotes dos quais você depende.</span><span class="sxs-lookup"><span data-stu-id="01e51-121">A good way to reduce the likelihood of a diamond dependency breaking your library is to minimize the number of packages you depend on.</span></span>

<span data-ttu-id="01e51-122">**✔️ FAÇA** a análise da sua biblioteca do .NET quanto a dependências desnecessárias.</span><span class="sxs-lookup"><span data-stu-id="01e51-122">**✔️ DO** review your .NET library for unnecessary dependencies.</span></span>

## <a name="nuget-dependency-version-ranges"></a><span data-ttu-id="01e51-123">Intervalos de versão de dependência do NuGet</span><span class="sxs-lookup"><span data-stu-id="01e51-123">NuGet dependency version ranges</span></span>

<span data-ttu-id="01e51-124">Uma referência de pacote especifica o intervalo de pacotes válidos que ela permite.</span><span class="sxs-lookup"><span data-stu-id="01e51-124">A package reference specifies the range of valid packages it allows.</span></span> <span data-ttu-id="01e51-125">Normalmente, a versão de referência de pacote no arquivo de projeto é a versão mínima e não há um máximo.</span><span class="sxs-lookup"><span data-stu-id="01e51-125">Typically, the package reference version in the project file is the minimum version and there's no maximum.</span></span>

```xml
<!-- Accepts any version 1.0 and above. -->
<PackageReference Include="ExamplePackage" Version="1.0" />
```

<span data-ttu-id="01e51-126">As regras que o NuGet usa ao resolver as dependências são [complexas](/nuget/consume-packages/dependency-resolution), mas o NuGet procura sempre a versão mais antiga aplicável.</span><span class="sxs-lookup"><span data-stu-id="01e51-126">The rules that NuGet uses when resolving dependencies are [complex](/nuget/consume-packages/dependency-resolution), but NuGet always looks for the lowest applicable version.</span></span> <span data-ttu-id="01e51-127">O NuGet prefere a versão mais antiga aplicável, em vez de usar a mais alta disponível, porque a mais baixa terá menos problemas de compatibilidade.</span><span class="sxs-lookup"><span data-stu-id="01e51-127">NuGet prefers the lowest applicable version over using the highest available because the lowest will have the least compatibility issues.</span></span>

<span data-ttu-id="01e51-128">Devido à regra de versão mais baixa aplicável do NuGet, não é necessário colocar uma versão superior ou o intervalo exato em referências de pacote para evitar obter a versão mais recente.</span><span class="sxs-lookup"><span data-stu-id="01e51-128">Because of NuGet's lowest applicable version rule, it isn't necessary to place an upper version or exact range on package references to avoid getting the latest version.</span></span> <span data-ttu-id="01e51-129">O NuGet já tenta encontrar a versão mais baixa e mais compatível para você.</span><span class="sxs-lookup"><span data-stu-id="01e51-129">NuGet already tries to find the lowest, most compatible version for you.</span></span>

```xml
<!-- Accepts 1.0 up to 1.x, but not 2.0 and higher. -->
<PackageReference Include="ExamplePackage" Version="[1.0,2.0)" />

<!-- Accepts exactly 1.0. -->
<PackageReference Include="ExamplePackage" Version="[1.0]" />
```

<span data-ttu-id="01e51-130">Limites de versão superior fará com que o NuGet falhe se houver um conflito.</span><span class="sxs-lookup"><span data-stu-id="01e51-130">Upper version limits will cause NuGet to fail if there's a conflict.</span></span> <span data-ttu-id="01e51-131">Por exemplo, uma biblioteca aceita exatamente 1.0, enquanto a outra biblioteca exige 2.0 ou superior.</span><span class="sxs-lookup"><span data-stu-id="01e51-131">For example, one library accepts exactly 1.0 while another library requires 2.0 or above.</span></span> <span data-ttu-id="01e51-132">Embora alterações da falha possam ter sido introduzidas na versão 2.0, uma dependência de versão do limite superior ou estrita garantirá um erro.</span><span class="sxs-lookup"><span data-stu-id="01e51-132">While breaking changes may have been introduced in version 2.0, a strict or upper limit version dependency guarantees an error.</span></span>

<span data-ttu-id="01e51-133">![Conflitos de dependência de losango](./media/dependencies/diamond-dependency-conflict.png "Conflito de dependência de losango")</span><span class="sxs-lookup"><span data-stu-id="01e51-133">![Diamond dependency conflict](./media/dependencies/diamond-dependency-conflict.png "Diamond dependency conflict")</span></span>

<span data-ttu-id="01e51-134">**❌ NÃO** tenha referências de pacote do NuGet sem versão mínima.</span><span class="sxs-lookup"><span data-stu-id="01e51-134">**❌ DO NOT** have NuGet package references with no minimum version.</span></span>

<span data-ttu-id="01e51-135">**❌ EVITAR** referências do pacote NuGet que demandam uma versão exata.</span><span class="sxs-lookup"><span data-stu-id="01e51-135">**❌ AVOID** NuGet package references that demand an exact version.</span></span>

<span data-ttu-id="01e51-136">**❌ EVITE** referências ao pacote NuGet com um limite superior de versão.</span><span class="sxs-lookup"><span data-stu-id="01e51-136">**❌ AVOID** NuGet package references with a version upper limit.</span></span>

## <a name="nuget-shared-source-packages"></a><span data-ttu-id="01e51-137">Pacotes de código-fonte compartilhado do NuGet</span><span class="sxs-lookup"><span data-stu-id="01e51-137">NuGet shared source packages</span></span>

<span data-ttu-id="01e51-138">Uma maneira de reduzir as dependências externas do pacote NuGet é fazer referência a pacotes de origem compartilhados.</span><span class="sxs-lookup"><span data-stu-id="01e51-138">One way to reduce external NuGet package dependencies is to reference shared source packages.</span></span> <span data-ttu-id="01e51-139">Um pacote de origem compartilhado contém [arquivos de código-fonte](/nuget/reference/nuspec#including-content-files) incluídos em um projeto quando referenciados.</span><span class="sxs-lookup"><span data-stu-id="01e51-139">A shared source package contains [source code files](/nuget/reference/nuspec#including-content-files) that are included in a project when referenced.</span></span> <span data-ttu-id="01e51-140">Como você está apenas incluindo arquivos de código-fonte compilados com o restante do seu projeto, não há dependência externa nem chance de conflito.</span><span class="sxs-lookup"><span data-stu-id="01e51-140">Because you're just including source code files that are compiled with the rest of your project, there's no external dependency and chance of conflict.</span></span>

<span data-ttu-id="01e51-141">Pacotes de origem compartilhados são ótimos para incluir pequenas funcionalidades.</span><span class="sxs-lookup"><span data-stu-id="01e51-141">Shared source packages are great for including small pieces of functionality.</span></span> <span data-ttu-id="01e51-142">Por exemplo, um pacote origem compartilhado de métodos auxiliares para fazer chamadas HTTP.</span><span class="sxs-lookup"><span data-stu-id="01e51-142">For example, a shared source package of helper methods for making HTTP calls.</span></span>

<span data-ttu-id="01e51-143">![Pacote de origem compartilhado](./media/dependencies/shared-source-package.png "Pacote de origem compartilhado")</span><span class="sxs-lookup"><span data-stu-id="01e51-143">![Shared source package](./media/dependencies/shared-source-package.png "Shared source package")</span></span>

```xml
<PackageReference Include="Microsoft.Extensions.Buffers.Testing.Sources" PrivateAssets="All" Version="1.0" />
```

<span data-ttu-id="01e51-144">![Projeto de origem compartilhado](./media/dependencies/shared-source-project.png "Projeto de origem compartilhado")</span><span class="sxs-lookup"><span data-stu-id="01e51-144">![Shared source project](./media/dependencies/shared-source-project.png "Shared source project")</span></span>

<span data-ttu-id="01e51-145">Pacotes de origem compartilhado têm algumas limitações.</span><span class="sxs-lookup"><span data-stu-id="01e51-145">Shared source packages have some limitations.</span></span> <span data-ttu-id="01e51-146">Eles só podem ser referenciados por `PackageReference`, portanto, projetos `packages.config` mais antigos são excluídos.</span><span class="sxs-lookup"><span data-stu-id="01e51-146">They can only be referenced by `PackageReference`, so older `packages.config` projects are excluded.</span></span> <span data-ttu-id="01e51-147">Também pacotes de origem compartilhados somente são utilizáveis por projetos com o mesmo tipo de linguagem.</span><span class="sxs-lookup"><span data-stu-id="01e51-147">Also shared source packages are only usable by projects with the same language type.</span></span> <span data-ttu-id="01e51-148">Devido a essas limitações, pacotes de origem compartilhados são melhor usados para compartilhar a funcionalidade dentro de um projeto de código-fonte aberto.</span><span class="sxs-lookup"><span data-stu-id="01e51-148">Because of these limitations shared source packages are best used to share functionality within an open-source project.</span></span>

<span data-ttu-id="01e51-149">**✔️ CONSIDERE** fazer referência a de código-fonte compartilhados para pequenas funcionalidades internas.</span><span class="sxs-lookup"><span data-stu-id="01e51-149">**✔️ CONSIDER** referencing shared source packages for small, internal pieces of functionality.</span></span>

<span data-ttu-id="01e51-150">**✔️ CONSIDERE** tornar seu pacote de um pacote de origem compartilhado se ele oferecer pequenas funcionalidades internas.</span><span class="sxs-lookup"><span data-stu-id="01e51-150">**✔️ CONSIDER** making your package a shared source package if it provides small, internal pieces of functionality.</span></span>

<span data-ttu-id="01e51-151">**✔️ FAÇA** referência a pacotes de origem compartilhados com `PrivateAssets="All"`.</span><span class="sxs-lookup"><span data-stu-id="01e51-151">**✔️ DO** reference shared source packages with `PrivateAssets="All"`.</span></span>

> <span data-ttu-id="01e51-152">Essa configuração informa que o pacote do NuGet deve ser usado apenas no tempo de desenvolvimento e não deve ser exposto como uma dependência pública.</span><span class="sxs-lookup"><span data-stu-id="01e51-152">This setting tells NuGet the package is only to be used at development time and shouldn't be exposed as a public dependency.</span></span>

<span data-ttu-id="01e51-153">**❌ NÃO** tenha tipos de pacote de origem compartilhados na sua API pública.</span><span class="sxs-lookup"><span data-stu-id="01e51-153">**❌ DO NOT** have shared source package types in your public API.</span></span>

> <span data-ttu-id="01e51-154">Tipos de origem compartilhada são compilados no assembly de referência e não podem ser trocados entre os limites de assembly.</span><span class="sxs-lookup"><span data-stu-id="01e51-154">Shared source types are compiled into the referencing assembly and can't be exchanged across assembly boundaries.</span></span> <span data-ttu-id="01e51-155">Por exemplo, um tipo `IRepository` de origem compartilhada em um projeto é um tipo separado do mesmo `IRepository` de origem compartilhada em outro projeto.</span><span class="sxs-lookup"><span data-stu-id="01e51-155">For example, a shared-source `IRepository` type in one project is a separate type from the same shared-source `IRepository` in another project.</span></span> <span data-ttu-id="01e51-156">Tipos em pacotes de origem compartilhados devem ter uma visibilidade `internal`.</span><span class="sxs-lookup"><span data-stu-id="01e51-156">Types in shared source packages should have an `internal` visibility.</span></span>

<span data-ttu-id="01e51-157">**❌ NÃO** publique pacotes de origem compartilhados em NuGet.org.</span><span class="sxs-lookup"><span data-stu-id="01e51-157">**❌ DO NOT** publish shared source packages to NuGet.org.</span></span>

> <span data-ttu-id="01e51-158">Pacotes de origem compartilhados contêm código-fonte e só podem ser usados por projetos com o mesmo tipo de linguagem.</span><span class="sxs-lookup"><span data-stu-id="01e51-158">Shared source packages contain source code and can only be used by projects with the same language type.</span></span> <span data-ttu-id="01e51-159">Por exemplo, um pacote de origem compartilhado em C# não pode ser usado por um aplicativo em F#.</span><span class="sxs-lookup"><span data-stu-id="01e51-159">For example, a C# shared source package cannot be used by an F# application.</span></span>
>
> <span data-ttu-id="01e51-160">Publicar pacotes de origem compartilhados em um [feed local ou no MyGet](./publish-nuget-package.md) para consumi-los internamente dentro de seu projeto.</span><span class="sxs-lookup"><span data-stu-id="01e51-160">Publish shared source packages to a [local feed or MyGet](./publish-nuget-package.md) to consume them internally within your project.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="01e51-161">[Anterior](nuget.md)
>[Próximo](sourcelink.md)</span><span class="sxs-lookup"><span data-stu-id="01e51-161">[Previous](nuget.md)
[Next](sourcelink.md)</span></span>