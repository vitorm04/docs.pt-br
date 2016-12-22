---
title: "Como rotular instru&#231;&#245;es (Visual Basic) | Microsoft Docs"
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
  - "caractere separador :"
  - "dois-pontos (:)"
  - "instruções [Visual Basic], rótulos"
  - "código do Visual Basic, rotulando instruções"
ms.assetid: 38f1ff43-2054-42cb-963b-1998e60c6ed4
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como rotular instru&#231;&#245;es (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Blocos de intruções são compostos de linhas de código delimitado por vírgulas.  Linhas de código precedidas por um indentificador inteiro ou cadeia de caracteres são por se dizer  *rotuladas* .   Rótulos de instruções são usados para marcar uma linha de código para identificá\-lo para uso com outras instruções, como `On Error Goto`.  
  
 Rótulos podem ser qualquer um dos identificadores válidodeVisual Basic — tais como aqueles que identificam os elementos de programação — ou literais de inteiro .   Um rótulo deve aparecer no início da linha de código\-fonte e deve ser seguido por dois\-pontos, independentemente se ele é seguido uma instrução na mesma linha.  
  
 O compilador identifica rótulos, verificando se o início da linha coincide com nenhum identificador já\-definidos.  Se não tiver, o compilador pressupõe que ele é um rótulo.  
  
 Rótulos tem seu próprio espaço de declaração e não interferem em outros identificadores.  Um escolo de rótulos é o corpo do método.  Declaração de rótulo terá precedência em qualquer situação ambígua.  
  
> [!NOTE]
>  Rótulos podem ser usados somente em declarações executáveis dentro métodos.  
  
### Para rotular uma linha de código  
  
-   Coloque um identificador, seguido por dois pontos, no início da linha de código\-fonte.  
  
     Por exemplo, as seguintes linhas de código são rotuladas com `Jump` e `120`, respectivamente:  
  
     [!code-vb[VbVbalrStatements#708](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-label-statements_1.vb)]  
  
## Consulte também  
 [Instruções](../../../visual-basic/programming-guide/language-features/statements.md)   
 [Nomes de elemento declarados](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)   
 [Estrutura do programa e convenções de código](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)