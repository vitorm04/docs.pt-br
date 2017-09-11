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
# <a name="how-to-identify-a-nullable-type-c-programming-guide"></a><span data-ttu-id="c45a1-102">Como identificar um tipo anulável (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="c45a1-102">How to: Identify a Nullable Type (C# Programming Guide)</span></span>
<span data-ttu-id="c45a1-103">É possível usar o operador [typeof](../../../csharp/language-reference/keywords/typeof.md) do C# para criar um objeto <xref:System.Type> que representa um tipo que permite valor nulo:</span><span class="sxs-lookup"><span data-stu-id="c45a1-103">You can use the C# [typeof](../../../csharp/language-reference/keywords/typeof.md) operator to create a <xref:System.Type> object that represents a Nullable type:</span></span>  
  
```  
System.Type type = typeof(int?);  
```  
  
 <span data-ttu-id="c45a1-104">Também é possível usar as classes e métodos do namespace <xref:System.Reflection> para gerar objetos <xref:System.Type> que representam tipos que permitem valor nulo.</span><span class="sxs-lookup"><span data-stu-id="c45a1-104">You can also use the classes and methods of the <xref:System.Reflection> namespace to generate <xref:System.Type> objects that represent Nullable types.</span></span> <span data-ttu-id="c45a1-105">No entanto, se você tentar obter informações de tipo de variáveis que permitem valor nulo em tempo de execução usando o método <xref:System.Object.GetType%2A> ou o operador `is`, o resultado será um objeto <xref:System.Type> que representa o tipo subjacente e não o próprio tipo que permite valor nulo.</span><span class="sxs-lookup"><span data-stu-id="c45a1-105">However, if you try to obtain type information from Nullable variables at runtime by using the <xref:System.Object.GetType%2A> method or the `is` operator, the result is a <xref:System.Type> object that represents the underlying type, not the Nullable type itself.</span></span>  
  
 <span data-ttu-id="c45a1-106">Chamar `GetType` em um tipo que permite valor nulo faz com que uma operação de conversão boxing seja executada quando o tipo for convertido implicitamente para <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="c45a1-106">Calling `GetType` on a Nullable type causes a boxing operation to be performed when the type is implicitly converted to <xref:System.Object>.</span></span> <span data-ttu-id="c45a1-107">Portanto, <xref:System.Object.GetType%2A> sempre retorna um objeto <xref:System.Type> que representa o tipo subjacente e não o tipo que permite valor nulo.</span><span class="sxs-lookup"><span data-stu-id="c45a1-107">Therefore <xref:System.Object.GetType%2A> always returns a <xref:System.Type> object that represents the underlying type, not the Nullable type.</span></span>  
  
```  
int? i = 5;  
Type t = i.GetType();  
Console.WriteLine(t.FullName); //"System.Int32"  
```  
  
 <span data-ttu-id="c45a1-108">O operador [is](../../../csharp/language-reference/keywords/is.md) do C# também opera no tipo subjacente de um anulável.</span><span class="sxs-lookup"><span data-stu-id="c45a1-108">The C# [is](../../../csharp/language-reference/keywords/is.md) operator also operates on a Nullable's underlying type.</span></span> <span data-ttu-id="c45a1-109">Portanto, não é possível usar `is` para determinar se uma variável é um tipo que permite valor nulo.</span><span class="sxs-lookup"><span data-stu-id="c45a1-109">Therefore you cannot use `is` to determine whether a variable is a Nullable type.</span></span> <span data-ttu-id="c45a1-110">O exemplo a seguir mostra que o operador `is` trata uma variável anulável\<int> como um int.</span><span class="sxs-lookup"><span data-stu-id="c45a1-110">The following example shows that the `is` operator treats a Nullable\<int> variable as an int.</span></span>  
  
```  
static void Main(string[] args)  
{  
  int? i = 5;  
  if (i is int) // true  
    //…  
}  
```  
  
## <a name="example"></a><span data-ttu-id="c45a1-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c45a1-111">Example</span></span>  
 <span data-ttu-id="c45a1-112">Use o código a seguir para determinar se um objeto <xref:System.Type> representa um tipo que permite valor nulo.</span><span class="sxs-lookup"><span data-stu-id="c45a1-112">Use the following code to determine whether a <xref:System.Type> object represents a Nullable type.</span></span> <span data-ttu-id="c45a1-113">Lembre-se de que esse código sempre retorna false se o objeto `Type` tiver sido retornado de uma chamada para <xref:System.Object.GetType%2A>, conforme explicado anteriormente neste tópico.</span><span class="sxs-lookup"><span data-stu-id="c45a1-113">Remember that this code always returns false if the `Type` object was returned from a call to <xref:System.Object.GetType%2A>, as explained earlier in this topic.</span></span>  
  
```  
if (type.IsGenericType && type.GetGenericTypeDefinition() == typeof(Nullable<>)) {…}  
```  
  
## <a name="see-also"></a><span data-ttu-id="c45a1-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c45a1-114">See Also</span></span>  
 <span data-ttu-id="c45a1-115">[Tipos que permitem valor nulo](../../../csharp/programming-guide/nullable-types/index.md) </span><span class="sxs-lookup"><span data-stu-id="c45a1-115">[Nullable Types](../../../csharp/programming-guide/nullable-types/index.md) </span></span>  
 [<span data-ttu-id="c45a1-116">Conversão boxing de tipos que permitem valor nulo</span><span class="sxs-lookup"><span data-stu-id="c45a1-116">Boxing Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/boxing-nullable-types.md)

