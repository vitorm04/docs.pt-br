---
title: Como inicializar um dicionário com um inicializador de coleção – Guia de Programação em C#
ms.custom: seodec18
ms.date: 12/20/2018
helpviewer_keywords:
- collection initializers [C#], with Dictionary
ms.assetid: 25283922-f8ee-40dc-a639-fac30804ec71
ms.openlocfilehash: acd426b7652705ff395df9a81cde8ef549af0e31
ms.sourcegitcommit: d09c77414e9e4fc72c79b04deee7a756a120674e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54084687"
---
# <a name="how-to-initialize-a-dictionary-with-a-collection-initializer-c-programming-guide"></a>Como inicializar um dicionário com um inicializador de coleção (Guia de Programação em C#)

Um <xref:System.Collections.Generic.Dictionary%602> contém uma coleção de pares de chave-valor. Seu método <xref:System.Collections.Generic.Dictionary%602.Add*> recebe dois parâmetros, um para a chave e outro para o valor. Uma maneira de inicializar um <xref:System.Collections.Generic.Dictionary%602> ou qualquer coleção cujo método `Add` use vários parâmetros, é colocar cada conjunto de parâmetros entre chaves, conforme mostrado no exemplo a seguir. Outra opção é usar um inicializador de índice, também mostrado no exemplo a seguir.

## <a name="example"></a>Exemplo

No exemplo de código a seguir, um <xref:System.Collections.Generic.Dictionary%602> é inicializado com instâncias do tipo `StudentName`.  A primeira inicialização usa o método `Add` com dois argumentos. O compilador gera uma chamada para `Add` para cada um dos pares de chaves `int` e valores `StudentName`. A segunda usa um método de indexador público de leitura/gravação da classe `Dictionary`:

[!code-csharp-interactive[InitializerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToDictionaryInitializer.cs#HowToDictionaryInitializer)]  

Observe os dois pares de chaves em cada elemento da coleção na primeira declaração. As chaves internas circundam o inicializador de objeto do `StudentName` e as chaves mais externas circundam o inicializador do par chave/valor que será adicionado ao `students` <xref:System.Collections.Generic.Dictionary%602>. Por fim, todo o inicializador de coleção do dicionário é colocado entre chaves. Na segunda inicialização, o lado esquerdo da atribuição é a chave e o lado direito é o valor, usando um inicializador de objeto para `StudentName`.

## <a name="see-also"></a>Consulte também

- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)
- [Inicializadores de objeto e coleção](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)
