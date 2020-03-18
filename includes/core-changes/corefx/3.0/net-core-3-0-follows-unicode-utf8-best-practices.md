---
ms.openlocfilehash: db1d09c8c9e606b5327a42977a74a74703282d84
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74568220"
---
### <a name="net-core-30-follows-unicode-best-practices-when-replacing-ill-formed-utf-8-byte-sequences"></a>O Núcleo 3.0 do .NET segue as práticas recomendadas da Unicode ao substituir sequências de bytes UTF-8 mal formadas

Quando <xref:System.Text.UTF8Encoding> a classe encontra uma seqüência de bytes UTF-8 mal formada durante uma operação de transcodificação byte-to-character, ela substituirá essa seqüência por um ' (U+FFFD REPLACEMENT CHARACTER) na seqüência de saída. O .NET Core 3.0 difere das versões anteriores do .NET Core e do .NET Framework, seguindo as práticas recomendadas do Unicode para realizar essa substituição durante a operação de transcodificação.

Isso faz parte de um esforço maior para melhorar o manuseio do <xref:System.Text.Unicode.Utf8?displayProperty=nameWithType> <xref:System.Text.Rune?displayProperty=nameWithType> UTF-8 em todo o .NET, inclusive pelos novos e tipos. O <xref:System.Text.UTF8Encoding> tipo recebeu mecânica de manuseio de erros melhorada para que produza saída consistente com os tipos recém-introduzidos.

#### <a name="change-description"></a>Descrição da alteração

Começando com o .NET Core 3.0, ao transcodificar bytes para caracteres, a classe executa a <xref:System.Text.UTF8Encoding> substituição de caracteres com base nas práticas recomendadas do Unicode. O mecanismo de substituição utilizado é descrito pelo [Unicode Standard, Versão 12.0, Sec. 3.9 (PDF)](https://www.unicode.org/versions/Unicode12.0.0/ch03.pdf) no título intitulado _U+FFFD Replacement of Maximal Subparts_.

Esse comportamento _só_ se aplica quando a seqüência de bytes de entrada contém dados UTF-8 mal formados. Além disso, <xref:System.Text.UTF8Encoding> se a instância `throwOnInvalidBytes: true` tiver sido construída com (consulte a documentação do construtor UTF8Encoding](<xref:System.Text.UTF8Encoding.%23ctor(System.Boolean,System.Boolean)>, a `UTF8Encoding` instância continuará a jogar em entrada inválida em vez de executar a substituição U+FFFD.

O seguinte ilustra o impacto desta mudança com uma entrada inválida de 3 bytes:

|Entrada mal formada de 3 bytes|Saída antes do .NET Core 3.0|Saída começando com .NET Core 3.0|
|---|---|---|
| `[ ED A0 90 ]` | `[ FFFD FFFD ]`(Saída de 2 caracteres)| `[ FFFD FFFD FFFD ]`(Saída de 3 caracteres)|

Esta saída de 3 char é a saída preferida, de acordo com a _Tabela 3-9_ do PDF Padrão Unicode anteriormente vinculado.

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="recommended-action"></a>Ação recomendada

Nenhuma ação é necessária por parte do desenvolvedor.

#### <a name="category"></a>Categoria

CoreFx

#### <a name="affected-apis"></a>APIs afetadas

- <xref:System.Text.UTF8Encoding.GetCharCount%2A?displayProperty=nameWithType>
- <xref:System.Text.UTF8Encoding.GetChars%2A?displayProperty=nameWithType>
- <xref:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)?displayProperty=nameWithType>

<!--

### Affected APIs

- `Overload:System.Text.UTF8Encoding.GetCharCount`
- `Overload:System.Text.UTF8Encoding.GetChars`
- `M:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)`

-->
