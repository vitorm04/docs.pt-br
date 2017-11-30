---
title: "Usando structs (Guia de Programação em C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: structs [C#], using
ms.assetid: cea4a459-9eb9-442b-8d08-490e0797ba38
caps.latest.revision: "28"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 94181c42ce913dc76c9a074e4bcbb8240764c896
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="using-structs-c-programming-guide"></a>Usando structs (Guia de Programação em C#)
O tipo `struct` é adequado para representar objetos leves como `Point`, `Rectangle` e `Color`. Embora seja conveniente representar um ponto como uma [classe](../../../csharp/language-reference/keywords/class.md) com [Propriedades Auto-implementadas](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md), um [struct](../../../csharp/language-reference/keywords/struct.md) pode ser mais eficiente em alguns cenários. Por exemplo, se você declarar uma matriz de 1000 objetos `Point`, alocará memória adicional para referenciar cada objeto, nesse caso, um struct será mais barato. Como o [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] contém um objeto chamado <xref:System.Drawing.Point>, o struct neste exemplo é chamado “CoOrds”.  
  
 [!code-csharp[csProgGuideObjects#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_1.cs)]  
  
 É um erro ao definir um construtor (sem parâmetros) padrão para um struct. Também é um erro ao inicializar um campo de instância em um corpo de struct. Você pode inicializar os membros de struct externamente acessível somente por meio de um construtor com parâmetros, implícito, o construtor padrão, um [inicializador de objeto](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md), ou acessar os membros individualmente depois que a estrutura é declarada. Todos os membros particulares ou inacessíveis requerem o uso de construtores exclusivamente.
  
 Quando você cria um objeto de estrutura usando o [novo](../../../csharp/language-reference/keywords/new.md) operador, ele é criado e o construtor apropriado é chamado de acordo com o [assinatura do construtor](../../../csharp/programming-guide/classes-and-structs/constructors.md#constructor-syntax). Diferentemente das classes, os structs podem ser instanciados sem usar o operador `new`. Nesse caso, não há nenhuma chamada do construtor, o que torna a alocação mais eficiente. No entanto, os campos permanecerão não atribuídos e o objeto não poderá ser usado até que todos os campos sejam inicializados. Isso inclui a incapacidade de obter ou definir valores por meio das propriedades implementadas automaticamente.
 
 Se você criar um objeto de estrutura usando o padrão, o construtor sem parâmetros, todos os membros são atribuídos de acordo com seus [valores padrão](../../../csharp/programming-guide/statements-expressions-operators/default-value-expressions.md).
  
 Ao escrever um construtor com parâmetros para um struct, você deverá inicializar explicitamente todos os membros; Caso contrário, um ou mais membros permanecem não atribuídos e struct não pode ser usado, produzindo o erro do compilador CS0171.  
  
 Não há nenhuma herança para structs como há para classes. Um struct não pode herdar de outra estrutura ou classe e ele não pode ser a base de uma classe. No entanto, os structs herdam da classe base <xref:System.Object>. Um struct pode implementar interfaces e ele faz isso exatamente como as classes.  
  
 Você não pode declarar uma classe usando a palavra-chave `struct`. No C#, as classes e os structs são semanticamente diferentes. Um struct é um tipo de valor, enquanto uma classe é um tipo de referência. Para obter mais informações, consulte [Value Types](../../../csharp/language-reference/keywords/value-types.md) (Tipos de Valor).  
  
 A menos que você precise de semântica de tipo de referência, uma pequena classe pode ser tratada com mais eficiência pelo sistema se você declará-la como um struct em vez disso.  
  
## <a name="example-1"></a>Exemplo 1  
  
### <a name="description"></a>Descrição  
 Este exemplo demonstra a inicialização de `struct` usando construtores parametrizados e padrão.  
  
### <a name="code"></a>Código  
 [!code-csharp[csProgGuideObjects#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_1.cs)]  
  
 [!code-csharp[csProgGuideObjects#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_2.cs)]  
  
## <a name="example-2"></a>Exemplo 2  
  
### <a name="description"></a>Descrição  
 Este exemplo demonstra um recurso que é exclusivo para struct. Ele cria um objeto CoOrds sem usar o operador `new`. Se você substituir a palavra `struct` pela palavra `class`, o programa não compilará.  
  
### <a name="code"></a>Código  
 [!code-csharp[csProgGuideObjects#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_1.cs)]  
  
 [!code-csharp[csProgGuideObjects#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_3.cs)]  
  
## <a name="see-also"></a>Consulte também  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Classes e Structs](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [Estruturas](../../../csharp/programming-guide/classes-and-structs/structs.md)
