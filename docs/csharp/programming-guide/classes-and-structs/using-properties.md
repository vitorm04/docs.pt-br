---
title: "Usando propriedades (Guia de Programação em C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- set accessor [C#]
- get accessor [C#]
- properties [C#], about properties
ms.assetid: f7f67b05-0983-4cdb-96af-1855d24c967c
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 36345748e514f0e0a4c945d8ead149c7d8ca9a19
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2018
---
# <a name="using-properties-c-programming-guide"></a>Usando propriedades (Guia de Programação em C#)
As propriedades combinam aspectos de métodos e campos. Para o usuário de um objeto, uma propriedade parece ser um campo. Acessar a propriedade requer a mesma sintaxe. Para o implementador de uma classe, uma propriedade consiste em um ou dois blocos de código, que representam um acessador [get](../../../csharp/language-reference/keywords/get.md) e/ou um acessador [set](../../../csharp/language-reference/keywords/set.md). O bloco de código para o acessador `get` é executado quando a propriedade é lida. O bloco de código para o acessador `set` é executado quando um novo valor é atribuído à propriedade. Uma propriedade sem um acessador `set` é considerada como somente leitura. Uma propriedade sem um acessador `get` é considerada como somente gravação. Uma propriedade que tem os dois acessadores é leitura/gravação.  
  
 Diferentemente dos campos, as propriedades não são classificadas como variáveis. Portanto, você não pode passar uma propriedade como um parâmetro [ref](../../../csharp/language-reference/keywords/ref.md) ou [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md).  
  
 As propriedades têm muitos usos: elas podem validar os dados antes de permitir uma alteração; elas podem expor, de forma transparente, os dados em uma classe em que esses dados são realmente recuperados de outra origem qualquer, como um banco de dados; elas podem executar uma ação quando os dados são alterados, como acionar um evento ou alterar o valor de outros campos.  
  
 As propriedades são declaradas no bloco de classe, especificando o nível de acesso do campo, seguido pelo tipo da propriedade, pelo nome da propriedade e por um bloco de código que declara um acessador `get` e/ou um acessador `set`. Por exemplo:  
  
 [!code-csharp[csProgGuideProperties#7](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_1.cs)]  
  
 Neste exemplo, `Month` é declarado como uma propriedade de maneira que o acessador `set` possa garantir que o valor `Month` esteja definido entre 1 e 12. A propriedade `Month` usa um campo particular para rastrear o valor real. O local real dos dados de uma propriedade é conhecido, em geral, como o "repositório de backup" da propriedade. É comum as propriedades usarem campos particulares como um repositório de backup. O campo é marcado como particular para garantir que ele só pode ser alterado ao chamar a propriedade. Para obter mais informações sobre as restrições de acesso público e particular, consulte [Modificadores de acesso](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
 As propriedades autoimplementadas fornecem sintaxe simplificada para declarações de propriedade simples. Para obter mais informações, consulte [Propriedades autoimplementadas](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).  
  
## <a name="the-get-accessor"></a>O acessador get  
 O corpo do acessador `get` assemelha-se ao de um método. Ele deve retornar um valor do tipo de propriedade. A execução do acessador `get` é equivalente à leitura do valor do campo. Por exemplo, quando você estiver retornando a variável particular do acessador `get` e as otimizações estiverem habilitadas, a chamada ao método do acessador `get` será embutida pelo compilador, portanto, não haverá nenhuma sobrecarga de chamada de método. No entanto, um método do acessador `get` virtual não pode ser embutido porque o compilador não sabe, em tempo de compilação, qual método pode ser chamado em tempo de execução. A seguir está um acessador `get` que retorna o valor de um campo particular `name`:  
  
 [!code-csharp[csProgGuideProperties#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_2.cs)]  
  
 Quando você referencia a propriedade, exceto como o destino de uma atribuição, o acessador `get` é invocado para ler o valor da propriedade. Por exemplo:  
  
 [!code-csharp[csProgGuideProperties#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_3.cs)]  
  
 O acessador `get` deve terminar em uma instrução [return](../../../csharp/language-reference/keywords/return.md) ou [throw](../../../csharp/language-reference/keywords/throw.md) e o controle não pode fluir para fora do corpo do acessador.  
  
 Alterar o estado do objeto usando o acessador `get` é um estilo ruim de programação. Por exemplo, o acessador a seguir produz o efeito colateral de alterar o estado do objeto sempre que o campo `number` é acessado.  
  
 [!code-csharp[csProgGuideProperties#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_4.cs)]  
  
 O acessador `get` pode ser usado para retornar o valor do campo ou para calculá-lo e retorná-lo. Por exemplo:  
  
 [!code-csharp[csProgGuideProperties#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_5.cs)]  
  
 No segmento de código anterior, se você não atribuir um valor para a propriedade `Name`, ela retornará o valor NA.  
  
## <a name="the-set-accessor"></a>O acessador set  
 O acessador `set` é semelhante a um método cujo tipo de retorno é [void](../../../csharp/language-reference/keywords/void.md). Ele usa uma parâmetro implícito chamado `value`, cujo tipo é o tipo da propriedade. No exemplo a seguir, uma acessador `set` é adicionado à propriedade `Name`:  
  
 [!code-csharp[csProgGuideProperties#12](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_6.cs)]  
  
 Quando você atribui um valor à propriedade, o acessador `set` é invocado por meio do uso de um argumento que fornece o novo valor. Por exemplo:  
  
 [!code-csharp[csProgGuideProperties#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_7.cs)]  
  
 É um erro usar o nome de parâmetro implícito `value`, para uma declaração de variável local em um acessador `set`.  
  
## <a name="remarks"></a>Comentários  
 As propriedades podem ser marcadas como `public`, `private`, `protected`, `internal`, `protected internal` ou `private protected`. Esses modificadores de acesso definem como os usuários da classe podem acessar a propriedade. Os acessadores `get` e `set` para a mesma propriedade podem ter modificadores de acesso diferentes. Por exemplo, o `get` pode ser `public` para permitir acesso somente leitura de fora do tipo e o `set` pode ser `private` ou `protected`. Para obter mais informações, consulte [Modificadores de Acesso](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
 Uma propriedade pode ser declarada como uma propriedade estática, usando a palavra-chave `static`. Isso torna a propriedade disponível para chamadores a qualquer momento, mesmo se não existir nenhuma instância da classe. Para obter mais informações, consulte [Classes estáticas e membros de classes estáticas](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
 Uma propriedade pode ser marcada como uma propriedade virtual, usando a palavra-chave [virtual](../../../csharp/language-reference/keywords/virtual.md). Isso habilita as classes derivadas a substituírem o comportamento da propriedade, usando a palavra-chave [override](../../../csharp/language-reference/keywords/override.md). Para obter mais informações sobre essas opções, consulte [Herança](../../../csharp/programming-guide/classes-and-structs/inheritance.md).  
  
 Uma propriedade que substitui uma propriedade virtual também pode ser [sealed](../../../csharp/language-reference/keywords/sealed.md), especificando que ela não é mais virtual para classes derivadas. Por fim, uma propriedade pode ser declarada [abstract](../../../csharp/language-reference/keywords/abstract.md). Isso significa que não há nenhuma implementação na classe e as classes derivadas devem escrever sua própria implementação. Para obter mais informações sobre essas opções, consulte [Classes e membros de classes abstract e sealed](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
> [!NOTE]
>  É um erro usar um modificador [virtual](../../../csharp/language-reference/keywords/virtual.md), [abstract](../../../csharp/language-reference/keywords/abstract.md) ou [override](../../../csharp/language-reference/keywords/override.md) em um acessador de uma propriedade [static](../../../csharp/language-reference/keywords/static.md).  
  
## <a name="example"></a>Exemplo  
 Este exemplo demonstra as propriedades instância, estática e somente leitura. Ele aceita o nome do funcionário digitado no teclado, incrementa `NumberOfEmployees` em 1 e exibe o nome e o número do funcionário.  
  
 [!code-csharp[csProgGuideProperties#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_8.cs)]  
  
## <a name="example"></a>Exemplo  
 Este exemplo demonstra como acessar uma propriedade em uma classe base que está oculta por outra propriedade que tem o mesmo nome em uma classe derivada.  
  
 [!code-csharp[csProgGuideProperties#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_9.cs)]  
  
 A seguir estão os pontos importantes do exemplo anterior:  
  
-   A propriedade `Name` na classe derivada oculta a propriedade `Name` na classe base. Nesse caso, o modificador `new` é usado na declaração da propriedade na classe derivada:  
  
     [!code-csharp[csProgGuideProperties#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_10.cs)]  
  
-   A conversão `(Employee)` é usada para acessar a propriedade oculta na classe base:  
  
     [!code-csharp[csProgGuideProperties#5](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_11.cs)]  
  
     Para obter mais informações sobre como ocultar membros, consulte o [Modificador new](../../../csharp/language-reference/keywords/new-modifier.md).  
  
## <a name="example"></a>Exemplo  
 Neste exemplo, duas classes, `Cube` e `Square`, implementam uma classe abstrata `Shape` e substituem sua propriedade `Area` abstrata. Observe o uso do modificador [override](../../../csharp/language-reference/keywords/override.md) nas propriedades. O programa aceita o lado como uma entrada e calcula as áreas para o cubo e o quadrado. Ele também aceita a área como uma entrada e calcula o lado correspondente para o cubo e o quadrado.  
  
 [!code-csharp[csProgGuideProperties#6](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_12.cs)]  
  
## <a name="see-also"></a>Consulte também  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Propriedades](../../../csharp/programming-guide/classes-and-structs/properties.md)  
 [Propriedades de interface](../../../csharp/programming-guide/classes-and-structs/interface-properties.md)  
 [Propriedades Autoimplementadas](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md)
