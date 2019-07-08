---
title: Membros – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- types [C#], nested types
- C# language, type members
ms.assetid: 4a30a4ab-d690-4936-9124-92ce9448665a
ms.openlocfilehash: affe2752712bfd40516861abf84bdee11528168c
ms.sourcegitcommit: eaa6d5cd0f4e7189dbe0bd756e9f53508b01989e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/07/2019
ms.locfileid: "67609485"
---
# <a name="members-c-programming-guide"></a>Membros (Guia de Programação em C#)

Classes e structs têm membros que representam seus dados e comportamento. Os membros de uma classe incluem todos os membros declarados na classe, juntamente com todos os membros (exceto construtores e finalizadores) declarados em todas as classes em sua hierarquia de herança. Os membros privados em classes base são herdados, mas não podem ser acessados de classes derivadas.  
  
 A tabela a seguir lista os tipos de membros que uma classe ou struct pode conter:  
  
|Membro|DESCRIÇÃO|  
|------------|-----------------|  
|[Campos](../../../csharp/programming-guide/classes-and-structs/fields.md)|Os campos são variáveis declaradas no escopo da classe. Um campo pode ser um tipo numérico interno ou uma instância de outra classe. Por exemplo, uma classe de calendário pode ter um campo que contém a data atual.|  
|[Constantes](../../../csharp/programming-guide/classes-and-structs/constants.md)|Constantes são campos cujo valor é definido em tempo de compilação e não pode ser alterado.|  
|[Propriedades](../../../csharp/programming-guide/classes-and-structs/properties.md)|As propriedades são métodos de uma classe acessados como se fossem campos dessa classe. Uma propriedade pode fornecer proteção para um campo de classe para evitar que ele seja alterado sem o conhecimento do objeto.|  
|[Métodos](../../../csharp/programming-guide/classes-and-structs/methods.md)|Os métodos definem as ações que uma classe pode executar. Métodos podem usar parâmetros que fornecem dados de entrada e retornar dados de saída por meio de parâmetros. Os métodos também podem retornar um valor diretamente, sem usar um parâmetro.|  
|[Eventos](../../../csharp/programming-guide/events/index.md)|Os eventos fornecem notificações sobre ocorrências a outros objetos, como cliques de botão ou a conclusão bem-sucedida de um método. Eventos são definidos e disparados pelos delegados.|  
|[Operadores](../../../csharp/programming-guide/statements-expressions-operators/operators.md)|Os operadores sobrecarregados são considerados membros de tipo. Ao sobrecarregar um operador, ele é definido como um método estático público em um tipo. Para obter mais informações, consulte [Sobrecarga de operador](../../../csharp/language-reference/operators/operator-overloading.md).|  
|[Indexadores](../../../csharp/programming-guide/indexers/index.md)|Os indexadores permitem que um objeto seja indexado de maneira semelhante às matrizes.|  
|[Construtores](../../../csharp/programming-guide/classes-and-structs/constructors.md)|Os construtores são os métodos chamados quando o objeto é criado pela primeira vez. Geralmente, eles são usados para inicializar os dados de um objeto.|  
|[Finalizadores](../../../csharp/programming-guide/classes-and-structs/destructors.md)|Os finalizadores raramente são usados no C#. Eles são métodos chamados pelo mecanismo de tempo de execução quando o objeto está prestes a ser removido da memória. Geralmente, eles são usados para garantir que recursos que devem ser liberados sejam manipulados corretamente.|  
|[Tipos aninhados](../../../csharp/programming-guide/classes-and-structs/nested-types.md)|Os tipos aninhados são tipos declarados dentro de outro tipo. Geralmente, eles são usados para descrever objetos utilizados somente pelos tipos que os contêm.|  
  
## <a name="see-also"></a>Consulte também

- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)
- [Classes](../../../csharp/programming-guide/classes-and-structs/classes.md)
- [Métodos](../../../csharp/programming-guide/classes-and-structs/methods.md)
- [Construtores](../../../csharp/programming-guide/classes-and-structs/constructors.md)
- [Finalizadores](../../../csharp/programming-guide/classes-and-structs/destructors.md)
- [Propriedades](../../../csharp/programming-guide/classes-and-structs/properties.md)
- [Campos](../../../csharp/programming-guide/classes-and-structs/fields.md)
- [Indexadores](../../../csharp/programming-guide/indexers/index.md)
- [Eventos](../../../csharp/programming-guide/events/index.md)
- [Tipos aninhados](../../../csharp/programming-guide/classes-and-structs/nested-types.md)
- [Operadores](../../../csharp/programming-guide/statements-expressions-operators/operators.md)
