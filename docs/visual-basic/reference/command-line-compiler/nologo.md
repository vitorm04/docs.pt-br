---
title: "/nologo (Visual Basic) | Microsoft Docs"
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
  - "Opção de compilador /nologo [Visual Basic]"
  - "faixas, suprimindo a inicialização"
  - "Opção de compilador nologo [Visual Basic]"
  - "Opção de compilador -nologo [Visual Basic]"
ms.assetid: 25ef54b6-d676-4639-a2d2-a747a158bc07
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# /nologo (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Suprime a exibição da faixa de direitos autorais e mensagens informativas durante a compilação.  
  
## Sintaxe  
  
```  
/nologo  
```  
  
## Comentários  
 Se você especificar `/nologo`, o compilador não exibirá uma faixa de direitos autorais.  Por default, `/nologo` não está ativo.  
  
> [!NOTE]
>  A opção `/nologo` não está disponível dentro do ambiente de desenvolvimento Visual Studio. Ela está disponível apenas quando se compila da linha de comando.  
  
## Exemplo  
 O código a seguir compila `T2.vb` e não exibe uma faixa de direitos autorais.  
  
```  
vbc /nologo t2.vb  
```  
  
## Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Linhas de comando de compilação de exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)