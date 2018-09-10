---
title: Usando construtores (Guia de Programação em C#)
ms.date: 07/20/2015
helpviewer_keywords:
- constructors [C#], about constructors
ms.assetid: 464253b2-fd5d-469a-836d-df0fdf2a43f7
ms.openlocfilehash: b19676b2549bbb54af7fb1d72ff0e98352c61383
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43529014"
---
# <a name="using-constructors-c-programming-guide"></a>Usando construtores (Guia de Programação em C#)
Quando uma [classe](../../../csharp/language-reference/keywords/class.md) ou [struct](../../../csharp/language-reference/keywords/struct.md) é criado, seu construtor é chamado. Os construtores têm o mesmo nome que a classe ou struct e eles geralmente inicializam os membros de dados do novo objeto.  
  
 No exemplo a seguir, uma classe chamada `Taxi` é definida usando um construtor simples. A classe é então instanciada com o operador [new](../../../csharp/language-reference/keywords/new.md). O construtor `Taxi` é invocado pelo operador `new` imediatamente após a memória ser alocada para o novo objeto.  
  
 [!code-csharp[csProgGuideObjects#53](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_1.cs)]  
  
 Um construtor sem parâmetros é chamado de um *construtor padrão*. Os construtores padrão são invocados sempre que um objeto é instanciado usando o operador `new` e nenhum argumento é fornecido para `new`. Para obter mais informações, consulte [Construtores de instâncias](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).  
  
 A menos que a classe seja [static](../../../csharp/language-reference/keywords/static.md), as classes sem construtores recebem um construtor padrão público pelo compilador C# para habilitar a instanciação de classe. Para obter mais informações, consulte [Classes estáticas e membros de classes estáticas](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
 Você pode impedir que uma classe seja instanciada tornando o construtor privado, da seguinte maneira:  
  
 [!code-csharp[csProgGuideObjects#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_2.cs)]  
  
 Para obter mais informações, consulte [Construtores particulares](../../../csharp/programming-guide/classes-and-structs/private-constructors.md).  
  
 Os construtores de tipos [struct](../../../csharp/language-reference/keywords/struct.md) são semelhantes aos construtores de classe, mas `structs` não podem conter um construtor padrão explícito porque um é fornecido automaticamente pelo compilador. Este construtor inicializa todos os campos no `struct` com os valores padrão. Para obter mais informações, consulte [Tabela de opções padrão](../../../csharp/language-reference/keywords/default-values-table.md). No entanto, esse construtor padrão é invocado apenas se o `struct` é instanciado com `new`. Por exemplo, esse código usa o construtor padrão para <xref:System.Int32>, de modo que você tenha certeza de que o inteiro é inicializado:  
  
```csharp  
int i = new int();  
Console.WriteLine(i);  
```  
  
 O código a seguir, no entanto, causa um erro do compilador porque ele não usa `new` e porque ele tenta usar um objeto que não foi inicializado:  
  
```  
int i;  
Console.WriteLine(i);  
```  
  
 Como alternativa, os objetos com base em `structs` (incluindo todos os tipos numéricos internos) podem ser inicializados ou atribuídos e, em seguida, usados como no exemplo a seguir:  
  
```  
int a = 44;  // Initialize the value type...  
int b;  
b = 33;      // Or assign it before using it.  
Console.WriteLine("{0}, {1}", a, b);  
```  
  
 Portanto, não é necessário chamar o construtor padrão para um tipo de valor.  
  
 Ambas as classes e `structs` podem definir construtores que usam parâmetros. Os construtores que usam parâmetros devem ser chamados por meio de uma instrução `new` ou uma instrução [base](../../../csharp/language-reference/keywords/base.md). As classes e `structs` também pode definem vários construtores e nenhum deles precisa definir um construtor padrão. Por exemplo:  
  
 [!code-csharp[csProgGuideObjects#54](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_3.cs)]  
  
 Essa classe pode ser criada usando qualquer uma das instruções a seguir:  
  
 [!code-csharp[csProgGuideObjects#55](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_4.cs)]  
  
 Um construtor pode usar a palavra-chave `base` para chamar o construtor de uma classe base. Por exemplo:  
  
 [!code-csharp[csProgGuideObjects#56](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_5.cs)]  
  
 Neste exemplo, o construtor da classe base é chamado antes de o bloco do construtor ser executado. A palavra-chave `base` pode ser usada com ou sem parâmetros. Os parâmetros para o construtor podem ser usados como parâmetros para `base` ou como parte de uma expressão. Para obter mais informações, consulte [base](../../../csharp/language-reference/keywords/base.md).  
  
 Em uma classe derivada, se um construtor de classe base não for chamado explicitamente usando a palavra-chave `base`, o construtor padrão, se houver, será chamado implicitamente. Isso significa que as seguintes declarações de construtor são efetivamente iguais:  
  
 [!code-csharp[csProgGuideObjects#58](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_6.cs)]  
  
 [!code-csharp[csProgGuideObjects#57](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_7.cs)]  
  
 Se uma classe base não oferecer um construtor padrão, a classe derivada deverá fazer uma chamada explícita para um construtor base usando `base`.  
  
 Um construtor pode invocar outro construtor no mesmo objeto usando a palavra-chave [this](../../../csharp/language-reference/keywords/this.md). Como `base`, `this` pode ser usado com ou sem parâmetros e todos os parâmetros no construtor estão disponíveis como parâmetros para `this` ou como parte de uma expressão. Por exemplo, o segundo construtor no exemplo anterior pode ser reescrito usando `this`:  
  
 [!code-csharp[csProgGuideObjects#59](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_8.cs)]  
  
 O uso da palavra-chave `this` no exemplo anterior faz com que esse construtor seja chamado:  
  
 [!code-csharp[csProgGuideObjects#60](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_9.cs)]  
  
 Os construtores podem ser marcados como [public](../../../csharp/language-reference/keywords/public.md), [private](../../../csharp/language-reference/keywords/private.md), [protected](../../../csharp/language-reference/keywords/protected.md), [internal](../../../csharp/language-reference/keywords/internal.md), [protected internal](../../../csharp/language-reference/keywords/protected-internal.md) ou [private protected](../../../csharp/language-reference/keywords/private-protected.md). Esses modificadores de acesso definem como os usuários da classe podem construir a classe. Para obter mais informações, consulte [Modificadores de Acesso](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
 Um construtor pode ser declarado estático usando a palavra-chave [static](../../../csharp/language-reference/keywords/static.md). Os construtores estáticos são chamados automaticamente, imediatamente antes de qualquer campo estático ser acessado e geralmente são usados para inicializar membros da classe estática. Para obter mais informações, consulte [Construtores estáticos](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
- [Classes e Structs](../../../csharp/programming-guide/classes-and-structs/index.md)  
- [Construtores](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
- [Finalizadores](../../../csharp/programming-guide/classes-and-structs/destructors.md)
