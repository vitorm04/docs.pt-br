---
title: "Restrições a parâmetros de tipo (Guia de Programação em C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- generics [C#], type constraints
- type constraints [C#]
- type parameters [C#], constraints
- unbound type parameter [C#]
ms.assetid: 141b003e-1ddb-4e1c-bcb2-e1c3870e6a51
caps.latest.revision: "41"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f5382b0050b81ed3bb1a075a042bdc4034a3975d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="constraints-on-type-parameters-c-programming-guide"></a>Restrições a parâmetros de tipo (Guia de Programação em C#)
Ao definir uma classe genérica, é possível aplicar restrições às modalidades de tipos que o código de cliente pode utilizar para argumentos de tipo ao criar uma instância da classe. Se o código de cliente tentar criar uma instância da classe usando um tipo não permitido por uma restrição, o resultado será um erro em tempo de compilação. Essas restrições são chamadas de restrições. Restrições são especificadas usando a palavra-chave contextual `where`. A tabela a seguir lista os seis tipos de restrições:  
  
|Restrição|Descrição|  
|----------------|-----------------|  
|em que T: struct|O argumento de tipo deve ser um tipo de valor. Qualquer valor de tipo com exceção de <xref:System.Nullable> pode ser especificado. Para obter mais informações, consulte [Usando Tipos Anuláveis](../../../csharp/programming-guide/nullable-types/using-nullable-types.md).|  
|em que T: class|O argumento de tipo deve ser um tipo de referência. Isso também se aplica a qualquer classe, interface, delegado ou tipo de matriz.|  
|em que T: new()|O argumento de tipo deve ter um construtor público sem parâmetros. Quando usado em conjunto com outras restrições, a restrição `new()` deve ser a última a ser especificada.|  
|em que T: \<base class name>|O argumento de tipo deve ser ou derivar da classe base especificada.|  
|em que T: \<interface name>|O argumento de tipo deve ser ou implementar a interface especificada. Várias restrições de interface podem ser especificadas. A interface de restrição também pode ser genérica.|  
|em que T: U|O argumento de tipo fornecido para T deve ser ou derivar do argumento fornecido para U.|  
  
## <a name="why-use-constraints"></a>Por que usar restrições  
 Caso queira examinar um item em uma lista genérica a fim de determinar se ele é válido ou compará-lo a outro item, o compilador deve ter a garantia de que o operador ou método a ser chamado terá suporte de qualquer argumento de tipo especificado pelo código de cliente. Essa garantia é obtida pela aplicação de uma ou mais restrições à definição de classe genérica. Por exemplo, a restrição de classe base informa ao compilador que somente os objetos desse tipo ou derivados desse tipo serão usados como argumentos de tipo. Uma vez que o compilador tiver essa garantia, ele poderá permitir que métodos desse tipo sejam chamados na classe genérica. As restrições são aplicadas usando a palavra-chave contextual `where`. O exemplo de código a seguir demonstra a funcionalidade que pode ser adicionada à classe `GenericList<T>` (em [Introdução aos Genéricos](../../../csharp/programming-guide/generics/introduction-to-generics.md)) ao aplicar uma restrição de classe base.  
  
 [!code-csharp[csProgGuideGenerics#11](../../../csharp/programming-guide/generics/codesnippet/CSharp/constraints-on-type-parameters_1.cs)]  
  
 A restrição permite que a classe genérica use a propriedade `Employee.Name`, pois há a garantia de que todos os itens do tipo T são um objeto `Employee` ou um objeto que herda de `Employee`.  
  
 Várias restrições podem ser aplicadas ao mesmo parâmetro de tipo e as restrições em si podem ser tipos genéricos, da seguinte maneira:  
  
 [!code-csharp[csProgGuideGenerics#12](../../../csharp/programming-guide/generics/codesnippet/CSharp/constraints-on-type-parameters_2.cs)]  
  
 Ao restringir o parâmetro de tipo, aumenta-se a quantidade de operações e chamadas de método permitidas àqueles com suporte do tipo de restrição e de todos os tipos de sua hierarquia de herança. Portanto, ao projetar classes genéricas ou métodos, caso deseje executar qualquer operação nos membros genéricos (além da simples atribuição) ou chamar métodos sem suporte de `System.Object`, será necessário aplicar restrições ao parâmetro de tipo.  
  
 Ao aplicar a restrição `where T : class`, evite os operadores `==` e `!=` no parâmetro de tipo, pois esses operadores testarão somente a identidade de referência e não a igualdade de valor. Esse será o caso mesmo se esses operadores forem sobrecarregados em um tipo usado como argumento. O código a seguir ilustra esse ponto; a saída é false, muito embora a classe <xref:System.String> sobrecarregue o operador `==`.  
  
 [!code-csharp[csProgGuideGenerics#13](../../../csharp/programming-guide/generics/codesnippet/CSharp/constraints-on-type-parameters_3.cs)]  
  
 O motivo para esse comportamento é que, no tempo de compilação, o compilador só sabe que T é um tipo de referência e, portanto, deve usar os operadores padrão válidos para todos os tipos de referência. Caso seja necessário testar a igualdade de valor, recomenda-se aplicar a restrição `where T : IComparable<T>` e implementar essa interface na classe que será usada para construir a classe genérica.  
  
## <a name="constraining-multiple-parameters"></a>Restrição de Vários Parâmetros  
 É possível aplicar restrições a vários parâmetros e várias restrições a um único parâmetro, conforme mostrado no exemplo a seguir:  
  
 [!code-csharp[csProgGuideGenerics#64](../../../csharp/programming-guide/generics/codesnippet/CSharp/constraints-on-type-parameters_4.cs)]  
  
## <a name="unbounded-type-parameters"></a>Parâmetros de Tipo Não Associado  
 Os parâmetros de tipo que não têm restrições, como o T na classe pública `SampleClass<T>{}`, são denominados “parâmetros de tipo não associado”. Os parâmetros de tipo não associado têm as seguintes regras:  
  
-   Os operadores `!=` e `==` não podem ser usados, pois não há garantia de que o argumento de tipo concreto oferecerá suporte a esses operadores.  
  
-   Eles podem ser convertidos para e de `System.Object` ou explicitamente convertidos para qualquer tipo de interface.  
  
-   É possível compará-los a [nulo](../../../csharp/language-reference/keywords/null.md). Se um parâmetro não associado for comparado a `null`, a comparação sempre retornará false se o argumento de tipo for um tipo de valor.  
  
## <a name="type-parameters-as-constraints"></a>Parâmetros de Tipo como Restrições  
 O uso de um parâmetro de tipo genérico como uma restrição será útil quando uma função membro com parâmetro de tipo próprio tiver que restringir esse parâmetro para o parâmetro de tipo do tipo recipiente, conforme mostrado no exemplo a seguir:  
  
 [!code-csharp[csProgGuideGenerics#14](../../../csharp/programming-guide/generics/codesnippet/CSharp/constraints-on-type-parameters_5.cs)]  
  
 No exemplo anterior, `T` é uma restrição de tipo no contexto do método `Add` e um parâmetro de tipo não associado no contexto da classe `List`.  
  
 Parâmetros de tipo também podem ser usados como restrições em definições de classe genérica. Observe que o parâmetro de tipo deve ser declarado entre colchetes angulares junto com quaisquer outros parâmetros de tipo:  
  
 [!code-csharp[csProgGuideGenerics#15](../../../csharp/programming-guide/generics/codesnippet/CSharp/constraints-on-type-parameters_6.cs)]  
  
 A utilidade dos parâmetros de tipo como restrições com classes genéricas é bastante limitada, pois o compilador não pode presumir nada sobre o parâmetro de tipo, exceto que ele deriva de `System.Object`. Use parâmetros de tipo como restrições em classes genéricas em cenários nos quais deseja impor uma relação de herança entre dois parâmetros de tipo.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Collections.Generic>  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Introdução aos genéricos](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
 [Classes genéricas](../../../csharp/programming-guide/generics/generic-classes.md)  
 [Restrição new](../../../csharp/language-reference/keywords/new-constraint.md)
