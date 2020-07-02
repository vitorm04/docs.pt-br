---
ms.openlocfilehash: 0bd90b3d479a7e0897aaf78b7718ae156a4a239f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619773"
---
### <a name="assemblies-compiled-with-regexcompiletoassembly-breaks-between-40-and-45"></a><span data-ttu-id="152be-101">Assemblies compilados com interrupções Regex.CompileToAssembly entre o 4.0 e o 4.5</span><span class="sxs-lookup"><span data-stu-id="152be-101">Assemblies compiled with Regex.CompileToAssembly breaks between 4.0 and 4.5</span></span>

#### <a name="details"></a><span data-ttu-id="152be-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="152be-102">Details</span></span>

<span data-ttu-id="152be-103">Se uma assembly de expressões regulares compiladas é trabalhada com o .NET Framework 4.5 mas é destinada ao .NET Framework 4, numa tentativa de usar uma das expressões regulares em que a assembly de um sistema com .NET Framework 4 instalado gera uma exceção.</span><span class="sxs-lookup"><span data-stu-id="152be-103">If an assembly of compiled regular expressions is built with the .NET Framework 4.5 but targets the .NET Framework 4, attempting to use one of the regular expressions in that assembly on a system with .NET Framework 4 installed throws an exception.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="152be-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="152be-104">Suggestion</span></span>

<span data-ttu-id="152be-105">Para solucionar esse problema, pode-se seguir uma das seguintes alternativas:</span><span class="sxs-lookup"><span data-stu-id="152be-105">To work around this problem, you can do either of the following:</span></span><ul><li><span data-ttu-id="152be-106">Compilar o assembly que contém as expressões regulares com o .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="152be-106">Build the assembly that contains the regular expressions with the .NET Framework 4.</span></span></li><li><span data-ttu-id="152be-107">Use uma expressão regular interpretada.</span><span class="sxs-lookup"><span data-stu-id="152be-107">Use an interpreted regular expression.</span></span></li></ul>

| <span data-ttu-id="152be-108">Name</span><span class="sxs-lookup"><span data-stu-id="152be-108">Name</span></span>    | <span data-ttu-id="152be-109">Valor</span><span class="sxs-lookup"><span data-stu-id="152be-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="152be-110">Escopo</span><span class="sxs-lookup"><span data-stu-id="152be-110">Scope</span></span>   |<span data-ttu-id="152be-111">Secundária</span><span class="sxs-lookup"><span data-stu-id="152be-111">Minor</span></span>|
|<span data-ttu-id="152be-112">Versão</span><span class="sxs-lookup"><span data-stu-id="152be-112">Version</span></span>|<span data-ttu-id="152be-113">4.5</span><span class="sxs-lookup"><span data-stu-id="152be-113">4.5</span></span>|
|<span data-ttu-id="152be-114">Type</span><span class="sxs-lookup"><span data-stu-id="152be-114">Type</span></span>|<span data-ttu-id="152be-115">Runtime</span><span class="sxs-lookup"><span data-stu-id="152be-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="152be-116">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="152be-116">Affected APIs</span></span>

-<xref:System.Text.RegularExpressions.Regex.CompileToAssembly(System.Text.RegularExpressions.RegexCompilationInfo[],System.Reflection.AssemblyName)?displayProperty=nameWithType></li><li><xref:System.Text.RegularExpressions.Regex.CompileToAssembly(System.Text.RegularExpressions.RegexCompilationInfo[],System.Reflection.AssemblyName,System.Reflection.Emit.CustomAttributeBuilder[])?displayProperty=nameWithType></li><li><xref:System.Text.RegularExpressions.Regex.CompileToAssembly(System.Text.RegularExpressions.RegexCompilationInfo[],System.Reflection.AssemblyName,System.Reflection.Emit.CustomAttributeBuilder[],System.String)?displayProperty=nameWithType></li></ul>|
