---
title: Métodos genéricos (Guia de Programação em C#)
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], methods
ms.assetid: 673eeea2-4b48-4faa-9c4e-2e89449221b9
ms.openlocfilehash: 04bc59d41eb7883e08138382b396bc737c7f11bb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33329862"
---
# <a name="generic-methods-c-programming-guide"></a>Métodos genéricos (Guia de Programação em C#)
Um método genérico é um método declarado com parâmetros de tipo, da seguinte maneira:  
  
 [!code-csharp[csProgGuideGenerics#22](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_1.cs)]  
  
 O exemplo de código a seguir mostra uma maneira de chamar o método usando `int` para o argumento de tipo:  
  
 [!code-csharp[csProgGuideGenerics#23](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_2.cs)]  
  
 Também é possível omitir o argumento de tipo e o compilador o inferirá. Esta chamada para `Swap` é equivalente à chamada anterior:  
  
 [!code-csharp[csProgGuideGenerics#24](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_3.cs)]  
  
 As mesmas regras de inferência de tipos se aplicam a métodos estáticos e métodos de instância. O compilador pode inferir os parâmetros de tipo com base nos argumentos de método passados; não é possível inferir os parâmetros de tipo somente de uma restrição ou valor retornado. Portanto, a inferência de tipos não funciona com métodos que não têm parâmetros. A inferência de tipos ocorre em tempo de compilação, antes de o compilador tentar resolver assinaturas de método sobrecarregadas. O compilador aplica a lógica da inferência de tipos a todos os métodos genéricos que compartilham o mesmo nome. Na etapa de resolução de sobrecarga, o compilador incluirá somente os métodos genéricos em que a inferência de tipos foi bem-sucedida.  
  
 Em uma classe genérica, métodos não genéricos podem acessar os parâmetros de tipo de nível de classe, da seguinte maneira:  
  
 [!code-csharp[csProgGuideGenerics#25](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_4.cs)]  
  
 Se um método genérico que usa os mesmos parâmetros de tipo da classe que o contém for definido, o compilador gerará um aviso CS0693, pois, dentro do escopo do método, o argumento fornecido para o `T` interno oculta o argumento fornecido para o `T` externo. Caso seja necessária a flexibilidade de chamar um método de classe genérica com argumentos de tipo diferentes dos fornecidos quando a instância da classe foi criada, considere fornecer outro identificador ao parâmetro de tipo do método, conforme mostrado no `GenericList2<T>` do exemplo a seguir.  
  
 [!code-csharp[csProgGuideGenerics#26](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_5.cs)]  
  
 Use restrições para permitir operações mais especializadas em parâmetros de tipo de métodos. Essa versão do `Swap<T>`, agora denominada `SwapIfGreater<T>`, pode ser usada somente com argumentos de tipo que implementam <xref:System.IComparable%601>.  
  
 [!code-csharp[csProgGuideGenerics#27](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_6.cs)]  
  
 Métodos genéricos podem ser sobrecarregados vários parâmetros de tipo. Por exemplo, todos os seguintes métodos podem ser localizados na mesma classe:  
  
 [!code-csharp[csProgGuideGenerics#28](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_7.cs)]  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 Para obter mais informações, consulte a [Especificação da linguagem C#](../../../csharp/language-reference/language-specification/index.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Collections.Generic>  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Introdução aos genéricos](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
 [Métodos](../../../csharp/programming-guide/classes-and-structs/methods.md)
