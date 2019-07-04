---
title: Usando construtores – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- constructors [C#], about constructors
ms.assetid: 464253b2-fd5d-469a-836d-df0fdf2a43f7
ms.openlocfilehash: 14ff272fe940c265dc8984d6b20985bb2d2ba12d
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/26/2019
ms.locfileid: "67398245"
---
# <a name="using-constructors-c-programming-guide"></a>Usando construtores (Guia de Programação em C#)

Quando uma [classe](../../../csharp/language-reference/keywords/class.md) ou [struct](../../../csharp/language-reference/keywords/struct.md) é criado, seu construtor é chamado. Os construtores têm o mesmo nome que a classe ou struct e eles geralmente inicializam os membros de dados do novo objeto.  
  
 No exemplo a seguir, uma classe chamada `Taxi` é definida usando um construtor simples. A classe é então instanciada com o operador [new](../../../csharp/language-reference/operators/new-operator.md). O construtor `Taxi` é invocado pelo operador `new` imediatamente após a memória ser alocada para o novo objeto.  
  
 [!code-csharp[csProgGuideObjects#53](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#53)]  
  
 Um construtor que não tem nenhum parâmetro é chamado de *construtor sem parâmetros*. Os construtores padrão são invocados sempre que um objeto é instanciado usando o operador `new` e nenhum argumento é fornecido para `new`. Para obter mais informações, consulte [Construtores de instâncias](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).  
  
 A menos que a classe seja [static](../../../csharp/language-reference/keywords/static.md), as classes sem construtores recebem um construtor sem parâmetros público pelo compilador C# para habilitar a instanciação de classe. Para obter mais informações, consulte [Classes estáticas e membros de classes estáticas](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
 Você pode impedir que uma classe seja instanciada tornando o construtor privado, da seguinte maneira:  
  
 [!code-csharp[csProgGuideObjects#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#11)]  
  
 Para obter mais informações, consulte [Construtores particulares](../../../csharp/programming-guide/classes-and-structs/private-constructors.md).  
  
 Os construtores de tipos [struct](../../../csharp/language-reference/keywords/struct.md) são semelhantes aos construtores de classe, mas `structs` não podem conter um construtor sem parâmetros explícito porque um é fornecido automaticamente pelo compilador. Este construtor inicializa todos os campos no `struct` com os valores padrão. Para obter mais informações, consulte [Tabela de opções padrão](../../../csharp/language-reference/keywords/default-values-table.md). No entanto, esse construtor sem parâmetro será invocado apenas se o `struct` for instanciado com `new`. Por exemplo, esse código usa o construtor sem parâmetros para <xref:System.Int32>, de modo que você tenha certeza de que o inteiro é inicializado:  
  
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
  
 Portanto, não é necessário chamar o construtor sem parâmetros para um tipo de valor.  
  
 Ambas as classes e `structs` podem definir construtores que usam parâmetros. Os construtores que usam parâmetros devem ser chamados por meio de uma instrução `new` ou uma instrução [base](../../../csharp/language-reference/keywords/base.md). As classes e `structs` também podem definir vários construtores e nenhum deles precisa definir um construtor sem parâmetros. Por exemplo:  
  
 [!code-csharp[csProgGuideObjects#54](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#54)]  
  
 Essa classe pode ser criada usando qualquer uma das instruções a seguir:  
  
 [!code-csharp[csProgGuideObjects#55](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#55)]  
  
 Um construtor pode usar a palavra-chave `base` para chamar o construtor de uma classe base. Por exemplo:  
  
 [!code-csharp[csProgGuideObjects#56](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#56)]  
  
 Neste exemplo, o construtor da classe base é chamado antes de o bloco do construtor ser executado. A palavra-chave `base` pode ser usada com ou sem parâmetros. Os parâmetros para o construtor podem ser usados como parâmetros para `base` ou como parte de uma expressão. Para obter mais informações, consulte [base](../../../csharp/language-reference/keywords/base.md).  
  
 Em uma classe derivada, se um construtor de classe base não for chamado explicitamente usando a palavra-chave `base`, o construtor sem parâmetros, se houver, será chamado implicitamente. Isso significa que as seguintes declarações de construtor são efetivamente iguais:  
  
 [!code-csharp[csProgGuideObjects#58](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#58)]  
  
 [!code-csharp[csProgGuideObjects#57](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#57)]  
  
 Se uma classe base não oferecer um construtor sem parâmetros, a classe derivada deverá fazer uma chamada explícita para um construtor base usando `base`.  
  
 Um construtor pode invocar outro construtor no mesmo objeto usando a palavra-chave [this](../../../csharp/language-reference/keywords/this.md). Como `base`, `this` pode ser usado com ou sem parâmetros e todos os parâmetros no construtor estão disponíveis como parâmetros para `this` ou como parte de uma expressão. Por exemplo, o segundo construtor no exemplo anterior pode ser reescrito usando `this`:  
  
 [!code-csharp[csProgGuideObjects#59](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#59)]  
  
 O uso da palavra-chave `this` no exemplo anterior faz com que esse construtor seja chamado:  
  
 [!code-csharp[csProgGuideObjects#60](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#60)]  
  
 Os construtores podem ser marcados como [public](../../../csharp/language-reference/keywords/public.md), [private](../../../csharp/language-reference/keywords/private.md), [protected](../../../csharp/language-reference/keywords/protected.md), [internal](../../../csharp/language-reference/keywords/internal.md), [protected internal](../../../csharp/language-reference/keywords/protected-internal.md) ou [private protected](../../../csharp/language-reference/keywords/private-protected.md). Esses modificadores de acesso definem como os usuários da classe podem construir a classe. Para obter mais informações, consulte [Modificadores de Acesso](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
 Um construtor pode ser declarado estático usando a palavra-chave [static](../../../csharp/language-reference/keywords/static.md). Os construtores estáticos são chamados automaticamente, imediatamente antes de qualquer campo estático ser acessado e geralmente são usados para inicializar membros da classe estática. Para obter mais informações, consulte [Construtores estáticos](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  

Para obter mais informações, veja [Construtores de instância](~/_csharplang/spec/classes.md#instance-constructors) e [Construtores estáticos](~/_csharplang/spec/classes.md#static-constructors) na [Especificação de Linguagem C#](../../language-reference/language-specification/index.md). A especificação da linguagem é a fonte definitiva para a sintaxe e o uso de C#.
  
## <a name="see-also"></a>Consulte também

- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)
- [Classes e Structs](../../../csharp/programming-guide/classes-and-structs/index.md)
- [Construtores](../../../csharp/programming-guide/classes-and-structs/constructors.md)
- [Finalizadores](../../../csharp/programming-guide/classes-and-structs/destructors.md)
