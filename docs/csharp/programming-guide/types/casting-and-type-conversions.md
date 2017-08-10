---
title: "Conversões cast e conversões de tipo (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- type conversion [C#]
- data type conversion [C#]
- numeric conversions [C#]
- conversions [C#], type
- casting [C#]
- converting types [C#]
ms.assetid: 568df58a-d292-4b55-93ba-601578722878
caps.latest.revision: 52
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
ms.openlocfilehash: 20743c07c8e9c6b7ec24cf52a28bb9f451ba9df5
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="casting-and-type-conversions-c-programming-guide"></a>Conversões cast e conversões de tipo (Guia de Programação em C#)
Depois que uma variável é declarada, ela não pode ser declarada novamente ou usada para armazenar valores de outro tipo, a menos que esse tipo possa ser convertido para o tipo da variável, pois a C# é tipada estaticamente no tempo de compilação. Por exemplo, não há conversão de um inteiro para qualquer cadeia de caracteres arbitrária. Portanto, depois de declarar `i` como um inteiro, você não pode atribuir a cadeia de caracteres "Hello" a ela, conforme mostrado no código a seguir.  
  
```csharp  
int i;  
i = "Hello"; // Error: "Cannot implicitly convert type 'string' to 'int'"  
```  
  
 No entanto, às vezes é necessário copiar um valor para uma variável ou um parâmetro de método de outro tipo. Por exemplo, você pode ter que passar uma variável de inteiro para um método cujo parâmetro é digitado como `double`. Ou talvez precise atribuir uma variável de classe a uma variável de um tipo de interface. Esses tipos de operações são chamados de *conversões de tipo*. No C#, você pode realizar os seguintes tipos de conversões:  
  
-   **Conversões implícitas**: nenhuma sintaxe especial é necessária porque a conversão é de tipo seguro e nenhum dado será perdido. Exemplos incluem conversões de tipos integrais menores para maiores e conversões de classes derivadas para classes base.  
  
-   **Conversões explícitas (casts)**: as conversões explícitas exigem um operador cast. A conversão é necessária quando as informações podem ser perdidas na conversão ou quando a conversão pode não funcionar por outros motivos.  Exemplos típicos incluem a conversão numérica para um tipo que tem menos precisão ou um intervalo menor e a conversão de uma instância de classe base para uma classe derivada.  
  
-   **Conversões definidas pelo usuário**: as conversões definidas pelo usuário são realizadas por métodos especiais que podem ser definidos para habilitar conversões explícitas e implícitas entre tipos personalizados que não têm uma relação de classe base/classe derivada. Para obter mais informações, consulte [Operadores de Conversão](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md).  
  
-   **Conversões com classes auxiliares**: para converter entre tipos não compatíveis, assim como inteiros e objetos <xref:System.DateTime?displayProperty=fullName>, ou cadeias de caracteres hexadecimais e matrizes de bytes, você pode usar a classe <xref:System.BitConverter?displayProperty=fullName>, a classe <xref:System.Convert?displayProperty=fullName> e os métodos `Parse` dos tipos numéricos internos, tais como <xref:System.Int32.Parse%2A?displayProperty=fullName>. Para obter mais informações, consulte [Como converter uma matriz de bytes em um int](../../../csharp/programming-guide/types/how-to-convert-a-byte-array-to-an-int.md), [Como converter uma cadeia de caracteres em um número](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md) e [Como converter entre cadeias de caracteres hexadecimais e tipos numéricos](../../../csharp/programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md).  
  
## <a name="implicit-conversions"></a>Conversões implícitas  
 Para tipos numéricos internos, uma conversão implícita poderá ser feita quando o valor a ser armazenado puder se ajustar à variável sem ser truncado ou arredondado. Por exemplo, uma variável do tipo [long](../../../csharp/language-reference/keywords/long.md) (inteiro de 8 bytes) pode armazenar qualquer valor que uma [int](../../../csharp/language-reference/keywords/int.md) (4 bytes em um computador de 32 bits) pode armazenar. No exemplo a seguir, o compilador converte implicitamente o valor à direita para um tipo `long` antes de atribuí-lo à `bigNum`.  
  
 [!code-cs[csProgGuideTypes#34](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/casting-and-type-conversions_1.cs)]  
  
 Para obter uma lista completa de todas as conversões numéricas implícitas, consulte [Tabela de conversões numéricas implícitas](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).  
  
 Para tipos de referência, uma conversão implícita sempre existe de uma classe para qualquer uma das suas interfaces ou classes base diretas ou indiretas. Nenhuma sintaxe especial é necessária porque uma classe derivada sempre contém todos os membros de uma classe base.  
  
```  
Derived d = new Derived();  
Base b = d; // Always OK.  
```  
  
## <a name="explicit-conversions"></a>Conversões explícitas  
 No entanto, se uma conversão não puder ser realizada sem o risco de perda de informações, o compilador exigirá que você execute uma conversão explícita, que é chamada de *cast*. Uma conversão é uma maneira de informar explicitamente ao compilador que você pretende fazer a conversão e que você está ciente de que poderá ocorrer perda de dados. Para executar uma conversão, especifique entre parênteses o tipo para o qual você está convertendo, na frente do valor ou da variável a ser convertida. O seguinte programa converte um [double](../../../csharp/language-reference/keywords/double.md) em um [int](../../../csharp/language-reference/keywords/int.md). O programa não será compilado sem a conversão.  
  
 [!code-cs[csProgGuideTypes#2](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/casting-and-type-conversions_2.cs)]  
  
 Para obter uma lista de conversões numéricas explícitas que são permitidas, consulte [Tabela de conversões numéricas explícitas](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md).  
  
 Para tipos de referência, uma conversão explícita será necessária se você precisar converter de um tipo base para um tipo derivado:  
  
```csharp  
// Create a new derived type.  
Giraffe g = new Giraffe();  
  
// Implicit conversion to base type is safe.  
Animal a = g;  
  
// Explicit conversion is required to cast back  
// to derived type. Note: This will compile but will  
// throw an exception at run time if the right-side  
// object is not in fact a Giraffe.  
Giraffe g2 = (Giraffe) a;  
```  
  
 Uma operação de conversão entre tipos de referência não altera o tipo de tempo de execução do objeto subjacente. Ela apenas altera o tipo do valor que está sendo usado como uma referência a esse objeto. Para obter mais informações, consulte [Polimorfismo](../../../csharp/programming-guide/classes-and-structs/polymorphism.md).  
  
## <a name="type-conversion-exceptions-at-run-time"></a>Exceções de conversão de tipo em tempo de execução  
 Em algumas conversões de tipo de referência, o compilador não poderá determinar se uma conversão será válida. É possível que uma operação de conversão que é compilada corretamente falhe em tempo de execução. Conforme mostrado no exemplo a seguir, um tipo de conversão que falha em tempo de execução fará com que uma <xref:System.InvalidCastException> seja lançada.  
  
 [!code-cs[csProgGuideTypes#41](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/casting-and-type-conversions_3.cs)]  
  
 O C# fornece os operadores [is](../../../csharp/language-reference/keywords/is.md) e [as](../../../csharp/language-reference/keywords/as.md) para habilitar o teste de compatibilidade antes de realmente executar uma conversão. Para obter mais informações, consulte [Como executar a conversão com segurança usando operadores as e is](../../../csharp/programming-guide/types/how-to-safely-cast-by-using-as-and-is-operators.md).  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  

## <a name="see-also"></a>Consulte também  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Tipos](../../../csharp/programming-guide/types/index.md)   
 [Operador ()](../../../csharp/language-reference/operators/invocation-operator.md)   
 [explicit](../../../csharp/language-reference/keywords/explicit.md)   
 [implicit](../../../csharp/language-reference/keywords/implicit.md)   
 [Operadores de conversão](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md)   
 [Conversão de tipos generalizada](http://msdn.microsoft.com/library/49253ae6-7657-4810-82ab-1176a6feeada)   
 [Conversão de tipos exportados](http://msdn.microsoft.com/en-us/1dfe55f4-07a2-4b61-aabf-a8cf65783a6b)   
 [Como converter uma cadeia de caracteres em um número](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md)

