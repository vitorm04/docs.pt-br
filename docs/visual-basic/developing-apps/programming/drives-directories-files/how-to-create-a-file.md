---
title: "Como criar um arquivo no Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "Arquivos , criando"
  - "arquivos de texto, criando"
ms.assetid: 0253bb6d-5519-4a50-b882-b93ef5cca0d9
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como criar um arquivo no Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Este exemplo cria um arquivo de texto vazio no caminho especificado usando o método <xref:System.IO.File.Create%2A> na classe <xref:System.IO.File>.  
  
## Exemplo  
 [!code-vb[VbFileIOMisc#1](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-file_1.vb)]  
  
## Compilando o código  
 Use a variável `file` para escrever para o arquivo.  
  
## Programação robusta  
 Se o arquivo já existir, ele será substituído.  
  
 As seguintes condições podem causar uma exceção:  
  
-   O nome do caminho é incorreto.  Por exemplo, ele contém caracteres ilegais ou apenas espaços em branco \(<xref:System.ArgumentException>\).  
  
-   O caminho é somente leitura \(<xref:System.IO.IOException>\).  
  
-   O nome do caminho é `Nothing` \(<xref:System.ArgumentNullException>\).  
  
-   O caminho é muito longo \(<xref:System.IO.PathTooLongException>\).  
  
-   O caminho é inválido \(<xref:System.IO.DirectoryNotFoundException>\).  
  
-   O caminho é apenas dois\-pontos ": " \(<xref:System.NotSupportedException>\).  
  
## Segurança do .NET Framework  
 Uma <xref:System.Security.SecurityException> pode ser acionada em ambientes de confiança parcial.  
  
 A chamada para o método <xref:System.IO.File.Create%2A> requer <xref:System.Security.Permissions.FileIOPermission>.  
  
 Uma <xref:System.UnauthorizedAccessException> é apresentada se o usuário não tiver permissão para criar o arquivo.  
  
## Consulte também  
 <xref:System.IO>   
 <xref:System.IO.File.Create%2A>   
 [Usando bibliotecas de código parcialmente confiável](../Topic/Using%20Libraries%20from%20Partially%20Trusted%20Code.md)   
 [Noções básicas da segurança de acesso do código](../Topic/Code%20Access%20Security%20Basics.md)