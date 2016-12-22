---
title: "Passando par&#226;metros de tipo de refer&#234;ncia (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
  - "parâmetros de método [C#], tipos de referência"
  - "parâmetros [C#], referência"
ms.assetid: 9e6eb65c-942e-48ab-920a-b7ba9df4ea20
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Passando par&#226;metros de tipo de refer&#234;ncia (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Uma variável de um  [tipo de referência](../../../csharp/language-reference/keywords/reference-types.md) não contém seus dados diretamente. Ele contém uma referência a seus dados.  Quando você passa um parâmetro de tipo de referência por valor, é possível alterar os dados apontados por referência, como, por exemplo, o valor de um membro da classe.  No entanto, você não pode alterar o valor da referência propriamente dito; ou seja, você não pode usar a mesma referência alocar memória para uma nova classe e ainda persistem fora do bloco.  Para isso, passe o parâmetro usando o  [ref](../../../csharp/language-reference/keywords/ref.md) ou  [check\-out](../../../csharp/language-reference/keywords/out.md) palavra\-chave.  Para simplificar, os exemplos seguintes usam `ref`.  
  
## Tipos de referência de passagem por valor  
 O exemplo a seguir demonstra a passar um parâmetro de tipo de referência, `arr`, por valor, para um método, `Change`.  Porque o parâmetro é uma referência a `arr`, é possível alterar os valores dos elementos de matriz.  No entanto, a tentativa de reatribuir o parâmetro para um local de memória diferentes só funciona dentro do método e não afeta a variável original, `arr`.  
  
 [!code-cs[csProgGuideParameters#7](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-reference-type-parameters_1.cs)]  
  
 No exemplo anterior, a matriz, `arr`, que é um tipo de referência é passado para o método sem o `ref` parâmetro.  Nesse caso, uma cópia da referência, que aponta para `arr`, é passado para o método.  A saída mostra que é possível para o método alterar o conteúdo de um elemento de matriz, nesse caso, de `1` para `888`.  No entanto, alocar uma nova parte da memória usando o  [nova](../../../csharp/language-reference/keywords/new.md) operador dentro a `Change` método torna a variável `pArray` fazer referência a uma nova matriz.  Portanto, quaisquer alterações depois que isso não afetará a matriz original, `arr`, que é criado dentro de `Main`.  Na verdade, duas matrizes são criadas neste exemplo, um interno `Main` e um dentro do `Change` método.  
  
## Tipos de referência de passagem por referência  
 O exemplo a seguir é o mesmo do exemplo anterior, exceto que o `ref` palavra\-chave é adicionada ao cabeçalho do método e chamada.  Quaisquer alterações que ocorrem no método afetam a variável original no programa de chamada.  
  
 [!code-cs[csProgGuideParameters#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-reference-type-parameters_2.cs)]  
  
 Todas as alterações que ocorrem dentro do método afetam a matriz original em `Main`.  Na verdade, a matriz original é realocada em usando o `new` operador.  Assim, depois de chamar o `Change` método, qualquer referência aos `arr` aponta para a matriz de cinco elementos, o que é criada na `Change` método.  
  
## Trocando duas seqüências de caracteres  
 Troca de seqüências de caracteres é um bom exemplo de passar os parâmetros de tipo de referência por referência.  No exemplo, duas seqüências de caracteres, `str1` e `str2`, são inicializados em `Main` e passado para o `SwapStrings` o método como parâmetros modificado pela `ref` palavra\-chave.  As duas seqüências são trocadas dentro do método e interior `Main` também.  
  
 [!code-cs[csProgGuideParameters#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-reference-type-parameters_3.cs)]  
  
 Neste exemplo, os parâmetros precisam ser passados por referência para afetar as variáveis no programa de chamada.  Se você remover o `ref` palavra\-chave do cabeçalho do método e a chamada do método, nenhuma alteração ocorrerá no programa de chamada.  
  
 Para obter mais informações sobre seqüências de caracteres, consulte  [seqüência de caracteres](../../../csharp/language-reference/keywords/string.md).  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Passando parâmetros](../../../csharp/programming-guide/classes-and-structs/passing-parameters.md)   
 [Passando matrizes com o uso de ref e out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md)   
 [ref](../../../csharp/language-reference/keywords/ref.md)   
 [Tipos de referência](../../../csharp/language-reference/keywords/reference-types.md)