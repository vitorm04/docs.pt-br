---
title: "Fim de instru&#231;&#227;o esperado | Microsoft Docs"
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
  - "bc30205"
  - "vbc30205"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30205"
ms.assetid: 53c7f825-a737-4b76-a1fa-f67745b8bd40
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Fim de instru&#231;&#227;o esperado
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

A declaração é sintaticamente completa, mas um elemento de programação adicional vem depois do elemento que conclui a declaração.  Um terminador de linha é necessário no final da cada declaração.  
  
 Um terminador de linha divide os caracteres de um arquivo de origem Visual Basic em linhas.  Exemplos de linha são terminadores o caractere retorno de carro Unicode \(&HD\), o caractere de alimentação de linha de &HA Unicode \(\), e o caractere retorno de carro Unicode seguido pelo caractere de alimentação de linha Unicode.  Para obter mais informações sobre a linha terminadores, consulte o [Especificação da linguagem Visual Basic](../../../visual-basic/reference/language-specification.md).  
  
 **Identificação do erro:**  BC30205  
  
### Para corrigir este erro  
  
1.  Verifique se duas declarações diferentes foram inadvertidamente colocadas na mesma linha.  
  
2.  Insira um terminador de linha após o elemento que conclui a declaração.  
  
## Consulte também  
 [Como quebrar e combinar instruções no código](../Topic/How%20to:%20Break%20and%20Combine%20Statements%20in%20Code%20\(Visual%20Basic\).md)   
 [Instruções](../../../visual-basic/programming-guide/language-features/statements.md)