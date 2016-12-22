---
title: "Opcional (Visual Basic) | Microsoft Docs"
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
  - "vb.Optional"
  - "vb.optional"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "palavra-chave Optional"
  - "palavra-chave Optional, contextos"
ms.assetid: 4571ce88-a539-4115-b230-54eb277c6aa7
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Opcional (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Especifica que um argumento procedimento pode ser omitido quando o procedimento é chamado.  
  
## Comentários  
 Para cada parâmetro opcional, você deve especificar uma expressão constante como valor padrão desse parâmetro.  Se a expressão for avaliada como  [nada](../../../visual-basic/language-reference/nothing.md), o valor padrão do tipo de dados valor é usado como o valor padrão do parâmetro.  
  
 Se a lista de parâmetros contém um parâmetro opcional, cada parâmetro segue também deve ser opcional.  
  
 O modificador `Optional` pode ser utilizado nestes contextos:  
  
-   [Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
-   [Instrução função](../../../visual-basic/language-reference/statements/function-statement.md)  
  
-   [Propriedade declaração](../../../visual-basic/language-reference/statements/property-statement.md)  
  
-   [Declaração Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
> [!NOTE]
>  Ao chamar um procedimento com ou sem parâmetros opcionais, você pode passar argumentos por posição ou por nome.  Para mais informações, consulte [Passando argumentos por posição e nome](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md).  
  
> [!NOTE]
>  Você também pode definir um procedimento com parâmetros opcionais usando a sobrecarga.  Se você tiver um parâmetro opcional, você pode definir duas versões sobrecarregadas do procedimento, uma que aceita o parâmetro e um não.  Para mais informações, consulte [Sobrecarga de procedimento](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).  
  
## Exemplo  
 O exemplo a seguir define um procedimento que tem um parâmetro opcional.  
  
```  
Public Function FindMatches(ByRef values As List(Of String),  
                            ByVal searchString As String,  
                            Optional ByVal matchCase As Boolean = False) As List(Of String)  
  
    Dim results As IEnumerable(Of String)  
  
    If matchCase Then  
        results = From v In values  
                  Where v.Contains(searchString)  
    Else  
        results = From v In values  
                  Where UCase(v).Contains(UCase(searchString))  
    End If  
  
    Return results.ToList()  
End Function  
```  
  
## Exemplo  
 O exemplo a seguir demonstra como chamar um procedimento com argumentos passados por posição e argumentos passados por nome.  O procedimento tem dois parâmetros opcionais.  
  
 [!code-vb[VbVbalrKeywords#21](../../../visual-basic/language-reference/codesnippet/VisualBasic/optional_1.vb)]  
  
## Consulte também  
 [Lista de parâmetros](../../../visual-basic/language-reference/statements/parameter-list.md)   
 [Parâmetros opcionais](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)   
 [Palavras\-chave](../../../visual-basic/language-reference/keywords/index.md)