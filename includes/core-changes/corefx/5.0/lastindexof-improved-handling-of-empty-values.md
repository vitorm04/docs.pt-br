---
ms.openlocfilehash: 0ba77a6a6ac0e2d29036635ea3cdb9ba9a9da10e
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94440166"
---
### <a name="lastindexof-has-improved-handling-of-empty-search-strings"></a><span data-ttu-id="b645e-101">LastIndexOf aprimorou o tratamento de cadeias de caracteres de pesquisa vazias</span><span class="sxs-lookup"><span data-stu-id="b645e-101">LastIndexOf has improved handling of empty search strings</span></span>

<span data-ttu-id="b645e-102"><xref:System.String.LastIndexOf%2A?displayProperty=nameWithType> e as APIs relacionadas agora retornam valores corretos ao procurar uma subcadeia de caracteres de comprimento zero (ou equivalente de comprimento zero) em uma cadeia de caracteres maior.</span><span class="sxs-lookup"><span data-stu-id="b645e-102"><xref:System.String.LastIndexOf%2A?displayProperty=nameWithType> and related APIs now return correct values when searching for a zero-length (or zero-length equivalent) substring within a larger string.</span></span>

#### <a name="change-description"></a><span data-ttu-id="b645e-103">Descrição das alterações</span><span class="sxs-lookup"><span data-stu-id="b645e-103">Change description</span></span>

<span data-ttu-id="b645e-104">No .NET Framework e no .NET Core 1,0-3,1, <xref:System.String.LastIndexOf%2A?displayProperty=nameWithType> e APIs relacionadas podem retornar um valor incorreto quando o chamador procura uma subcadeia de caracteres de comprimento zero.</span><span class="sxs-lookup"><span data-stu-id="b645e-104">In .NET Framework and .NET Core 1.0 - 3.1, <xref:System.String.LastIndexOf%2A?displayProperty=nameWithType> and related APIs might return an incorrect value when the caller searches for a zero-length substring.</span></span>

```csharp
Console.WriteLine("Hello".LastIndexOf("")); // prints '4' (incorrect)

ReadOnlySpan<char> span = "Hello";
Console.WriteLine(span.LastIndexOf("")); // prints '0' (incorrect)
```

<span data-ttu-id="b645e-105">A partir do .NET 5,0, essas APIs retornam o valor correto para `LastIndexOf` .</span><span class="sxs-lookup"><span data-stu-id="b645e-105">Starting with .NET 5.0, these APIs return the correct value for `LastIndexOf`.</span></span>

```csharp
Console.WriteLine("Hello".LastIndexOf("")); // prints '5' (correct)

ReadOnlySpan<char> span = "Hello";
Console.WriteLine(span.LastIndexOf("")); // prints '5' (correct)
```

<span data-ttu-id="b645e-106">Nesses exemplos, `5` é a resposta correta porque `"Hello".Substring(5)` e `"Hello".AsSpan().Slice(5)` ambas produzem uma cadeia de caracteres vazia, que é trivialmente igual à subcadeia de caracteres vazia que é buscada.</span><span class="sxs-lookup"><span data-stu-id="b645e-106">In these examples, `5` is the correct answer because `"Hello".Substring(5)` and `"Hello".AsSpan().Slice(5)` both produce an empty string, which is trivially equal to the empty substring that is sought.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="b645e-107">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="b645e-107">Reason for change</span></span>

<span data-ttu-id="b645e-108">Essa alteração foi parte de um problema geral que corrige o esforço em relação à manipulação de cadeias de caracteres para o .NET 5.</span><span class="sxs-lookup"><span data-stu-id="b645e-108">This change was part of an overall bug fixing effort around string handling for .NET 5.</span></span> <span data-ttu-id="b645e-109">Ele também ajuda a unificar nosso comportamento entre plataformas Windows e não Windows.</span><span class="sxs-lookup"><span data-stu-id="b645e-109">It also helps unify our behavior between Windows and non-Windows platforms.</span></span> <span data-ttu-id="b645e-110">Para obter mais informações, consulte [dotnet/tempo de execução # 13383](https://github.com/dotnet/runtime/issues/13383) e [dotnet/tempo de execução # #13382](https://github.com/dotnet/runtime/issues/13382).</span><span class="sxs-lookup"><span data-stu-id="b645e-110">For more information, see [dotnet/runtime#13383](https://github.com/dotnet/runtime/issues/13383) and [dotnet/runtime##13382](https://github.com/dotnet/runtime/issues/13382).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="b645e-111">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="b645e-111">Version introduced</span></span>

<span data-ttu-id="b645e-112">5.0</span><span class="sxs-lookup"><span data-stu-id="b645e-112">5.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b645e-113">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="b645e-113">Recommended action</span></span>

<span data-ttu-id="b645e-114">Você não precisa realizar nenhuma ação.</span><span class="sxs-lookup"><span data-stu-id="b645e-114">You don't need to take any action.</span></span> <span data-ttu-id="b645e-115">O tempo de execução do .NET 5,0 fornece os novos comportamentos automaticamente.</span><span class="sxs-lookup"><span data-stu-id="b645e-115">The .NET 5.0 runtime provides the new behaviors automatically.</span></span>

<span data-ttu-id="b645e-116">Não há nenhuma opção de compatibilidade para restaurar o comportamento antigo.</span><span class="sxs-lookup"><span data-stu-id="b645e-116">There is no compatibility switch to restore the old behavior.</span></span>

#### <a name="category"></a><span data-ttu-id="b645e-117">Categoria</span><span class="sxs-lookup"><span data-stu-id="b645e-117">Category</span></span>

<span data-ttu-id="b645e-118">Bibliotecas principais do .NET</span><span class="sxs-lookup"><span data-stu-id="b645e-118">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b645e-119">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="b645e-119">Affected APIs</span></span>

- <xref:System.String.LastIndexOf%2A?displayProperty=fullName>
- <xref:System.Globalization.CompareInfo.LastIndexOf%2A?displayProperty=fullName>
- <xref:System.MemoryExtensions.LastIndexOf%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `Overload:System.String.LastIndexOf`
- `Overload:System.Globalization.CompareInfo.LastIndexOf`
- `Overload:System.MemoryExtensions.LastIndexOf`

-->
