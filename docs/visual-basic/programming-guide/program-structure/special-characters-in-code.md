---
title: "Caracteres especiais no c&#243;digo (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.)"
  - "vb.("
  - "vb.colon"
  - "vb.!"
  - "vb.."
  - "vb.:"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Operador !"
  - "Operador ."
  - "caractere separador :"
  - "Operador de adição"
  - "dois-pontos (:)"
  - "operadores de concatenação, caracteres especiais no código"
  - "operadores de concatenação, x Operador de adição"
  - "Operador de acesso a dicionário"
  - "Operador ponto (.)"
  - "Operador ponto de exclamação (!)"
  - "pontos de exclamação"
  - "Operador de acesso a membros"
  - "operadores [Visual Basic], acesso a dicionário"
  - "operadores [Visual Basic], acesso de membro"
  - "parênteses, uso em código"
  - "caractere ponto no código"
  - "separadores"
  - "separadores, uso em código"
  - "caracteres especiais, código in"
  - "código do Visual Basic, caracteres especiais"
ms.assetid: 310dce0c-45b5-4e0d-83e9-32df258d2a3e
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Caracteres especiais no c&#243;digo (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Às vezes você tem que usar caracteres especiais em seu código, ou seja, caracteres que são não em ordem alfabética ou numérica.  A pontuação e caracteres especiais no conjunto de caracteres do [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] têm vários usos, de texto do programa de organização a definir as tarefas que executa o compilador ou o programa compilado.  Eles não especificam uma operação a ser executada.  
  
## Parênteses.  
 Use parênteses quando você define um procedimento, como `Sub` ou `Function`.  Você deverá colocar todas as listas de argumentos de procedimentos entre parênteses.  Você também usar parênteses para colocar as variáveis ou argumentos em grupos lógicos, especialmente para substituir a ordem de padrão de precedência do operador em uma expressão complexa.  O exemplo a seguir ilustra isto:  
  
 [!code-vb[VbVbcnConventions#11](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/special-characters-in-code_1.vb)]  
  
 Após a execução do código anterior, o valor de `d` é 8.225 e o valor de `e` é 3.  O cálculo para `d` usa a precedência padrão de `/` em `+` e é equivalente a `d = b + (c / a)`.  Os parênteses no cálculo de `e` substituem a precedência padrão.  
  
## Separadores  
 Separadores fazem o que seu nome sugere: separar seções de código.  Em [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], o caractere separador é dois\-pontos \(`:`\).  Use separadores quando você deseja incluir várias declarações em uma única linha em vez de linhas separadas.  Isso economiza espaço e melhora a legibilidade do código.  O exemplo a seguir mostra três instruções separadas por vírgulas.  
  
 [!code-vb[VbVbcnConventions#12](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/special-characters-in-code_2.vb)]  
  
 Para obter mais informações, consulte [Como quebrar e combinar instruções no código](../Topic/How%20to:%20Break%20and%20Combine%20Statements%20in%20Code%20\(Visual%20Basic\).md).  
  
 Os dois\-pontos \(`:`\) caracteres também é usado para identificar um rótulo de instrução.  Para obter mais informações, consulte [Como rotular instruções](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).  
  
## Concatenação  
 Use o operador `&` para  *concatenação* , ou vinculando sequências de caracteres juntos.  Não o confunda com o operador `+`, que adiciona juntos valores numéricos.  Se você usar o operador `+` para concatenar quando você opera em valores numéricos, você pode obter resultados incorretos.  O exemplo a seguir demonstra isso.  
  
 [!code-vb[VbVbcnConventions#13](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/special-characters-in-code_3.vb)]  
  
 Após a execução do código anterior, o valor de `resultA` é 21.01 e o valor de `resultB` é "10.0111".  
  
## Operadores de Acesso a Membros  
 Para acessar um membro de um tipo, você usar o ponto \(`.`\) ou operador ponto de exclamação \(`!`\) entre o nome do tipo e o nome do membro.  
  
### Ponto \(.\) Operador  
 Use o operador `.` em uma classe, estrutura, interface ou enumeração como um membro de acesso do operador.  O membro pode ser um campo, propriedade, evento ou método.  O exemplo a seguir ilustra isto:  
  
 [!code-vb[VbVbcnConventions#14](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/special-characters-in-code_4.vb)]  
  
### Ponto de exclamação \(\!\) Operador  
 Use o operador `!` apenas em uma classe ou interface como um operador de acesso de dicionário.  A classe ou interface deve ter uma propriedade padrão que aceita um único argumento `String`.  O identificador imediatamente após o operador `!` se torna o argumento valor passado para a propriedade padrão como uma sequência de caracteres.  O exemplo a seguir demonstra isso.  
  
 [!code-vb[VbVbcnConventions#15](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/special-characters-in-code_5.vb)]  
  
 As linhas de saída três de `MsgBox` todas exibem o vaor `32856`.  A primeira linha usa o acesso a propriedade `index` tradicional, o segundo faz uso do fato que `index` é a propriedade padrão da classe `hasDefault`,e o terceiro usa dicionário acesso à classe.  
  
 Observe que o segundo operando do operador `!` deve ser um identificador válido Visual Basic não entre aspas duplas \(`" "`\) .  Em outras palavras, você não pode usar um sequência de caracteres literal ou sequência de caracteres variável.  A seguinte alteração para a última linha da chamada `MsgBox` gera um erro porque `"X"` é um literal de string.  
  
 `"Dictionary access returns " & hD!"X")`  
  
> [!NOTE]
>  As referências às coleções padrão devem ser explícitas.  Em particular, você não pode usar o operador `!` em uma variável com ligação tardia.  
  
 O caractere `!` também é usado como o caractere de tipo. `Single` .  
  
## Consulte também  
 [Estrutura do programa e convenções de código](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)   
 [Caracteres de tipo](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)