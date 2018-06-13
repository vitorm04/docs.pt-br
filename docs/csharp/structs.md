---
title: Structs – Guia de C#
description: Saiba mais sobre os tipos de struct e como criá-los
ms.date: 10/12/2016
ms.assetid: a7094b8c-7229-4b6f-82fc-824d0ea0ec40
ms.openlocfilehash: 9fe4e0278ecf46f762a93aa489030c0a9e5563b3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33349763"
---
# <a name="structs"></a>Structs
Um *struct* é um tipo de valor. Quando um struct é criado, a variável à qual o struct é atribuído contém os dados reais do struct. Quando o struct é atribuído a uma nova variável, ele é copiado. A nova variável e a variável original, portanto, contêm duas cópias separadas dos mesmos dados. As alterações feitas em uma cópia não afetam a outra cópia.

As variáveis de tipo de valor contêm diretamente seus valores, o que significa que a memória é alocada embutida em qualquer contexto em que a variável é declarada. Não há nenhuma alocação de heap separada ou sobrecarga de coleta de lixo para variáveis do tipo de valor.  
  
Há duas categorias de tipos de valor: [struct](./language-reference/keywords/struct.md) e [enum](./language-reference/keywords/enum.md).  
  
Os tipos numéricos internos são structs e têm propriedades e métodos que você pode acessar:  
  
[!code-csharp[Static Method](../../samples/snippets/csharp/concepts/structs/static-method.cs)]
  
Mas você declara e atribui valores a eles como se fossem tipos de não agregação simples:  
  
[!code-csharp[Assign Values](../../samples/snippets/csharp/concepts/structs/assign-value.cs)] 
  
Tipos de valor são *lacrados*, o que significa, por exemplo, que você não pode derivar um tipo de <xref:System.Int32> e não pode definir um struct para herdar de qualquer struct ou classe definida pelo usuário, porque um struct apenas pode herdar de <xref:System.ValueType>. No entanto, um struct pode implementar uma ou mais interfaces. Você pode converter um tipo de struct em um tipo de interface. Isso faz com que uma operação de *conversão boxing* encapsule o struct dentro de um objeto de tipo de referência no heap gerenciado. Operações de conversão boxing ocorrem quando você passa um tipo de valor para um método que usa um <xref:System.Object> como parâmetro de entrada. Para obter mais informações, consulte [Boxing e unboxing](./programming-guide/types/boxing-and-unboxing.md ).  
  
Você usa a palavra-chave [struct](./language-reference/keywords/struct.md) para criar seus próprios tipos de valor personalizados. Normalmente, um struct é usado como um contêiner para um pequeno conjunto de variáveis relacionadas, conforme mostrado no exemplo a seguir:  
  
[!code-csharp[Struct Keyword](../../samples/snippets/csharp/concepts/structs/struct-keyword.cs)]  
  
Para obter mais informações sobre os tipos de valor no .NET Framework, consulte [Common Type System](../standard/common-type-system.md).  
    
Na maioria das vezes, os structs compartilham a mesma sintaxe das classes, embora os structs sejam mais limitados que as classes:  
  
-   Dentro de uma declaração de struct, os campos não podem ser inicializados, a menos que sejam declarados como `const` ou `static`.  
  
-   Um struct não pode declarar um construtor padrão (um construtor sem parâmetros) ou um finalizador.  
  
-   Os structs são copiados na atribuição. Quando um struct recebe uma nova variável, todos os dados são copiados e qualquer modificação na nova cópia não altera os dados da cópia original. É importante se lembrar disso ao trabalhar com coleções de tipos de valor como Dictionary<string, myStruct>.  
  
-   Structs são tipos de valor e classes são tipos de referência.  
  
-   Diferentemente das classes, os structs podem ser instanciados sem usar um operador `new`.  
  
-   Os structs podem declarar construtores que têm parâmetros.  
  
-   Um struct não pode herdar de outra estrutura ou classe e ele não pode ser a base de uma classe. Todos os structs herdam diretamente do <xref:System.ValueType>, que herda do <xref:System.Object>.  
  
-   Um struct pode implementar interfaces.

## <a name="literal-values"></a>Valores literais  
No C#, valores literais recebem um tipo do compilador. Você pode especificar como um literal numérico deve ser digitado anexando uma letra ao final do número. Por exemplo, para especificar que o valor 4,56 deve ser tratado como um float, acrescente um "f" ou "F" após o número: `4.56f`. Se nenhuma letra for anexada, o compilador inferirá o tipo `double` para o literal. Para obter mais informações sobre quais tipos podem ser especificados com sufixos de letra, consulte as páginas de referência de tipos individuais em [Tipos de valor](./language-reference/keywords/value-types.md).  
  
Como os literais são tipados e todos os tipos derivam basicamente de <xref:System.Object>, você pode escrever e compilar o código como o seguinte:  
  
[!code-csharp[Literal Values](../../samples/snippets/csharp/concepts/structs/literals.cs)]

Os dois últimos exemplos demonstram os recursos de linguagem introduzidos no C# 7.0. O primeiro permite que você use um caractere de sublinhado como *separador de dígitos* dentro de literais numéricos. Você pode colocá-los onde quiser entre dígitos para melhorar a legibilidade. Eles não têm efeito sobre o valor.

O segundo demonstra *literais binários*, que permitem especificar os padrões de bit diretamente, em vez de usar notação hexadecimal.

## <a name="nullable-types"></a>Tipos que permitem valor nulo  
Os tipos comuns de valor não podem ter valor [nulo](./language-reference/keywords/null.md). No entanto, você pode criar tipos de valor que permitem valor nulo afixando um **?** após o tipo. Por exemplo, **int?** é um tipo **int** que também pode ter o valor [nulo](./language-reference/keywords/null.md). No CTS, os tipos anuláveis são instâncias do tipo struct genérico <xref:System.Nullable%601>. Os tipos que permitem valor nulo são especialmente úteis quando você está passando dados entre bancos de dados nos quais os valores numéricos podem ser nulos. Para obter mais informações, consulte [Tipos que permitem valor nulo (Guia de programação em C#)](./programming-guide/nullable-types/index.md).

## <a name="see-also"></a>Consulte também
[Classes](classes.md)

[Tipos Básicos](basic-types.md)
