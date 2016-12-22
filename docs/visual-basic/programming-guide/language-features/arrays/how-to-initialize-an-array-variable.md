---
title: "Como inicializar uma vari&#225;vel de matriz no Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
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
  - "matrizes [Visual Basic], declarando"
  - "matrizes [Visual Basic], inicializando"
  - "matrizes [Visual Basic], variáveis"
  - "variáveis [Visual Basic], inicializando"
ms.assetid: aadd7a60-7ca4-4608-b986-091f19e7fc10
caps.latest.revision: 42
caps.handback.revision: 42
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como inicializar uma vari&#225;vel de matriz no Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Inicialize uma variável de matriz incluindo um literal de matriz em uma cláusula de `New` e especificando os valores iniciais da matriz.  É possível especificar o tipo ou permitir que ele seja inferido dos valores no literal de matriz.  Para obter mais informações sobre como o tipo é inferido, consulte “Preencher uma matriz com valores iniciais” em [Matrizes](../../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
### Para inicializar uma variável de matriz usando um literal de matriz  
  
-   Na cláusula `New` ou quando você atribui o valor de matriz, forneça os valores do elemento entre chaves \(`{}`\).  O exemplo a seguir mostra várias maneiras de declarar, criar e inicializar uma variável para conter uma matriz com elementos do tipo `Char`.  
  
     [!CODE [VbVbalrArrays#16](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrArrays#16)]  
  
     Após a execução de cada instrução, a matriz criada tem um comprimento 3, com elementos no índice 0 até índice 2 que contém os valores iniciais.  Se você fornecer tanto o limite superior quanto os valores, deverá incluir um valor para cada elemento do índice 0 até o limite superior.  
  
     Observe que você não precisa especificar o limite superior do índice se fornecer valores de elemento em uma matriz literal.  Se nenhum limite superior é especificado, o tamanho da matriz é inferido com base no número de valores no literal da matriz.  
  
### Para inicializar uma variável de matriz multidimensional usando literais de matriz  
  
-   Aninhar valores dentro de chaves \(`{}`\) entre chaves.  Verifique se os literais de matriz aninhados são todos inferidos como matrizes do mesmo tipo e comprimento.  O exemplo de código mostra vários exemplos de inicialização de matriz multidimensional.  
  
     [!CODE [VbVbalrArrays#17](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrArrays#17)]  
  
-   É possível especificar explicitamente os limites da matriz, ou deixá\-los de fora e solicitar que o compilador infira os limites da matriz com base nos valores no literal de matriz.  Se você fornecer tanto os limites superiores como os valores, você deve incluir um valor para cada elemento do índice 0 até o limite superior de cada dimensão.  O exemplo a seguir mostra várias maneiras de declarar, criar e inicializar uma variável para conter uma matriz bidimensional com elementos do tipo `Short`  
  
     [!CODE [VbVbalrArrays#18](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrArrays#18)]  
  
     Depois que cada instrução é executada, a matriz criada contém seis elementos inicializados que têm índices `(0,0)`, `(0,1)`, `(0,2)`, `(1,0)`, `(1,1)` e `(1,2)`.  Cada local da matriz contém o valor `10`.  
  
-   O exemplo a seguir efetua iterações por meio de uma matriz multidimensional.  Em um aplicativo do console do Windows escrito em Visual Basic, cole o código no método `Sub Main()`.  Os últimos comentários mostram a saída.  
  
     [!CODE [VbVbalrArrays#31](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrArrays#31)]  
  
### Para inicializar uma variável de matriz denteada usando literais de matriz  
  
-   Valores de objeto aninhado entre chaves \(`{}`\).  Embora você também possa aninhar literais de matriz que especificam matrizes de comprimentos diferentes, no caso de uma matriz denteada, verifique se os literais de matriz aninhados são colocados entre parênteses \(`()`\).  Os parênteses impõe a avaliação dos literais de matriz aninhadas e as matrizes resultantes são usadas como os valores iniciais da matriz denteada.  O exemplo de código mostra dois exemplos de inicialização de matriz denteada.  
  
     [!CODE [VbVbalrArrays#19](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrArrays#19)]  
  
-   O exemplo a seguir efetua iterações por meio de uma matriz denteada.  Em um aplicativo do console do Windows escrito em Visual Basic, cole o código no método `Sub Main()`.  Os últimos comentários no código mostram a saída.  
  
     [!CODE [VbVbalrArrays#32](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrArrays#32)]  
  
## Consulte também  
 [Matrizes](../../../../visual-basic/programming-guide/language-features/arrays/index.md)   
 [Solucionando problemas de matrizes](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)