---
ms.openlocfilehash: 54bee14f6de409550357194e905b6ee5d8ef8f18
ms.sourcegitcommit: aa6d8a90a4f5d8fe0f6e967980b8c98433f05a44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90678987"
---
### <a name="outputtype-set-to-winexe-for-wpf-and-winforms-apps"></a><span data-ttu-id="4a8e7-101">OutputType definido como WinExe para aplicativos WPF e WinForms</span><span class="sxs-lookup"><span data-stu-id="4a8e7-101">OutputType set to WinExe for WPF and WinForms apps</span></span>

<span data-ttu-id="4a8e7-102">`OutputType` é definido automaticamente como `WinExe` para Windows Presentation Foundation (WPF) e Windows Forms aplicativos.</span><span class="sxs-lookup"><span data-stu-id="4a8e7-102">`OutputType` is automatically set to `WinExe` for Windows Presentation Foundation (WPF) and Windows Forms apps.</span></span> <span data-ttu-id="4a8e7-103">Quando `OutputType` é definido como `WinExe` , uma janela do console não é aberta quando o aplicativo é executado.</span><span class="sxs-lookup"><span data-stu-id="4a8e7-103">When `OutputType` is set to `WinExe`, a console window doesn't open when the app is executed.</span></span>

#### <a name="change-description"></a><span data-ttu-id="4a8e7-104">Descrição das alterações</span><span class="sxs-lookup"><span data-stu-id="4a8e7-104">Change description</span></span>

<span data-ttu-id="4a8e7-105">Nas versões anteriores do .NET, o valor especificado para `OutputType` no arquivo de projeto é usado.</span><span class="sxs-lookup"><span data-stu-id="4a8e7-105">In previous versions of .NET, the value that's specified for `OutputType` in the project file is used.</span></span> <span data-ttu-id="4a8e7-106">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="4a8e7-106">For example:</span></span>

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

<span data-ttu-id="4a8e7-107">A partir do .NET 5,0, `OutputType` é definido automaticamente como `WinExe` para aplicativos do WPF e Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="4a8e7-107">Starting in .NET 5.0, `OutputType` is automatically set to `WinExe` for WPF and Windows Forms apps.</span></span> <span data-ttu-id="4a8e7-108">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="4a8e7-108">For example:</span></span>

```xml
<PropertyGroup>
  <OutputType>WinExe</OutputType>
</PropertyGroup>
```

#### <a name="reason-for-change"></a><span data-ttu-id="4a8e7-109">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="4a8e7-109">Reason for change</span></span>

<span data-ttu-id="4a8e7-110">Supõe-se que a maioria dos usuários não queira que uma janela do console seja aberta quando um aplicativo do WPF ou Windows Forms é executado.</span><span class="sxs-lookup"><span data-stu-id="4a8e7-110">It's assumed that most users don't want a console window to open when a WPF or Windows Forms app is executed.</span></span> <span data-ttu-id="4a8e7-111">Além disso, [agora que esses tipos de aplicativos usam o SDK do .net](../../../../docs/core/compatibility/wpf.md#winforms-and-wpf-apps-use-microsoftnetsdk) em vez do SDK de área de trabalho do Windows, o padrão correto será definido.</span><span class="sxs-lookup"><span data-stu-id="4a8e7-111">In addition, [now that these application types use the .NET SDK](../../../../docs/core/compatibility/wpf.md#winforms-and-wpf-apps-use-microsoftnetsdk) instead of the Windows Desktop SDK, the correct default will be set.</span></span> <span data-ttu-id="4a8e7-112">Além disso, quando o suporte para o destino do iOS e do Android for adicionado, será mais fácil realizar vários destinos entre várias plataformas se todos usarem o mesmo tipo de saída.</span><span class="sxs-lookup"><span data-stu-id="4a8e7-112">Further, when support for targeting iOS and Android is added, it will be easier to multi-target between multiple platforms if they all use the same output type.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="4a8e7-113">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="4a8e7-113">Version introduced</span></span>

<span data-ttu-id="4a8e7-114">.NET 5,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="4a8e7-114">.NET 5.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="4a8e7-115">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="4a8e7-115">Recommended action</span></span>

<span data-ttu-id="4a8e7-116">Nenhuma ação é necessária em sua parte.</span><span class="sxs-lookup"><span data-stu-id="4a8e7-116">No action is required in your part.</span></span> <span data-ttu-id="4a8e7-117">No entanto, se você quiser reverter para o comportamento antigo, defina a `DisableWinExeOutputInference` propriedade como `true` em seu arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="4a8e7-117">However, if you want to revert to the old behavior, set the `DisableWinExeOutputInference` property to `true` in your project file.</span></span>

```xml
<DisableWinExeOutputInference>true</DisableWinExeOutputInference>
```

#### <a name="category"></a><span data-ttu-id="4a8e7-118">Categoria</span><span class="sxs-lookup"><span data-stu-id="4a8e7-118">Category</span></span>

- <span data-ttu-id="4a8e7-119">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4a8e7-119">Windows Forms</span></span>
- <span data-ttu-id="4a8e7-120">Windows Presentation Framework (WPF)</span><span class="sxs-lookup"><span data-stu-id="4a8e7-120">Windows Presentation Framework (WPF)</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="4a8e7-121">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="4a8e7-121">Affected APIs</span></span>

<span data-ttu-id="4a8e7-122">Não detectável via análise de API.</span><span class="sxs-lookup"><span data-stu-id="4a8e7-122">Not detectable via API analysis.</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis.

-->
