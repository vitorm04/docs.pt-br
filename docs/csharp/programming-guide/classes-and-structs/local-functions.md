---
title: Funções locais – Guia de Programação em C#
ms.custom: seodec18
ms.date: 06/14/2017
helpviewer_keywords:
- local functions [C#]
ms.openlocfilehash: 24b7d6f98e331110ddcd971d0d0b21003dbe023d
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736843"
---
# <a name="local-functions-c-programming-guide"></a>Funções locais (Guia de Programação em C#)

Começando com o C# 7.0, o C# é compatível com *funções locais*. Funções locais são métodos privados de um tipo que estão aninhados em outro membro. Eles só podem ser chamados do membro que os contém. Funções locais podem ser declaradas em e chamadas de:

- Métodos, especialmente os métodos iteradores e os métodos assíncronos
- Construtores
- Acessadores de propriedade
- Acessadores de eventos
- Métodos anônimos
- Expressões lambda
- Finalizadores
- Outras funções locais

No entanto, as funções locais não podem ser declaradas dentro de um membro apto para expressão.

> [!NOTE]
> Em alguns casos, você pode usar uma expressão lambda para implementar uma funcionalidade que também tem suporte por uma função local. Para obter uma comparação, consulte [Funções locais comparadas com expressões Lambda](../../local-functions-vs-lambdas.md).

Funções locais tornam a intenção do seu código clara. Qualquer pessoa que ler seu código poderá ver que o método não pode ser chamado, exceto pelo método que o contém. Para projetos de equipe, elas também impossibilitam que outro desenvolvedor chame o método por engano diretamente de qualquer outro lugar na classe ou no struct.
 
## <a name="local-function-syntax"></a>Sintaxe de função local

Uma função local é definida como um método aninhado dentro de um membro recipiente. Sua definição tem a seguinte sintaxe:

```csharp
<modifiers: async | unsafe> <return-type> <method-name> <parameter-list>
```

Funções locais podem usar os modificadores [async](../../language-reference/keywords/async.md) e [unsafe](../../language-reference/keywords/unsafe.md). 

Observe que todas as variáveis locais que estão definidas no membro recipiente, incluindo seus parâmetros de método, são acessíveis na função local. 

Ao contrário de uma definição de método, uma definição de função local não pode incluir o modificador de acesso de membro. Já que todas as funções locais são privadas, incluir um modificador de acesso como a palavra-chave `private` gera o erro do compilador CS0106, "O modificador 'private' não é válido para este item".

> [!NOTE]
> Antes de C# 8,0, as funções locais não podem incluir o modificador de `static`. Incluir a palavra-chave `static` gera o erro do compilador CS0106, "O modificador 'static' não é válido para este item".

Além disso, os atributos não podem ser aplicados à função local ou aos respectivos parâmetros e parâmetros de tipo. 
 
O exemplo a seguir define uma função local chamada `AppendPathSeparator` que é privada para um método chamado `GetText`:
   
[!code-csharp[LocalFunctionExample](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions1.cs)]  
   
## <a name="local-functions-and-exceptions"></a>Funções locais e exceções

Um dos recursos úteis de funções locais é que elas podem permitir que exceções sejam apresentadas imediatamente. Para iteradores de método, as exceções são apresentadas somente quando a sequência retornada é enumerada e não quando o iterador é recuperado. Para métodos assíncronos, as exceções geradas em um método assíncrono são observadas quando a tarefa retornada é esperada. 

O exemplo a seguir define um método `OddSequence` que enumera números ímpares entre um intervalo especificado. Já que ele passa um número maior que 100 para o método enumerador `OddSequence`, o método gera uma <xref:System.ArgumentOutOfRangeException>. Assim como demonstrado pela saída do exemplo, a exceção é apresentada somente quando você itera os números e não quando você recupera o enumerador.

[!code-csharp[LocalFunctionIterator1](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator1.cs)] 

Em vez disso, você pode lançar uma exceção ao executar a validação e antes de recuperar o iterador, retornando o iterador de uma função local, conforme mostrado no exemplo a seguir.

[!code-csharp[LocalFunctionIterator2](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator2.cs)]

Funções locais podem ser usadas de maneira semelhante para lidar com exceções fora da operação assíncrona. Em geral, exceções geradas no método assíncrono exigem que você examine as exceções internas de um <xref:System.AggregateException>. Funções locais permitem que seu código falhe no modo rápido e permitem que a exceção seja gerada e observada de forma síncrona.

O exemplo a seguir usa um método assíncrono chamado `GetMultipleAsync` para pausar para um número especificado de segundos e retornar um valor que é um múltiplo aleatório desse número de segundos. O atraso máximo é de 5 segundos; um <xref:System.ArgumentOutOfRangeException> resulta em se o valor for maior que 5. Como mostra o exemplo a seguir, a exceção que é lançada quando um valor de 6 é passada para o método `GetMultipleAsync` é encapsulada em um <xref:System.AggregateException> depois que o método `GetMultipleAsync` inicia sua execução.

[!code-csharp[LocalFunctionAsync](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async1.cs)] 

Assim como foi feito com o método iterador, podemos refatorar o código deste exemplo para executar a validação antes de chamar o método assíncrono. Assim como demonstrado pela saída de exemplo a seguir, o <xref:System.ArgumentOutOfRangeException> não é empacotado em uma <xref:System.AggregateException>.

[!code-csharp[LocalFunctionAsync](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async2.cs)] 

## <a name="see-also"></a>Consulte também

- [Métodos](methods.md)
