---
title: "Restri&#231;&#245;es a par&#226;metros de tipo (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
  - "genéricos [C#], restrições de tipo"
  - "restrições de tipo [C#]"
  - "parâmetros de tipo [C#], restrições"
  - "parâmetro de tipo não associado [C#]"
ms.assetid: 141b003e-1ddb-4e1c-bcb2-e1c3870e6a51
caps.latest.revision: 41
caps.handback.revision: 41
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Restri&#231;&#245;es a par&#226;metros de tipo (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Quando você define uma classe genérico, você pode aplicar restrições para os tipos de tipos que código de cliente pode usar para argumentos Tipo quando ele instancia sua classe.  Se o código do cliente tenta instanciar sua classe usando um tipo que não é permitido por uma restrição, o resultado é um erro de tempo de compilação.  Essas restrições são chamadas restrições.  As restrições são especificadas usando o `where` palavra\-chave contextual.  A tabela a seguir lista os seis tipos de restrições :  
  
|Restrição|Descrição|  
|---------------|---------------|  
|where T: struct|O argumento Tipo deve ser um tipo de valor.  Qualquer tipo, com exceção do valor <xref:System.Nullable> pode ser especificado.  Consulte [Usando tipos anuláveis](../../../csharp/programming-guide/nullable-types/using-nullable-types.md) para obter mais informações.|  
|where T: class|O argumento de tipo deve ser um tipo de referência; Isso se aplica também a qualquer classe, interface, representante ou tipo de matriz.|  
|where T: New\(\)|O argumento Tipo deve ter um construtor sem\-parâmetros público.  Quando usado em conjunto com outras restrições, o `new()` restrição deve ser especificada pela última vez.|  
|onde basear: \< t nome da classe \>|O argumento Tipo deve ser ou derivar de classe base especificada.|  
|onde T: \< nome da interface \>|O argumento Tipo deve ser ou implementam a interface especificada.  Várias restrições interface podem ser especificadas.  A interface restrições também pode ser genérica.|  
|where T: U|O argumento de tipo fornecido para t deve ser ou derivar o argumento fornecido para u.|  
  
## Por que usar restrições  
 Se você desejar examinar um item em uma lista genérica para determinar se é válido ou compará\-lo com algum outro item, o compilador deve ter alguns garante que o operador ou o método que ele precisa chamar terá suporte por qualquer argumento de tipo que pode ser especificado pelo código do cliente.  ESTA GARANTIA é obtida ao aplicar uma ou mais restrições para a definição de classe genérico.  Por exemplo, a restrição classe base informa o compilador que somente objetos desse tipo ou derivado desse tipo será usado como argumentos Tipo.  Depois que o compilador não tem essa garantia, ele pode permitir que os métodos desse tipo a ser chamado na classe genérica.  Restrições são aplicadas usando a palavra\-chave contextual `where`.  O exemplo de código a seguir demonstra a funcionalidade que adicionamos para o `GenericList<T>` classe \(em [Introdução aos genéricos](../../../csharp/programming-guide/generics/introduction-to-generics.md)\), aplicando uma restrição de classe base.  
  
 [!code-cs[csProgGuideGenerics#11](../../../csharp/programming-guide/generics/codesnippet/CSharp/constraints-on-type-parameters_1.cs)]  
  
 A restrição permite que a classe genérica usar o `Employee.Name` propriedade porque todos os itens do tipo t são garantidos como um `Employee` objeto ou um objeto que herda de `Employee`.  
  
 Várias restrições podem ser aplicadas para o mesmo parâmetro, tipo e as restrições próprios podem ser tipos genéricos, da seguinte forma:  
  
 [!code-cs[csProgGuideGenerics#12](../../../csharp/programming-guide/generics/codesnippet/CSharp/constraints-on-type-parameters_2.cs)]  
  
 Restringindo o parâmetro de tipo, você aumentar o número de operações permitidas e chamadas de método aos quais o tipo de restrições e todos os tipos na sua hierarquia de herança.  Portanto, quando você cria classes genéricas ou métodos, se você irá realizar qualquer operação nos membros genéricos além da atribuição simples ou chamar quaisquer métodos não suportados pelo `System.Object`, você terá que aplicar restrições para o parâmetro de tipo.  
  
 Ao aplicar o `where T : class` restrição, evitar a `==` e `!=` operadores no parâmetro de tipo porque esses operadores serão testado quanto a identidade da referência apenas, não para a igualdade do valor.  Esse é o caso mesmo se esses operadores são sobrecarregados em um tipo que é usado como um argumento.  O código a seguir ilustra este ponto; a saída é false mesmo que o <xref:System.String> sobrecargas de classe a `==` operador.  
  
 [!code-cs[csProgGuideGenerics#13](../../../csharp/programming-guide/generics/codesnippet/CSharp/constraints-on-type-parameters_3.cs)]  
  
 A razão para esse comportamento é que, ao tempo de compilação, o compilador somente sabe que T é um tipo de referência, e portanto deve utilizar os operadores padrão que são válidos para todos os tipos de referência.  Se você deve testar a igualdade do valor, a maneira recomendada é também se aplicam a `where T : IComparable<T>` restrição e implementar a interface em qualquer classe que será usado para construir a classe genérica.  
  
## A restrição de vários parâmetros  
 Você pode aplicar restrições para vários parâmetros e várias restrições para um único parâmetro, conforme mostrado no exemplo a seguir:  
  
 [!code-cs[csProgGuideGenerics#64](../../../csharp/programming-guide/generics/codesnippet/CSharp/constraints-on-type-parameters_4.cs)]  
  
## Unbounded parâmetros tipo  
 Parâmetros tipo que têm sem restrições, como T na classe `SampleClass<T>{}` pública, são chamados parâmetros tipo unbounded.  Parâmetros tipo unbounded ter as seguintes regras:  
  
-   O `!=` e `==` operadores não podem ser usados porque não há nenhuma garantia de que o argumento do tipo concreto suportará esses operadores.  
  
-   Pode ser convertidos de e para `System.Object` ou explicitamente convertido para qualquer tipo de interface.  
  
-   Você pode comparar e  [Nulo](../../../csharp/language-reference/keywords/null.md).  Se um parâmetro não vinculado é comparado ao `null`, a comparação sempre retornará false se o argumento de tipo é um tipo de valor.  
  
## Parâmetros de tipo como restrições  
 O uso de um parâmetro de tipo genérico como uma restrição é útil quando uma função de membro com o seu próprio tipo de parâmetro possui que restringir esse parâmetro para o parâmetro de tipo do tipo recipiente, como mostrado no exemplo a seguir:  
  
 [!code-cs[csProgGuideGenerics#14](../../../csharp/programming-guide/generics/codesnippet/CSharp/constraints-on-type-parameters_5.cs)]  
  
 No exemplo anterior, `T` é uma restrição de tipo no contexto da `Add` método e no contexto de um parâmetro de tipo não vinculado a `List` classe.  
  
 Parâmetros de tipo também podem ser utilizados como restrições nas definições de classe genérica.  Observe que o parâmetro de tipo deve ser declarado nos colchetes junto com quaisquer outros parâmetros de tipo:  
  
 [!code-cs[csProgGuideGenerics#15](../../../csharp/programming-guide/generics/codesnippet/CSharp/constraints-on-type-parameters_6.cs)]  
  
 A utilidade dos parâmetros de tipo como restrições de classes genéricas é muito limitada porque o compilador pode assumir nada sobre o parâmetro de tipo, exceto que ela deriva de `System.Object`.  Use os parâmetros de tipo como restrições de classes genéricas em cenários em que você deseja impor um relacionamento de herança entre dois parâmetros de tipo.  
  
## Consulte também  
 <xref:System.Collections.Generic>   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Introdução aos genéricos](../../../csharp/programming-guide/generics/introduction-to-generics.md)   
 [Classes genéricas](../../../csharp/programming-guide/generics/generic-classes.md)   
 [Restrição new](../../../csharp/language-reference/keywords/new-constraint.md)