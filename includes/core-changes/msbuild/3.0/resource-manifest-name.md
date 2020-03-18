---
ms.openlocfilehash: 16ee73bfc0ab33b04ea3e2fa6d0eec521a9b8634
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78968253"
---
### <a name="resource-manifest-file-names"></a><span data-ttu-id="41f0d-101">Nomes de arquivos de manifesto de recursos</span><span class="sxs-lookup"><span data-stu-id="41f0d-101">Resource manifest file names</span></span>

<span data-ttu-id="41f0d-102">A partir do .NET Core 3.0, o nome do arquivo de manifesto de recurso gerado foi alterado.</span><span class="sxs-lookup"><span data-stu-id="41f0d-102">Starting in .NET Core 3.0, the generated resource manifest file name has changed.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="41f0d-103">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="41f0d-103">Version introduced</span></span>

<span data-ttu-id="41f0d-104">3.0</span><span class="sxs-lookup"><span data-stu-id="41f0d-104">3.0</span></span>

#### <a name="change-description"></a><span data-ttu-id="41f0d-105">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="41f0d-105">Change description</span></span>

<span data-ttu-id="41f0d-106">Antes do .NET Core 3.0, quando [dependentUpon](/visualstudio/msbuild/common-msbuild-project-items#compile) metadata foi definido para um arquivo de recurso *(.resx)* no arquivo do projeto MSBuild, o nome do manifesto gerado era *Namespace.Classname.resources*.</span><span class="sxs-lookup"><span data-stu-id="41f0d-106">Prior to .NET Core 3.0, when [DependentUpon](/visualstudio/msbuild/common-msbuild-project-items#compile) metadata was set for a resource (*.resx*) file in the MSBuild project file, the generated manifest name was *Namespace.Classname.resources*.</span></span> <span data-ttu-id="41f0d-107">Quando [DependentUpon](/visualstudio/msbuild/common-msbuild-project-items#compile) não foi definido, o nome do manifesto gerado era *Namespace.Classname.FolderPathRelativeToRoot.Culture.resources*.</span><span class="sxs-lookup"><span data-stu-id="41f0d-107">When [DependentUpon](/visualstudio/msbuild/common-msbuild-project-items#compile) was not set, the generated manifest name was *Namespace.Classname.FolderPathRelativeToRoot.Culture.resources*.</span></span>

<span data-ttu-id="41f0d-108">A partir do .NET Core 3.0, quando um arquivo *.resx* é localizado com um arquivo de origem de mesmo nome, por exemplo, nos aplicativos Do Windows Forms, o nome do manifesto de recursos é gerado a partir do nome completo do primeiro tipo no arquivo de origem.</span><span class="sxs-lookup"><span data-stu-id="41f0d-108">Starting in .NET Core 3.0, when a *.resx* file is colocated with a source file of the same name, for example, in Windows Forms apps, the resource manifest name is generated from the full name of the first type in the source file.</span></span> <span data-ttu-id="41f0d-109">Por exemplo, se *Type.cs* for localizado com *Type.resx,* o nome do manifesto gerado é *Namespace.Classname.resources*.</span><span class="sxs-lookup"><span data-stu-id="41f0d-109">For example, if *Type.cs* is colocated with *Type.resx*, the generated manifest name is *Namespace.Classname.resources*.</span></span> <span data-ttu-id="41f0d-110">No entanto, se você modificar `EmbeddedResource` qualquer um dos atributos na propriedade para o arquivo *.resx,* o nome do arquivo manifesto gerado pode ser diferente:</span><span class="sxs-lookup"><span data-stu-id="41f0d-110">However, if you modify any of the attributes on the `EmbeddedResource` property for the *.resx* file, the generated manifest file name may be different:</span></span>

- <span data-ttu-id="41f0d-111">Se `LogicalName` o atributo na `EmbeddedResource` propriedade for definido, esse valor será usado como o nome do arquivo manifesto de recursos.</span><span class="sxs-lookup"><span data-stu-id="41f0d-111">If the `LogicalName` attribute on the `EmbeddedResource` property is set, that value is used as the resource manifest file name.</span></span>

  <span data-ttu-id="41f0d-112">Exemplos:</span><span class="sxs-lookup"><span data-stu-id="41f0d-112">Examples:</span></span>

  ```xml
  <EmbeddedResource Include="X.resx" LogicalName="SomeName.resources" />
  -or-
  <EmbeddedResource Include="X.fr-FR.resx" LogicalName="SomeName.resources" />
  ```

  <span data-ttu-id="41f0d-113">**Nome do arquivo de manifesto de recursos gerado**: *SomeName.resources* (independentemente do nome ou cultura do arquivo *.resx* ou qualquer outro metadados).</span><span class="sxs-lookup"><span data-stu-id="41f0d-113">**Generated resource manifest file name**: *SomeName.resources* (regardless of the *.resx* file name or culture or any other metadata).</span></span>

- <span data-ttu-id="41f0d-114">Se `LogicalName` não for definido, mas o atributo `ManifestResourceName` na `EmbeddedResource` propriedade for definido, seu valor, combinado com a extensão de arquivo *.resources,* é usado como o nome do arquivo manifesto de recursos.</span><span class="sxs-lookup"><span data-stu-id="41f0d-114">If `LogicalName` is not set, but the `ManifestResourceName` attribute on the `EmbeddedResource` property is set, its value, combined with the file extension *.resources*, is used as the resource manifest file name.</span></span>

  <span data-ttu-id="41f0d-115">Exemplos:</span><span class="sxs-lookup"><span data-stu-id="41f0d-115">Examples:</span></span>

  ```xml
  <EmbeddedResource Include="X.resx" ManifestResourceName="SomeName" />
  -or-
  <EmbeddedResource Include="X.fr-FR.resx" ManifestResourceName="SomeName.fr-FR" />
  ```

  <span data-ttu-id="41f0d-116">**Nome do arquivo de manifesto de recursos gerado:** *SomeName.resources* ou *SomeName.fr-FR.resources*.</span><span class="sxs-lookup"><span data-stu-id="41f0d-116">**Generated resource manifest file name**: *SomeName.resources* or *SomeName.fr-FR.resources*.</span></span>

- <span data-ttu-id="41f0d-117">Se as regras anteriores não `DependentUpon` se aplicarem e o atributo no `EmbeddedResource` elemento for definido como um arquivo de origem, o nome de tipo da primeira classe no arquivo de origem será usado no nome do arquivo manifesto de recursos.</span><span class="sxs-lookup"><span data-stu-id="41f0d-117">If the previous rules don't apply, and the `DependentUpon` attribute on the `EmbeddedResource` element is set to a source file, the type name of the first class in the source file is used in the resource manifest file name.</span></span> <span data-ttu-id="41f0d-118">Mais especificamente, o nome do arquivo gerado é *\[Namespace.Classname . Cultura].recursos*.</span><span class="sxs-lookup"><span data-stu-id="41f0d-118">More specifically, the generated file name is *Namespace.Classname\[.Culture].resources*.</span></span>

  <span data-ttu-id="41f0d-119">Exemplos:</span><span class="sxs-lookup"><span data-stu-id="41f0d-119">Examples:</span></span>

  ```xml
  <EmbeddedResource Include="X.resx" DependentUpon="MyTypes.cs">
  -or-
  <EmbeddedResource Include="X.fr-FR.resx" DependentUpon="MyTypes.cs">
  ```

  <span data-ttu-id="41f0d-120">**Nomea** *namespace.classname.resources* ou *recursos Namespace.Classname.fr-FR.(onde* `Namespace.Classname` está o nome da primeira classe em *MyTypes.cs*).</span><span class="sxs-lookup"><span data-stu-id="41f0d-120">**Generated resource manifest file name**: *Namespace.Classname.resources* or *Namespace.Classname.fr-FR.resources* (where `Namespace.Classname` is the name of the first class in *MyTypes.cs*).</span></span>

- <span data-ttu-id="41f0d-121">Se as regras anteriores `EmbeddedResourceUseDependentUponConvention` não `true` se aplicarem, é (o padrão para .NET Core), e há um arquivo de origem localizado com um arquivo *.resx* que tem o mesmo nome de arquivo base, o arquivo *.resx* é feito dependendo do arquivo de origem correspondente, e o nome gerado é o mesmo que na regra anterior.</span><span class="sxs-lookup"><span data-stu-id="41f0d-121">If the previous rules don't apply, `EmbeddedResourceUseDependentUponConvention` is `true` (the default for .NET Core), and there's a source file colocated with a *.resx* file that has the same base file name, the *.resx* file is made dependent upon the matching source file, and the generated name is the same as in the previous rule.</span></span> <span data-ttu-id="41f0d-122">Esta é a regra "configurações padrão" para projetos .NET Core.</span><span class="sxs-lookup"><span data-stu-id="41f0d-122">This is the "default settings" rule for .NET Core projects.</span></span>
  
  <span data-ttu-id="41f0d-123">Exemplos:</span><span class="sxs-lookup"><span data-stu-id="41f0d-123">Examples:</span></span>
  
  <span data-ttu-id="41f0d-124">Os *arquivos MyTypes.cs* e *MyTypes.resx* ou *MyTypes.fr-FR.resx* existem na mesma pasta.</span><span class="sxs-lookup"><span data-stu-id="41f0d-124">Files *MyTypes.cs* and *MyTypes.resx* or *MyTypes.fr-FR.resx* exist in the same folder.</span></span>
  
  <span data-ttu-id="41f0d-125">**Nomea** *namespace.classname.resources* ou *recursos Namespace.Classname.fr-FR.(onde* `Namespace.Classname` está o nome da primeira classe em *MyTypes.cs*).</span><span class="sxs-lookup"><span data-stu-id="41f0d-125">**Generated resource manifest file name**: *Namespace.Classname.resources* or *Namespace.Classname.fr-FR.resources* (where `Namespace.Classname` is the name of the first class in *MyTypes.cs*).</span></span>

- <span data-ttu-id="41f0d-126">Se nenhuma das regras anteriores se aplicar, o nome do arquivo de manifesto de recurso gerado é *RootNamespace.RelativePathWithDotsForSlashes.\[ Cultura.] recursos*.</span><span class="sxs-lookup"><span data-stu-id="41f0d-126">If none of the previous rules apply, the generated resource manifest file name is *RootNamespace.RelativePathWithDotsForSlashes.\[Culture.]resources*.</span></span> <span data-ttu-id="41f0d-127">O caminho relativo é `Link` o `EmbeddedResource` valor do atributo do elemento se ele estiver definido.</span><span class="sxs-lookup"><span data-stu-id="41f0d-127">The relative path is the value of the `Link` attribute of the `EmbeddedResource` element if it's set.</span></span> <span data-ttu-id="41f0d-128">Caso contrário, o caminho relativo `Identity` é `EmbeddedResource` o valor do atributo do elemento.</span><span class="sxs-lookup"><span data-stu-id="41f0d-128">Otherwise, the relative path is the value of the `Identity` attribute of the `EmbeddedResource` element.</span></span> <span data-ttu-id="41f0d-129">No Visual Studio, este é o caminho da raiz do projeto para o arquivo no Solution Explorer.</span><span class="sxs-lookup"><span data-stu-id="41f0d-129">In Visual Studio, this is the path from the project root to the file in Solution Explorer.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="41f0d-130">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="41f0d-130">Recommended action</span></span>

<span data-ttu-id="41f0d-131">Se você não está satisfeito com os nomes manifestos gerados, você pode:</span><span class="sxs-lookup"><span data-stu-id="41f0d-131">If you're unsatisfied with the generated manifest names, you can:</span></span>

- <span data-ttu-id="41f0d-132">Modifique os metadados do arquivo de recursos de acordo com uma das regras de nomeação descritas anteriormente.</span><span class="sxs-lookup"><span data-stu-id="41f0d-132">Modify your resource file metadata according to one of the previously described naming rules.</span></span>

- <span data-ttu-id="41f0d-133">`EmbeddedResourceUseDependentUponConvention` Defina `false` em seu arquivo de projeto para desativar totalmente a nova convenção:</span><span class="sxs-lookup"><span data-stu-id="41f0d-133">Set `EmbeddedResourceUseDependentUponConvention` to `false` in your project file to opt out of the new convention entirely:</span></span>

   ```xml
   <EmbeddedResourceUseDependentUponConvention>false</EmbeddedResourceUseDependentUponConvention>
   ```

   > [!NOTE]
   > <span data-ttu-id="41f0d-134">Se `LogicalName` os `ManifestResourceName` atributos estiverem presentes, seus valores ainda serão usados para o nome do arquivo gerado.</span><span class="sxs-lookup"><span data-stu-id="41f0d-134">If the `LogicalName` or `ManifestResourceName` attributes are present, their values will still be used for the generated file name.</span></span>

#### <a name="category"></a><span data-ttu-id="41f0d-135">Categoria</span><span class="sxs-lookup"><span data-stu-id="41f0d-135">Category</span></span>

<span data-ttu-id="41f0d-136">MSBuild</span><span class="sxs-lookup"><span data-stu-id="41f0d-136">MSBuild</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="41f0d-137">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="41f0d-137">Affected APIs</span></span>

<span data-ttu-id="41f0d-138">N/D</span><span class="sxs-lookup"><span data-stu-id="41f0d-138">N/A</span></span>
