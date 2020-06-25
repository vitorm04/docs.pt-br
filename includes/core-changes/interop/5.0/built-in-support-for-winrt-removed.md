---
ms.openlocfilehash: d21b2e092d460fdfc367d0f490228ed44ad5c6cc
ms.sourcegitcommit: 63bb83322814f5e5e5c5b69939b14a3139a6ca7e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/25/2020
ms.locfileid: "85365631"
---
### <a name="built-in-support-for-winrt-is-removed-from-net"></a><span data-ttu-id="1faaa-101">O suporte interno para o WinRT é removido do .NET</span><span class="sxs-lookup"><span data-stu-id="1faaa-101">Built-in support for WinRT is removed from .NET</span></span>

<span data-ttu-id="1faaa-102">O suporte interno para consumo de APIs do [tempo de execução do Windows (WinRT)](/uwp/winrt-cref/winrt-type-system) no .net foi removido.</span><span class="sxs-lookup"><span data-stu-id="1faaa-102">Built-in support for consumption of [Windows runtime (WinRT)](/uwp/winrt-cref/winrt-type-system) APIs in .NET is removed.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="1faaa-103">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="1faaa-103">Version introduced</span></span>

<span data-ttu-id="1faaa-104">5,0 Preview 6</span><span class="sxs-lookup"><span data-stu-id="1faaa-104">5.0 Preview 6</span></span>

#### <a name="change-description"></a><span data-ttu-id="1faaa-105">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="1faaa-105">Change description</span></span>

<span data-ttu-id="1faaa-106">Anteriormente, o CoreCLR poderia consumir [arquivos de metadados do Windows (WinMD)](/uwp/winrt-cref/winmd-files) para ativar e consumir tipos de WinRT.</span><span class="sxs-lookup"><span data-stu-id="1faaa-106">Previously, CoreCLR could consume [Windows metadata (WinMD) files](/uwp/winrt-cref/winmd-files) to active and consume WinRT types.</span></span> <span data-ttu-id="1faaa-107">A partir do .NET 5,0, o CoreCLR não pode mais consumir arquivos WinMD diretamente.</span><span class="sxs-lookup"><span data-stu-id="1faaa-107">Starting in .NET 5.0, CoreCLR can no longer consume WinMD files directly.</span></span>

<span data-ttu-id="1faaa-108">Se você tentar fazer referência a um assembly sem suporte, obterá um <xref:System.IO.FileNotFoundException> .</span><span class="sxs-lookup"><span data-stu-id="1faaa-108">If you attempt to reference an unsupported assembly, you'll get a <xref:System.IO.FileNotFoundException>.</span></span> <span data-ttu-id="1faaa-109">Se você ativar uma classe do WinRT, obterá um <xref:System.PlatformNotSupportedException> .</span><span class="sxs-lookup"><span data-stu-id="1faaa-109">If you activate a WinRT class, you'll get a <xref:System.PlatformNotSupportedException>.</span></span>

<span data-ttu-id="1faaa-110">Essa alteração significativa foi feita pelos seguintes motivos:</span><span class="sxs-lookup"><span data-stu-id="1faaa-110">This breaking change was made for the following reasons:</span></span>

- <span data-ttu-id="1faaa-111">Portanto, o WinRT pode ser desenvolvido e aprimorado separadamente do tempo de execução do .NET.</span><span class="sxs-lookup"><span data-stu-id="1faaa-111">So WinRT can be developed and improved separately from the .NET runtime.</span></span>
- <span data-ttu-id="1faaa-112">Para simetria com sistemas de interoperabilidade fornecidos para outros sistemas operacionais, como iOS e Android.</span><span class="sxs-lookup"><span data-stu-id="1faaa-112">For symmetry with interop systems provided for other operating systems, such as iOS and Android.</span></span>
- <span data-ttu-id="1faaa-113">Para tirar proveito de outros recursos do .NET, como recursos C#, vinculação de IL (linguagem intermediária) e compilação de AOT (antecipadamente de tempo).</span><span class="sxs-lookup"><span data-stu-id="1faaa-113">To take advantage of other .NET features, such as C# features, intermediate language (IL) linking, and ahead-of-time (AOT) compilation.</span></span>
- <span data-ttu-id="1faaa-114">Para simplificar a base de código .NET Runtime.</span><span class="sxs-lookup"><span data-stu-id="1faaa-114">To simplify the .NET runtime codebase.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="1faaa-115">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="1faaa-115">Recommended action</span></span>

- <span data-ttu-id="1faaa-116">Remova as referências ao [pacote Microsoft. Windows. Sdk. Contracts](https://www.nuget.org/packages/Microsoft.Windows.SDK.Contracts) e substitua-as por referências ao [pacote Microsoft.Windows.Sdk.net](https://www.nuget.org/packages/microsoft.windows.sdk.net).</span><span class="sxs-lookup"><span data-stu-id="1faaa-116">Remove references to the [Microsoft.Windows.SDK.Contracts package](https://www.nuget.org/packages/Microsoft.Windows.SDK.Contracts) and replace them with references to the [Microsoft.Windows.SDK.NET package](https://www.nuget.org/packages/microsoft.windows.sdk.net).</span></span>

- <span data-ttu-id="1faaa-117">Use a cadeia de ferramentas [/WinRT do C#](/windows/uwp/csharp-winrt/) para gerar ou personalizar APIs e tipos do WinRT no .NET 5,0 e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="1faaa-117">Use the [C#/WinRT](/windows/uwp/csharp-winrt/) tool chain to generate or customize WinRT APIs and types in .NET 5.0 and later versions.</span></span>

#### <a name="category"></a><span data-ttu-id="1faaa-118">Categoria</span><span class="sxs-lookup"><span data-stu-id="1faaa-118">Category</span></span>

<span data-ttu-id="1faaa-119">Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="1faaa-119">Interop</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="1faaa-120">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="1faaa-120">Affected APIs</span></span>

- <xref:System.IO.WindowsRuntimeStorageExtensions?displayProperty=fullName>
- <xref:System.IO.WindowsRuntimeStreamExtensions?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.WindowsRuntime?displayProperty=fullName>
- <xref:System.WindowsRuntimeSystemExtensions?displayProperty=fullName>
- <xref:Windows.Foundation.Point?displayProperty=fullName>
- <xref:Windows.Foundation.Size?displayProperty=fullName>
- <xref:Windows.UI.Color?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.IO.WindowsRuntimeStorageExtensions`
- `T: System.IO.WindowsRuntimeStreamExtensions`
- `N:System.Runtime.InteropServices.WindowsRuntime`
- `T:System.WindowsRuntimeSystemExtensions`
- `T:Windows.Foundation.Point`
- `T:Windows.Foundation.Size`
- `T:Windows.UI.Color`

-->
