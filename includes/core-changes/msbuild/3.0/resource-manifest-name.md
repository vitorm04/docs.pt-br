---
ms.openlocfilehash: f24a29a00a1bff34a452c43716d76bf72ef277b5
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83206230"
---
### <a name="resource-manifest-file-name-change"></a><span data-ttu-id="8f0fd-101">Alteração de nome de arquivo de manifesto de recurso</span><span class="sxs-lookup"><span data-stu-id="8f0fd-101">Resource manifest file name change</span></span>

<span data-ttu-id="8f0fd-102">A partir do .NET Core 3,0, no caso padrão, o MSBuild gera um nome de arquivo de manifesto diferente para os arquivos de recurso.</span><span class="sxs-lookup"><span data-stu-id="8f0fd-102">Starting in .NET Core 3.0, in the default case, MSBuild generates a different manifest file name for resource files.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="8f0fd-103">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="8f0fd-103">Version introduced</span></span>

<span data-ttu-id="8f0fd-104">3.0</span><span class="sxs-lookup"><span data-stu-id="8f0fd-104">3.0</span></span>

#### <a name="change-description"></a><span data-ttu-id="8f0fd-105">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="8f0fd-105">Change description</span></span>

<span data-ttu-id="8f0fd-106">Antes do .NET Core 3,0, se nenhum `LogicalName` `ManifestResourceName` metadado, ou `DependentUpon` foi especificado para um `EmbeddedResource` item no arquivo de projeto, o MSBuild gerou um nome de arquivo de manifesto no padrão `<RootNamespace>.<ResourceFilePathFromProjectRoot>.resources` .</span><span class="sxs-lookup"><span data-stu-id="8f0fd-106">Prior to .NET Core 3.0, if no `LogicalName`, `ManifestResourceName`, or `DependentUpon` metadata was specified for an `EmbeddedResource` item in the project file, MSBuild generated a manifest file name in the pattern `<RootNamespace>.<ResourceFilePathFromProjectRoot>.resources`.</span></span> <span data-ttu-id="8f0fd-107">Se `RootNamespace` não estiver definido no arquivo de projeto, o padrão será o nome do projeto.</span><span class="sxs-lookup"><span data-stu-id="8f0fd-107">If `RootNamespace` is not defined in the project file, it defaults to the project name.</span></span> <span data-ttu-id="8f0fd-108">Por exemplo, o nome de manifesto gerado para um arquivo de recurso chamado *Form1. resx* no diretório do projeto raiz era *MyProject. Form1. Resources*.</span><span class="sxs-lookup"><span data-stu-id="8f0fd-108">For example, the generated manifest name for a resource file named *Form1.resx* in the root project directory was *MyProject.Form1.resources*.</span></span>

<span data-ttu-id="8f0fd-109">A partir do .NET Core 3,0, se um arquivo de recurso estiver colocalizado com um arquivo de origem com o mesmo nome (por exemplo, *Form1. resx* e *Form1.cs*), o MSBuild usará informações de tipo do arquivo de origem para gerar o nome do arquivo de manifesto no padrão `<Namespace>.<ClassName>.resources` .</span><span class="sxs-lookup"><span data-stu-id="8f0fd-109">Starting in .NET Core 3.0, if a resource file is colocated with a source file of the same name (for example, *Form1.resx* and *Form1.cs*), MSBuild uses type information from the source file to generate the manifest file name in the pattern `<Namespace>.<ClassName>.resources`.</span></span> <span data-ttu-id="8f0fd-110">O namespace e o nome da classe são extraídos do primeiro tipo no arquivo de origem colocalizado.</span><span class="sxs-lookup"><span data-stu-id="8f0fd-110">The namespace and class name are extracted from the first type in the colocated source file.</span></span> <span data-ttu-id="8f0fd-111">Por exemplo, o nome de manifesto gerado para um arquivo de recurso chamado *Form1. resx* que está colocalizado com um arquivo de origem chamado *Form1.cs* é *MyNamespace. Form1. Resources*.</span><span class="sxs-lookup"><span data-stu-id="8f0fd-111">For example, the generated manifest name for a resource file named *Form1.resx* that's colocated with a source file named *Form1.cs* is *MyNamespace.Form1.resources*.</span></span> <span data-ttu-id="8f0fd-112">O importante a observar é que a primeira parte do nome do arquivo é diferente para as versões anteriores do .NET Core (*MyNamespace* em vez de *MyProject*).</span><span class="sxs-lookup"><span data-stu-id="8f0fd-112">The key thing to note is that the first part of the file name is different to prior versions of .NET Core (*MyNamespace* instead of *MyProject*).</span></span>

> [!NOTE]
> <span data-ttu-id="8f0fd-113">Se você tiver `LogicalName` `ManifestResourceName` o, o ou os `DependentUpon` metadados especificados em um `EmbeddedResource` item no arquivo de projeto, essa alteração não afetará esse arquivo de recurso.</span><span class="sxs-lookup"><span data-stu-id="8f0fd-113">If you have `LogicalName`, `ManifestResourceName`, or `DependentUpon` metadata specified on an `EmbeddedResource` item in the project file, then this change does not affect that resource file.</span></span>

<span data-ttu-id="8f0fd-114">Essa alteração significativa foi introduzida com a adição da `EmbeddedResourceUseDependentUponConvention` Propriedade aos projetos do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8f0fd-114">This breaking change was introduced with the addition of the `EmbeddedResourceUseDependentUponConvention` property to .NET Core projects.</span></span> <span data-ttu-id="8f0fd-115">Por padrão, os arquivos de recurso não são explicitamente listados em um arquivo de projeto do .NET Core, portanto, não têm `DependentUpon` metadados para especificar como nomear o arquivo *. Resources* gerado.</span><span class="sxs-lookup"><span data-stu-id="8f0fd-115">By default, resource files aren't explicitly listed in a .NET Core project file, so they have no `DependentUpon` metadata to specify how to name the generated *.resources* file.</span></span> <span data-ttu-id="8f0fd-116">Quando `EmbeddedResourceUseDependentUponConvention` é definido como `true` , que é o padrão, o MSBuild procura um arquivo de origem colocalizado e extrai um namespace e um nome de classe desse arquivo.</span><span class="sxs-lookup"><span data-stu-id="8f0fd-116">When `EmbeddedResourceUseDependentUponConvention` is set to `true`, which is the default, MSBuild looks for a colocated source file and extracts a namespace and class name from that file.</span></span> <span data-ttu-id="8f0fd-117">Se você definir `EmbeddedResourceUseDependentUponConvention` como `false` , o MSBuild gerará o nome do manifesto de acordo com o comportamento anterior, que combina `RootNamespace` e o caminho do arquivo relativo.</span><span class="sxs-lookup"><span data-stu-id="8f0fd-117">If you set `EmbeddedResourceUseDependentUponConvention` to `false`, MSBuild generates the manifest name according to the previous behavior, which combines `RootNamespace` and the relative file path.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="8f0fd-118">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="8f0fd-118">Recommended action</span></span>

<span data-ttu-id="8f0fd-119">Na maioria dos casos, nenhuma ação é necessária na parte do desenvolvedor e seu aplicativo deve continuar a funcionar.</span><span class="sxs-lookup"><span data-stu-id="8f0fd-119">In most cases, no action is required on the part of the developer, and your app should continue to work.</span></span> <span data-ttu-id="8f0fd-120">No entanto, se essa alteração interromper seu aplicativo, você poderá:</span><span class="sxs-lookup"><span data-stu-id="8f0fd-120">However, if this change breaks your app, you can either:</span></span>

- <span data-ttu-id="8f0fd-121">Altere seu código para esperar o novo nome do manifesto.</span><span class="sxs-lookup"><span data-stu-id="8f0fd-121">Change your code to expect the new manifest name.</span></span>

- <span data-ttu-id="8f0fd-122">Cancele a nova Convenção de nomenclatura definindo `EmbeddedResourceUseDependentUponConvention` como `false` em seu arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="8f0fd-122">Opt out of the new naming convention by setting `EmbeddedResourceUseDependentUponConvention` to `false` in your project file.</span></span>

  ```xml
  <PropertyGroup>
    <EmbeddedResourceUseDependentUponConvention>false</EmbeddedResourceUseDependentUponConvention>
  </PropertyGroup>
  ```

#### <a name="category"></a><span data-ttu-id="8f0fd-123">Categoria</span><span class="sxs-lookup"><span data-stu-id="8f0fd-123">Category</span></span>

<span data-ttu-id="8f0fd-124">MSBuild</span><span class="sxs-lookup"><span data-stu-id="8f0fd-124">MSBuild</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="8f0fd-125">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="8f0fd-125">Affected APIs</span></span>

<span data-ttu-id="8f0fd-126">N/D</span><span class="sxs-lookup"><span data-stu-id="8f0fd-126">N/A</span></span>
