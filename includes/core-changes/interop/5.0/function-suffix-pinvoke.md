---
ms.openlocfilehash: e128bdb5735b3e4844356ad4807cc092f6f2b105
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/11/2020
ms.locfileid: "88062413"
---
### <a name="no-aw-suffix-probing-on-non-windows-platforms"></a><span data-ttu-id="a6c83-101">Nenhuma investigação de sufixo A/W em plataformas não Windows</span><span class="sxs-lookup"><span data-stu-id="a6c83-101">No A/W suffix probing on non-Windows platforms</span></span>

<span data-ttu-id="a6c83-102">Os tempos de execução do .NET não adicionam mais um `A` `W` sufixo ou aos nomes de exportação de função durante a investigação de P/Invokes em plataformas não Windows.</span><span class="sxs-lookup"><span data-stu-id="a6c83-102">The .NET runtimes no longer add an `A` or `W` suffix to function export names during probing for P/Invokes on non-Windows platforms.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="a6c83-103">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="a6c83-103">Version introduced</span></span>

<span data-ttu-id="a6c83-104">5,0 versão prévia 4</span><span class="sxs-lookup"><span data-stu-id="a6c83-104">5.0 Preview 4</span></span>

#### <a name="change-description"></a><span data-ttu-id="a6c83-105">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="a6c83-105">Change description</span></span>

<span data-ttu-id="a6c83-106">O [Windows tem uma convenção](/windows/win32/intl/conventions-for-function-prototypes) de adicionar `A` um `W` sufixo ou para SDK do Windows nomes de função, que correspondem à página de código do Windows e às versões Unicode, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="a6c83-106">[Windows has a convention](/windows/win32/intl/conventions-for-function-prototypes) of adding an `A` or `W` suffix to Windows SDK function names, which correspond to the Windows code page and Unicode versions, respectively.</span></span>

<span data-ttu-id="a6c83-107">Nas versões anteriores do .NET, os tempos de execução do CoreCLR e do mono adicionam um `A` `W` sufixo ou ao nome de exportação durante a descoberta de exportação para P/Invokes *em todas as plataformas*.</span><span class="sxs-lookup"><span data-stu-id="a6c83-107">In previous versions of .NET, both the CoreCLR and Mono runtimes add an `A` or `W` suffix to the export name during export discovery for P/Invokes *on all platforms*.</span></span>

<span data-ttu-id="a6c83-108">No .NET 5,0 e versões posteriores, `A` um `W` sufixo ou é adicionado ao nome de exportação durante a descoberta *de exportação somente no Windows*.</span><span class="sxs-lookup"><span data-stu-id="a6c83-108">In .NET 5.0 and later versions, an `A` or `W` suffix is added to the export name during export discovery *on Windows only*.</span></span> <span data-ttu-id="a6c83-109">Em plataformas UNIX, o sufixo não é adicionado.</span><span class="sxs-lookup"><span data-stu-id="a6c83-109">On Unix platforms, the suffix is not added.</span></span> <span data-ttu-id="a6c83-110">A semântica de ambos os tempos de execução na plataforma Windows permanece inalterada.</span><span class="sxs-lookup"><span data-stu-id="a6c83-110">The semantics of both runtimes on the Windows platform remain unchanged.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="a6c83-111">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="a6c83-111">Reason for change</span></span>

<span data-ttu-id="a6c83-112">Essa alteração foi feita para simplificar a investigação de plataforma cruzada.</span><span class="sxs-lookup"><span data-stu-id="a6c83-112">This change was made to simplify cross-platform probing.</span></span> <span data-ttu-id="a6c83-113">É uma sobrecarga que não deve ser incorrida, Considerando que plataformas não Windows não contêm essa semântica.</span><span class="sxs-lookup"><span data-stu-id="a6c83-113">It's overhead that shouldn't be incurred, given that non-Windows platforms don't contain this semantic.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="a6c83-114">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="a6c83-114">Recommended action</span></span>

<span data-ttu-id="a6c83-115">Para atenuar a alteração, você pode adicionar manualmente o sufixo desejado em plataformas que não são do Windows.</span><span class="sxs-lookup"><span data-stu-id="a6c83-115">To mitigate the change, you can manually add the desired suffix on non-Windows platforms.</span></span> <span data-ttu-id="a6c83-116">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="a6c83-116">For example:</span></span>

```csharp
[DllImport(...)]
extern static void SetWindowTextW();
```

#### <a name="category"></a><span data-ttu-id="a6c83-117">Categoria</span><span class="sxs-lookup"><span data-stu-id="a6c83-117">Category</span></span>

<span data-ttu-id="a6c83-118">Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="a6c83-118">Interop</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a6c83-119">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="a6c83-119">Affected APIs</span></span>

- <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Runtime.InteropServices.DllImportAttribute`

-->
