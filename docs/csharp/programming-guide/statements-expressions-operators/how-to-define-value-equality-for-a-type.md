---
title: Como definir a igualdade de valor para um tipo - C# Guia de Programação
ms.date: 07/20/2015
helpviewer_keywords:
- overriding Equals method [C#]
- object equivalence [C#]
- Equals method [C#], overriding
- value equality [C#]
- equivalence [C#]
ms.assetid: 4084581e-b931-498b-9534-cf7ef5b68690
ms.openlocfilehash: 140be18698a40be8f394b31fcd42b97d6685cb98
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79157085"
---
# <a name="how-to-define-value-equality-for-a-type-c-programming-guide"></a>Como definir a igualdade de valor para um tipo (Guia de Programação C#)

Quando você define uma classe ou struct, decide se faz sentido criar uma definição personalizada de igualdade de valor (ou equivalência) para o tipo. Normalmente, você implementa igualdade de valor quando objetos do tipo devem ser adicionados a uma coleção de algum tipo ou quando seu objetivo principal é armazenar um conjunto de campos ou propriedades. Você pode basear sua definição de igualdade de valor em uma comparação de todos os campos e propriedades no tipo ou pode basear a definição em um subconjunto.

Em ambos os casos, e em ambas as classes e estruturas, sua implementação deve seguir `x` `y` as `z` cinco garantias de equivalência (Para as seguintes regras, assuma que , e não são nulas):  
  
1. `x.Equals(x)` retorna `true`. Isso é chamado de propriedade reflexiva.  
  
2. `x.Equals(y)` retorna o mesmo valor que `y.Equals(x)`. Isso é chamado de propriedade simétrica.  
  
3. se `(x.Equals(y) && y.Equals(z))` retornar `true`, então `x.Equals(z)` retornará `true`. Isso é chamado de propriedade transitiva.  
  
4. Invocações sucessivas de `x.Equals(y)` retornam o mesmo valor, contanto que os objetos referenciados por x e y não sejam modificados.  
  
5. Qualquer valor não nulo não é igual a nulo. No entanto, a CLR verifica se `NullReferenceException` há `this` nulidade em todas as chamadas do método e lança um se a referência seria nula. Portanto, `x.Equals(y)` abre uma `x` exceção quando é nulo. Isso quebra as regras 1 ou `Equals`2, dependendo do argumento para .

 Qualquer struct que você define já tem uma implementação padrão de igualdade de valor que ele herda da substituição <xref:System.ValueType?displayProperty=nameWithType> do método <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType>. Essa implementação usa a reflexão para examinar todos os campos e propriedades no tipo. Embora essa implementação produza resultados corretos, ela é relativamente lenta em comparação com uma implementação personalizada escrita especificamente para o tipo.  
  
 Os detalhes de implementação para a igualdade de valor são diferentes para classes e struct. No entanto, as classes e structs exigem as mesmas etapas básicas para implementar a igualdade:  
  
1. Substitua o método [virtual](../../language-reference/keywords/virtual.md) <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType>. Na maioria dos casos, sua implementação de `bool Equals( object obj )` deve apenas chamar o método `Equals` específico do tipo que é a implementação da interface <xref:System.IEquatable%601?displayProperty=nameWithType>. (Consulte a etapa 2.)  
  
2. Implemente a interface <xref:System.IEquatable%601?displayProperty=nameWithType> fornecendo um método `Equals` específico do tipo. Isso é o local em que a comparação de equivalência de fato é realizada. Por exemplo, você pode decidir definir a igualdade comparando apenas um ou dois campos em seu tipo. Não lance exceções de `Equals`. Para classes somente: esse método deve examinar somente os campos que são declarados na classe. Ele deve chamar `base.Equals` para examinar os campos que estão na classe base. (Não faça isso se o tipo herda diretamente de <xref:System.Object>, pois a implementação <xref:System.Object> de <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> executa uma verificação de igualdade de referência.)  
  
3. Opcional, mas recomendado: [==](../../language-reference/operators/equality-operators.md#equality-operator-) Sobrecarregue os operadores [e !=](../../language-reference/operators/equality-operators.md#inequality-operator-) .  
  
4. Substitua <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType> para que os dois objetos que têm a igualdade de valor produzam o mesmo código hash.  
  
5. Opcional: Para suportar definições para "maior es) <xref:System.IComparable%601> ou "menos que", implementar [<=](../../language-reference/operators/comparison-operators.md#less-than-or-equal-operator-) [>=](../../language-reference/operators/comparison-operators.md#greater-than-or-equal-operator-) a interface para o seu tipo e também sobrecarregar os operadores e operadores.  
  
 O primeiro exemplo a seguir mostra uma implementação da classe. O segundo exemplo mostra uma implementação de struct.  

## <a name="example"></a>Exemplo

 O exemplo a seguir mostra como implementar a igualdade de valor em uma classe (tipo de referência).  
  
 [!code-csharp[csProgGuideStatements#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#19)]  
  
 Em classes (tipo de referência), a implementação padrão de ambos os métodos <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> executa uma comparação de igualdade de referência, não uma verificação de igualdade de valor. Quando um implementador substitui o método virtual, o objetivo é fornecer semântica de igualdade de valor.  
  
 Os operadores `==` e `!=` podem ser usados com classes, mesmo se a classe não sobrecarregá-los. No entanto, o comportamento padrão é executar uma verificação de igualdade de referência. Em uma classe, se você sobrecarregar o método `Equals`, você deverá sobrecarregar os operadores `==` e `!=`, mas isso não é necessário.  

## <a name="example"></a>Exemplo

 O exemplo a seguir mostra como implementar a igualdade de valor em um struct (tipo de valor):  
  
 [!code-csharp[csProgGuideStatements#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#20)]  
  
 Para estruturas, a implementação padrão de <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> (que é a versão substituída em <xref:System.ValueType?displayProperty=nameWithType>) executa uma verificação de igualdade de valor por meio de reflexão para comparar os valores de cada campo no tipo. Quando um implementador substitui o método `Equals` virtual em uma estrutura, a finalidade é fornecer uma maneira mais eficiente de executar a verificação de igualdade de valor e, opcionalmente, basear a comparação em algum subconjunto dos campos ou propriedades do struct.  
  
 Os [==](../../language-reference/operators/equality-operators.md#equality-operator-) operadores [e !=](../../language-reference/operators/equality-operators.md#inequality-operator-) não podem operar em uma estrutura, a menos que a estrutura os sobrecarregue explicitamente.  
  
## <a name="see-also"></a>Confira também

- [Comparações de igualdade](equality-comparisons.md)
- [Guia de programação em C#](../index.md)
