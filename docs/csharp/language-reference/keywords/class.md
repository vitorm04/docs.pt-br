---
title: "class (Referência de C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- class_CSharpKeyword
- class
dev_langs:
- CSharp
helpviewer_keywords:
- class keyword [C#]
ms.assetid: b95d8815-de18-4c3f-a8cc-a0a53bdf8690
caps.latest.revision: 30
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: a5ed524a1b17f7be8903f998cbd732594faab831
ms.openlocfilehash: 02491e64813f84d031debdca09161d88aab1b94c
ms.contentlocale: pt-br
ms.lasthandoff: 05/15/2017

---
# <a name="class-c-reference"></a>class (Referência de C#)
Classes são declaradas usando a palavra-chave `class`, conforme mostrado no exemplo a seguir:  
  
```  
      class TestClass  
{  
    // Methods, properties, fields, events, delegates   
    // and nested classes go here.  
}  
```  
  
## <a name="remarks"></a>Comentários  
 Somente a herança única é permitida em C#. Em outras palavras, uma classe pode herdar a implementação de apenas uma classe base. No entanto, uma classe pode implementar mais de uma interface. A tabela a seguir mostra exemplos de implementação de interface e herança de classe:  
  
|Herança|Exemplo|  
|-----------------|-------------|  
|Nenhum|`class ClassA { }`|  
|Simples|`class DerivedClass: BaseClass { }`|  
|Nenhuma, implementa duas interfaces|`class ImplClass: IFace1, IFace2 { }`|  
|Única, implementa uma interface|`class ImplDerivedClass: BaseClass, IFace1 { }`|  
  
 Classes que você declara diretamente dentro de um namespace, não aninhadas em outras classes, podem ser [públicas](../../../csharp/language-reference/keywords/public.md) ou [internas](../../../csharp/language-reference/keywords/internal.md). As classes são `internal` por padrão.  
  
 Membros de classe, incluindo classes aninhadas, podem ser [públicos](../../../csharp/language-reference/keywords/public.md), `protected internal`, [protegidos](../../../csharp/language-reference/keywords/protected.md), [internos](../../../csharp/language-reference/keywords/internal.md) ou [particulares](../../../csharp/language-reference/keywords/private.md). Os membros são [particulares](../../../csharp/language-reference/keywords/private.md) por padrão.  
  
 Para obter mais informações, consulte [Modificadores de Acesso](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
 É possível declarar classes genéricas que têm parâmetros de tipo. Para obter mais informações, consulte [Classes genéricas](../../../csharp/programming-guide/generics/generic-classes.md).  
  
 Uma classe pode conter declarações dos seguintes membros:  
  
-   [Construtores](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
  
-   [Constantes](../../../csharp/programming-guide/classes-and-structs/constants.md)  
  
-   [Campos](../../../csharp/programming-guide/classes-and-structs/fields.md)  
  
-   [Finalizadores](../../../csharp/programming-guide/classes-and-structs/destructors.md)  

-   [Métodos](../../../csharp/programming-guide/classes-and-structs/methods.md)  
  
-   [Propriedades](../../../csharp/programming-guide/classes-and-structs/properties.md)  
  
-   [Indexadores](../../../csharp/programming-guide/indexers/index.md)  
  
-   [Operadores](../../../csharp/programming-guide/statements-expressions-operators/operators.md)  
  
-   [Eventos](../../../csharp/programming-guide/events/index.md)  
  
-   [Delegados](../../../csharp/programming-guide/delegates/index.md)  
  
-   [Classes](../../../csharp/programming-guide/classes-and-structs/classes.md)  
  
-   [Interfaces](../../../csharp/programming-guide/interfaces/index.md)  
  
-   [Estruturas](../../../csharp/programming-guide/classes-and-structs/structs.md)  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra a declaração de métodos, construtores e campos de classe. Ele também demonstra a instanciação de objetos e a impressão de dados de instância. Neste exemplo, duas classes são declaradas, a classe `Child`, que contém dois campos particulares (`name` e `age`) e dois métodos públicos. A segunda classe, `StringTest`, é usada para conter `Main`.  
  
 [!code-cs[csrefKeywordsTypes#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/class_1.cs)]  
  
## <a name="comments"></a>Comentários  
 Observe que, no exemplo anterior, os campos particulares (`name` e `age`) só podem ser acessados por meio dos métodos públicos da classe `Child`. Por exemplo, você não pode imprimir o nome do filho, do método `Main`, usando uma instrução como esta:  
  
```  
Console.Write(child1.name);   // Error  
```  
  
 Acessar membros particulares de `Child` de `Main` seria possível apenas se `Main` fosse um membro da classe.  
  
 Tipos declarados dentro de uma classe sem um modificador de acesso têm o valor padrão de `private`, portanto, os membros de dados neste exemplo ainda seriam `private` se a palavra-chave fosse removida.  
  
 Por fim, observe que, para o objeto criado usando o construtor padrão (`child3`), o campo de idade foi inicializado como zero por padrão.  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Palavras-chave de C#](../../../csharp/language-reference/keywords/index.md)   
 [Tipos de referência](../../../csharp/language-reference/keywords/reference-types.md)

