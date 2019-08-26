---
title: Construtores – Guia de Programação em C#
ms.custom: seodec18
ms.date: 05/05/2017
helpviewer_keywords:
- constructors [C#]
- classes [C#], constructors
- C# language, constructors
ms.assetid: df2e2e9d-7998-418b-8e7d-890c17ff6c95
ms.openlocfilehash: ea780fc983ed46c8a5ccb54ab618d1a0a2a928d1
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69597094"
---
# <a name="constructors-c-programming-guide"></a>Construtores (Guia de Programação em C#)

Sempre que uma [classe](../../language-reference/keywords/class.md) ou [struct](../../language-reference/keywords/struct.md) é criada, o construtor é chamado. Uma classe ou struct pode ter vários construtores que usam argumentos diferentes. Os construtores permitem que o programador defina valores padrão, limite a instanciação e grave códigos flexíveis e fáceis de ler. Para obter mais informações e exemplos, consulte [Usando Construtores](./using-constructors.md) e [Construtores de Instância](./instance-constructors.md).  

## <a name="parameterless-constructors"></a>Construtores sem parâmetros
  
Se um construtor não for fornecido para a classe, o C# criará por padrão um construtor que instancia o objeto e define variáveis de membro para os valores padrão, conforme listado na [Tabela de Valores Padrão](../../language-reference/keywords/default-values-table.md). Se você não fornecer um construtor para o struct, o C# dependerá de um *construtor sem parâmetro implícito* para inicializar automaticamente a cada campo de um tipo de valor para o valor padrão conforme listado na [Tabela de Valores Padrão](../../language-reference/keywords/default-values-table.md). Para obter mais informações e exemplos, consulte [Construtores de Instância](./instance-constructors.md).  

## <a name="constructor-syntax"></a>Sintaxe do construtor

Um construtor é um método cujo nome é igual ao nome de seu tipo. Sua assinatura do método inclui apenas o nome do método e lista de parâmetros, ele não inclui um tipo de retorno. O exemplo a seguir mostra o construtor para uma classe denominada `Person`.

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#1)]  

Se um construtor puder ser implementado como uma única instrução, você poderá usar uma [definição de corpo da expressão](../statements-expressions-operators/expression-bodied-members.md). O exemplo a seguir define uma classe `Location` cujo construtor tem um único parâmetro de cadeia de caracteres chamado *nome*. A definição de corpo da expressão atribui o argumento ao campo `locationName`.

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

## <a name="static-constructors"></a>Construtores estáticos

Os exemplos anteriores têm todos os construtores de instância mostrado, que criam um novo objeto. Uma classe ou struct também pode ter um construtor estático, que inicializa membros estáticos do tipo.  Construtores estáticos não têm parâmetros. Se você não fornecer um construtor estático para inicializar campos estáticos, o compilador C# inicializará campos estáticos com seu valor padrão, conforme listado na [Tabela de Valores Padrão](../../language-reference/keywords/default-values-table.md).

O exemplo a seguir usa um construtor estático para inicializar um campo estático.

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#2)]  

Você também pode definir um construtor estático com uma definição de corpo da expressão, como mostra o exemplo a seguir. 

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#3)]  

Para obter mais informações e exemplos, consulte [Construtores Estáticos](./static-constructors.md).  
  
## <a name="in-this-section"></a>Nesta seção  
 [Usando construtores](./using-constructors.md)  
  
 [Construtores de instância](./instance-constructors.md)  
  
 [Construtores particulares](./private-constructors.md)  
  
 [Construtores estáticos](./static-constructors.md)  
  
 [Como: escrever um construtor de cópia](./how-to-write-a-copy-constructor.md)  
  
## <a name="see-also"></a>Consulte também

- [Guia de Programação em C#](../index.md)
- [Classes e Structs](./index.md)
- [Finalizadores](./destructors.md)
- [static](../../language-reference/keywords/static.md)
- [Por que os inicializadores são executados na ordem oposta, como construtores? Parte 1](https://blogs.msdn.microsoft.com/ericlippert/2008/02/15/why-do-initializers-run-in-the-opposite-order-as-constructors-part-one)
