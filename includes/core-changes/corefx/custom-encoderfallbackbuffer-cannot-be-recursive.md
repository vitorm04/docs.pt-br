---
ms.openlocfilehash: b4b49b55cda26ac9d9760f93e9758aab940ad135
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117257"
---
### <a name="custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively"></a>Instâncias EncoderFallbackBuffer personalizadas não podem retornar recursivamente

As <xref:System.Text.EncoderFallbackBuffer> instâncias personalizadas não podem fazer fallback recursivamente. A implementação de <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> deve resultar em uma sequência de caracteres que é conversível para a codificação de destino. Caso contrário, ocorrerá uma exceção. 

#### <a name="details"></a>Detalhes

Durante uma operação de transcodificação de caractere para byte, o tempo de execução detecta sequências UTF-16 mal formadas ou não conversíveis e fornece <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> esses caracteres para o método. O `Fallback` método determina quais caracteres devem ser substituídos pelos dados originais não conversíveis e esses caracteres são drenados chamando <xref:System.Text.EncoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> em um loop.

Em seguida, o tempo de execução tenta transcodificar esses caracteres de substituição para a codificação de destino. Se essa operação for realizada com sucesso, o tempo de execução continuará transcodificando de onde parou na cadeia de caracteres de entrada original. 

No .NET Core Preview 7 e versões anteriores, implementações personalizadas <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> do podem retornar sequências de caracteres que não são conversíveis para a codificação de destino. Se os caracteres substituídos não puderem ser transcodificados para a codificação de destino, o tempo <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> de execução invocará o método novamente com os caracteres <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> de substituição, esperando que o método retorne uma nova sequência de substituição. Esse processo continua até que o tempo de execução eventualmente Veja uma substituição bem formada, conversível ou até que uma contagem de recursão máxima seja atingida.

A partir do .NET Core 3,0, implementações <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> personalizadas do devem retornar sequências de caracteres que são conversíveis para a codificação de destino. Se os caracteres substituídos não puderem ser transcodificados para a codificação de <xref:System.ArgumentException> destino, um será lançado. O tempo de execução não fará mais chamadas recursivas <xref:System.Text.EncoderFallbackBuffer> na instância. 

Esse comportamento se aplica somente quando todas as três condições a seguir são atendidas:

- O tempo de execução detecta uma sequência UTF-16 mal formada ou uma sequência UTF-16 que não pode ser convertida para a codificação de destino.
- Um personalizado <xref:System.Text.EncoderFallback> foi especificado.
- As tentativas <xref:System.Text.EncoderFallback> personalizadas de substituir uma nova sequência UTF-16 mal formada ou não conversível.

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="recommended-action"></a>Ação recomendada

A maioria dos desenvolvedores não precisam realizar nenhuma ação.

Se um aplicativo usar uma classe <xref:System.Text.EncoderFallback> e <xref:System.Text.EncoderFallbackBuffer> personalizada, verifique se a implementação <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> de popula o buffer de fallback com dados UTF-16 bem formados que são conversíveis diretamente para a codificação de <xref:System.Text.EncoderFallbackBuffer.Fallback%2A> destino quando o método é invocado pela primeira vez pelo tempo de execução.

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