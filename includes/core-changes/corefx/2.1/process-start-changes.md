---
ms.openlocfilehash: 58cb3580c8701773452ae8338f036a94bbee80c5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77449381"
---
### <a name="change-in-default-value-of-useshellexecute"></a><span data-ttu-id="3618d-101">Alterar o valor padrão do UseShellExecute</span><span class="sxs-lookup"><span data-stu-id="3618d-101">Change in default value of UseShellExecute</span></span>

<span data-ttu-id="3618d-102"><xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType>tem um valor `false` padrão de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3618d-102"><xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> has a default value of `false` on .NET Core.</span></span> <span data-ttu-id="3618d-103">No .NET Framework, seu `true`valor padrão é .</span><span class="sxs-lookup"><span data-stu-id="3618d-103">On .NET Framework, its default value is `true`.</span></span>

#### <a name="change-description"></a><span data-ttu-id="3618d-104">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="3618d-104">Change description</span></span>

<span data-ttu-id="3618d-105"><xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>permite que você inicie um aplicativo diretamente, `Process.Start("mspaint.exe")` por exemplo, com código como o que lança o Paint.</span><span class="sxs-lookup"><span data-stu-id="3618d-105"><xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> lets you launch an application directly, for example, with code such as `Process.Start("mspaint.exe")` that launches Paint.</span></span> <span data-ttu-id="3618d-106">Ele também permite que você lance <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> indiretamente `true`um aplicativo associado se estiver definido como .</span><span class="sxs-lookup"><span data-stu-id="3618d-106">It also lets you indirectly launch an associated application if <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> is set to `true`.</span></span> <span data-ttu-id="3618d-107">No .NET Framework, o <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> `true`valor padrão para `Process.Start("mytextfile.txt")` é , o que significa que o código como seria lançado Notepad, se você tiver associado arquivos *.txt* com esse editor.</span><span class="sxs-lookup"><span data-stu-id="3618d-107">On .NET Framework, the default value for <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> is `true`, meaning that code such as `Process.Start("mytextfile.txt")` would launch Notepad, if you've associated *.txt* files with that editor.</span></span> <span data-ttu-id="3618d-108">Para evitar a inicialção indireta de um aplicativo <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> `false`no .NET Framework, você deve definir explicitamente para .</span><span class="sxs-lookup"><span data-stu-id="3618d-108">To prevent indirectly launching an app on .NET Framework, you must explicitly set <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> to `false`.</span></span> <span data-ttu-id="3618d-109">No .NET Core, o <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> `false`valor padrão para é .</span><span class="sxs-lookup"><span data-stu-id="3618d-109">On .NET Core, the default value for <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> is `false`.</span></span> <span data-ttu-id="3618d-110">Isso significa que, por padrão, os aplicativos `Process.Start`associados não são lançados quando você chama .</span><span class="sxs-lookup"><span data-stu-id="3618d-110">This means that, by default, associated applications are not launched when you call `Process.Start`.</span></span>

<span data-ttu-id="3618d-111">Essa mudança foi introduzida no .NET Core por razões de desempenho.</span><span class="sxs-lookup"><span data-stu-id="3618d-111">This change was introduced in .NET Core for performance reasons.</span></span> <span data-ttu-id="3618d-112">Normalmente, <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> é usado para lançar um aplicativo diretamente.</span><span class="sxs-lookup"><span data-stu-id="3618d-112">Typically, <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> is used to launch an application directly.</span></span> <span data-ttu-id="3618d-113">Lançar um aplicativo diretamente não precisa envolver o shell do Windows e incorrer no custo de desempenho associado.</span><span class="sxs-lookup"><span data-stu-id="3618d-113">Launching an app directly does not need to involve the Windows shell and incur the associated performance cost.</span></span> <span data-ttu-id="3618d-114">Para tornar este caso padrão mais rápido, <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> o `false`.NET Core altera o valor padrão de .</span><span class="sxs-lookup"><span data-stu-id="3618d-114">To make this default case faster, .NET Core changes the default value of <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> to `false`.</span></span> <span data-ttu-id="3618d-115">Você pode optar pelo caminho mais lento se precisar.</span><span class="sxs-lookup"><span data-stu-id="3618d-115">You can opt in to the slower path if you need it.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="3618d-116">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="3618d-116">Version introduced</span></span>

<span data-ttu-id="3618d-117">2.1</span><span class="sxs-lookup"><span data-stu-id="3618d-117">2.1</span></span>

> [!NOTE]
> <span data-ttu-id="3618d-118">Em versões anteriores `UseShellExecute` do .NET Core, não foi implementado para windows.</span><span class="sxs-lookup"><span data-stu-id="3618d-118">In earlier versions of .NET Core, `UseShellExecute` was not implemented for Windows.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="3618d-119">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="3618d-119">Recommended action</span></span>

<span data-ttu-id="3618d-120">Se o seu aplicativo se <xref:System.Diagnostics.Process.Start(System.Diagnostics.ProcessStartInfo)?displayProperty=nameWithType> basear no comportamento antigo, ligue com <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute> set para `true` o <xref:System.Diagnostics.ProcessStartInfo> objeto.</span><span class="sxs-lookup"><span data-stu-id="3618d-120">If your app relies on the old behavior, call <xref:System.Diagnostics.Process.Start(System.Diagnostics.ProcessStartInfo)?displayProperty=nameWithType> with <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute> set to `true` on the <xref:System.Diagnostics.ProcessStartInfo> object.</span></span>

#### <a name="category"></a><span data-ttu-id="3618d-121">Categoria</span><span class="sxs-lookup"><span data-stu-id="3618d-121">Category</span></span>

<span data-ttu-id="3618d-122">CoreFx</span><span class="sxs-lookup"><span data-stu-id="3618d-122">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="3618d-123">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="3618d-123">Affected APIs</span></span>

- <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.ProcessStartInfo?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Diagnostics.Process.Start`
- `M:System.Diagnostics.ProcessStartInfo`

-->
