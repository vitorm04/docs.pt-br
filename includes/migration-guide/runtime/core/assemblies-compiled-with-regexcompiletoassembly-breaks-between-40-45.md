---
ms.openlocfilehash: 424872b25436c7fcbe603639028e813eed6f9b99
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496705"
---
### <a name="assemblies-compiled-with-regexcompiletoassembly-breaks-between-40-and-45"></a><span data-ttu-id="956a1-101">Assemblies compilados com interrupções Regex.CompileToAssembly entre o 4.0 e o 4.5</span><span class="sxs-lookup"><span data-stu-id="956a1-101">Assemblies compiled with Regex.CompileToAssembly breaks between 4.0 and 4.5</span></span>

#### <a name="details"></a><span data-ttu-id="956a1-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="956a1-102">Details</span></span>

<span data-ttu-id="956a1-103">Se uma assembly de expressões regulares compiladas é trabalhada com o .NET Framework 4.5 mas é destinada ao .NET Framework 4, numa tentativa de usar uma das expressões regulares em que a assembly de um sistema com .NET Framework 4 instalado gera uma exceção.</span><span class="sxs-lookup"><span data-stu-id="956a1-103">If an assembly of compiled regular expressions is built with the .NET Framework 4.5 but targets the .NET Framework 4, attempting to use one of the regular expressions in that assembly on a system with .NET Framework 4 installed throws an exception.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="956a1-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="956a1-104">Suggestion</span></span>

<span data-ttu-id="956a1-105">Para solucionar esse problema, pode-se seguir uma das seguintes alternativas:</span><span class="sxs-lookup"><span data-stu-id="956a1-105">To work around this problem, you can do either of the following:</span></span><ul><li><span data-ttu-id="956a1-106">Compilar o assembly que contém as expressões regulares com o .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="956a1-106">Build the assembly that contains the regular expressions with the .NET Framework 4.</span></span></li><li><span data-ttu-id="956a1-107">Use uma expressão regular interpretada.</span><span class="sxs-lookup"><span data-stu-id="956a1-107">Use an interpreted regular expression.</span></span></li></ul>

| <span data-ttu-id="956a1-108">Nome</span><span class="sxs-lookup"><span data-stu-id="956a1-108">Name</span></span>    | <span data-ttu-id="956a1-109">Valor</span><span class="sxs-lookup"><span data-stu-id="956a1-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="956a1-110">Escopo</span><span class="sxs-lookup"><span data-stu-id="956a1-110">Scope</span></span>   |<span data-ttu-id="956a1-111">Secundária</span><span class="sxs-lookup"><span data-stu-id="956a1-111">Minor</span></span>|
|<span data-ttu-id="956a1-112">Versão</span><span class="sxs-lookup"><span data-stu-id="956a1-112">Version</span></span>|<span data-ttu-id="956a1-113">4.5</span><span class="sxs-lookup"><span data-stu-id="956a1-113">4.5</span></span>|
|<span data-ttu-id="956a1-114">Tipo</span><span class="sxs-lookup"><span data-stu-id="956a1-114">Type</span></span>|<span data-ttu-id="956a1-115">Runtime</span><span class="sxs-lookup"><span data-stu-id="956a1-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="956a1-116">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="956a1-116">Affected APIs</span></span>

- <xref:System.Text.RegularExpressions.Regex.CompileToAssembly(System.Text.RegularExpressions.RegexCompilationInfo[],System.Reflection.AssemblyName)?displayProperty=nameWithType>
- <xref:System.Text.RegularExpressions.Regex.CompileToAssembly(System.Text.RegularExpressions.RegexCompilationInfo[],System.Reflection.AssemblyName,System.Reflection.Emit.CustomAttributeBuilder[])?displayProperty=nameWithType>
- <xref:System.Text.RegularExpressions.Regex.CompileToAssembly(System.Text.RegularExpressions.RegexCompilationInfo[],System.Reflection.AssemblyName,System.Reflection.Emit.CustomAttributeBuilder[],System.String)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Text.RegularExpressions.Regex.CompileToAssembly(System.Text.RegularExpressions.RegexCompilationInfo[],System.Reflection.AssemblyName)`
- `M:System.Text.RegularExpressions.Regex.CompileToAssembly(System.Text.RegularExpressions.RegexCompilationInfo[],System.Reflection.AssemblyName,System.Reflection.Emit.CustomAttributeBuilder[])`
- `M:System.Text.RegularExpressions.Regex.CompileToAssembly(System.Text.RegularExpressions.RegexCompilationInfo[],System.Reflection.AssemblyName,System.Reflection.Emit.CustomAttributeBuilder[],System.String)`

-->
