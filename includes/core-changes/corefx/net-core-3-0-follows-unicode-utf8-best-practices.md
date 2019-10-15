---
ms.openlocfilehash: db1d09c8c9e606b5327a42977a74a74703282d84
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/09/2019
ms.locfileid: "72237280"
---
### <a name="net-core-30-follows-unicode-best-practices-when-replacing-ill-formed-utf-8-byte-sequences"></a>O .NET Core 3,0 segue as práticas recomendadas de Unicode ao substituir sequências de bytes UTF-8 malformadas

Quando a classe <xref:System.Text.UTF8Encoding> encontra uma sequência de bytes UTF-8 mal formada durante uma operação de transcodificação byte a caractere, ela substituirá essa sequência por um caractere ' ' (caractere de substituição U + FFFD) na cadeia de caracteres de saída. O .NET Core 3,0 é diferente das versões anteriores do .NET Core e do .NET Framework seguindo a prática recomendada de Unicode para executar essa substituição durante a operação de transcodificação.

Isso faz parte de um esforço maior para melhorar a manipulação de UTF-8 em todo o .NET, incluindo os novos tipos <xref:System.Text.Unicode.Utf8?displayProperty=nameWithType> e <xref:System.Text.Rune?displayProperty=nameWithType>. O tipo <xref:System.Text.UTF8Encoding> recebeu um mecanismo de tratamento de erros aprimorado para que ele produza uma saída consistente com os tipos introduzidos recentemente.

#### <a name="change-description"></a>Alterar descrição

A partir do .NET Core 3,0, ao transcodificar bytes em caracteres, a classe <xref:System.Text.UTF8Encoding> executa a substituição de caracteres com base nas práticas recomendadas Unicode. O mecanismo de substituição usado é descrito pelo [padrão Unicode, versão 12,0, seg. 3,9 (PDF)](https://www.unicode.org/versions/Unicode12.0.0/ch03.pdf) no título intitulado _U + FFFD substituição de subpartes do máximo_.

Esse comportamento se aplica _somente_ quando a sequência de bytes de entrada contém dados UTF-8 mal formados. Além disso, se a instância <xref:System.Text.UTF8Encoding> tiver sido construída com `throwOnInvalidBytes: true` (consulte a [documentação do construtor do UTF8Encoding] (<xref:System.Text.UTF8Encoding.%23ctor(System.Boolean,System.Boolean)>, a instância `UTF8Encoding` continuará a gerar uma entrada inválida em vez de executar a substituição U + FFFD.

O seguinte ilustra o impacto dessa alteração com uma entrada de 3 bytes inválida:

|Entrada de 3 bytes formada incorretamente|Saída antes do .NET Core 3,0|Saída a partir do .NET Core 3,0|
|---|---|---|
| `[ ED A0 90 ]` | `[ FFFD FFFD ]` (saída de 2 caracteres)| `[ FFFD FFFD FFFD ]` (saída de 3 caracteres)|

Essa saída de 3 caracteres é a saída preferida, de acordo com a _tabela 3-9_ do PDF padrão Unicode vinculado anteriormente.

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="recommended-action"></a>Ação recomendada

Nenhuma ação é necessária na parte do desenvolvedor.

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
