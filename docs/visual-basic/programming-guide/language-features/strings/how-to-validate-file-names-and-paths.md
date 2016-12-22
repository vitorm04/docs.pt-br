---
title: "Como validar nomes de arquivo e caminhos no Visual Basic | Microsoft Docs"
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
  - "Valores boolianos"
  - "nomes de arquivos, validando"
  - "caminhos, validando"
  - "cadeias de caracteres {Visual Basic], validando"
ms.assetid: f673462d-57b7-4120-b13a-6a7592f7ab2c
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como validar nomes de arquivo e caminhos no Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Este exemplo retorna um `Boolean` valor que indica se uma seqüência de caracteres representa um nome de arquivo ou caminho.  A validação verifica se o nome contém caracteres que não são permitidas pelo sistema de arquivos.  
  
## Exemplo  
 [!code-vb[VbVbcnRegEx#4](../../../../visual-basic/programming-guide/language-features/strings/codesnippet/VisualBasic/how-to-validate-file-names-and-paths_1.vb)]  
  
 Este exemplo verifica se o nome tiver colocado incorretamente dois\-pontos ou diretórios sem nome, ou se o comprimento do nome excede o comprimento máximo definido pelo sistema.  Ela também verifica se o aplicativo tem permissão para acessar o recurso de sistema de arquivos com o nome especificado.  
  
## Consulte também  
 <xref:System.IO.Path.GetInvalidPathChars%2A>   
 [Validando cadeias de caracteres no Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)