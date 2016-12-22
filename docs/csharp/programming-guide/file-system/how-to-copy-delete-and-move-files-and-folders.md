---
title: "Como copiar, excluir e mover arquivos e pastas (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "E/S [C#]"
ms.assetid: 62e52cd7-9597-4e4a-acf9-1315f5cdbf05
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Como copiar, excluir e mover arquivos e pastas (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Os exemplos a seguir mostram como copiar, mover e excluir arquivos e pastas de maneira síncrona usando o <xref:System.IO.File?displayProperty=fullName>, <xref:System.IO.Directory?displayProperty=fullName>, <xref:System.IO.FileInfo?displayProperty=fullName>, e <xref:System.IO.DirectoryInfo?displayProperty=fullName> classes a partir do <xref:System.IO?displayProperty=fullName> namespace.  Esses exemplos não fornecem uma barra de progresso ou qualquer outra interface de usuário.  Se você desejar fornecer uma caixa de diálogo de progresso padrão, consulte [Como fornecer uma caixa de diálogo de progresso para operações de arquivo](../../../csharp/programming-guide/file-system/how-to-provide-a-progress-dialog-box-for-file-operations.md).  
  
 Use <xref:System.IO.FileSystemWatcher?displayProperty=fullName> para fornecer eventos que permitem que você calcule o progresso ao operar em vários arquivos.  Outra abordagem é usar a plataforma invoke para chamar os métodos relevantes relacionadas a arquivos no Shell do Windows.  Para obter informações sobre como executar essas operações de arquivo de forma assíncrona, consulte [E\/S de arquivo assíncrona](../Topic/Asynchronous%20File%20I-O.md).  
  
## Exemplo  
 O exemplo a seguir mostra como copiar arquivos e diretórios.  
  
 [!code-cs[csFilesandFolders#7](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-copy-delete-and-move-files-and-folders_1.cs)]  
  
## Exemplo  
 O exemplo a seguir mostra como mover arquivos e diretórios.  
  
 [!code-cs[csFilesandFolders#8](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-copy-delete-and-move-files-and-folders_2.cs)]  
  
## Exemplo  
 O exemplo a seguir mostra como excluir arquivos e diretórios.  
  
 [!code-cs[csFilesandFolders#9](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-copy-delete-and-move-files-and-folders_3.cs)]  
  
## Consulte também  
 <xref:System.IO?displayProperty=fullName>   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Sistema de arquivos e o Registro](../../../csharp/programming-guide/file-system/file-system-and-the-registry.md)   
 [Como fornecer uma caixa de diálogo de progresso para operações de arquivo](../../../csharp/programming-guide/file-system/how-to-provide-a-progress-dialog-box-for-file-operations.md)   
 [E\/S de arquivo e de fluxo](../Topic/File%20and%20Stream%20I-O.md)   
 [Tarefas comuns de E\/S](../Topic/Common%20I-O%20Tasks.md)