---
title: "Como definir a igualdade de valor para um tipo (Guia de Programação em C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- overriding Equals method [C#]
- object equivalence [C#]
- Equals method [C#] , overriding
- value equality [C#]
- equivalence [C#]
ms.assetid: 4084581e-b931-498b-9534-cf7ef5b68690
caps.latest.revision: 15
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 33b2ab2252fac8442caa7b2f3e9b5b311cc0f9b6
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-define-value-equality-for-a-type-c-programming-guide"></a>Como definir a igualdade de valor para um tipo (Guia de Programação em C#)
Quando você define uma classe ou struct, decide se faz sentido criar uma definição personalizada de igualdade de valor (ou equivalência) para o tipo. Normalmente, você implementa igualdade de valor quando objetos do tipo devem ser adicionados a uma coleção de algum tipo ou quando seu objetivo principal é armazenar um conjunto de campos ou propriedades. Você pode basear sua definição de igualdade de valor em uma comparação de todos os campos e propriedades no tipo ou pode basear a definição em um subconjunto. Mas, em ambos os casos e em classes e struct, sua implementação deve seguir as cinco garantias de equivalência:  
  
1.  x.`Equals`(x) retorna `true.` Isso é chamado de propriedade reflexiva.  
  
2.  x.`Equals`(y) retorna o mesmo valor que y.`Equals`(x). Isso é chamado de propriedade simétrica.  
  
3.  se (x.`Equals`(y) && y.`Equals`(z)) retorna `true`, então x.`Equals`(z) retorna `true`. Isso é chamado de propriedade transitiva.  
  
4.  Invocações sucessivas de x.`Equals`(y) retornam o mesmo valor contanto que os objetos referenciados por x e y não sejam modificados.  
  
5.  x.`Equals`(null) retorna `false`. No entanto, null.Equals(null) lança uma exceção, ele não obedece à regra número dois acima.  
  
 Qualquer estrutura que você definir já tem uma implementação padrão de igualdade de valor que ela herda da substituição <xref:System.ValueType?displayProperty=fullName> do método <xref:System.Object.Equals%28System.Object%29?displayProperty=fullName>. Essa implementação usa a reflexão para examinar todos os campos e propriedades no tipo. Embora essa implementação produza resultados corretos, ela é relativamente lenta em comparação com uma implementação personalizada escrita especificamente para o tipo.  
  
 Os detalhes de implementação para a igualdade de valor são diferentes para classes e struct. No entanto, as classes e structs exigem as mesmas etapas básicas para implementar a igualdade:  
  
1.  Substitua o método <xref:System.Object.Equals%28System.Object%29?displayProperty=fullName> [virtual](../../../csharp/language-reference/keywords/virtual.md). Na maioria dos casos, sua implementação de `bool Equals( object obj )` deve apenas chamar o método `Equals` específico do tipo que é a implementação da interface <xref:System.IEquatable%601?displayProperty=fullName>. (Consulte a etapa 2.)  
  
2.  Implemente a interface <xref:System.IEquatable%601?displayProperty=fullName> fornecendo o método `Equals` específico do tipo. Isso é o local em que a comparação de equivalência de fato é realizada. Por exemplo, você pode decidir definir a igualdade comparando apenas um ou dois campos em seu tipo. Não lance exceções de `Equals`. Para classes somente: esse método deve examinar somente os campos que são declarados na classe. Ele deve chamar `base.Equals` para examinar os campos que estão na classe base. (Não faça isso se o tipo herdar diretamente de <xref:System.Object>, porque a implementação <xref:System.Object> de <xref:System.Object.Equals%28System.Object%29?displayProperty=fullName> realiza uma verificação de igualdade de referência.)  
  
3.  Opcional, mas recomendado: sobrecarregue os operadores [==](../../../csharp/language-reference/operators/equality-comparison-operator.md) e [!=](../../../csharp/language-reference/operators/not-equal-operator.md).  
  
4.  Substitua <xref:System.Object.GetHashCode%2A?displayProperty=fullName> para que dois objetos que têm a igualdade de valor produzam o mesmo código hash.  
  
5.  Opcional: para dar suporte às definições para “maior que” ou “menor que”, implemente a interface <xref:System.IComparable%601> para seu tipo e também sobrecarregue os operadores [<=](../../../csharp/language-reference/operators/less-than-equal-operator.md) e [>=](../../../csharp/language-reference/operators/greater-than-equal-operator.md).  
  
 O primeiro exemplo a seguir mostra uma implementação da classe. O segundo exemplo mostra uma implementação de struct.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como implementar a igualdade de valor em uma classe (tipo de referência).  
  
 [!code-cs[csProgGuideStatements#19](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-value-equality-for-a-type_1.cs)]  
  
 Em classes (tipo de referência), a implementação padrão de ambos os métodos <xref:System.Object.Equals%28System.Object%29?displayProperty=fullName> executa uma comparação de igualdade de referência, não uma verificação de igualdade de valor. Quando um implementador substitui o método virtual, o objetivo é fornecer semântica de igualdade de valor.  
  
 Os operadores `==` e `!=` podem ser usados com classes, mesmo se a classe não sobrecarregá-los. No entanto, o comportamento padrão é executar uma verificação de igualdade de referência. Em uma classe, se você sobrecarregar o método `Equals`, você deverá sobrecarregar os operadores `==` e `!=`, mas isso não é necessário.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como implementar a igualdade de valor em um struct (tipo de valor):  
  
 [!code-cs[csProgGuideStatements#20](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-value-equality-for-a-type_2.cs)]  
  
 Para structs, a implementação padrão de <xref:System.Object.Equals%28System.Object%29?displayProperty=fullName> (que é a versão substituída em <xref:System.ValueType?displayProperty=fullName>) executa uma verificação de igualdade de valor usando a reflexão para comparar os valores de todos os campos no tipo. Quando um implementador substitui o método `Equals` virtual em uma estrutura, a finalidade é fornecer uma maneira mais eficiente de executar a verificação de igualdade de valor e, opcionalmente, basear a comparação em algum subconjunto dos campos ou propriedades do struct.  
  
 Os operadores [==](../../../csharp/language-reference/operators/equality-comparison-operator.md) e [!=](../../../csharp/language-reference/operators/not-equal-operator.md) não podem operar em um struct a menos que o struct explicitamente os sobrecarregue.  
  
## <a name="see-also"></a>Consulte também  
 [Comparações de igualdade](../../../csharp/programming-guide/statements-expressions-operators/equality-comparisons.md)   
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)

