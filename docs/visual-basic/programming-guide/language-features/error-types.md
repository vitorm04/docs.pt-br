---
title: "Tipos de erro (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "erros [Visual Basic], lógica"
  - "erros [Visual Basic], sintaxe"
  - "erros [Visual Basic], tipos"
  - "exceções, tipos"
  - "erros de lógica, Visual Basic"
  - "erros de tempo de execução, tipos de erros"
  - "erros de sintaxe, Visual Basic"
ms.assetid: 3048aabf-8c97-4e13-9150-853769cb5f6f
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Tipos de erro (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Em [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], erros \(também chamados  *exceções* \) se enquadram em uma das três categorias: erros de sintaxe, erros em tempo de execução e erros lógicos.  
  
## Erros de sintaxe  
 *Erros de sintaxe* são aqueles que aparecem enquanto você escreve o código.  [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]verifica o seu código conforme você digita\-lo no  **O Editor de código** janela e o alerta se você cometer um erro, como, por exemplo, digitar incorretamente uma palavra ou usando um elemento de linguagem incorretamente.  Erros de sintaxe são o tipo mais comum de erros.  Você pode corrigi\-los facilmente no ambiente de codificação, assim que eles ocorrem.  
  
> [!NOTE]
>  A instrução `Option Explicit` é um meio de evitar erros de sintaxe.  Ela força que você declare, com antecedência, todas as variáveis a serem usadas no aplicativo.  Portanto, quando essas variáveis são usadas no código, qualquer erro tipográfico é detectado imediatamente e pode ser corrigido.  
  
## Erros de Tempo de Execução  
 *Run\-time errors* são aqueles que aparecem somente após você compilar e executar seu código.  Esses envolvem código que pode parecer estar correto no sentido que ele não tem erros de sintaxe, mas que não será executado.  Por exemplo, você pode escrever corretamente uma linha de código para abrir um arquivo.  Mas, se o arquivo está corrompido, o aplicativo não pode executar a função `Open`, e ele deixará de ser executado.  Você pode corrigir a maioria dos erros de tempo de execução por reescrever o código defeituoso e em seguida, recompilá\-lo e executá\-lo novamente.  
  
## Erros de lógica  
 *Logic errors* são aqueles que aparecem depois que o aplicativo estiver em uso.  Eles são normalmente resultados indesejados ou inesperados em resposta às ações do usuário.  Por exemplo, uma chave digitada incorretamente ou outra fora da influência externa pode fazer com que seu aplicativo pare de funcionar dentro dos parâmetros esperados, ou completamente.  Os erros lógicos são geralmente o tipo mais difícil para corrigir, pois não é sempre claro onde eles se originam.  
  
## Consulte também  
 [Instrução Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)   
 [Noções básicas do depurador](/visual-studio/debugger/debugger-basics)