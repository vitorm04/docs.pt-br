---
title: "Caracter&#237;sticas do elemento declarado (Visual Basic) | Microsoft Docs"
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
  - "níveis de acesso, elementos declarados"
  - "tipos de dados [Visual Basic], elementos declarados"
  - "elementos declarados, nível de acesso"
  - "elementos declarados, tempo de vida"
  - "elementos declarados, escopo"
  - "elementos declarados, visibilidade"
  - "elementos, programação"
  - "tempo de vida, elementos declarados"
  - "escopo, elementos declarados"
  - "visibilidade, elementos declarados"
ms.assetid: 1bc40fb8-b67c-4428-90a4-76b630ae2583
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Caracter&#237;sticas do elemento declarado (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Uma *característica* de um elemento declarado é um aspecto do elemento que afeta como o código pode interagir com ele.  Cada elemento declarado possui uma ou mais das seguintes características associadas a ele:  
  
-   *Tipo de dados* — os valores que o elemento pode conter e como ele armazena esses valores.  Para obter mais informações, consulte [Tipos de dados](../../../../visual-basic/language-reference/data-types/data-type-summary.md).  
  
-   *Vida útil*  — o período de tempo de execução durante o qual o elemento está disponível para uso.  Para obter mais informações, consulte [Tempo de vida no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md).  
  
-   *Escopo*  — o conjunto de todo os códigos que podem se referir ao elemento sem qualificar seu nome.  Para obter mais informações, consulte [Como controlar o escopo de uma variável](../Topic/How%20to:%20Control%20the%20Scope%20of%20a%20Variable%20\(Visual%20Basic\).md).  
  
-   *Nível de acesso* — a permissão para o código fazer uso do elemento.  Para obter mais informações, consulte [Como controlar a disponibilidade de uma variável](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-availability-of-a-variable.md).  
  
## Características dos elementos  
 A tabela a seguir mostra os elementos declarados e as características que se aplicam a cada um deles.  
  
|Elemento|Tipo de dados|Tempo de Vida|Escopo <sup>1</sup>|Nível de Acesso|  
|--------------|-------------------|-------------------|-------------------------|---------------------|  
|Variável|Sim|Sim|Sim|Sim|  
|Constante|Sim|Não|Sim|Sim|  
|Enumeração|Sim|Não|Sim|Sim|  
|Estrutura|Não|Não|Sim|Sim|  
|Propriedade|Sim|Sim|Sim|Sim|  
|Método|Não|Sim|Sim|Sim|  
|Procedimento \(`Sub` ou `Function`\)|Não|Sim|Sim|Sim|  
|Parâmetro de procedimento|Sim|Sim|Sim|Não|  
|Retorno de função|Sim|Sim|Sim|Não|  
|Operador|Sim|Não|Sim|Sim|  
|Interface|Não|Não|Sim|Sim|  
|Classe|Não|Não|Sim|Sim|  
|Evento|Não|Não|Sim|Sim|  
|Delegado|Não|Não|Sim|Sim|  
  
 <sup>1</sup> Escopo é às vezes referido como  *Visibilidade* .  
  
## Consulte também  
 [Elementos declarados](../../../../visual-basic/programming-guide/language-features/declared-elements/index.md)   
 [Nomes de elemento declarados](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)   
 [Referências a elementos declarados](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)   
 [Tempo de vida no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)   
 [Escopo no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)   
 [Níveis de acesso no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)   
 [Tipos de dados](../../../../visual-basic/programming-guide/language-features/data-types/index.md)   
 [Declaração de variável](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)