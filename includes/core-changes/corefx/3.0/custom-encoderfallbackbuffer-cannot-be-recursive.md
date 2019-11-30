---
ms.openlocfilehash: 58d1c8cd3aff52703522391c14348bd81c108587
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568105"
---
### <a name="custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively"></a>Instâncias EncoderFallbackBuffer personalizadas não podem retornar recursivamente

As instâncias de <xref:System.Text.EncoderFallbackBuffer> personalizadas não podem retornar recursivamente. A implementação de <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> deve resultar em uma sequência de caracteres que é conversível para a codificação de destino. Caso contrário, ocorrerá uma exceção.

#### <a name="change-description"></a>Alterar descrição

Durante uma operação de transcodificação de caractere para byte, o tempo de execução detecta sequências UTF-16 mal formadas ou não conversíveis e fornece esses caracteres para o método de <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType>. O método `Fallback` determina quais caracteres devem ser substituídos pelos dados não conversíveis originais, e esses caracteres são drenados chamando <xref:System.Text.EncoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> em um loop.

Em seguida, o tempo de execução tenta transcodificar esses caracteres de substituição para a codificação de destino. Se essa operação for realizada com sucesso, o tempo de execução continuará transcodificando de onde parou na cadeia de caracteres de entrada original.

No .NET Core Preview 7 e versões anteriores, implementações personalizadas de <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> podem retornar sequências de caracteres que não são conversíveis para a codificação de destino. Se os caracteres substituídos não puderem ser transcodificados para a codificação de destino, o tempo de execução invocará o método <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> mais uma vez com os caracteres de substituição, esperando que o método <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> retorne uma nova sequência de substituição. Esse processo continua até que o tempo de execução eventualmente Veja uma substituição bem formada, conversível ou até que uma contagem de recursão máxima seja atingida.

A partir do .NET Core 3,0, implementações personalizadas de <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> devem retornar sequências de caracteres que são conversíveis para a codificação de destino. Se os caracteres substituídos não puderem ser transcodificados para a codificação de destino, um <xref:System.ArgumentException> será lançado. O tempo de execução não fará mais chamadas recursivas na instância de <xref:System.Text.EncoderFallbackBuffer>.

Esse comportamento se aplica somente quando todas as três condições a seguir são atendidas:

- O tempo de execução detecta uma sequência UTF-16 mal formada ou uma sequência UTF-16 que não pode ser convertida para a codificação de destino.
- Um <xref:System.Text.EncoderFallback> personalizado foi especificado.
- O <xref:System.Text.EncoderFallback> personalizado tenta substituir uma nova sequência UTF-16 mal formada ou não conversível.

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="recommended-action"></a>Ação recomendada

A maioria dos desenvolvedores não precisam realizar nenhuma ação.

Se um aplicativo usar uma classe <xref:System.Text.EncoderFallback> e <xref:System.Text.EncoderFallbackBuffer> personalizadas, verifique se a implementação de <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> popula o buffer de fallback com dados UTF-16 bem formados que são conversíveis diretamente para a codificação de destino quando o método <xref:System.Text.EncoderFallbackBuffer.Fallback%2A> é invocado pela primeira vez pelo tempo de execução.

#### <a name="category"></a>Categoria

CoreFx

#### <a name="affected-apis"></a>APIs afetadas

- <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType>
- <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType>

<!--

### Affected APIs

- `Overload:System.Text.EncoderFallbackBuffer.Fallback`
- `M:System.Text.EncoderFallbackBuffer.GetNextChar`

-->
