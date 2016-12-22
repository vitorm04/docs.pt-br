---
title: "Diferen&#231;as entre argumentos modific&#225;veis e n&#227;o modific&#225;veis (Visual Basic) | Microsoft Docs"
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
  - "argumentos [Visual Basic], modificável"
  - "argumentos [Visual Basic], não modificável"
  - "argumentos de procedimento"
  - "procedimentos, argumentos"
  - "código do Visual Basic, procedimentos"
ms.assetid: 87b2df69-e1f7-4657-9caf-b3f48d693428
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Diferen&#231;as entre argumentos modific&#225;veis e n&#227;o modific&#225;veis (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Quando você chama um procedimento, você normalmente passa um ou mais argumentos para ele.  Cada argumento corresponde a um elemento de programação subjacente.  Tanto os elementos subjacentes e os próprios argumentos podem ser tanto modificáveis ou não modificáveis.  
  
## Elementos modificável e Não\-modificável  
 Um elemento de programação pode ser tanto um *elemento modificável*, o qual pode ter seu valor alterado, ou um *elemento não modificável*, que tem um valor fixo após ele ter sido criado.  
  
 A tabela a seguir lista elementos de programação modificáveis e não modificáveis.  
  
|Elementos modificáveis|Elementos não modificáveis|  
|----------------------------|--------------------------------|  
|Variáveis locais \(declaradas dentro de procedimentos\), incluindo variáveis de objeto, exceto para somente leitura|Variáveis somente\-leitura, campos e propriedades|  
|Campos \(membro variáveis de módulos, classes e estruturas\), exceto para somente leitura|Literais e constantes|  
|Propriedades, exceto para somente leitura|Membros de enumeração|  
|Elementos da matriz|Expressões \(mesmo se seus elementos são modificáveis\)|  
  
## Elementos modificáveis e não modificáveis  
 Um *argumento modificável* é uma com um elemento subjacente modificável.  O código de chamada pode armazenar um novo valor a qualquer momento, e se você passar o argumento [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), o código no procedimento também pode modificar o elemento subjacente no código de chamada.  
  
 Um argumento *não modificável* possui um elemento subjacente não modificável ou é passado [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).  O procedimento não pode modificar o elemento subjacente no código de chamada, mesmo se ele for um elemento modificável.  Se ele é um elemento não modificável, o próprio código de chamada não pode modificá\-lo.  
  
 O procedimento chamado pode modificar sua cópia local de um argumento não modificável, mas esta modificação não afeta o elemento sunjacente no código de chamada.  
  
## Consulte também  
 [Procedimentos](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Parâmetros e argumentos de procedimento](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Como passar argumentos para um procedimento](../../../../visual-basic/programming-guide/language-features/procedures/how-to-pass-arguments-to-a-procedure.md)   
 [Passando argumentos por valor e por referência](../../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)   
 [Diferenças entre passar um argumento por valor e por referência](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md)   
 [Como alterar o valor de um argumento de procedimento](../../../../visual-basic/programming-guide/language-features/procedures/how-to-change-the-value-of-a-procedure-argument.md)   
 [Como proteger um argumento de procedimento contra alterações de valor](../../../../visual-basic/programming-guide/language-features/procedures/how-to-protect-a-procedure-argument-against-value-changes.md)   
 [Como forçar um argumento a ser passado por Valor](../Topic/How%20to:%20Force%20an%20Argument%20to%20Be%20Passed%20by%20Value%20\(Visual%20Basic\).md)   
 [Passando argumentos por posição e nome](../../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md)   
 [Tipos de valor e referência](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)