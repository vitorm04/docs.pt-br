---
ms.openlocfilehash: 0ba77a6a6ac0e2d29036635ea3cdb9ba9a9da10e
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94440166"
---
### <a name="lastindexof-has-improved-handling-of-empty-search-strings"></a>LastIndexOf aprimorou o tratamento de cadeias de caracteres de pesquisa vazias

<xref:System.String.LastIndexOf%2A?displayProperty=nameWithType> e as APIs relacionadas agora retornam valores corretos ao procurar uma subcadeia de caracteres de comprimento zero (ou equivalente de comprimento zero) em uma cadeia de caracteres maior.

#### <a name="change-description"></a>Descrição das alterações

No .NET Framework e no .NET Core 1,0-3,1, <xref:System.String.LastIndexOf%2A?displayProperty=nameWithType> e APIs relacionadas podem retornar um valor incorreto quando o chamador procura uma subcadeia de caracteres de comprimento zero.

```csharp
Console.WriteLine("Hello".LastIndexOf("")); // prints '4' (incorrect)

ReadOnlySpan<char> span = "Hello";
Console.WriteLine(span.LastIndexOf("")); // prints '0' (incorrect)
```

A partir do .NET 5,0, essas APIs retornam o valor correto para `LastIndexOf` .

```csharp
Console.WriteLine("Hello".LastIndexOf("")); // prints '5' (correct)

ReadOnlySpan<char> span = "Hello";
Console.WriteLine(span.LastIndexOf("")); // prints '5' (correct)
```

Nesses exemplos, `5` é a resposta correta porque `"Hello".Substring(5)` e `"Hello".AsSpan().Slice(5)` ambas produzem uma cadeia de caracteres vazia, que é trivialmente igual à subcadeia de caracteres vazia que é buscada.

#### <a name="reason-for-change"></a>Motivo da alteração

Essa alteração foi parte de um problema geral que corrige o esforço em relação à manipulação de cadeias de caracteres para o .NET 5. Ele também ajuda a unificar nosso comportamento entre plataformas Windows e não Windows. Para obter mais informações, consulte [dotnet/tempo de execução # 13383](https://github.com/dotnet/runtime/issues/13383) e [dotnet/tempo de execução # #13382](https://github.com/dotnet/runtime/issues/13382).

#### <a name="version-introduced"></a>Versão introduzida

5.0

#### <a name="recommended-action"></a>Ação recomendada

Você não precisa realizar nenhuma ação. O tempo de execução do .NET 5,0 fornece os novos comportamentos automaticamente.

Não há nenhuma opção de compatibilidade para restaurar o comportamento antigo.

#### <a name="category"></a>Categoria

Bibliotecas principais do .NET

#### <a name="affected-apis"></a>APIs afetadas

- <xref:System.String.LastIndexOf%2A?displayProperty=fullName>
- <xref:System.Globalization.CompareInfo.LastIndexOf%2A?displayProperty=fullName>
- <xref:System.MemoryExtensions.LastIndexOf%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `Overload:System.String.LastIndexOf`
- `Overload:System.Globalization.CompareInfo.LastIndexOf`
- `Overload:System.MemoryExtensions.LastIndexOf`

-->
