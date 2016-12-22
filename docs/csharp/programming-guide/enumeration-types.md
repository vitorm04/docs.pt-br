---
title: "Tipos de enumera&#231;&#227;o (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "sinalizadores de bits [C#]"
  - "Linguagem C#, enums"
  - "enumerações [C#]"
  - "enums [C#]"
ms.assetid: 64a9b731-9e3c-4336-8a09-018db2aa10b7
caps.latest.revision: 17
caps.handback.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Tipos de enumera&#231;&#227;o (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../csharp/includes/vs2017banner.md)]

Um tipo de enumeração \(também chamado uma enumeração ou enum\) fornece uma maneira eficiente para definir um conjunto de constantes nomeadas inteiro que podem ser atribuídas a uma variável.  Por exemplo, suponha que você precisa definir uma variável cujo valor representa um dia da semana.  Há apenas sete valores descritivos que essa variável armazenará nunca.  Para definir esses valores, você pode usar um tipo de enumeração, que é declarada usando a palavra\-chave de [enum](../../csharp/language-reference/keywords/enum.md) .  
  
 [!code-cs[csProgGuideEnums#1](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_1.cs)]  
  
 Por padrão o tipo subjacente de cada elemento em enum é [int](../../csharp/language-reference/keywords/int.md).  Você pode especificar um outro tipo numérico integral usando dois pontos, conforme mostrado no exemplo anterior.  Para obter uma lista completa de tipos possíveis, consulte [enum \(referência do C\#\)](../../csharp/language-reference/keywords/enum.md).  
  
 Você pode verificar os valores numéricos para o tipo subjacente converter subjacente, como mostra o exemplo a seguir.  
  
```c#  
Days today = Days.Monday;  
int dayNumber =(int)today;  
Console.WriteLine("{0} is day number #{1}.", today, dayNumber);  
  
Months thisMonth = Months.Dec;  
byte monthNumber = (byte)thisMonth;  
Console.WriteLine("{0} is month number #{1}.", thisMonth, monthNumber);  
  
// Output:  
// Monday is day number #1.  
// Dec is month number #11.  
```  
  
 A seguir estão vantagens de usar um enum em vez de um tipo numérico:  
  
-   Você especifica claramente para o código do cliente que os valores são válidas para a variável.  
  
-   Em [!INCLUDE[vsprvs](../../csharp/includes/vsprvs_md.md)], o IntelliSense lista os valores definidos.  
  
 Quando você não especificar os valores dos elementos no enumerador listas, os valores são incrementadas automaticamente por 1.  No exemplo anterior, `Days.Sunday` tem um valor de 0, `Days.Monday` tem um valor de 1, e assim por diante.  Quando você cria um novo objeto de `Days` , terá um valor padrão de `Days.Sunday` \(0\) se você não explicitamente atribui um valor.  Quando você cria um enum, selecione o valor padrão mais lógico e dê\-lhe um valor de zero.  Isso fará com que todos os enum terem aquele valor padrão se não são atribuídos explicitamente um valor quando eles são criados.  
  
 Se `meetingDay` variável é do tipo `Days`, então \(sem uma conversão explícita\) você só pode atribuir um dos valores definidos por `Days`.  E se o dia de reunião for alterado, você pode atribuir um novo valor de `Days` a `meetingDay`:  
  
 [!code-cs[csProgGuideEnums#4](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_2.cs)]  
  
> [!NOTE]
>  É possível atribuir qualquer valor inteiro arbitrário a `meetingDay`.  Por exemplo, esta linha de código não produz um erro: `meetingDay = (Days) 42`.  No entanto, você não deve fazer isso porque a expectativa implícita é que uma variável enum conterá somente um dos valores definidos por enum.  Para atribuir um valor arbitrário a uma variável de um tipo de enumeração é um risco alto para gerar erros.  
  
 Você pode atribuir valores para todos os elementos na lista de enumerador de um tipo de enumeração, e você também pode usar valores calculados:  
  
 [!code-cs[csProgGuideEnums#3](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_3.cs)]  
  
## Tipos de enumeração como sinalizadores de bit  
 Você pode usar um tipo de enumeração para definir sinalizadores de bit, que permite uma instância do tipo de enumeração para armazenar qualquer combinação de valores que são definidos na lista de enumeração.  \(Naturalmente, algumas combinações não podem ser significativos ou permitidas em seu código de programa.\)  
  
 Você cria um enum de sinalizadores de bit aplicando o atributo de <xref:System.FlagsAttribute?displayProperty=fullName> e definindo os valores de forma apropriada para que `AND`, `OR`, `NOT` e as operações bit a bit de `XOR` podem ser executados neles.  Em um bit sinaliza enum, incluem uma constante nomeada com um valor de zero que significa “nenhum parâmetro é definido.” Não de um sinalizador um valor de zero se não significa “nenhum parâmetro é definido”.  
  
 No exemplo, outra versão enum de `Days` , que é chamado `Days2`, é definida.  `Days2` tem o atributo de `Flags` e cada valor seja atribuído a potência próximo maior que 2.  Isso permite que você crie uma variável de `Days2` cujo valor é `Days2.Tuesday` e `Days2.Thursday`.  
  
 [!code-cs[csProgGuideEnums#2](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_4.cs)]  
  
 Para definir um sinalizador em um enum, use o operador bit a bit de `OR` conforme mostrado no exemplo o seguir:  
  
 [!code-cs[csProgGuideEnums#6](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_5.cs)]  
  
 Para determinar se um sinalizador específica está definido, use uma operação bit a bit de `AND` , conforme mostrado no exemplo o seguir:  
  
 [!code-cs[csProgGuideEnums#7](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_6.cs)]  
  
 Para obter mais informações sobre o que considerar quando você define tipos de enumeração com o atributo de <xref:System.FlagsAttribute?displayProperty=fullName> , consulte <xref:System.Enum?displayProperty=fullName>.  
  
## Usando os métodos de System.Enum para descobrir e manipular valores enum  
 Todos os enum são instâncias do tipo de <xref:System.Enum?displayProperty=fullName> .  Você não pode derivar novas classes de <xref:System.Enum?displayProperty=fullName>, mas você pode usar seus métodos para descobrir quais informações sobre e para manipular valores em um enum instância.  
  
 [!code-cs[csProgGuideEnums#5](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_7.cs)]  
  
 Para obter mais informações, consulte <xref:System.Enum?displayProperty=fullName>.  
  
 Você também pode criar um novo método para um enum usando um método de extensão.  Para obter mais informações, consulte [Como criar um novo método para uma enumeração](../../csharp/programming-guide/classes-and-structs/how-to-create-a-new-method-for-an-enumeration.md).  
  
## Capítulo caracterizado book  
 [Mais sobre variáveis](http://go.microsoft.com/fwlink/?LinkId=221230) em [Início Visual C\# 2010](http://go.microsoft.com/fwlink/?LinkId=221214)  
  
## Consulte também  
 <xref:System.Enum?displayProperty=fullName>   
 [Guia de Programação em C\#](../../csharp/programming-guide/index.md)   
 [enum](../../csharp/language-reference/keywords/enum.md)