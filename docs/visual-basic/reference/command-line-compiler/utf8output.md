---
title: "/utf8output (Visual Basic) | Microsoft Docs"
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
  - "Opção de compilador /utf8output [Visual Basic]"
  - "Opção de compilador utf8output [Visual Basic]"
  - "Opção de compilador -utf8output [Visual Basic]"
ms.assetid: 8ab36b1e-027a-49ac-85b4-f48997d9e4d6
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# /utf8output (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Exibe a saída do compilador usando a codificação UTF\-8.  
  
## Sintaxe  
  
```  
/utf8output[+ | -]  
```  
  
## Argumentos  
 `+` &#124; `-`  
 Opcional.  O padrão para essa opção é `/utf8output-`, o que significa que a saída do compilador não usa a codificação UTF\-8.  Especificar `/utf8output` é o mesmo que especificar `/utf8output+`.  
  
## Comentários  
 Em algumas configurações internacionais, saída do compilador não pode ser exibida corretamente no console.  Em tais situações, use `/utf8output` e redirecione a saída do compilador para um arquivo.  
  
> [!NOTE]
>  A opção `/utf8output` não está disponível de dentro do ambiente de desenvolvimento Visual Studio. Ela está disponível apenas quando se compila da linha de comando.  
  
## Exemplo  
 O código a seguir compila `In.vb` e direciona o compilador para exibir a saída usando a codificação UTF\-8.  
  
```  
vbc /utf8output in.vb  
```  
  
## Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Linhas de comando de compilação de exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)