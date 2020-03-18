---
title: volatile – Referência de C#
ms.date: 10/24/2018
f1_keywords:
- volatile_CSharpKeyword
- volatile
helpviewer_keywords:
- volatile keyword [C#]
ms.assetid: 78089bc7-7b38-4cfd-9e49-87ac036af009
ms.openlocfilehash: c7a6c442c33ac2b41f652805837f455a957819de
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712839"
---
# <a name="volatile-c-reference"></a>volatile (Referência de C#)

A palavra-chave `volatile` indica que um campo pode ser modificado por vários threads que estão em execução ao mesmo tempo. O compilador, o sistema do runtime e até mesmo o hardware podem reorganizar as leituras e gravações para locais de memória por motivos de desempenho. Os campos que são declarados `volatile` não estão sujeitos a essas otimizações. A adição do modificador `volatile` garante que todos os threads observarão gravações voláteis executadas por qualquer outro thread na ordem em que elas foram executadas. Não há nenhuma garantia de uma única ordenação total de gravações voláteis como visto em todos os threads de execução.

A palavra-chave `volatile` pode ser aplicada a campos desses tipos:

- Tipos de referência.
- Tipos de ponteiro (em um contexto sem segurança). Observe que embora o ponteiro em si possa ser volátil, o objeto para o qual ele aponta não pode. Em outras palavras, você não pode declarar um "ponteiro como volátil".
- Tipos simples, como `sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `char`, `float` e `bool`.
- Um tipo `enum` com um dos seguintes tipos base: `byte`, `sbyte`, `short`, `ushort`, `int` ou `uint`.
- Parâmetros de tipo genérico conhecidos por serem tipos de referência.
- <xref:System.IntPtr> e <xref:System.UIntPtr>.

Outros tipos, inclusive `double` e `long`, não podem ser marcados como `volatile`, pois as leituras e gravações nos campos desses tipos não podem ser garantidas como atômicas. Para proteger o acesso multi-threaded a <xref:System.Threading.Interlocked> esses tipos de campos, use os membros da classe ou proteja o acesso usando a [`lock`](lock-statement.md) declaração.

A palavra-chave `volatile` pode ser aplicada somente aos campos de uma `class` ou `struct`. As variáveis locais não podem ser declaradas como `volatile`.

## <a name="example"></a>Exemplo

O exemplo a seguir mostra como declarar uma variável de campo público como `volatile`.

[!code-csharp[declareVolatile](~/samples/snippets/csharp/language-reference/keywords/volatile/Program.cs#Declaration)]

O exemplo a seguir demonstra como um thread de trabalho ou auxiliar pode ser criado e usado para executar o processamento em paralelo com o do thread primário. Para saber mais sobre multithreading, confira [Threading gerenciado](../../../standard/threading/index.md).

[!code-csharp[declareVolatile](~/samples/snippets/csharp/language-reference/keywords/volatile/Program.cs#Volatile)]

Com o modificador `volatile` adicionado à declaração de `_shouldStop` definida, você sempre obterá os mesmos resultados (semelhante ao trecho mostrado no código anterior). No entanto, sem esse modificador no membro `_shouldStop`, o comportamento é imprevisível. O método `DoWork` pode otimizar o acesso do membro, resultando na leitura de dados obsoletos. Devido à natureza da programação multithreaded, o número de leituras obsoletas é imprevisível. Diferentes execuções do programa produzirão resultados um pouco diferentes.

## <a name="c-language-specification"></a>especificação da linguagem C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Confira também

- [Especificação da linguagem C#: palavra-chave volatile](../../../../_csharplang/spec/classes.md#volatile-fields)
- [C# Referência](../index.md)
- [C# Guia de Programação](../../programming-guide/index.md)
- [Palavras-chave do C#](index.md)
- [Modificadores](index.md)
- [declaração de bloqueio](lock-statement.md)
- <xref:System.Threading.Interlocked>
