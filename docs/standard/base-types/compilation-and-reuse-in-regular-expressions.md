---
title: Compilação e reutilização em expressões regulares
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- parsing text with regular expressions, compilation
- searching with regular expressions, compilation
- .NET Framework regular expressions, engines
- .NET Framework regular expressions, compilation
- regular expressions, compilation
- compilation, regular expressions
- pattern-matching with regular expressions, compilation
- regular expressions, engines
ms.assetid: 182ec76d-5a01-4d73-996c-0b0d14fcea18
ms.openlocfilehash: 3e1dfe8373145286b03e503f038e267ff0d4c4f3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73091737"
---
# <a name="compilation-and-reuse-in-regular-expressions"></a>Compilação e reutilização em expressões regulares
Você pode otimizar o desempenho de aplicativos que fazem uso intensivo de expressões regulares compreendendo como o mecanismo de expressões regulares compila expressões e como as expressões regulares são armazenadas em cache. Este tópico discute a compilação e o cache.  
  
## <a name="compiled-regular-expressions"></a>Expressões regulares compiladas  
 Por padrão, o mecanismo de expressões regulares compila uma expressão regular para uma sequência de instruções internas (esses são códigos de alto nível que são diferentes da Microsoft Intermediate Language ou MSIL). Quando o mecanismo executa uma expressão regular, ele interpreta os códigos internos.  
  
 Se um objeto <xref:System.Text.RegularExpressions.Regex> for construído com a opção <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType>, ele compilará a expressão regular para o código explícito em MSIL, em vez de instruções internas de expressões regulares de alto nível. Isso permite que o compilador JIT (just-in-time) do .NET converta a expressão para um código de computador nativo para um melhor desempenho.  
  
No entanto, a MSIL gerada não pode ser descarregada. A única maneira de descarregar o código é descarregar todo o domínio de aplicativo (ou seja, descarregar todo o código do aplicativo). Na verdade, quando uma expressão regular é compilada com a opção <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType>, o .NET nunca libera os recursos usados pela expressão compilada, mesmo que a expressão regular tenha sido criada por um objeto <xref:System.Text.RegularExpressions.Regex> liberado para a coleta de lixo.  
  
 Você precisa ser cuidadoso para limitar o número de expressões regulares diferentes que compila com a opção <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> para evitar consumir recursos em demasia. Se um aplicativo precisar usar um número grande ou ilimitado de expressões regulares, cada expressão deve ser interpretada, não compilada. No entanto, se um número pequeno de expressões regulares forem usadas repetidamente, elas devem ser compiladas com <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> para melhorar o desempenho. Uma alternativa é usar expressões regulares pré-compiladas. Você pode compilar todas as suas expressões em uma DLL reutilizável usando o método <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A>. Isso evita a necessidade de compilar no runtime enquanto ainda se beneficia da velocidade das expressões regulares compiladas.  
  
## <a name="the-regular-expressions-cache"></a>Cache de expressões regulares  
 Para melhorar o desempenho, o mecanismo de expressões regulares mantém um cache em todo o aplicativo com as expressões regulares compiladas. O cache armazena padrões de expressões regulares que são usados somente em chamadas de método estático. (Padrões de expressão regular fornecidos para métodos de instância não são armazenados em cache.) Isso evita a necessidade de analisar novamente uma expressão em um código de byte de alto nível sempre que ela for usada.  
  
 O número máximo de expressões regulares em cache é determinado pelo valor da propriedade `static` (`Shared` no Visual Basic) <xref:System.Text.RegularExpressions.Regex.CacheSize%2A?displayProperty=nameWithType>. Por padrão, o mecanismo de expressões regulares armazena em cache até 15 expressões regulares compiladas. Se o número de expressões regulares compiladas ultrapassar o tamanho do cache, a expressão regular menos utilizada recentemente será descartada e a nova expressão regular será armazenada em cache.  
  
 Seu aplicativo pode tirar proveito de expressões regulares pré-compiladas de uma das duas maneiras a seguir:  
  
- Usando um método estático do objeto <xref:System.Text.RegularExpressions.Regex> para definir a expressão regular. Se você estiver usando um padrão de expressão regular que já foi definido em outra chamada de método estático, o mecanismo de expressões regulares o recuperará do cache. Caso contrário, o mecanismo compilará a expressão regular e a adicionará ao cache.  
  
- Reutilizando um objeto <xref:System.Text.RegularExpressions.Regex> existente enquanto o padrão de expressão regular for necessário.  
  
 Devido à sobrecarga da instanciação de objetos e à compilação da expressão regular, criar e destruir rapidamente vários objetos <xref:System.Text.RegularExpressions.Regex> é um processo muito caro. Para aplicativos que usam um grande número de expressões regulares diferentes, você pode otimizar o desempenho usando chamadas para métodos `Regex` estáticos e, possivelmente, aumentando o tamanho do cache de expressão regular.  
  
## <a name="see-also"></a>Consulte também

- [Expressões regulares do .NET](../../../docs/standard/base-types/regular-expressions.md)
