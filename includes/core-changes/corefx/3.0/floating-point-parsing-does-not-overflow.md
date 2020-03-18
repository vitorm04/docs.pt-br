---
ms.openlocfilehash: 30580b3fde5b8a99862896bb7d31c6c4024f97e8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74568234"
---
### <a name="floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception"></a>As operações de análise de ponto flutuante não falham mais ou lançam uma Exceção de Estouro

Os métodos de análise de ponto <xref:System.OverflowException> flutuante `false` já não jogam um ou retornam quando analisam <xref:System.Single> uma <xref:System.Double> seqüência cujo valor numérico está fora do alcance do tipo ou ponto flutuante.

#### <a name="change-description"></a>Descrição da alteração

Em .NET Core 2.2 e <xref:System.Double.Parse%2A?displayProperty=nameWithType> <xref:System.Single.Parse%2A?displayProperty=nameWithType> versões <xref:System.OverflowException> anteriores, os métodos e os métodos lançam um para valores que estão fora do alcance de seu respectivo tipo. Os <xref:System.Double.TryParse%2A?displayProperty=nameWithType> <xref:System.Single.TryParse%2A?displayProperty=nameWithType> métodos `false` retornam para as representações de string de valores numéricos fora do alcance.

Começando com .NET Core 3.0, <xref:System.Double.Parse%2A?displayProperty=nameWithType>os <xref:System.Double.TryParse%2A?displayProperty=nameWithType> <xref:System.Single.Parse%2A?displayProperty=nameWithType>métodos e <xref:System.Single.TryParse%2A?displayProperty=nameWithType> métodos não falham mais ao analisar strings numéricas fora de alcance. Em vez <xref:System.Double> disso, os <xref:System.Double.PositiveInfinity?displayProperty=nameWithType> métodos de <xref:System.Double.MaxValue?displayProperty=nameWithType>análise retornam <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> para valores <xref:System.Double.MinValue?displayProperty=nameWithType>que excedem , e eles retornam para valores inferiores a . Da mesma <xref:System.Single> forma, os métodos de <xref:System.Single.PositiveInfinity?displayProperty=nameWithType> <xref:System.Single.MaxValue?displayProperty=nameWithType>análise retornam <xref:System.Single.NegativeInfinity?displayProperty=nameWithType> para valores que <xref:System.Single.MinValue?displayProperty=nameWithType>excedem , e eles retornam para valores inferiores a .

Essa mudança foi feita para uma melhor conformidade do IEEE 754:2008.

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="recommended-action"></a>Ação recomendada

Essa alteração pode afetar seu código de duas maneiras:

- Seu código depende do manipulador <xref:System.OverflowException> para ser executado quando ocorre um estouro. Neste caso, você deve `catch` remover a declaração `If` e colocar <xref:System.Double.IsInfinity%2A?displayProperty=nameWithType> qualquer <xref:System.Single.IsInfinity%2A?displayProperty=nameWithType> `true`código necessário em uma declaração que teste se ou é .

- Seu código pressupõe que os `Infinity`valores de ponto flutuante não são . Neste caso, você deve adicionar o código necessário para `PositiveInfinity` `NegativeInfinity`verificar se há valores de ponto flutuante de e .

#### <a name="category"></a>Categoria

CoreFx

#### <a name="affected-apis"></a>APIs afetadas

- <xref:System.Double.Parse%2A?displayProperty=nameWithType>
- <xref:System.Double.TryParse%2A?displayProperty=nameWithType>
- <xref:System.Single.Parse%2A?displayProperty=nameWithType>
- <xref:System.Single.TryParse%2A?displayProperty=nameWithType>

<!--

### Affected APIs

- `Overload:System.Double.Parse`
- `Overload:System.Double.TryParse`
- `Overload:System.Single.Parse`
- `Overload:System.Single.TryParse`

-->
