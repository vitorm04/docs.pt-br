---
title: "No&#231;&#245;es b&#225;sicas de cadeias de caracteres no Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "cadeias de caracteres {Visual Basic], Operador Like"
  - "cadeias de caracteres {Visual Basic], expressões regulares"
  - "cadeias de caracteres {Visual Basic], Visual Basic"
ms.assetid: 5674418d-f00d-4f72-9f98-d15897793350
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# No&#231;&#245;es b&#225;sicas de cadeias de caracteres no Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

O `String` tipo de dados representa uma série de caracteres \(cada representando por sua vez uma instância das `Char` tipo de dados\).  Este tópico apresenta os conceitos básicos de cadeias de caracteres em [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
## Variáveis de cadeia de caracteres  
 Uma instância de uma cadeia de caracteres pode ser atribuída um valor literal que representa uma seqüência de caracteres.  Por exemplo:  
  
 [!code-vb[VbVbalrStrings#63](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_1.vb)]  
  
 Um `String` variável também pode aceitar qualquer expressão avaliada como uma cadeia de caracteres.  Exemplos são mostrados abaixo:  
  
 [!code-vb[VbVbalrStrings#64](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_2.vb)]  
  
 Qualquer literal que é atribuído a um `String` variável deve ser colocado entre aspas \(""\).  Isso significa que aspas dentro de uma cadeia de caracteres não pode ser representada por aspas.  Por exemplo, o código a seguir causa um erro do compilador:  
  
 [!code-vb[VbVbalrStrings#65](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_3.vb)]  
  
 Esse código causa um erro porque o compilador termina a string após a segunda aspas, e o restante da cadeia de caracteres é interpretado como código.  Para resolver esse problema, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] interpreta duas aspas em uma cadeia de caracteres literal como uma aspas na cadeia de caracteres.  O exemplo a seguir demonstra a maneira correta de incluir aspas em uma cadeia de caracteres:  
  
 [!code-vb[VbVbalrStrings#66](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_4.vb)]  
  
 No exemplo anterior, as duas aspas antes da palavra `Look` se tornam uma aspas na cadeia de caracteres.  As três aspas no final da linha representam uma aspas na cadeia de caracteres e o caractere de terminação de cadeia de caracteres.  
  
 Literais de cadeia de caracteres podem conter várias linhas:  
  
```vb  
Dim x = "hello  
world"  
  
```  
  
 A cadeia de caracteres resultante contém sequências de nova linha que você usou em sua cadeia de caracteres literal \(vbcr, vbcrlf, etc.\).  Você não precisa usar a solução antiga:  
  
```vb  
Dim x = <xml><![CDATA[Hello  
World]]></xml>.Value  
  
```  
  
## Caracteres em cadeias de caracteres  
 Uma cadeia de caracteres pode ser pensada como uma série de `Char` valores e o `String` tipo tem funções internas que permitem que você execute muitas manipulações em uma cadeia de caracteres parecidas com as manipulações permitidas por arrays.  Como todos os arrays no [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)], esses são arrays baseados em zero.  Você pode se referir a um caractere específico em uma cadeia de caracteres por meio do `Chars` propriedade, que fornece uma maneira de acessar um caractere pela posição em que aparece na cadeia de caracteres.  Por exemplo:  
  
 [!code-vb[VbVbalrStrings#67](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_5.vb)]  
  
 No exemplo acima, os `Chars` propriedade da cadeia de caracteres retorna o quarto caractere na cadeia de caracteres, que é `D`, e a atribui `myChar`.  Você também pode obter o comprimento de uma cadeia de caracteres específica por meio do `Length` propriedade.  Se você precisar executar várias manipulações de tipo de matriz em uma cadeia de caracteres, você pode convertê\-la em uma matriz de `Char` instâncias usando o `ToCharArray` função da cadeia de caracteres.  Por exemplo:  
  
 [!code-vb[VbVbalrStrings#68](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_6.vb)]  
  
 A variável `myArray` agora contém uma matriz de `Char` valores, cada um representando um caractere de `myString`.  
  
## A imutabilidade de cadeias de caracteres  
 Uma cadeia de caracteres *imutáveis*, que significa que seu valor não pode ser alterado quando ela foi criada.  No entanto, isso não impede que você atribua mais de um valor a uma variável de cadeia de caracteres.  Considere o exemplo a seguir:  
  
 [!code-vb[VbVbalrStrings#69](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_7.vb)]  
  
 Aqui, uma variável de cadeia de caracteres é criada, dado um valor, e, em seguida, seu valor é alterado.  
  
 Mais especificamente, na primeira linha, uma instância do tipo `String` é criada e receberá o valor `This string is immutable`.  Na segunda linha do exemplo, uma nova instância é criada e receberá o valor `Or is it?`, e a variável de cadeia de caracteres descarta sua referência para a primeira instância e armazena uma referência para a nova instância.  
  
 Diferentemente de outros tipos de dados intrínsecos, `String` é um tipo de referência.  Quando uma variável de tipo de referência é passada como um argumento para uma função ou sub\-rotina, uma referência para o endereço de memória onde os dados são armazenados é passada em vez do valor real da cadeia de caracteres.  No exemplo anterior, o nome da variável permanece o mesmo, mas ela aponta para uma instância nova e diferente de `String` classe, que contém o novo valor.  
  
## Consulte também  
 [Introdução a cadeias de caracteres no Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)   
 [Tipo de dados da cadeia de caracteres](../../../../visual-basic/language-reference/data-types/string-data-type.md)   
 [Tipo de dados Char](../../../../visual-basic/language-reference/data-types/char-data-type.md)   
 [Operações básicas de cadeias de caracteres](../Topic/Basic%20String%20Operations%20in%20the%20.NET%20Framework.md)