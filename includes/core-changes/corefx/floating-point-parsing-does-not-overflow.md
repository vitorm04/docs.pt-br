---
ms.openlocfilehash: 192873aa5069aa4f96a18716afb066c80b223e29
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002453"
---
### <a name="floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception"></a>Operações de análise de ponto flutuante não falham mais ou geram uma estourexception

Os métodos de análise de ponto flutuante não lançam mais um <xref:System.OverflowException> ou retornam `false` quando analisam uma cadeia de caracteres cujo valor numérico está fora do intervalo do tipo de ponto flutuante <xref:System.Single> ou <xref:System.Double>.

#### <a name="change-description"></a>Alterar descrição

No .NET Core 2,2 e em versões anteriores, os métodos <xref:System.Double.Parse%2A?displayProperty=nameWithType> e <xref:System.Single.Parse%2A?displayProperty=nameWithType> lançam um <xref:System.OverflowException> para valores que estão fora do intervalo de seus respectivos tipos. Os métodos <xref:System.Double.TryParse%2A?displayProperty=nameWithType> e <xref:System.Single.TryParse%2A?displayProperty=nameWithType> retornam `false` para as representações de cadeia de caracteres de valores numéricos fora do intervalo.

A partir do .NET Core 3,0, os métodos <xref:System.Double.Parse%2A?displayProperty=nameWithType>, <xref:System.Double.TryParse%2A?displayProperty=nameWithType>, <xref:System.Single.Parse%2A?displayProperty=nameWithType> e <xref:System.Single.TryParse%2A?displayProperty=nameWithType> não falham mais ao analisar cadeias de caracteres numéricas fora do intervalo. Em vez disso, os métodos de análise <xref:System.Double> retornam <xref:System.Double.PositiveInfinity?displayProperty=nameWithType> para valores que excedem <xref:System.Double.MaxValue?displayProperty=nameWithType> e retornam <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> para valores menores que <xref:System.Double.MinValue?displayProperty=nameWithType>. Da mesma forma, os métodos de análise <xref:System.Single> retornam <xref:System.Single.PositiveInfinity?displayProperty=nameWithType> para valores que excedem <xref:System.Single.MaxValue?displayProperty=nameWithType> e retornam <xref:System.Single.NegativeInfinity?displayProperty=nameWithType> para valores menores que <xref:System.Single.MinValue?displayProperty=nameWithType>.

Essa alteração foi feita para melhorar a conformidade com o IEEE 754:2008. 

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="recommended-action"></a>Ação recomendada

Essa alteração pode afetar o código de uma das duas maneiras:

- Seu código depende do manipulador para que o <xref:System.OverflowException> seja executado quando ocorrer um estouro. Nesse caso, você deve remover a instrução `catch` e inserir qualquer código necessário em uma instrução `If` que testa se <xref:System.Double.IsInfinity%2A?displayProperty=nameWithType> ou <xref:System.Single.IsInfinity%2A?displayProperty=nameWithType> é `true`.

- Seu código supõe que os valores de ponto flutuante não são `Infinity`. Nesse caso, você deve adicionar o código necessário para verificar valores de ponto flutuante de `PositiveInfinity` e `NegativeInfinity`.

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
