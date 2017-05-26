---
title: "Conversões boxing e unboxing (Guia de Programação em C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- cs.boxing
dev_langs:
- CSharp
helpviewer_keywords:
- C# language, boxing
- C# language, unboxing
- unboxing [C#]
- boxing [C#]
ms.assetid: 8da9bbf4-bce9-4b08-b2e5-f64c11c56514
caps.latest.revision: 34
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
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: e6e0a70abd0f3311324f30eb5155000c09fc29cd
ms.contentlocale: pt-br
ms.lasthandoff: 03/13/2017

---
# <a name="boxing-and-unboxing-c-programming-guide"></a>Conversões boxing e unboxing (Guia de Programação em C#)
Conversão boxing é o processo de conversão de um [tipo de valor](../../../csharp/language-reference/keywords/value-types.md) para o tipo `object` ou para qualquer tipo de interface implementada por esse tipo de valor. Quando o CLR realiza a conversão boxing de um tipo de valor, ele encapsula o valor dentro de System.Object e o armazena no heap gerenciado. A conversão unboxing extrai o tipo de valor do objeto. A conversão boxing é implícita, a conversão unboxing é explícita. O conceito de conversões boxing e unboxing serve como base para a exibição unificada de C# do sistema de tipos em que um valor de qualquer tipo pode ser tratado como um objeto.  
  
 No exemplo a seguir, a variável de inteiro `i` é submetida à *conversão boxing* e atribuída ao objeto `o`.  
  
 [!code-cs[csProgGuideTypes#14](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_1.cs)]  
  
 O objeto `o` pode ser submetido à conversão unboxing e atribuído à variável de inteiro `i`:  
  
 [!code-cs[csProgGuideTypes#15](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_2.cs)]  
  
 Os exemplos a seguir ilustram como a conversão boxing é usada em C#.  
  
 [!code-cs[csProgGuideTypes#47](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_3.cs)]  
  
## <a name="performance"></a>Desempenho  
 Em relação às atribuições simples, as conversões boxing e unboxing são processos computacionalmente dispendiosos. Quando um tipo de valor é submetido à conversão boxing, um novo objeto deve ser alocado e construído. A um grau menor, a conversão necessária para a conversão unboxing também é computacionalmente dispendiosa. Para obter mais informações, consulte [Desempenho](https://msdn.microsoft.com/library/ms173196(VS.110).aspx).  
  
## <a name="boxing"></a>Boxing  
 A conversão boxing é usada para armazenar tipos de valor no heap coletado como lixo. A conversão boxing é uma conversão implícita de um [tipo de valor](../../../csharp/language-reference/keywords/value-types.md) para o tipo `object` ou para qualquer tipo de interface implementada por esse tipo de valor. A conversão boxing de um tipo de valor aloca uma instância de objeto no heap e copia o valor no novo objeto.  
  
 Considere a seguinte declaração de uma variável de tipo de valor:  
  
 [!code-cs[csProgGuideTypes#17](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_4.cs)]  
  
 A instrução a seguir aplica implicitamente a operação de conversão boxing na variável `i`:  
  
 [!code-cs[csProgGuideTypes#18](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_5.cs)]  
  
 O resultado dessa instrução é a criação de uma referência de objeto `o`, na pilha, que faz referência a um valor do tipo `int`, no heap. Esse valor é uma cópia do valor do tipo de valor atribuído à variável `i`. A diferença entre as duas variáveis, `i` e `o`, é ilustrada na figura a seguir.  
  
 ![Gráfico de BoxingConversion](../../../csharp/programming-guide/types/media/vcboxingconversion.gif "vcBoxingConversion")  
Conversão boxing  
  
 Também é possível executar a conversão boxing explicitamente como no exemplo a seguir, mas a conversão boxing explícita nunca é necessária:  
  
 [!code-cs[csProgGuideTypes#19](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_6.cs)]  
  
## <a name="description"></a>Descrição  
 Este exemplo converte uma variável de inteiro `i` em um objeto `o` usando a conversão boxing. Em seguida, o valor armazenado na variável `i` é alterado de `123` para `456`. O exemplo mostra que o tipo do valor original e o objeto submetido à conversão boxing usa locais de memória separados e, portanto, pode armazenar valores diferentes.  
  
## <a name="example"></a>Exemplo  
 [!code-cs[csProgGuideTypes#16](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_7.cs)]  
  
## <a name="unboxing"></a>Unboxing  
 A conversão unboxing é uma conversão explícita do tipo `object` para um [tipo de valor](../../../csharp/language-reference/keywords/value-types.md) ou de um tipo de interface para um tipo de valor que implementa a interface. Uma operação de conversão unboxing consiste em:  
  
-   Verificar a instância do objeto para garantir que ele é um valor da conversão boxing de um determinado tipo de valor.  
  
-   Copiar o valor da instância para a variável de tipo de valor.  
  
 As instruções a seguir demonstram operações conversão boxing e unboxing:  
  
 [!code-cs[csProgGuideTypes#21](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_8.cs)]  
  
 A figura a seguir demonstra o resultado das instruções anteriores.  
  
 ![Gráfico de conversão unboxing](../../../csharp/programming-guide/types/media/vcunboxingconversion.gif "vcUnBoxingConversion")  
Conversão unboxing  
  
 Para a conversão unboxing de tipos de valor ter êxito em tempo de execução, o item sendo submetido à conversão unboxing deve ser uma referência para um objeto que foi criado anteriormente ao realizar a conversão boxing de uma instância desse tipo de valor. Tentar realizar a conversão unbox de `null` causa uma <xref:System.NullReferenceException>. Tentar realizar a conversão unbox de uma referência para um tipo de valor incompatível causa uma <xref:System.InvalidCastException>.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra um caso de conversão unboxing inválida e o `InvalidCastException` resultante. Usando `try` e `catch`, uma mensagem de erro é exibida quando o erro ocorre.  
  
 [!code-cs[csProgGuideTypes#20](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_9.cs)]  
  
 Este programa produz:  
  
 `Specified cast is not valid. Error: Incorrect unboxing.`  
  
 Se você alterar a instrução:  
  
```  
int j = (short) o;  
```  
  
 para:  
  
```  
int j = (int) o;  
```  
  
 a conversão será executada e você receberá a saída:  
  
 `Unboxing OK.`  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="related-sections"></a>Seções relacionadas  
 Para saber mais:  
  
-   [Tipos de referência](../../../csharp/language-reference/keywords/reference-types.md)  
  
-   [Tipos de valor](../../../csharp/language-reference/keywords/value-types.md)  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)
