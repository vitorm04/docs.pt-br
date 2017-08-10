---
title: "Como identificar um tipo anulável (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- nullable types [C#], identifying
ms.assetid: d4b67ee2-66e8-40c1-ae9d-545d32c71387
caps.latest.revision: 7
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
ms.openlocfilehash: c9e05bfe8be45e5b71a8db06ce4f2502c5397fd4
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-identify-a-nullable-type-c-programming-guide"></a>Como identificar um tipo anulável (Guia de Programação em C#)
É possível usar o operador [typeof](../../../csharp/language-reference/keywords/typeof.md) do C# para criar um objeto <xref:System.Type> que representa um tipo que permite valor nulo:  
  
```  
System.Type type = typeof(int?);  
```  
  
 Também é possível usar as classes e métodos do namespace <xref:System.Reflection> para gerar objetos <xref:System.Type> que representam tipos que permitem valor nulo. No entanto, se você tentar obter informações de tipo de variáveis que permitem valor nulo em tempo de execução usando o método <xref:System.Object.GetType%2A> ou o operador `is`, o resultado será um objeto <xref:System.Type> que representa o tipo subjacente e não o próprio tipo que permite valor nulo.  
  
 Chamar `GetType` em um tipo que permite valor nulo faz com que uma operação de conversão boxing seja executada quando o tipo for convertido implicitamente para <xref:System.Object>. Portanto, <xref:System.Object.GetType%2A> sempre retorna um objeto <xref:System.Type> que representa o tipo subjacente e não o tipo que permite valor nulo.  
  
```  
int? i = 5;  
Type t = i.GetType();  
Console.WriteLine(t.FullName); //"System.Int32"  
```  
  
 O operador [is](../../../csharp/language-reference/keywords/is.md) do C# também opera no tipo subjacente de um anulável. Portanto, não é possível usar `is` para determinar se uma variável é um tipo que permite valor nulo. O exemplo a seguir mostra que o operador `is` trata uma variável anulável\<int> como um int.  
  
```  
static void Main(string[] args)  
{  
  int? i = 5;  
  if (i is int) // true  
    //…  
}  
```  
  
## <a name="example"></a>Exemplo  
 Use o código a seguir para determinar se um objeto <xref:System.Type> representa um tipo que permite valor nulo. Lembre-se de que esse código sempre retorna false se o objeto `Type` tiver sido retornado de uma chamada para <xref:System.Object.GetType%2A>, conforme explicado anteriormente neste tópico.  
  
```  
if (type.IsGenericType && type.GetGenericTypeDefinition() == typeof(Nullable<>)) {…}  
```  
  
## <a name="see-also"></a>Consulte também  
 [Tipos que permitem valor nulo](../../../csharp/programming-guide/nullable-types/index.md)   
 [Conversão boxing de tipos que permitem valor nulo](../../../csharp/programming-guide/nullable-types/boxing-nullable-types.md)

