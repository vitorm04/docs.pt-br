---
ms.openlocfilehash: 086dac69d085d070511fcfd5820bd2644ee4598e
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496599"
---
### <a name="marshalsizeof-and-marshalptrtostructure-overloads-break-dynamic-code"></a><span data-ttu-id="7b4cc-101">As sobrecargas Marshal.SizeOf e Marshal.PtrToStructure interrompem o código dinâmico</span><span class="sxs-lookup"><span data-stu-id="7b4cc-101">Marshal.SizeOf and Marshal.PtrToStructure overloads break dynamic code</span></span>

#### <a name="details"></a><span data-ttu-id="7b4cc-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="7b4cc-102">Details</span></span>

<span data-ttu-id="7b4cc-103">A partir do .NET Framework 4.5.1, a associação dinâmica aos métodos <xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601>, <xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601(%60%600)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Object)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Type)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr)> ou <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr,%60%600)> (por meio do Windows PowerShell, IronPython ou da palavra-chave dinâmica do C#, por exemplo) pode resultar em <code>MethodInvocationExceptions</code>, pois novas sobrecargas desses métodos que foram adicionadas podem ser ambíguas para os mecanismos de script.</span><span class="sxs-lookup"><span data-stu-id="7b4cc-103">Beginning in the .NET Framework 4.5.1, dynamically binding to the methods <xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601>, <xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601(%60%600)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Object)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Type)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr)>, or <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr,%60%600)>, (via Windows PowerShell, IronPython, or the C# dynamic keyword, for example) can result in <code>MethodInvocationExceptions</code> because new overloads of these methods have been added that may be ambiguous to the scripting engines.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="7b4cc-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="7b4cc-104">Suggestion</span></span>

<span data-ttu-id="7b4cc-105">Atualize os scripts para indicar claramente qual sobrecarga deve ser usada.</span><span class="sxs-lookup"><span data-stu-id="7b4cc-105">Update scripts to clearly indicate which overload should be used.</span></span> <span data-ttu-id="7b4cc-106">Normalmente, isso pode ser feito convertendo explicitamente os parâmetros de tipo dos métodos como <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="7b4cc-106">This can typically done by explicitly casting the methods' type parameters as <xref:System.Type>.</span></span> <span data-ttu-id="7b4cc-107">Clique [neste link](https://support.microsoft.com/kb/2909958/) para obter mais detalhes e exemplos de como contornar o problema.</span><span class="sxs-lookup"><span data-stu-id="7b4cc-107">See [this link](https://support.microsoft.com/kb/2909958/) for more detail and examples of how to workaround the issue.</span></span>

| <span data-ttu-id="7b4cc-108">Nome</span><span class="sxs-lookup"><span data-stu-id="7b4cc-108">Name</span></span>    | <span data-ttu-id="7b4cc-109">Valor</span><span class="sxs-lookup"><span data-stu-id="7b4cc-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="7b4cc-110">Escopo</span><span class="sxs-lookup"><span data-stu-id="7b4cc-110">Scope</span></span>   |<span data-ttu-id="7b4cc-111">Secundária</span><span class="sxs-lookup"><span data-stu-id="7b4cc-111">Minor</span></span>|
|<span data-ttu-id="7b4cc-112">Versão</span><span class="sxs-lookup"><span data-stu-id="7b4cc-112">Version</span></span>|<span data-ttu-id="7b4cc-113">4.5.1</span><span class="sxs-lookup"><span data-stu-id="7b4cc-113">4.5.1</span></span>|
|<span data-ttu-id="7b4cc-114">Tipo</span><span class="sxs-lookup"><span data-stu-id="7b4cc-114">Type</span></span>|<span data-ttu-id="7b4cc-115">Runtime</span><span class="sxs-lookup"><span data-stu-id="7b4cc-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="7b4cc-116">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="7b4cc-116">Affected APIs</span></span>

<span data-ttu-id="7b4cc-117">Não detectável via análise de API.</span><span class="sxs-lookup"><span data-stu-id="7b4cc-117">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
