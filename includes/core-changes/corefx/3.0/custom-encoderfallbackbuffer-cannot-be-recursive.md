---
ms.openlocfilehash: 58d1c8cd3aff52703522391c14348bd81c108587
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74568105"
---
### <a name="custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively"></a>As instâncias de EncoderFallbackBuffer personalizadas não podem recuar recursivamente

As <xref:System.Text.EncoderFallbackBuffer> instâncias personalizadas não podem recuar recursivamente. A implementação de deve resultar em uma seqüência de <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> caracteres conversível para a codificação de destino. Caso contrário, ocorre uma exceção.

#### <a name="change-description"></a>Descrição da alteração

Durante uma operação de transcodificação de caracteres para bytes, o tempo de execução detecta <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> seqüências UTF-16 mal formadas ou não conversíveis e fornece esses caracteres para o método. O `Fallback` método determina quais caracteres devem ser substituídos pelos dados originais <xref:System.Text.EncoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> não conversíveis, e esses caracteres são drenados por chamada em um loop.

O tempo de execução, então, tenta transcodificar esses caracteres de substituição para a codificação de destino. Se esta operação for bem sucedida, o tempo de execução continuará a transcodificação de onde parou na seqüência de entrada original.

Em .NET Core Preview 7 e versões anteriores, implementações personalizadas podem retornar seqüências de <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> caracteres que não são conversíveis para a codificação de destino. Se os caracteres substituídos não puderem ser transcodificados para <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> a codificação de destino, <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> o tempo de execução invoca o método mais uma vez com os caracteres de substituição, esperando que o método retorne uma nova seqüência de substituição. Este processo continua até que o tempo de execução eventualmente veja uma substituição bem formada e conversível, ou até que uma contagem máxima de recursão seja alcançada.

A partir do .NET Core 3.0, implementações personalizadas de sequências de <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> caracteres devem retornar conversíveis para a codificação de destino. Se os caracteres substituídos não puderem ser <xref:System.ArgumentException> transcodificados para a codificação do destino, um será jogado. O tempo de execução não fará mais <xref:System.Text.EncoderFallbackBuffer> chamadas recursivas para a instância.

Esse comportamento só se aplica quando todas as três condições são atendidas:

- O tempo de execução detecta uma seqüência UTF-16 mal formada ou uma seqüência UTF-16 que não pode ser convertida para a codificação de destino.
- Um <xref:System.Text.EncoderFallback> costume foi especificado.
- O <xref:System.Text.EncoderFallback> costume tenta substituir uma nova seqüência UTF-16 mal formada ou não conversível.

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="recommended-action"></a>Ação recomendada

A maioria dos desenvolvedores não precisa tomar nenhuma ação.

Se um aplicativo <xref:System.Text.EncoderFallback> usar <xref:System.Text.EncoderFallbackBuffer> um personalizado e <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> uma classe, assegure-se de que a implementação preencha o buffer de <xref:System.Text.EncoderFallbackBuffer.Fallback%2A> recuo com dados UTF-16 bem formados que são diretamente conversíveis para a codificação de destino quando o método é invocado pela primeira vez pelo tempo de execução.

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
