---
title: "Instru&#231;&#227;o Stop (Visual Basic) | Microsoft Docs"
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
  - "vb.Stop"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "pontos de interrupção, instruções Stop"
  - "execução, parando"
  - "execução, suspensão"
  - "processos, interrompendo"
  - "processando, interrompendo"
  - "instruções Stop"
  - "instruções Stop, sintaxe"
ms.assetid: c9a9fde0-d649-4662-9bef-bd0146ebc2a7
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Instru&#231;&#227;o Stop (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Suspende a execução.  
  
## Sintaxe  
  
```  
Stop  
```  
  
## Comentários  
 Você pode colocar `Stop` as instruções em qualquer lugar em procedimentos para suspender a execução.  Usando o `Stop` declaração é semelhante à configuração de um ponto de interrupção no código.  
  
 A instrução `Stop` suspende a execução, mas diferentemente de `End`, não fecha os arquivos nem desmarca todas as variáveis, a menos que ela seja encontrada em um arquivo executável \(.exe\) compilado.  
  
> [!NOTE]
>  Se a `Stop` instrução é encontrada no código que está sendo executado fora do ambiente de desenvolvimento integrado \(IDE\), o depurador é chamado.  Isso é verdadeiro independentemente se o código foi compilado no modo de depuração ou de varejo.  
  
## Exemplo  
 Este exemplo usa a `Stop` instrução para suspender a execução para cada iteração por meio do `For...Next` loop.  
  
 [!code-vb[VbVbalrStatements#56](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/stop-statement_1.vb)]  
  
## Consulte também  
 [Instrução End](../../../visual-basic/language-reference/statements/end-statement.md)