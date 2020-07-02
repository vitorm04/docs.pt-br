---
ms.openlocfilehash: c462c7b4ec8423ce8fd331d3cd31154283cf1f1d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619786"
---
### <a name="marshalsizeof-and-marshalptrtostructure-overloads-break-dynamic-code"></a><span data-ttu-id="a3a2b-101">As sobrecargas Marshal.SizeOf e Marshal.PtrToStructure interrompem o código dinâmico</span><span class="sxs-lookup"><span data-stu-id="a3a2b-101">Marshal.SizeOf and Marshal.PtrToStructure overloads break dynamic code</span></span>

#### <a name="details"></a><span data-ttu-id="a3a2b-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="a3a2b-102">Details</span></span>

<span data-ttu-id="a3a2b-103">A partir do .NET Framework 4.5.1, a associação dinâmica aos métodos <xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601>, <xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601(%60%600)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Object)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Type)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr)> ou <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr,%60%600)> (por meio do Windows PowerShell, IronPython ou da palavra-chave dinâmica do C#, por exemplo) pode resultar em <code>MethodInvocationExceptions</code>, pois novas sobrecargas desses métodos que foram adicionadas podem ser ambíguas para os mecanismos de script.</span><span class="sxs-lookup"><span data-stu-id="a3a2b-103">Beginning in the .NET Framework 4.5.1, dynamically binding to the methods <xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601>, <xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601(%60%600)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Object)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Type)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr)>, or <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr,%60%600)>, (via Windows PowerShell, IronPython, or the C# dynamic keyword, for example) can result in <code>MethodInvocationExceptions</code> because new overloads of these methods have been added that may be ambiguous to the scripting engines.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="a3a2b-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="a3a2b-104">Suggestion</span></span>

<span data-ttu-id="a3a2b-105">Atualize os scripts para indicar claramente qual sobrecarga deve ser usada.</span><span class="sxs-lookup"><span data-stu-id="a3a2b-105">Update scripts to clearly indicate which overload should be used.</span></span> <span data-ttu-id="a3a2b-106">Normalmente, isso pode ser feito convertendo explicitamente os parâmetros de tipo dos métodos como <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="a3a2b-106">This can typically done by explicitly casting the methods' type parameters as <xref:System.Type>.</span></span> <span data-ttu-id="a3a2b-107">Clique [neste link](https://support.microsoft.com/kb/2909958/) para obter mais detalhes e exemplos de como contornar o problema.</span><span class="sxs-lookup"><span data-stu-id="a3a2b-107">See [this link](https://support.microsoft.com/kb/2909958/) for more detail and examples of how to workaround the issue.</span></span>

| <span data-ttu-id="a3a2b-108">Name</span><span class="sxs-lookup"><span data-stu-id="a3a2b-108">Name</span></span>    | <span data-ttu-id="a3a2b-109">Valor</span><span class="sxs-lookup"><span data-stu-id="a3a2b-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="a3a2b-110">Escopo</span><span class="sxs-lookup"><span data-stu-id="a3a2b-110">Scope</span></span>   |<span data-ttu-id="a3a2b-111">Secundária</span><span class="sxs-lookup"><span data-stu-id="a3a2b-111">Minor</span></span>|
|<span data-ttu-id="a3a2b-112">Versão</span><span class="sxs-lookup"><span data-stu-id="a3a2b-112">Version</span></span>|<span data-ttu-id="a3a2b-113">4.5.1</span><span class="sxs-lookup"><span data-stu-id="a3a2b-113">4.5.1</span></span>|
|<span data-ttu-id="a3a2b-114">Type</span><span class="sxs-lookup"><span data-stu-id="a3a2b-114">Type</span></span>|<span data-ttu-id="a3a2b-115">Runtime</span><span class="sxs-lookup"><span data-stu-id="a3a2b-115">Runtime</span></span>|
