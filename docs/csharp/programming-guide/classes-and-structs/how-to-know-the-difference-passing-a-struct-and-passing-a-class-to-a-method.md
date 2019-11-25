---
title: Como saber a diferença entre passar uma struct e passar uma referência de classe para um guia de C# programação de método
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- structs [C#], passing as method parameter
- passing parameters [C#], structs vs. classes
- methods [C#], passing classes vs. structs
ms.assetid: 9c1313a6-32a8-4ea7-a59f-450f66af628b
ms.openlocfilehash: 9bacc7b3913a6e353e39f1e45fa99ea2dcdbe668
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73970550"
---
# <a name="how-to-know-the-difference-between-passing-a-struct-and-passing-a-class-reference-to-a-method-c-programming-guide"></a>Como saber a diferença entre passar uma struct e passar uma referência de classe para um método (C# guia de programação)
O exemplo a seguir demonstra como passar um [struct](../../language-reference/keywords/struct.md) para um método difere de passar uma instância de [classe](../../language-reference/keywords/class.md) para um método. No exemplo, ambos os argumentos (struct e instância de classe) são passados por valor e ambos os métodos alteram o valor de um campo do argumento. No entanto, os resultados dos dois métodos não são os mesmos, pois o que é passado ao passar um struct é diferente do que é passado ao passar uma instância de uma classe.  
  
 Como um struct é um [tipo de valor](../../language-reference/keywords/value-types.md), ao [passar um struct por valor](./passing-value-type-parameters.md) a um método, esse método receberá e operará em uma cópia do argumento do struct. O método não tem acesso ao struct original no método de chamada e, portanto, não é possível alterá-lo de forma alguma. O método pode alterar somente a cópia.  
  
 Uma instância de classe é um [tipo de referência](../../language-reference/keywords/reference-types.md) e não é um tipo de valor. Quando [um tipo de referência é passado por valor](./passing-reference-type-parameters.md) a um método, esse método receberá uma cópia da referência para a instância da classe. Ou seja, o método chamado recebe uma cópia do endereço da instância e o método de chamada retém o endereço original da instância. A instância de classe no método de chamada tem um endereço, o parâmetro do método chamado tem uma cópia do endereço e os dois endereços se referem ao mesmo objeto. Como o parâmetro contém apenas uma cópia do endereço, o método chamado não pode alterar o endereço da instância de classe no método de chamada. No entanto, o método chamado pode usar a cópia do endereço para acessar os membros da classe que o endereço original e a cópia da referência do endereço. Se o método chamado alterar um membro de classe, a instância da classe original no método de chamada também será alterada.  
  
 O resultado do exemplo a seguir ilustra a diferença. O valor do campo `willIChange` da instância da classe foi alterado pela chamada ao método `ClassTaker`, pois o método usa o endereço no parâmetro para localizar o campo especificado da instância da classe. O campo `willIChange` do struct no método de chamada não foi alterado pela chamada ao método `StructTaker`, pois o valor do argumento é uma cópia do próprio struct e não uma cópia de seu endereço. `StructTaker` altera a cópia e a cópia será perdida quando a chamada para `StructTaker` for concluída.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[csProgGuideObjects#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#32)]  
  
## <a name="see-also"></a>Consulte também

- [Guia de Programação em C#](../index.md)
- [Classes](./classes.md)
- [Structs](./structs.md)
- [Passando parâmetros](./passing-parameters.md)
