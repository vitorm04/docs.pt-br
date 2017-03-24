---
title: "Noções básicas no Visual Basic de cadeia de caracteres | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- strings [Visual Basic], Like operator
- strings [Visual Basic], Visual Basic
- strings [Visual Basic], regular expressions
ms.assetid: 5674418d-f00d-4f72-9f98-d15897793350
caps.latest.revision: 14
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: a9475c57f01c78fd5c4e2d2674f22f18ad4772e5
ms.lasthandoff: 03/13/2017

---
# <a name="string-basics-in-visual-basic"></a>Noções básicas de cadeias de caracteres no Visual Basic
O `String` tipo de dados representa uma série de caracteres (cada um representando por sua vez uma instância das `Char` tipo de dados). Este tópico apresenta os conceitos básicos de cadeias de caracteres em [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
## <a name="string-variables"></a>Variáveis de cadeia de caracteres  
 Um valor literal que representa uma sequência de caracteres pode ser atribuída a uma instância de uma cadeia de caracteres. Por exemplo:  
  
 [!code-vb[VbVbalrStrings&#63;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_1.vb)]  
  
 Um `String` variável também pode aceitar qualquer expressão avaliada como uma cadeia de caracteres. São mostrados exemplos abaixo:  
  
 [!code-vb[VbVbalrStrings&#64;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_2.vb)]  
  
 Qualquer literal que é atribuído a um `String` variável deve ser colocada entre aspas (""). Isso significa que aspas dentro de uma cadeia de caracteres não pode ser representada por aspas. Por exemplo, o código a seguir causa um erro do compilador:  
  
 [!code-vb[VbVbalrStrings&#65;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_3.vb)]  
  
 Esse código causa um erro porque o compilador termina a string após a segunda aspas, e o restante da cadeia de caracteres é interpretado como código. Para resolver esse problema, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] interpreta duas aspas em uma cadeia de caracteres literal como uma aspas na cadeia de caracteres. O exemplo a seguir demonstra a maneira correta de incluir aspas em uma cadeia de caracteres:  
  
 [!code-vb[VbVbalrStrings&#66;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_4.vb)]  
  
 No exemplo anterior, as duas aspas antes da palavra `Look` se tornam uma aspas na cadeia de caracteres. As três aspas no final da linha representam uma aspas na string e o caractere de terminação de cadeia de caracteres.  
  
 Literais de cadeia de caracteres podem conter várias linhas:  
  
```vb  
Dim x = "hello  
world"  
  
```  
  
 A cadeia de caracteres resultante contém sequências de nova linha que você usou em sua cadeia de caracteres literal (vbcr, vbcrlf, etc.).  Você não precisa usar a solução antiga:  
  
```vb  
Dim x = <xml><![CDATA[Hello  
World]]></xml>.Value  
  
```  
  
## <a name="characters-in-strings"></a>Caracteres em cadeias de caracteres  
 Uma cadeia de caracteres pode ser pensada como uma série de `Char` valores e o `String` tipo tem funções internas que permitem que você execute muitas manipulações em uma cadeia de caracteres parecidas com as manipulações permitidas por arrays. Como todos os arrays no [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)], esses são arrays baseados em zero. Você pode se referir a um caractere específico em uma cadeia de caracteres por meio de `Chars` property, que fornece uma maneira de acessar um caractere pela posição em que aparece na cadeia de caracteres. Por exemplo:  
  
 [!code-vb[VbVbalrStrings&#67;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_5.vb)]  
  
 No exemplo acima, o `Chars` propriedade da cadeia de caracteres retorna o quarto caractere na cadeia de caracteres, que é `D`e a atribui `myChar`. Você também pode obter o comprimento de uma cadeia de caracteres específica por meio de `Length` propriedade. Se você precisar executar várias manipulações de tipo de matriz em uma cadeia de caracteres, você pode convertê-la em uma matriz de `Char` instâncias usando o `ToCharArray` função da cadeia de caracteres. Por exemplo:  
  
 [!code-vb[VbVbalrStrings&#68;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_6.vb)]  
  
 A variável `myArray` agora contém uma matriz de `Char` valores, cada um representando um caractere de `myString`.  
  
## <a name="the-immutability-of-strings"></a>A imutabilidade de cadeias de caracteres  
 Uma cadeia de caracteres *imutável*, que significa que seu valor não pode ser alterado depois ter sido criado. No entanto, isso não impede que você atribua mais de um valor a uma variável de cadeia de caracteres. Considere o exemplo a seguir:  
  
 [!code-vb[VbVbalrStrings&#69;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_7.vb)]  
  
 Aqui, uma variável de cadeia de caracteres é criada, dado um valor, e, em seguida, seu valor é alterado.  
  
 Mais especificamente, na primeira linha, uma instância do tipo `String` é criada e receberá o valor `This string is immutable`. Na segunda linha do exemplo, uma nova instância é criada e receberá o valor `Or is it?`, e a variável de cadeia de caracteres descarta sua referência para a primeira instância e armazena uma referência para a nova instância.  
  
 Ao contrário de outros tipos de dados intrínsecos, `String` é um tipo de referência. Quando uma variável de tipo de referência é passada como um argumento para uma função ou sub-rotina, uma referência para o endereço de memória onde os dados são armazenados é passada em vez do valor real da cadeia de caracteres. No exemplo anterior, o nome da variável permanece o mesmo, mas ela aponta para uma instância nova e diferente de `String` classe, que contém o novo valor.  
  
## <a name="see-also"></a>Consulte também  
 [Introdução a cadeias de caracteres no Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)   
 [Tipo de dados String](../../../../visual-basic/language-reference/data-types/string-data-type.md)   
 [Tipo de dados char](../../../../visual-basic/language-reference/data-types/char-data-type.md)   
 [Operações de cadeias de caracteres básicas](http://msdn.microsoft.com/library/8133d357-90b5-4b62-9927-43323d99b6b6)
