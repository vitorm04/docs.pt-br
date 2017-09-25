---
title: "Operador new (Referência de C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- new operator keyword [C#]
ms.assetid: a212b697-a79b-4105-9923-1f7b108036e8
caps.latest.revision: 22
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 59e1cc2006548df9a7a10283a34044040e5c2fef
ms.contentlocale: pt-br
ms.lasthandoff: 09/25/2017

---
# <a name="new-operator-c-reference"></a>Operador new (Referência de C#)
Usado para criar objetos e invocar construtores. Por exemplo:  
  
```  
Class1 obj  = new Class1();  
```  
  
 Ele também é usado para criar instâncias de tipos anônimos:  
  
```  
var query = from cust in customers  
            select new {Name = cust.Name, Address = cust.PrimaryAddress};  
```  
  
 O operador `new` também é usado para invocar o construtor padrão para tipos de valor. Por exemplo:  
  
```  
int i = new int();  
```  
  
 Na instrução anterior, `i` é inicializado como `0`, que é o valor padrão do tipo `int`. A instrução tem o mesmo efeito que o seguinte:  
  
```  
int i = 0;  
```  
  
 Para ver uma lista completa dos valores padrão, consulte [Tabela de valores padrão](../../../csharp/language-reference/keywords/default-values-table.md).  
  
 Lembre-se de que é um erro declarar um construtor padrão para um [struct](../../../csharp/language-reference/keywords/struct.md), porque cada tipo de valor tem implicitamente um construtor padrão público. É possível declarar construtores parametrizados em um tipo de struct para definir seus valores iniciais, mas isso só é necessário se valores diferentes do padrão forem necessários.  
  
 Objetos de tipo de valor, como structs, são criados na pilha, enquanto objetos de tipo de referência, como classes, são criadas no heap. Os dois tipos de objeto são destruídos automaticamente, mas objetos baseados em tipos de valor são destruídos quando saem do escopo, enquanto objetos baseados em tipos de referência são destruídos em um momento não especificado após a última referência a eles ser removida. Para tipos de referência que consomem recursos fixos, como grandes quantidades de memória, identificadores de arquivos ou conexões de rede, às vezes é desejável empregar a finalização determinística para garantir que o objeto seja destruído assim que possível. Para obter mais informações, consulte [Instrução using](../../../csharp/language-reference/keywords/using-statement.md).  
  
 O operador `new` não pode ser sobrecarregado.  
  
 Se o operador `new` não conseguir alocar memória, ele gerará a exceção <xref:System.OutOfMemoryException>.  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, um objeto `struct` e um objeto de classe são criados e inicializados usando o operador `new` e, em seguida, valores atribuídos. Os valores padrão e atribuídos são exibidos.  
  
 [!code-cs[csrefKeywordsOperator#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-operator_1.cs)]  
  
 Observe, no exemplo, que o valor padrão de uma cadeia de caracteres é `null`. Portanto, ele não é exibido.  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Palavras-chave de C#](../../../csharp/language-reference/keywords/index.md)   
 [Palavras-chave do operador](../../../csharp/language-reference/keywords/operator-keywords.md)   
 [new](../../../csharp/language-reference/keywords/new.md)   
 [Tipos Anônimos](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)

