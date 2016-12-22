---
title: "/nowin32manifest (Visual Basic) | Microsoft Docs"
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
  - "Opção de compilador /nowin32manifest [Visual Basic]"
  - "Opção de compilador nowin32manifest [Visual Basic]"
  - "Opção de compilador -nowin32manifest [Visual Basic]"
ms.assetid: c0528aae-83b3-4425-99f0-19448e9843e3
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# /nowin32manifest (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Instrui o compilador não incorporar o manifesto do aplicativo no arquivo executável.  
  
## Sintaxe  
  
```  
/nowin32manifest  
```  
  
## Comentários  
 Quando esta opção for usada, o aplicativo será sujeito a virtualização no Windows Vista, a menos que você forneça um manifesto de aplicativo em um arquivo de recurso do Win32 ou durante uma etapa de compilação posterior.  Para mais informações sobre virtualização, consulte [Implantação do ClickOnce no Windows Vista](/visual-studio/deployment/clickonce-deployment-on-windows-vista).  
  
 Para obter mais informações sobre a criação de manifesto, consulte [\/win32manifest](../../../visual-basic/reference/command-line-compiler/win32manifest.md).  
  
## Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Página de Aplicativo, Designer de Projeto \(Visual Basic\)](/visual-studio/ide/reference/application-page-project-designer-visual-basic)