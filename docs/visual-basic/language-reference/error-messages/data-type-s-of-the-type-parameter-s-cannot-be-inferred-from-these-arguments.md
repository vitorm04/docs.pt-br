---
title: "N&#227;o &#233; poss&#237;vel inferir o(s) tipo(s) de dados do(s) par&#226;metro(s) de tipo a partir destes argumentos | Microsoft Docs"
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
  - "bc36644"
  - "bc36647"
  - "vbc36647"
  - "vbc36644"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC36644"
  - "BC36647"
ms.assetid: 0e0050f2-2039-4311-b260-f0ebfde84189
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# N&#227;o &#233; poss&#237;vel inferir o(s) tipo(s) de dados do(s) par&#226;metro(s) de tipo a partir destes argumentos
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Tipos de dados dos parâmetros de tipo não podem ser deduzidos a partir desses argumentos.Especificando os dados tipos explicitamente deve corrigir esse erro.  
  
 Este erro ocorre quando a falha na resolução de sobrecarga.  Ele ocorre como uma subordinada mensagem informando por que um candidato sobrecarga específica foi eliminado.  A mensagem de erro explica que o compilador não pode usar inferência de tipo para localizar os tipos de dados para os parâmetros de tipo.  
  
> [!NOTE]
>  Ao especificar argumentos não for uma opção \(por exemplo, para os operadores de consulta em expressões de consulta\), a mensagem de erro é exibido sem a segunda frase.  
  
 O código a seguir demonstra o erro.  
  
```vb#  
Module Module1  
  
    Sub Main()  
  
        '' Not Valid.  
        'OverloadedGenericMethod("Hello", "World")  
  
    End Sub  
  
    Sub OverloadedGenericMethod(Of T)(ByVal x As String,   
                                      ByVal y As InterfaceExample(Of T))  
    End Sub  
  
    Sub OverloadedGenericMethod(Of T, R)(ByVal x As T,   
                                         ByVal y As InterfaceExample(Of R))  
    End Sub  
  
End Module  
  
Interface InterfaceExample(Of T)  
End Interface  
```  
  
 **Identificação de erro:** BC36647 e BC36644  
  
### Para corrigir este erro  
  
-   Você poderá especificar um tipo de dados para o parâmetro de tipo ou os parâmetros em vez de depender de inferência de tipos.  
  
## Consulte também  
 [Conversão de delegado reduzida](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)   
 [Procedimentos genéricos no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md)   
 [Conversões de tipo no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)