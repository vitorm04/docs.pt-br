---
ms.openlocfilehash: 92c03328414410d56a2ff5f445639757367b42c7
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420416"
---
### <a name="processstartinfo-throws-invalidoperationexception-for-processes-you-didnt-start"></a><span data-ttu-id="e2a97-101">Process. StartInfo gera InvalidOperationException para processos que você não iniciou</span><span class="sxs-lookup"><span data-stu-id="e2a97-101">Process.StartInfo throws InvalidOperationException for processes you didn't start</span></span>

<span data-ttu-id="e2a97-102">Ler a <xref:System.Diagnostics.Process.StartInfo?displayProperty=nameWithType> propriedade para processos que seu código não iniciou lança um <xref:System.InvalidOperationException> .</span><span class="sxs-lookup"><span data-stu-id="e2a97-102">Reading the <xref:System.Diagnostics.Process.StartInfo?displayProperty=nameWithType> property for processes that your code didn't start throws an <xref:System.InvalidOperationException>.</span></span>

#### <a name="change-description"></a><span data-ttu-id="e2a97-103">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="e2a97-103">Change description</span></span>

<span data-ttu-id="e2a97-104">Em .NET Framework, o acesso à <xref:System.Diagnostics.Process.StartInfo?displayProperty=nameWithType> propriedade para processos que seu código não iniciou retorna um <xref:System.Diagnostics.ProcessStartInfo> objeto fictício.</span><span class="sxs-lookup"><span data-stu-id="e2a97-104">In .NET Framework, accessing the <xref:System.Diagnostics.Process.StartInfo?displayProperty=nameWithType> property for processes that your code didn't start returns a dummy <xref:System.Diagnostics.ProcessStartInfo> object.</span></span> <span data-ttu-id="e2a97-105">O objeto fictício contém valores padrão para todas as suas propriedades, exceto <xref:System.Diagnostics.ProcessStartInfo.EnvironmentVariables> .</span><span class="sxs-lookup"><span data-stu-id="e2a97-105">The dummy object contains default values for all of its properties except <xref:System.Diagnostics.ProcessStartInfo.EnvironmentVariables>.</span></span>

<span data-ttu-id="e2a97-106">A partir do .NET Core 1,0, se você ler a <xref:System.Diagnostics.Process.StartInfo?displayProperty=nameWithType> propriedade para um processo que não iniciou (ou seja, chamando <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> ), um <xref:System.InvalidOperationException> será lançado.</span><span class="sxs-lookup"><span data-stu-id="e2a97-106">Starting in .NET Core 1.0, if you read the <xref:System.Diagnostics.Process.StartInfo?displayProperty=nameWithType> property for a process that you didn't start (that is, by calling <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>), an <xref:System.InvalidOperationException> is thrown.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="e2a97-107">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="e2a97-107">Version introduced</span></span>

<span data-ttu-id="e2a97-108">1.0</span><span class="sxs-lookup"><span data-stu-id="e2a97-108">1.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e2a97-109">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="e2a97-109">Recommended action</span></span>

<span data-ttu-id="e2a97-110">Não acesse a <xref:System.Diagnostics.Process.StartInfo?displayProperty=nameWithType> propriedade para processos que seu código não iniciou.</span><span class="sxs-lookup"><span data-stu-id="e2a97-110">Do not access the <xref:System.Diagnostics.Process.StartInfo?displayProperty=nameWithType> property for processes that your code didn't start.</span></span> <span data-ttu-id="e2a97-111">Por exemplo, não leia esta propriedade para processos retornados por <xref:System.Diagnostics.Process.GetProcesses%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="e2a97-111">For example, don't read this property for processes returned by <xref:System.Diagnostics.Process.GetProcesses%2A?displayProperty=nameWithType>.</span></span>

#### <a name="category"></a><span data-ttu-id="e2a97-112">Categoria</span><span class="sxs-lookup"><span data-stu-id="e2a97-112">Category</span></span>

<span data-ttu-id="e2a97-113">Bibliotecas principais do .NET</span><span class="sxs-lookup"><span data-stu-id="e2a97-113">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e2a97-114">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="e2a97-114">Affected APIs</span></span>

- <xref:System.Diagnostics.Process.StartInfo?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Diagnostics.Process.StartInfo`

-->
