---
title: "Usando propriedades (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "acessador get [C#]"
  - "propriedades [C#], sobre propriedades"
  - "acessador set [C#]"
ms.assetid: f7f67b05-0983-4cdb-96af-1855d24c967c
caps.latest.revision: 24
caps.handback.revision: 24
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Usando propriedades (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Propriedades de combinam os aspectos de métodos e campos.  Para o usuário de um objeto, uma propriedade parece ser um campo, acessando a propriedade requer a mesma sintaxe.  Para o implementador de uma classe, uma propriedade é um ou dois blocos de código, representando um  [obter](../../../csharp/language-reference/keywords/get.md) acessador e\/ou um  [Definir](../../../csharp/language-reference/keywords/set.md) acessador.  O bloco de código para o `get` o acessador é executado quando a propriedade é leitura; o bloco de código para o `set` o acessador é executado quando a propriedade é atribuída um novo valor.  Uma propriedade sem um `set` o acessador é considerado somente leitura.  Uma propriedade sem um `get` o acessador é considerado somente para gravação.  Uma propriedade que possui os acessadores é leitura\-gravação.  
  
 Ao contrário dos campos, propriedades não são classificadas como variáveis.  Portanto, você não pode passar uma propriedade como um [ref](../../../csharp/language-reference/keywords/ref.md) ou [out](../../../csharp/language-reference/keywords/out.md) parâmetro.  
  
 Propriedades têm muitos usos: eles podem validar dados antes de permitir que uma alteração; modo transparente, eles podem expor dados em uma classe onde esses dados são recuperados, na verdade, a partir de outra fonte, como, por exemplo, um banco de dados; eles podem executar uma ação quando dados são alterados, como disparar um evento ou alterar o valor de outros campos.  
  
 Propriedades são declaradas no bloco de classe, especificando o nível de acesso do campo, seguidas do tipo da propriedade, seguidas do nome da propriedade e seguidas de um bloco de código que declara um `get`\-assessor e\/ou um `set` acessador.  Por exemplo:  
  
 [!code-cs[csProgGuideProperties#7](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_1.cs)]  
  
 Neste exemplo, `Month` é declarada como uma propriedade assim que o `set` acessador pode Certifique\-se de que o `Month` valor é definido entre 1 e 12.  O `Month` propriedade utiliza um campo privado para acompanhar o valor real.  O local real dos dados de uma propriedade é conhecido como "fazendo o armazenamento" a definição da propriedade. É comum para as propriedades usar campos particulares, como um armazenamento de backup.  O campo será marcado como particular para certificar\-se de que ele só pode ser alterado chamando a propriedade.  Para obter mais informações sobre restrições de acesso público e particular, consulte [Modificadores de acesso](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
 Propriedades de auto\-implementado fornecem sintaxe simplificada para declarações de propriedade simples.  Para obter mais informações, consulte [Propriedades autoimplementadas](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).  
  
## O acessador get  
 O corpo da `get` acessador semelhante ao de um método.  Ele deve retornar um valor do tipo de propriedade.  A execução da `get` o acessador é equivalente ao ler o valor do campo.  Por exemplo, quando você retornar a variável private da `get` acessador e otimizações forem ativadas, a chamada para o `get` método do acessador estiver embutido pelo compilador, portanto não há nenhuma sobrecarga de chamada de método.  No entanto, um virtual `get` método do acessador não pode ser embutido porque o compilador não sabe em qual método, na verdade, pode ser chamado em tempo de execução de tempo de compilação.  A seguir está uma `get` acessador retorna o valor de um campo particular `name`:  
  
 [!code-cs[csProgGuideProperties#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_2.cs)]  
  
 Quando você faz referência a propriedade, exceto quando o destino de uma atribuição, o `get` o acessador é invocado para ler o valor da propriedade.  Por exemplo:  
  
 [!code-cs[csProgGuideProperties#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_3.cs)]  
  
 O `get` acessador deve terminar em um  [retornar](../../../csharp/language-reference/keywords/return.md) ou  [lança](../../../csharp/language-reference/keywords/throw.md) instrução e controle não podem fluir fora do corpo do acessador.  
  
 É um estilo de programação ruim para alterar o estado do objeto usando o `get` acessador.  Por exemplo, o acessador seguir produz o efeito colateral de alterar o estado do objeto sempre que o `number` campo é acessado.  
  
 [!code-cs[csProgGuideProperties#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_4.cs)]  
  
 O `get` acessador pode ser usado para retornar o valor do campo ou para computá\-lo e devolvê\-lo.  Por exemplo:  
  
 [!code-cs[csProgGuideProperties#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_5.cs)]  
  
 No segmento de código anterior, se você não atribuir um valor para o `Name` propriedade, ela retornará o valor NA.  
  
## O conjunto de acessador  
 O `set` o acessador é semelhante a um método cujo tipo de retorno é  [void](../../../csharp/language-reference/keywords/void.md).  Ele usa um parâmetro implícito chamado `value`, cujo tipo é o tipo da propriedade.  No exemplo a seguir, um `set` acessador é adicionado para o `Name` propriedade:  
  
 [!code-cs[csProgGuideProperties#12](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_6.cs)]  
  
 Quando você atribui um valor à propriedade, o `set` o acessador é chamado usando\-se um argumento que fornece o novo valor.  Por exemplo:  
  
 [!code-cs[csProgGuideProperties#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_7.cs)]  
  
 É um erro para usar o nome do parâmetro implícito, `value`, para uma declaração de variável local em um `set` acessador.  
  
## Comentários  
 Properties can be marked as `public`, `private`, `protected`, `internal`, or `protected internal`.  Esses modificadores de acesso definem como os usuários da classe podem acessar a propriedade.  O `get` e `set` acessadores para a mesma propriedade podem ter modificadores de acesso diferentes.  Por exemplo, o `get` pode ser `public` para permitir o acesso de leitura e de fora o tipo e o `set` pode ser `private` ou `protected`.  Para obter mais informações, consulte [Modificadores de acesso](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
 Uma propriedade pode ser declarada como uma propriedade estática usando o `static` palavra\-chave.  Isso torna a propriedade disponível para chamadores a qualquer momento, mesmo que exista nenhuma ocorrência da classe.  Para obter mais informações, consulte [Classes static e membros de classes static](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
 Uma propriedade pode ser marcada como uma propriedade virtual usando o  [virtual](../../../csharp/language-reference/keywords/virtual.md) palavra\-chave.  Isso permite que as classes derivadas substituir o comportamento de propriedade usando o  [Substituir](../../../csharp/language-reference/keywords/override.md) palavra\-chave.  Para obter mais informações sobre essas opções, consulte [Herança](../../../csharp/programming-guide/classes-and-structs/inheritance.md).  
  
 Uma propriedade de substituição de uma propriedade virtual também pode ser  [lacrado](../../../csharp/language-reference/keywords/sealed.md), especificando que para classes derivadas não é mais virtual.  Por fim, uma propriedade pode ser declarada  [abstrata](../../../csharp/language-reference/keywords/abstract.md).  Isso significa que não há nenhuma implementação na classe e classes derivadas devem escrever sua própria implementação.  Para obter mais informações sobre essas opções, consulte [Classes e membros de classes abstract e sealed](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
> [!NOTE]
>  É errado usar uma [virtual](../../../csharp/language-reference/keywords/virtual.md), [abstract](../../../csharp/language-reference/keywords/abstract.md), ou [override](../../../csharp/language-reference/keywords/override.md) modificador em um acessador de um  [estático](../../../csharp/language-reference/keywords/static.md) propriedade.  
  
## Exemplo  
 Este exemplo demonstra as propriedades de instância, estática e somente leitura.  Ele aceita o nome do funcionário do teclado, incrementos `NumberOfEmployees` por 1 e exibe o funcionário de nome e número.  
  
 [!code-cs[csProgGuideProperties#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_8.cs)]  
  
## Exemplo  
 Este exemplo demonstra como acessar uma propriedade na classe base que está ocultos por outra propriedade que tem o mesmo nome em uma classe derivada.  
  
 [!code-cs[csProgGuideProperties#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_9.cs)]  
  
 Estes são os pontos importantes no exemplo anterior:  
  
-   A propriedade `Name` na classe derivada oculta a propriedade `Name` na classe base.  Nesse caso, o `new` modificador é usado na declaração da propriedade na classe derivada:  
  
     [!code-cs[csProgGuideProperties#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_10.cs)]  
  
-   A projeção `(Employee)` é usado para acessar a propriedade oculta na classe base:  
  
     [!code-cs[csProgGuideProperties#5](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_11.cs)]  
  
     Para obter mais informações sobre como ocultar membros, consulte a [Modificador new](../../../csharp/language-reference/keywords/new-modifier.md).  
  
## Exemplo  
 Neste exemplo, duas classes, `Cube` e `Square`, implementar uma classe abstrata, `Shape`e substituir seu resumo `Area` propriedade.  Observe o uso da  [Substituir](../../../csharp/language-reference/keywords/override.md) modificador nas propriedades.  O programa aceita o lado como entrada e calcula as áreas para o quadrado e cubo.  Ele também aceita a área como entrada e calcula o lado correspondente para o quadrado e cubo.  
  
 [!code-cs[csProgGuideProperties#6](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_12.cs)]  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Propriedades](../../../csharp/programming-guide/classes-and-structs/properties.md)   
 [Propriedades de interface](../../../csharp/programming-guide/classes-and-structs/interface-properties.md)   
 [Propriedades autoimplementadas](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md)