---
title: Valores ref return e ref local (Guia de C#)
description: Saiba como definir e usar os valores ref return e ref local
author: rpetrusha
ms.author: ronpet
ms.date: 04/04/2018
ms.openlocfilehash: 6250d2b0c3490cce18623d6b06d5e1a352f22c09
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/14/2018
ms.locfileid: "45616134"
---
# <a name="ref-returns-and-ref-locals"></a>Ref returns e ref locals

Começando com C# 7.0, C# dá suporte a valores de referência de devolução. Um valor retornado por referência permite que um método retorne uma referência a uma variável, em vez de um valor, de volta para um chamador. O chamador pode optar por tratar a variável retornada como se tivesse sido retornada por valor ou referência. O chamador pode criar uma nova variável que seja uma referência ao valor retornado, chamado de ref local.

## <a name="what-is-a-reference-return-value"></a>O que é um valor retornado por referência?

A maioria dos desenvolvedores estão familiarizados com passar um argumento para um método chamado *por referência*. A lista de argumentos de um método chamado inclui uma variável passada por referência. Todas as alterações feitas pelo método chamado ao valor são observadas pelo chamador. Um *valor retornado de referência* significa que um método retorna uma *referência* (ou um alias) para alguma variável. O escopo da variável deve incluir o método. O tempo de vida da variável deve ultrapassar o retorno do método. As modificações no valor retornado do método pelo chamador são feitas na variável que é retornada pelo método.

Declarar que um método retorna um *valor retornado de referência* indica que o método retorna um alias para uma variável. A intenção de design muitas vezes é que o código de chamada deve ter acesso a essa variável por meio do alias, inclusive para modificá-lo. Por conseguinte, métodos retornados por referência não podem ter o tipo de retorno `void`.

Há algumas restrições quanto à expressão que um método pode retornar como um valor retornado por referência. As restrições incluem:

- O valor retornado deve ter um tempo de vida que ultrapasse a execução do método. Em outras palavras, não pode ser uma variável local no método que o retorna. Ele pode ser uma instância ou um campo estático de uma classe ou pode ser um argumento passado para o método. Tentar retornar a uma variável local gera o erro do compilador CS8168, "não é possível retornar o 'obj' local por referência porque ele não é um ref local".

- O valor retornado não pode ser um `null` literal. Retornar `null` gera o erro do compilador CS8156, "Uma expressão não pode ser usada neste contexto porque ela não pode ser retornada por referência."

   Um método com um retorno de referência pode retornar um alias para uma variável cujo valor é atualmente o valor nulo (não instanciado) ou um [tipo anulável](../nullable-types/index.md) para um tipo de valor.
 
- O valor retornado não pode ser uma constante, um membro de enumeração, o valor retornado por valor de uma propriedade ou um método `class` ou `struct`. Violar essa regra gera o erro do compilador CS8156, "Uma expressão não pode ser usada neste contexto porque ela não pode ser retornada por referência."

Além disso, valores retornados de referência não são permitidos em métodos assíncronos. Um método assíncrono pode retornar antes de concluir a execução, enquanto o valor retornado ainda é desconhecido.
 
## <a name="defining-a-ref-return-value"></a>Definindo um valor retornado ref

Um método que retorna um *valor retornado de referência* deve satisfazer as duas condições a seguir:

- A assinatura do método inclui a palavra-chave [ref](../../language-reference/keywords/ref.md) na frente do tipo de retorno.
- Cada instrução [return](../../language-reference/keywords/return.md) no corpo do método inclui a palavra-chave [ref](../../language-reference/keywords/ref.md) antes do nome da instância retornada.

O exemplo a seguir mostra um método que satisfaz essas condições e retorna uma referência a um objeto `Person` chamado `p`:

```csharp
public ref Person GetContactInformation(string fname, string lname)
{
    // ...method implementation...
    return ref p;
}
```

## <a name="consuming-a-ref-return-value"></a>Consumindo um valor retornado ref

O valor retornado de ref é um alias para outra variável no escopo do método chamado. Você pode interpretar qualquer uso do retorno de ref como usando a variável da qual ele é um alias:

- Ao atribuir o valor, você atribui um valor à variável da qual ele é um alias.
- Ao ler o valor, você lê o valor da variável da qual ele é um alias.
- Se o retornar *por referência*, você retornará um alias para a mesma variável.
- Se o passar para outro método *por referência*, você passará uma referência à variável da qual ele é um alias.
- Ao criar um alias de [referência local](#ref-locals), você cria um novo alias para a mesma variável.


## <a name="ref-locals"></a>Ref locals

Suponha que o método `GetContactInformation` seja declarado como uma referência de retorno:

```csharp
public ref Person GetContactInformation(string fname, string lname)
```

Uma atribuição por valor lê o valor de uma variável e o atribui a uma nova variável:

```csharp
Person p = contacts.GetContactInformation("Brandie", "Best");
```

A atribuição anterior declara `p` como uma variável local. O valor inicial é copiado da leitura do valor retornado por `GetContactInformation`. As atribuições futuras para `p` não alterarão o valor da variável retornado por `GetContactInformation`. A variável `p` não é um alias para a variável retornada.

Você declara uma variável *ref local* para copiar o alias para o valor original. Na atribuição de seguir, `p` é um alias para a variável retornada de `GetContactInformation`.

```csharp
ref Person p = ref contacts.GetContactInformation("Brandie", "Best");
```

O uso subsequente de `p` é o mesmo que usar a variável retornada pelo `GetContactInformation` porque `p` é um alias dessa variável. As alterações em `p` também alteram a variável retornada de `GetContactInformation`.

A palavra-chave `ref` é usada antes da declaração de variável local *e* antes da chamada de método. 

Você pode acessar um valor por referência da mesma maneira. Em alguns casos, acessar um valor por referência aumenta o desempenho, evitando uma operação de cópia potencialmente dispendiosa. Por exemplo, a instrução a seguir mostra como é possível definir um valor de local de ref que é usado para fazer referência a um valor.

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct;
```

A palavra-chave `ref` é usada antes da declaração da variável local *e* antes do valor, no segundo exemplo. A falha ao incluir as palavras-chave `ref` na declaração e na atribuição da variável nos dois exemplos resulta no erro do compilador CS8172, "Não é possível inicializar uma variável por referência com um valor." 

Antes do C# 7.3, variáveis locais de referência não podiam ser reatribuídas para se referir a um armazenamento diferente depois de serem inicializadas. Essa restrição foi removida. O exemplo a seguir mostra uma transferência:

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct; // initialization
refLocal = ref anotherVeryLargeStruct; // reassigned, refLocal refers to different storage.
```

 Variáveis locais de referência ainda devem ser inicializadas quando são declaradas.

## <a name="ref-returns-and-ref-locals-an-example"></a>Ref returns e ref locals: um exemplo

O exemplo a seguir define uma classe `NumberStore` que armazena uma matriz de valores inteiros. O método `FindNumber` retorna por referência o primeiro número maior ou igual ao número passado como um argumento. Se nenhum número for maior ou igual ao argumento, o método retornará o número no índice 0. 

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStore.cs#1)]

A exemplo a seguir chama o método `NumberStore.FindNumber` para recuperar o primeiro valor maior ou igual a 16. O chamador então dobra o valor retornado pelo método. A saída do exemplo mostra a alteração refletida no valor dos elementos de matriz da instância `NumberStore`.

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStore.cs#2)]

Sem suporte para valores retornados por referência, essa operação é executada retornando-se o índice do elemento de matriz, juntamente com o respectivo valor. O chamador pode usar esse índice para modificar o valor em uma chamada de método separada. No entanto, o chamador também pode modificar o índice para acessar e possivelmente modificar outros valores de matriz.  

A exemplo a seguir mostra como o método `FindNumber` poderia ser reescrito após o C# 7.3 para usar a transferência de local de referência:

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStoreUpdated.cs#1)]

Essa segunda versão é mais eficiente, com sequências mais longas em cenários em que o número procurado é mais próximo ao final da matriz.

## <a name="see-also"></a>Consulte também

- [ref keyword](../../language-reference/keywords/ref.md)  
- [Semântica de referência com Tipos de valor](../../../csharp/reference-semantics-with-value-types.md)
