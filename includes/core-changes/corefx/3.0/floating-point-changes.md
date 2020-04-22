---
ms.openlocfilehash: 22dbb1e982f83687a9e0eb288ed72c78c676db77
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021628"
---
### <a name="floating-point-formatting-and-parsing-behavior-changed"></a>O comportamento de formatação e análise de pontos flutuantes mudou

O comportamento de análise e formatação <xref:System.Double> <xref:System.Single> de pontos flutuantes (pelos e tipos) agora está em conformidade com o IEEE.

#### <a name="change-description"></a>Descrição da alteração

Em .NET Core 2.2 e versões anteriores, formatação <xref:System.Single.Parse%2A?displayProperty=nameWithType>com <xref:System.Single.TryParse%2A?displayProperty=nameWithType> <xref:System.Double.ToString%2A?displayProperty=nameWithType> e <xref:System.Single.ToString%2A?displayProperty=nameWithType>, e parsing com <xref:System.Double.Parse%2A?displayProperty=nameWithType>, <xref:System.Double.TryParse%2A?displayProperty=nameWithType>, , e não são compatíveis com IEEE. Como resultado, é impossível garantir que um valor irá fazer uma ida e volta com qualquer seqüência de formato padrão ou personalizado suportado. Para algumas entradas, a tentativa de analisar um valor formatado pode falhar, e para outros, o valor analisado não é igual ao valor original.

Começando com o .NET Core 3.0, as operações de análise e formatação são compatíveis com o IEEE 754. Isso garante que o comportamento dos tipos de ponto flutuante no .NET corresponda ao de linguagens compatíveis com o IEEE, como C#. Para obter mais informações, consulte as melhorias de análise e formatação de pontos flutuantes no post do blog [.NET Core 3.0.](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/)

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="recommended-action"></a>Ação recomendada

A seção "Impacto potencial ao código existente" da análise de ponto flutuante e melhorias de formatação no post do blog [.NET Core 3.0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) sugere alterações no seu código se você observar uma mudança de comportamento quando comparado com aplicativos .NET Core 2.2 Geralmente, isso envolve o uso de uma seqüência de formato padrão ou personalizado diferente para impor o comportamento desejado. Alguns resultados podem não ter uma solução se estiverem anteriormente incorretos.

#### <a name="category"></a>Categoria

Bibliotecas Core .NET

#### <a name="affected-apis"></a>APIs afetadas

- <xref:System.Double.ToString%2A?displayProperty=nameWithType>
- <xref:System.Single.ToString%2A?displayProperty=nameWithType>
- <xref:System.Double.Parse%2A?displayProperty=nameWithType>
- <xref:System.Double.TryParse%2A?displayProperty=nameWithType>
- <xref:System.Single.Parse%2A?displayProperty=nameWithType>
- <xref:System.Single.TryParse%2A?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `Overload:System.Double.ToString`
- `Overload:System.Single.ToString`
- `Overload:System.Double.Parse`
- `Overload:System.Double.TryParse`
- `Overload:System.Single.Parse`
- `Overload:System.Single.TryParse`

-->
