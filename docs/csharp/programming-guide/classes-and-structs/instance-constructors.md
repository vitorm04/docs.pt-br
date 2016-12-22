---
title: "Construtores de inst&#226;ncias (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
  - "construtores [C#], construtores de instância"
  - "construtores de instância [C#]"
ms.assetid: 24663779-c1e5-4af4-a942-ca554e4c542d
caps.latest.revision: 26
caps.handback.revision: 26
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Construtores de inst&#226;ncias (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Construtores de instância são usados para criar e inicializar variáveis de membro qualquer instância quando você usa o  [nova](../../../csharp/language-reference/keywords/new.md) a expressão para criar um objeto de um  [classe](../../../csharp/language-reference/keywords/class.md).  Para inicializar um  [estático](../../../csharp/language-reference/keywords/static.md) classe ou variáveis estáticas em uma classe não\-estático, você deve definir um construtor estático.  Para obter mais informações, consulte [Construtores estáticos](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).  
  
 O exemplo a seguir mostra um construtor de instância:  
  
 [!code-cs[csProgGuideObjects#5](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_1.cs)]  
  
> [!NOTE]
>  Para maior clareza, essa classe contém campos públicos.  O uso de campos públicos não é uma prática recomendada de programação, pois permite que qualquer método em qualquer lugar em um programa irrestrito e sem a verificação de acesso ao funcionamento interno de um objeto.  Membros de dados costuma ser particulares e devem ser acessados apenas por meio de propriedades e métodos da classe.  
  
 Este construtor de instância é chamado sempre que um objeto se baseia o `CoOrds` classe é criada.  Um construtor como esta, que leva sem argumentos, será chamado de um  *construtor padrão*.  No entanto, muitas vezes é útil fornecer construtores adicionais.  Por exemplo, podemos adicionar um construtor para o `CoOrds` classe que nos permite especificar os valores iniciais para os membros de dados:  
  
 [!code-cs[csProgGuideObjects#76](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_2.cs)]  
  
 Isso permite que `CoOrd` objetos a serem criados com padrão ou valores iniciais específicos, como este:  
  
 [!code-cs[csProgGuideObjects#77](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_3.cs)]  
  
 Se uma classe não tem um construtor, um construtor padrão é gerado automaticamente e os valores padrão serão usados para inicializar os campos do objeto.  Por exemplo, um  [int](../../../csharp/language-reference/keywords/int.md) é inicializado para 0.  Para obter mais informações sobre valores padrão, consulte [Tabela de valores padrão](../../../csharp/language-reference/keywords/default-values-table.md).  Portanto, porque o `CoOrds` construtor padrão da classe inicializa todos os membros de dados para zero, pode ser totalmente removido sem alterar o funcionamento da classe.  Um exemplo completo usando vários construtores é fornecido no exemplo 1, posteriormente neste tópico, e um exemplo de um construtor gerado automaticamente é fornecido no exemplo 2.  
  
 Construtores de instância também podem ser usados para chamar os construtores de instância de classes base.  O construtor da classe pode chamar o construtor da classe base através do inicializador, da seguinte maneira:  
  
 [!code-cs[csProgGuideObjects#78](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_4.cs)]  
  
 Neste exemplo, o `Circle` classe passa os valores que representam o radius e a altura para o construtor fornecido por `Shape` do qual `Circle` é derivado.  Um exemplo completo usando `Shape` e `Circle` aparece nesse tópico como exemplo 3.  
  
## Exemplo 1  
 O exemplo a seguir demonstra uma classe com construtores de classe dois um sem argumentos e com dois argumentos.  
  
 [!code-cs[csProgGuideObjects#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_5.cs)]  
  
## Exemplo 2  
 Neste exemplo, a classe `Person` não tem qualquer construtores, nesse caso, um construtor padrão é fornecido automaticamente e os campos são inicializados para seus valores padrão.  
  
 [!code-cs[csProgGuideObjects#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_6.cs)]  
  
 Observe que o valor padrão de `age` é `0` e o valor padrão de `name` é `null`.  Para obter mais informações sobre valores padrão, consulte [Tabela de valores padrão](../../../csharp/language-reference/keywords/default-values-table.md).  
  
## Exemplo 3  
 O exemplo a seguir demonstra o uso de inicializador de classe base.  O `Circle` classe é derivada da classe geral `Shape`e o `Cylinder` classe é derivada da `Circle` classe.  O construtor em cada classe derivada está usando seu inicializador de classe base.  
  
 [!code-cs[csProgGuideObjects#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_7.cs)]  
  
 Para obter mais exemplos sobre como chamar os construtores de classe base, consulte [virtual](../../../csharp/language-reference/keywords/virtual.md), [override](../../../csharp/language-reference/keywords/override.md), e [base](../../../csharp/language-reference/keywords/base.md).  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Classes e structs](../../../csharp/programming-guide/classes-and-structs/index.md)   
 [Construtores](../../../csharp/programming-guide/classes-and-structs/constructors.md)   
 [Destruidores](../../../csharp/programming-guide/classes-and-structs/destructors.md)   
 [static](../../../csharp/language-reference/keywords/static.md)