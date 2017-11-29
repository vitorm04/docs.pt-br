---
title: Valores ref return e ref local (Guia de C#)
description: Saiba como definir e usar os valores ref return e ref local
author: rpetrusha
ms.author: ronpet
ms.date: 05/30/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 18cf7a4b-29f0-4b14-85b8-80af754aabd8
ms.openlocfilehash: 1d8fb092b578602b5d4f791a3fd14f47dfae1ba6
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/18/2017
---
# <a name="ref-returns-and-ref-locals"></a>Ref returns e ref locals

Começando com o C# 7, o C# dá suporte a valores retornados por referência (ref returns). Um valor retornado por referência permite que um método retorne uma referência a um objeto, em vez de um valor, de volta para um chamador. O chamador pode optar por tratar o objeto retornado como se ele tivesse sido retornado por valor ou por referência. Um valor retornado por referência que o chamador trata como uma referência em vez de um valor é um ref local.

## <a name="what-is-a-reference-return-value"></a>O que é um valor retornado por referência?

A maioria dos desenvolvedores estão familiarizados com passar um argumento para um método chamado *por referência*. A lista de argumentos de um método chamado inclui um valor passado por referência e todas as alterações ao valor dele pelo método chamado são retornadas ao chamador. Um *valor retornado por referência* é o oposto:

- O valor retornado do método chamado é uma referência, em vez de ser um argumento passado a ele.

- O chamador, em vez do método chamado, pode modificar o valor retornado pelo método.

- Em vez de modificações ao argumento que são refletidas no estado do objeto no chamador, as modificações para o valor retornado do método pelo chamador são refletidas no estado do objeto cujo método foi chamado.

Valores retornados por referência podem produzir um código mais compacto, bem como permitir que um objeto exponha apenas os itens de dados individuais, tais como um elemento de matriz, que são de interesse do chamador. Isso reduz a probabilidade de que o chamador modifique inadvertidamente o estado do objeto.

Há algumas restrições quanto ao valor que um método pode retornar como um valor retornado por referência. Elas incluem:

- O valor retornado não pode ser `void`. Tentar definir um método com um valor retornado por referência `void` gera o erro do compilador CS1547, "A palavra-chave 'void' não pode ser usada neste contexto".
 
- O valor retornado não pode ser uma variável local no método que o retorna; ele deve ter um escopo que está fora do método que o retorna. Ele pode ser uma instância ou um campo estático de uma classe ou pode ser um argumento passado para o método. Tentar retornar a uma variável local gera o erro do compilador CS8168, "não é possível retornar o 'obj' local por referência porque ele não é um ref local".

- O valor retornado não pode ser um `null`. A tentativa de retornar `null` gera o erro do compilador CS8156, "Uma expressão não pode ser usada neste contexto porque ela não pode ser retornada por referência."

   Se um método com um ref return precisar retornar um valor nulo, você poderá retornar um valor nulo (não instanciado) para um tipo de referência ou um [tipo que permite valor nulo](../nullable-types/index.md) para um tipo de valor.
 
- O valor retornado não pode ser uma constante, um membro de enumeração ou uma propriedade de um `class` ou `struct`. A tentativa de retornar um deles gera o erro do compilador CS8156, "Uma expressão não pode ser usada neste contexto porque ela não pode ser retornada por referência."

Além disso, como um método assíncrono pode ser retornado antes de sua execução ser concluída, embora seu valor retornado ainda seja desconhecido, os valores retornados de referência não são permitidos em métodos assíncronos.
 
## <a name="defining-a-ref-return-value"></a>Definindo um valor retornado ref

Você define um valor retornado ref adicionando a palavra-chave [ref](../../language-reference/keywords/ref.md) ao tipo de retorno da assinatura de método. Por exemplo, a assinatura a seguir indica que a propriedade `GetContactInformation` retorna uma referência a um objeto `Person` ao chamador:

```csharp
public ref Person GetContactInformation(string fname, string lname);
```

Além disso, o nome do objeto retornado por cada instrução [return](../../language-reference/keywords/return.md) no corpo do método deve ser precedida pela palavra-chave [ref](../../language-reference/keywords/ref.md). Por exemplo, a instrução `return` a seguir retorna um objeto `Person` chamado `p` por referência:

```csharp
return ref p;
```

## <a name="consuming-a-ref-return-value"></a>Consumindo um valor retornado ref

Um chamador pode lidar com um valor retornado ref de uma de duas maneiras:

- Como um valor comum retornado pelo valor de um método. O chamador pode optar por ignorar que o valor retornado é um valor retornado por referência. Nesse caso, todas as alterações feitas ao valor retornado pela chamada de método não são refletidas no estado do tipo chamado. Se o valor retornado é um tipo de valor, todas as alterações feitas ao valor retornado pela chamada de método não são refletidas no estado do tipo chamado.

- Como um valor retornado por referência. O chamador deve definir a variável à qual o valor retornado por referência é atribuído como um [ref local](#ref-local) e as alterações para o valor retornado pela chamada de método são refletidas no estado do tipo chamado. 

## <a name="ref-locals"></a>Ref locals

Para lidar com o valor retornado por referência como uma referência, o chamador deve declarar o valor como sendo um *ref local* usando a palavra-chave `ref`. Por exemplo, se o valor retornado pelo método `Person.GetContactInfomation` deve ser consumido como uma referência em vez de um valor, a chamada de método é exibida como:

```csharp
ref Person p = ref contacts.GetContactInformation("Brandie", "Best");
```

Observe que a palavra-chave `ref` é usada antes da declaração de variável local *e* antes da chamada de método. Falha ao incluir palavras-chave `ref` na declaração da variável e resultados de atribuição no erro do compilador CS8172, "Não é possível inicializar uma variável por referência com um valor." 
 
As alterações subsequentes ao objeto `Person` retornado pelo método são refletidas no objeto `contacts`.

Se `p` não estiver definido como um ref local usando a palavra-chave `ref`, quaisquer alterações feitas a `p` pelo chamador não serão refletidas no objeto `contacts`.
 
## <a name="ref-returns-and-ref-locals-an-example"></a>Ref returns e ref locals: um exemplo

O exemplo a seguir define uma classe `NumberStore` que armazena uma matriz de valores inteiros. O método `FindNumber` retorna por referência o primeiro número maior ou igual ao número passado como um argumento. Se nenhum número for maior ou igual ao argumento, o método retornará o número no índice 0. 

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/ref-returns1.cs#1)]

A exemplo a seguir chama o método `NumberStore.FindNumber` para recuperar o primeiro valor maior ou igual a 16. O chamador então dobra o valor retornado pelo método. Assim como mostra a saída do exemplo, essa alteração é refletida no valor dos elementos de matriz da instância `NumberStore`.

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/ref-returns1.cs#2)]

Sem suporte para valores retornados por referência, essa operação normalmente é executada retornando-se o índice do elemento de matriz, juntamente com o respectivo valor. O chamador pode usar esse índice para modificar o valor em uma chamada de método separada. No entanto, o chamador também pode modificar o índice para acessar e possivelmente modificar outros valores de matriz.  
 
## <a name="see-also"></a>Consulte também

[ref keyword](../../language-reference/keywords/ref.md)
