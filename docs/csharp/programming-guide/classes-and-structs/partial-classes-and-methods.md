---
title: Classes e métodos partial (Guia de Programação em C#)
ms.date: 07/20/2015
helpviewer_keywords:
- partial methods [C#]
- partial classes [C#]
- C# language, partial classes and methods
ms.assetid: 804cecb7-62db-4f97-a99f-60975bd59fa1
ms.openlocfilehash: 2975b9e79824560c711e96382a9ccc03bdc72810
ms.sourcegitcommit: 3b1cb8467bd73dee854b604e306c0e7e3882d91a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2018
ms.locfileid: "43521163"
---
# <a name="partial-classes-and-methods-c-programming-guide"></a>Classes e métodos partial (Guia de Programação em C#)
É possível dividir a definição de uma [classe](../../../csharp/language-reference/keywords/class.md) ou [struct](../../../csharp/language-reference/keywords/struct.md), uma [interface](../../../csharp/language-reference/keywords/interface.md) ou um método em dois ou mais arquivos de origem. Cada arquivo de origem contém uma seção da definição de tipo ou método e todas as partes são combinadas quando o aplicativo é compilado.  
  
## <a name="partial-classes"></a>Classes parciais  
 Há várias situações em que a divisão de uma definição de classe é desejável:  
  
-   Ao trabalhar em projetos grandes, dividir uma classe em arquivos separados permite que vários programadores trabalhem ao mesmo tempo.  
  
-   Ao trabalhar com código-fonte gerado automaticamente, o código pode ser adicionado à classe sem precisar recriar o arquivo de origem. O Visual Studio usa essa abordagem quando cria Windows Forms, código de wrapper de serviço Web e assim por diante. Você pode criar código que usa essas classes sem precisar modificar o arquivo que o Visual Studio cria.  
  
-   Para dividir uma definição de classe, use o modificador de palavra-chave [partial](../../../csharp/language-reference/keywords/partial-type.md), como mostrado aqui:  
  
 [!code-csharp[csProgGuideObjects#26](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_1.cs)]  
  
 A palavra-chave `partial` indica que outras partes da classe, struct ou interface podem ser definidas no namespace. Todas as partes devem usar a palavra-chave `partial`. Todas as partes devem estar disponíveis em tempo de compilação para formar o tipo final. Todas as partes devem ter a mesma acessibilidade, tais como `public`, `private` e assim por diante.  
  
 Se alguma parte for declarada como abstrata, o tipo inteiro será considerado abstrato. Se alguma parte for declarada como lacrada, o tipo inteiro será considerado lacrado. Se alguma parte declarar um tipo base, o tipo inteiro herda dessa classe.  
  
 Todas as partes que especificam uma classe base devem concordar, mas partes que omitem uma classe base ainda herdam o tipo base. As partes podem especificar diferentes interfaces base e o tipo final implementa todas as interfaces listadas por todas as declarações parciais. Qualquer membro de classe, struct ou interface declarado em uma definição parcial está disponível para todas as outras partes. O tipo final é a combinação de todas as partes em tempo de compilação.  
  
> [!NOTE]
>  O modificador `partial` não está disponível em declarações de enumeração ou delegados.  
  
 O exemplo a seguir mostra que tipos aninhados podem ser parciais, mesmo se o tipo no qual eles estão aninhados não for parcial.  
  
 [!code-csharp[csProgGuideObjects#25](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_2.cs)]  
  
 Em tempo de compilação, atributos de definições de tipo parcial são mesclados. Por exemplo, considere as declarações a seguir:  
  
 [!code-csharp[csProgGuideObjects#23](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_3.cs)]  
  
 Elas são equivalentes às seguintes declarações:  
  
 [!code-csharp[csProgGuideObjects#24](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_4.cs)]  
  
 Os itens a seguir são mesclados de todas as definições de tipo parcial:  
  
-   comentários XML  
  
-   interfaces  
  
-   atributos de parâmetro de tipo genérico  
  
-   atributos class  
  
-   membros  
  
 Por exemplo, considere as declarações a seguir:  
  
 [!code-csharp[csProgGuideObjects#21](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_5.cs)]  
  
 Elas são equivalentes às seguintes declarações:  
  
 [!code-csharp[csProgGuideObjects#22](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_6.cs)]  
  
### <a name="restrictions"></a>Restrições  
 Há várias regras para seguir quando você está trabalhando com definições de classes parciais:  
  
-   Todas as definições de tipo parcial que devem ser partes do mesmo tipo devem ser modificadas com `partial`. Por exemplo, as seguintes declarações de classe geram um erro:  
  
     [!code-csharp[csProgGuideObjects#20](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_7.cs)]  
  
-   O modificador `partial` só pode aparecer imediatamente antes das palavras-chave `class`, `struct` ou `interface`.  
  
-   Tipos parciais aninhados são permitidos em definições de tipo parcial, conforme ilustrado no exemplo a seguir:  
  
     [!code-csharp[csProgGuideObjects#19](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_8.cs)]  
  
-   Todas as definições de tipo parcial que devem ser partes do mesmo tipo devem ser definidas no mesmo assembly e no mesmo módulo (arquivo .dll ou .exe). Definições parciais não podem abranger vários módulos.  
  
-   O nome de classe e os parâmetros de tipo genérico devem corresponder em todas as definições de tipo parcial. Tipos genéricos podem ser parciais. Cada declaração parcial deve usar os mesmos nomes de parâmetro na mesma ordem.  
  
-   As seguintes palavras-chave em uma definição de tipo parcial são opcionais, mas, se estiverem presentes em uma definição de tipo parcial, não podem entrar em conflito com as palavras-chave especificadas em outra definição parcial para o mesmo tipo:  
  
    -   [public](../../../csharp/language-reference/keywords/public.md)  
  
    -   [private](../../../csharp/language-reference/keywords/private.md)  
  
    -   [protected](../../../csharp/language-reference/keywords/protected.md)  
  
    -   [internal](../../../csharp/language-reference/keywords/internal.md)  
  
    -   [abstract](../../../csharp/language-reference/keywords/abstract.md)  
  
    -   [sealed](../../../csharp/language-reference/keywords/sealed.md)  
  
    -   classe base  
  
    -   modificador [new](../../../csharp/language-reference/keywords/new.md) (partes aninhadas)  
  
    -   restrições genéricas  
  
         Para obter mais informações, consulte [Restrições a parâmetros de tipo](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).  
  
## <a name="example-1"></a>Exemplo 1  
  
### <a name="description"></a>Descrição  
 No exemplo a seguir, os campos e o construtor da classe, `CoOrds`, são declarados em uma definição de classe parcial e o membro, `PrintCoOrds`, é declarado em outra definição de classe parcial.  
  
### <a name="code"></a>Código  
 [!code-csharp[csProgGuideObjects#17](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_9.cs)]  
  
## <a name="example-2"></a>Exemplo 2  
  
### <a name="description"></a>Descrição  
 O exemplo a seguir mostra que você também pode desenvolver interfaces e structs parciais.  
  
### <a name="code"></a>Código  
 [!code-csharp[csProgGuideObjects#18](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_10.cs)]  
  
## <a name="partial-methods"></a>Métodos parciais  
 Uma classe ou struct parcial pode conter um método parcial. Uma parte da classe contém a assinatura do método. Uma implementação opcional pode ser definida na mesma parte ou em outra parte. Se a implementação não for fornecida, o método e todas as chamadas para o método serão removidos em tempo de compilação.  
  
 Métodos parciais permitem que o implementador de uma parte de uma classe defina um método, semelhante a um evento. O implementador da outra parte da classe pode decidir implementará o método ou não. Se o método não for implementado, o compilador removerá a assinatura do método e todas as chamadas para o método. As chamadas para o método, incluindo qualquer resultado que ocorreria da avaliação de argumentos nas chamadas, não têm efeito em tempo de execução. Portanto, qualquer código na classe parcial pode usar livremente um método parcial, mesmo que a implementação não seja fornecida. Nenhum erro de tempo de compilação ou tempo de execução ocorrerá se o método for chamado, mas não implementado.  
  
 Métodos parciais são especialmente úteis como uma maneira de personalizar o código gerado. Eles permitem que um nome e uma assinatura de método sejam reservados, para que o código gerado possa chamar o método, mas o desenvolvedor possa decidir se deve implementar o método. Assim como as classes parciais, os métodos parciais habilitam o código criado por um gerador de código e o código criado por um desenvolvedor humano a funcionarem juntos sem custos de tempo de execução.  
  
 Uma declaração de método parcial consiste em duas partes: a definição e a implementação. Elas podem estar em partes separadas de uma classe parcial ou na mesma parte. Se não houver nenhuma declaração de implementação, o compilador otimizará a declaração de definição e todas as chamadas para o método.  
  
```csharp  
// Definition in file1.cs  
partial void onNameChanged();  
  
// Implementation in file2.cs  
partial void onNameChanged()  
{  
  // method body  
}  
```  
  
-   Declarações de métodos parcial devem começar com a palavra-chave contextual [partial](../../../csharp/language-reference/keywords/partial-type.md) e o método deve retornar [void](../../../csharp/language-reference/keywords/void.md).  
  
-   Os métodos parciais podem ter os parâmetros [in](../../../csharp/language-reference/keywords/in-parameter-modifier.md) ou [ref](../../../csharp/language-reference/keywords/ref.md), mas não [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md).  
  
-   Métodos parciais são implicitamente [private](../../../csharp/language-reference/keywords/private.md) e portanto não podem ser [virtual](../../../csharp/language-reference/keywords/virtual.md).  
  
-   Métodos parciais não podem ser [extern](../../../csharp/language-reference/keywords/extern.md), pois a presença do corpo determina se eles estão sendo definidos ou implementados.  
  
-   Métodos parciais podem ter modificadores [static](../../../csharp/language-reference/keywords/static.md) e [unsafe](../../../csharp/language-reference/keywords/unsafe.md).  
  
-   Métodos parciais podem ser genéricos. Restrições são colocadas quanto à declaração de método parcial de definição e, opcionalmente, podem ser repetidas na de implementação. Nomes de parâmetro e de tipo de parâmetro não precisam ser iguais na declaração de implementação e na de definição.  
  
-   Você pode fazer um [delegado](../../../csharp/language-reference/keywords/delegate.md) para um método parcial que foi definido e implementado, mas não para um método parcial que só foi definido.  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  

Para obter mais informações, veja [Tipos parciais](~/_csharplang/spec/classes.md#partial-types) na [Especificação da Linguagem C#](../../language-reference/language-specification/index.md). A especificação da linguagem é a fonte definitiva para a sintaxe e o uso de C#.
  
## <a name="see-also"></a>Consulte também

- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
- [Classes](../../../csharp/programming-guide/classes-and-structs/classes.md)  
- [Estruturas](../../../csharp/programming-guide/classes-and-structs/structs.md)  
- [Interfaces](../../../csharp/programming-guide/interfaces/index.md)  
- [(partial (tipo)](../../../csharp/language-reference/keywords/partial-type.md)
