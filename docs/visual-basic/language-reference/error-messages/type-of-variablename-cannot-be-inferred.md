---
title: "O tipo de &#39;&lt;variablename&gt;&#39; n&#227;o pode ser inferido porque os limites de loop e a vari&#225;vel step n&#227;o s&#227;o ampliados com o mesmo tipo | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30982"
  - "vbc30982"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30982"
ms.assetid: 741e85d9-a747-42ad-a1e1-a3f1928aaff5
caps.latest.revision: 30
caps.handback.revision: 30
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# O tipo de &#39;&lt;variablename&gt;&#39; n&#227;o pode ser inferido porque os limites de loop e a vari&#225;vel step n&#227;o s&#227;o ampliados com o mesmo tipo
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Você escreveu um loop `For...Next` no qual o compilador não pode inferir tipo e dados para a variável de controle de loop porque as seguintes condições são verdadeiras:  
  
-   O tipo de dados da variável de controle de loop não está especificada com uma cláusula `As`.  
  
-   O loop limita\-se e a variável de etapa contém pelo menos do tipos de dados.  
  
-   Não existe nenhuma conversão padrão entre os tipos de dados.  
  
 Por isso, o compilador não pode inferir o tipo de dados de uma variável de controle de loop.  
  
 No exemplo a seguir,  a variável de etapa é um caractere e os limites do loop são ambos inteiros.  Devido ao fato de que não existe conversão padrão entre caracteres e inteiros, este erro é relatado.  
  
```vb#  
Dim stepVar = "1"c  
Dim m = 0  
Dim n = 20  
  
' Not valid.  
' For i = 1 To 10 Step stepVar  
    ' Loop processing  
' Next  
```  
  
 **Identificação do erro:**  BC30982  
  
### Para corrigir este erro  
  
-   Altere os tipos dos limites do loop e da variável de etapa como necessário de modo que pelo menos um deles é um tipo para o qual os outros ampliam.  No exemplo anterior, altere o tipo de `stepVar` para `Integer`.  
  
    ```  
    Dim stepVar = 1  
    ```  
  
     \- ou \-  
  
    ```  
    Dim stepVar As Integer = 1  
    ```  
  
-   Use funções de conversão explícitas para converter os limites do loop e a variável de etapa para os tipos apropriados.  No exemplo anterior, aplique a função `Val` a `stepVar`.  
  
    ```  
    For i = 1 To 10 Step Val(stepVar)  
        ' Loop processing  
    Next  
    ```  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.Conversion.Val%2A>   
 [Instrução For...Next](../../../visual-basic/language-reference/statements/for-next-statement.md)   
 [Conversões implícitas e explícitas](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)   
 [Inferência de tipo local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [Instrução Option Infer](../../../visual-basic/language-reference/statements/option-infer-statement.md)   
 [Funções de conversão do tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [Conversões de Widening e Narrowing](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)