---
ms.openlocfilehash: 975e331ad3e7bd7e0e8f49b62795c6acc7031ca9
ms.sourcegitcommit: 1e8382d0ce8b5515864f8fbb178b9fd692a7503f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2020
ms.locfileid: "89656322"
---
### <a name="winforms-and-wpf-apps-use-microsoftnetsdk"></a><span data-ttu-id="71957-101">Os aplicativos WinForms e WPF usam Microsoft. NET. Sdk</span><span class="sxs-lookup"><span data-stu-id="71957-101">WinForms and WPF apps use Microsoft.NET.Sdk</span></span>

<span data-ttu-id="71957-102">Os aplicativos Windows Forms e Windows Presentation Framework (WPF) agora usam o SDK do .NET ( `Microsoft.NET.Sdk` ) em vez do .NET Core WinForms e do SDK do WPF ( `Microsoft.NET.Sdk.WindowsDesktop` ).</span><span class="sxs-lookup"><span data-stu-id="71957-102">Windows Forms and Windows Presentation Framework (WPF) apps now use the .NET SDK (`Microsoft.NET.Sdk`) instead of the .NET Core WinForms and WPF SDK (`Microsoft.NET.Sdk.WindowsDesktop`).</span></span>

#### <a name="change-description"></a><span data-ttu-id="71957-103">Descrição das alterações</span><span class="sxs-lookup"><span data-stu-id="71957-103">Change description</span></span>

<span data-ttu-id="71957-104">Nas versões anteriores do .NET Core, os aplicativos WinForms e WPF usavam um [SDK de projeto](../../../../docs/core/project-sdk/overview.md) separado ( `Microsoft.NET.Sdk.WindowsDesktop` ).</span><span class="sxs-lookup"><span data-stu-id="71957-104">In previous .NET Core versions, WinForms and WPF apps used a separate [project SDK](../../../../docs/core/project-sdk/overview.md) (`Microsoft.NET.Sdk.WindowsDesktop`).</span></span> <span data-ttu-id="71957-105">A partir do .NET 5,0, o SDK do WinForms e do WPF foi unificado com o SDK do .NET ( `Microsoft.NET.Sdk` ).</span><span class="sxs-lookup"><span data-stu-id="71957-105">Starting in .NET 5.0, the WinForms and WPF SDK has been unified with the .NET SDK (`Microsoft.NET.Sdk`).</span></span> <span data-ttu-id="71957-106">Além disso, novos [monikers do Framework de destino (TFM)](../../../../docs/standard/frameworks.md) substituem `netcoreapp` e `netstandard` no .NET 5.</span><span class="sxs-lookup"><span data-stu-id="71957-106">In addition, new [target framework monikers (TFM)](../../../../docs/standard/frameworks.md) replace `netcoreapp` and `netstandard` in .NET 5.</span></span> <span data-ttu-id="71957-107">O exemplo a seguir mostra as alterações que você precisaria fazer para um arquivo de projeto do WPF ao redirecionar para o .NET 5,0 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="71957-107">The following example shows the changes you'd need to make for a WPF project file when retargeting to .NET 5.0 or later.</span></span>

<span data-ttu-id="71957-108">Nas versões anteriores do .NET Core:</span><span class="sxs-lookup"><span data-stu-id="71957-108">In previous .NET Core versions:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.1</TargetFramework>
    <UseWPF>true</UseWPF>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="71957-109">No .NET 5,0 e versões posteriores:</span><span class="sxs-lookup"><span data-stu-id="71957-109">In .NET 5.0 and later versions:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>net5.0-windows</TargetFramework>
    <UseWPF>true</UseWPF>
  </PropertyGroup>

</Project>
```

#### <a name="version-introduced"></a><span data-ttu-id="71957-110">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="71957-110">Version introduced</span></span>

<span data-ttu-id="71957-111">.NET 5,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="71957-111">.NET 5.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="71957-112">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="71957-112">Recommended action</span></span>

<span data-ttu-id="71957-113">No seu arquivo de projeto do WPF ou Windows Forms:</span><span class="sxs-lookup"><span data-stu-id="71957-113">In your WPF or Windows Forms project file:</span></span>

- <span data-ttu-id="71957-114">Atualize o `Sdk` atributo para `Microsoft.NET.Sdk` .</span><span class="sxs-lookup"><span data-stu-id="71957-114">Update the `Sdk` attribute  to `Microsoft.NET.Sdk`.</span></span>
- <span data-ttu-id="71957-115">Atualize a `TargetFramework` propriedade para `net5.0-windows` .</span><span class="sxs-lookup"><span data-stu-id="71957-115">Update the `TargetFramework` property to `net5.0-windows`.</span></span>

#### <a name="category"></a><span data-ttu-id="71957-116">Categoria</span><span class="sxs-lookup"><span data-stu-id="71957-116">Category</span></span>

- <span data-ttu-id="71957-117">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="71957-117">Windows Forms</span></span>
- <span data-ttu-id="71957-118">Windows Presentation Framework (WPF)</span><span class="sxs-lookup"><span data-stu-id="71957-118">Windows Presentation Framework (WPF)</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="71957-119">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="71957-119">Affected APIs</span></span>

<span data-ttu-id="71957-120">Não detectável via análise de API.</span><span class="sxs-lookup"><span data-stu-id="71957-120">Not detectable via API analysis.</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis.

-->
