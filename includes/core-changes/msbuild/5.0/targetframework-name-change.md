---
ms.openlocfilehash: 1ddc2cea19872b44ff9659bcebd76117587ea89a
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92159477"
---
### <a name="targetframework-change-from-netcoreapp-to-net"></a><span data-ttu-id="ee801-101">TargetFramework alterar de netcoreapp para net</span><span class="sxs-lookup"><span data-stu-id="ee801-101">TargetFramework change from netcoreapp to net</span></span>

<span data-ttu-id="ee801-102">O valor da Propriedade MSBuild `TargetFramework` foi alterado de `netcoreapp3.1` para `net5.0` .</span><span class="sxs-lookup"><span data-stu-id="ee801-102">The value for the MSBuild `TargetFramework` property changed from `netcoreapp3.1` to `net5.0`.</span></span> <span data-ttu-id="ee801-103">Isso pode interromper o código que depende da análise do valor de `TargetFramework` .</span><span class="sxs-lookup"><span data-stu-id="ee801-103">This can break code that relies on parsing the value of `TargetFramework`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="ee801-104">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="ee801-104">Version introduced</span></span>

<span data-ttu-id="ee801-105">5.0</span><span class="sxs-lookup"><span data-stu-id="ee801-105">5.0</span></span>

#### <a name="change-description"></a><span data-ttu-id="ee801-106">Descrição das alterações</span><span class="sxs-lookup"><span data-stu-id="ee801-106">Change description</span></span>

<span data-ttu-id="ee801-107">No .NET Core 1,0-3,1, o valor da Propriedade MSBuild `TargetFramework` começa com `netcoreapp` , por exemplo, `netcoreapp3.1` para aplicativos direcionados ao .NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="ee801-107">In .NET Core 1.0 - 3.1, the value for the MSBuild `TargetFramework` property starts with `netcoreapp`, for example, `netcoreapp3.1` for apps that target .NET Core 3.1.</span></span> <span data-ttu-id="ee801-108">A partir do .NET 5,0, esse valor é simplificado apenas para começar `net` , por exemplo, `net5.0` para o .NET 5,0.</span><span class="sxs-lookup"><span data-stu-id="ee801-108">Starting in .NET 5.0, this value is simplified to just start with `net`, for example, `net5.0` for .NET 5.0.</span></span>

<span data-ttu-id="ee801-109">Para obter mais informações, consulte [o futuro de .net Standard](https://devblogs.microsoft.com/dotnet/the-future-of-net-standard/) e [nomes de estrutura de destino no .NET 5](https://github.com/dotnet/designs/blob/main/accepted/2020/net5/net5.md).</span><span class="sxs-lookup"><span data-stu-id="ee801-109">For more information, see [The future of .NET Standard](https://devblogs.microsoft.com/dotnet/the-future-of-net-standard/) and [Target framework names in .NET 5](https://github.com/dotnet/designs/blob/main/accepted/2020/net5/net5.md).</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="ee801-110">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="ee801-110">Reason for change</span></span>

- <span data-ttu-id="ee801-111">Simplifica o `TargetFramework` valor.</span><span class="sxs-lookup"><span data-stu-id="ee801-111">Simplifies the `TargetFramework` value.</span></span>
- <span data-ttu-id="ee801-112">Permite que os projetos incluam um `TargetPlatform` na `TargetFramework` propriedade.</span><span class="sxs-lookup"><span data-stu-id="ee801-112">Enables projects to include a `TargetPlatform` in the `TargetFramework` property.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="ee801-113">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="ee801-113">Recommended action</span></span>

<span data-ttu-id="ee801-114">Se você tiver uma lógica que analise o valor de `TargetFramework` , você precisará atualizá-la.</span><span class="sxs-lookup"><span data-stu-id="ee801-114">If you have logic that parses the value of `TargetFramework`, you'll need to update it.</span></span> <span data-ttu-id="ee801-115">Por exemplo, a seguinte condição do MSBuild depende do valor de `TargetFramework` .</span><span class="sxs-lookup"><span data-stu-id="ee801-115">For example, the following MSBuild condition relies on the value of `TargetFramework`.</span></span>

```xml
<PropertyGroup Condition="$(TargetFramework.StartsWith('netcoreapp'))">
```

<span data-ttu-id="ee801-116">Para esse requisito, você pode atualizar o código para comparar o identificador de estrutura de destino.</span><span class="sxs-lookup"><span data-stu-id="ee801-116">For this requirement, you can update the code to compare the target framework identifier instead.</span></span>

```xml
<PropertyGroup Condition="'$([MSBuild]::GetTargetFrameworkIdentifier('$(TargetFramework)'))' == '.NETCoreApp'">
```

#### <a name="category"></a><span data-ttu-id="ee801-117">Categoria</span><span class="sxs-lookup"><span data-stu-id="ee801-117">Category</span></span>

<span data-ttu-id="ee801-118">MSBuild</span><span class="sxs-lookup"><span data-stu-id="ee801-118">MSBuild</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ee801-119">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="ee801-119">Affected APIs</span></span>

<span data-ttu-id="ee801-120">N/D</span><span class="sxs-lookup"><span data-stu-id="ee801-120">N/A</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
