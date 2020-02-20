---
ms.openlocfilehash: 276268d31670b5e7dcd0ae9c0b7a61c3c38ca663
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77451871"
---
### <a name="resource-manifest-file-names"></a><span data-ttu-id="d9da0-101">Nomes de arquivo de manifesto de recurso</span><span class="sxs-lookup"><span data-stu-id="d9da0-101">Resource manifest file names</span></span>

<span data-ttu-id="d9da0-102">A partir do .NET Core 3,0, o nome do arquivo de manifesto do recurso gerado foi alterado.</span><span class="sxs-lookup"><span data-stu-id="d9da0-102">Starting in .NET Core 3.0, the generated resource manifest file name has changed.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d9da0-103">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="d9da0-103">Version introduced</span></span>

<span data-ttu-id="d9da0-104">3.0</span><span class="sxs-lookup"><span data-stu-id="d9da0-104">3.0</span></span>

#### <a name="change-description"></a><span data-ttu-id="d9da0-105">Alterar descrição</span><span class="sxs-lookup"><span data-stu-id="d9da0-105">Change description</span></span>

<span data-ttu-id="d9da0-106">Antes do .NET Core 3,0, quando os metadados do [DependentUpon](/visualstudio/msbuild/common-msbuild-project-items#compile) eram definidos para um arquivo de recurso ( *. resx*) no arquivo de projeto do MSBuild, o nome do manifesto gerado era *namespace. ClassName. Resources*.</span><span class="sxs-lookup"><span data-stu-id="d9da0-106">Prior to .NET Core 3.0, when [DependentUpon](/visualstudio/msbuild/common-msbuild-project-items#compile) metadata was set for a resource (*.resx*) file in the MSBuild project file, the generated manifest name was *Namespace.Classname.resources*.</span></span> <span data-ttu-id="d9da0-107">Quando [DependentUpon](/visualstudio/msbuild/common-msbuild-project-items#compile) não foi definido, o nome de manifesto gerado era *namespace. ClassName. FolderPathRelativeToRoot. Culture. Resources*.</span><span class="sxs-lookup"><span data-stu-id="d9da0-107">When [DependentUpon](/visualstudio/msbuild/common-msbuild-project-items#compile) was not set, the generated manifest name was *Namespace.Classname.FolderPathRelativeToRoot.Culture.resources*.</span></span>

<span data-ttu-id="d9da0-108">A partir do .NET Core 3,0, quando um arquivo *. resx* é colocado com um arquivo de origem com o mesmo nome, por exemplo, em aplicativos Windows Forms, o nome do manifesto do recurso é gerado a partir do nome completo do primeiro tipo no arquivo de origem.</span><span class="sxs-lookup"><span data-stu-id="d9da0-108">Starting in .NET Core 3.0, when a *.resx* file is colocated with a source file of the same name, for example, in Windows Forms apps, the resource manifest name is generated from the full name of the first type in the source file.</span></span> <span data-ttu-id="d9da0-109">Por exemplo, se *Type.cs* estiver colocalizado com *Type. resx*, o nome de manifesto gerado será *namespace. ClassName. Resources*.</span><span class="sxs-lookup"><span data-stu-id="d9da0-109">For example, if *Type.cs* is colocated with *Type.resx*, the generated manifest name is *Namespace.Classname.resources*.</span></span> <span data-ttu-id="d9da0-110">No entanto, se você modificar qualquer um dos atributos na propriedade `EmbeddedResource` para o arquivo *. resx* , o nome do arquivo de manifesto gerado poderá ser diferente:</span><span class="sxs-lookup"><span data-stu-id="d9da0-110">However, if you modify any of the attributes on the `EmbeddedResource` property for the *.resx* file, the generated manifest file name may be different:</span></span>

- <span data-ttu-id="d9da0-111">Se o atributo `LogicalName` na propriedade `EmbeddedResource` for definido, esse valor será usado como o nome do arquivo de manifesto do recurso.</span><span class="sxs-lookup"><span data-stu-id="d9da0-111">If the `LogicalName` attribute on the `EmbeddedResource` property is set, that value is used as the resource manifest file name.</span></span>

  <span data-ttu-id="d9da0-112">Exemplos:</span><span class="sxs-lookup"><span data-stu-id="d9da0-112">Examples:</span></span>

  ```xml
  <EmbeddedResource Include="X.resx" LogicalName="SomeName.resources" />
  -or-
  <EmbeddedResource Include="X.fr-FR.resx" LogicalName="SomeName.resources" />
  ```

  <span data-ttu-id="d9da0-113">**Nome do arquivo de manifesto de recurso gerado**: *somename. Resources* (independentemente do nome do arquivo *. resx* ou da cultura ou de qualquer outro metadado).</span><span class="sxs-lookup"><span data-stu-id="d9da0-113">**Generated resource manifest file name**: *SomeName.resources* (regardless of the *.resx* file name or culture or any other metadata).</span></span>

- <span data-ttu-id="d9da0-114">Se `LogicalName` não estiver definido, mas o atributo `ManifestResourceName` na propriedade `EmbeddedResource` for definido, seu valor, combinado com a extensão de arquivo *. Resources*, será usado como o nome do arquivo de manifesto de recurso.</span><span class="sxs-lookup"><span data-stu-id="d9da0-114">If `LogicalName` is not set, but the `ManifestResourceName` attribute on the `EmbeddedResource` property is set, its value, combined with the file extension *.resources*, is used as the resource manifest file name.</span></span>

  <span data-ttu-id="d9da0-115">Exemplos:</span><span class="sxs-lookup"><span data-stu-id="d9da0-115">Examples:</span></span>

  ```xml
  <EmbeddedResource Include="X.resx" ManifestResourceName="SomeName" />
  -or-
  <EmbeddedResource Include="X.fr-FR.resx" ManifestResourceName="SomeName.fr-FR" />
  ```

  <span data-ttu-id="d9da0-116">**Nome do arquivo de manifesto de recurso gerado**: *somename. Resources* ou *somename.fr-fr. Resources*.</span><span class="sxs-lookup"><span data-stu-id="d9da0-116">**Generated resource manifest file name**: *SomeName.resources* or *SomeName.fr-FR.resources*.</span></span>

- <span data-ttu-id="d9da0-117">Se as regras anteriores não se aplicarem e o atributo `DependentUpon` no elemento `EmbeddedResource` for definido como um arquivo de origem, o nome do tipo da primeira classe no arquivo de origem será usado no nome do arquivo de manifesto do recurso.</span><span class="sxs-lookup"><span data-stu-id="d9da0-117">If the previous rules don't apply, and the `DependentUpon` attribute on the `EmbeddedResource` element is set to a source file, the type name of the first class in the source file is used in the resource manifest file name.</span></span> <span data-ttu-id="d9da0-118">Mais especificamente, o nome de arquivo gerado é *namespace. Classname\[. Culture]. Resources*.</span><span class="sxs-lookup"><span data-stu-id="d9da0-118">More specifically, the generated file name is *Namespace.Classname\[.Culture].resources*.</span></span>

  <span data-ttu-id="d9da0-119">Exemplos:</span><span class="sxs-lookup"><span data-stu-id="d9da0-119">Examples:</span></span>

  ```xml
  <EmbeddedResource Include="X.resx" DependentUpon="MyTypes.cs">
  -or-
  <EmbeddedResource Include="X.fr-FR.resx" DependentUpon="MyTypes.cs">
  ```

  <span data-ttu-id="d9da0-120">**Nome do arquivo de manifesto de recurso gerado**: *namespace. ClassName. Resources* ou *namespace.ClassName.fr-fr. Resources* (em que `Namespace.Classname` é o nome da primeira classe em *myTypes.cs*).</span><span class="sxs-lookup"><span data-stu-id="d9da0-120">**Generated resource manifest file name**: *Namespace.Classname.resources* or *Namespace.Classname.fr-FR.resources* (where `Namespace.Classname` is the name of the first class in *MyTypes.cs*).</span></span>

- <span data-ttu-id="d9da0-121">Se as regras anteriores não se aplicarem, `EmbeddedResourceUseDependentUponConvention` é `true` (o padrão para .NET Core) e há um arquivo de origem colocalizado com um arquivo *. resx* que tem o mesmo nome de arquivo base, o arquivo *. resx* é tornado dependente do arquivo de origem correspondente e o nome gerado é o mesmo da regra anterior.</span><span class="sxs-lookup"><span data-stu-id="d9da0-121">If the previous rules don't apply, `EmbeddedResourceUseDependentUponConvention` is `true` (the default for .NET Core), and there's a source file colocated with a *.resx* file that has the same base file name, the *.resx* file is made dependent upon the matching source file, and the generated name is the same as in the previous rule.</span></span> <span data-ttu-id="d9da0-122">Essa é a regra de "configurações padrão" para projetos do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d9da0-122">This is the "default settings" rule for .NET Core projects.</span></span>
  
  <span data-ttu-id="d9da0-123">Exemplos:</span><span class="sxs-lookup"><span data-stu-id="d9da0-123">Examples:</span></span>
  
  <span data-ttu-id="d9da0-124">Os arquivos *myTypes.cs* e *myTypes. resx* ou *myTypes.fr-fr. resx* existem na mesma pasta.</span><span class="sxs-lookup"><span data-stu-id="d9da0-124">Files *MyTypes.cs* and *MyTypes.resx* or *MyTypes.fr-FR.resx* exist in the same folder.</span></span>
  
  <span data-ttu-id="d9da0-125">**Nome do arquivo de manifesto de recurso gerado**: *namespace. ClassName. Resources* ou *namespace.ClassName.fr-fr. Resources* (em que `Namespace.Classname` é o nome da primeira classe em *myTypes.cs*).</span><span class="sxs-lookup"><span data-stu-id="d9da0-125">**Generated resource manifest file name**: *Namespace.Classname.resources* or *Namespace.Classname.fr-FR.resources* (where `Namespace.Classname` is the name of the first class in *MyTypes.cs*).</span></span>
    
- <span data-ttu-id="d9da0-126">Se nenhuma das regras anteriores se aplicar, o nome do arquivo de manifesto de recurso gerado será *RootNamespace. RelativePathWithDotsForSlashes.\[Culture.] recursos*do.</span><span class="sxs-lookup"><span data-stu-id="d9da0-126">If none of the previous rules apply, the generated resource manifest file name is *RootNamespace.RelativePathWithDotsForSlashes.\[Culture.]resources*.</span></span> <span data-ttu-id="d9da0-127">O caminho relativo é o valor do atributo `Link` do elemento `EmbeddedResource` se ele estiver definido.</span><span class="sxs-lookup"><span data-stu-id="d9da0-127">The relative path is the value of the `Link` attribute of the `EmbeddedResource` element if it's set.</span></span> <span data-ttu-id="d9da0-128">Caso contrário, o caminho relativo é o valor do atributo `Identity` do elemento `EmbeddedResource`.</span><span class="sxs-lookup"><span data-stu-id="d9da0-128">Otherwise, the relative path is the value of the `Identity` attribute of the `EmbeddedResource` element.</span></span> <span data-ttu-id="d9da0-129">No Visual Studio, esse é o caminho da raiz do projeto para o arquivo em Gerenciador de Soluções.</span><span class="sxs-lookup"><span data-stu-id="d9da0-129">In Visual Studio, this is the path from the project root to the file in Solution Explorer.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d9da0-130">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="d9da0-130">Recommended action</span></span>

<span data-ttu-id="d9da0-131">Se você não estiver satisfeito com os nomes de manifesto gerados, poderá:</span><span class="sxs-lookup"><span data-stu-id="d9da0-131">If you're unsatisfied with the generated manifest names, you can:</span></span>

- <span data-ttu-id="d9da0-132">Modifique os metadados do arquivo de recursos de acordo com uma das regras de nomenclatura descritas anteriormente.</span><span class="sxs-lookup"><span data-stu-id="d9da0-132">Modify your resource file metadata according to one of the previously described naming rules.</span></span>

- <span data-ttu-id="d9da0-133">Defina `EmbeddedResourceUseDependentUponConvention` para `false` no arquivo de projeto para recusar totalmente a nova Convenção:</span><span class="sxs-lookup"><span data-stu-id="d9da0-133">Set `EmbeddedResourceUseDependentUponConvention` to `false` in your project file to opt out of the new convention entirely:</span></span>

   ```xml
   <EmbeddedResourceUseDependentUponConvention>false</EmbeddedResourceUseDependentUponConvention>
   ```

   > [!NOTE]
   > <span data-ttu-id="d9da0-134">Se os atributos `LogicalName` ou `ManifestResourceName` estiverem presentes, seus valores ainda serão usados para o nome de arquivo gerado.</span><span class="sxs-lookup"><span data-stu-id="d9da0-134">If the `LogicalName` or `ManifestResourceName` attributes are present, their values will still be used for the generated file name.</span></span>

#### <a name="category"></a><span data-ttu-id="d9da0-135">Categoria</span><span class="sxs-lookup"><span data-stu-id="d9da0-135">Category</span></span>

<span data-ttu-id="d9da0-136">MSBuild</span><span class="sxs-lookup"><span data-stu-id="d9da0-136">MSBuild</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d9da0-137">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="d9da0-137">Affected APIs</span></span>

<span data-ttu-id="d9da0-138">N/D</span><span class="sxs-lookup"><span data-stu-id="d9da0-138">N/A</span></span>
