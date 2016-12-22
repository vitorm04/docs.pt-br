---
title: "Como gravar texto em arquivos com um StreamWriter no Visual Basic | Microsoft Docs"
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
  - "Arquivos , gravando em"
  - "texto, escrevendo em arquivos"
  - "escrevendo em arquivos, StreamWriter"
ms.assetid: 99762e57-ef46-4dcc-8959-a8f79c22f067
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como gravar texto em arquivos com um StreamWriter no Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Este exemplo abre um objeto <xref:System.IO.StreamWriter> com o método `My.Computer.FileSystem.OpenTextFileWriter` e usa\-o para escrever uma sequência de caracteres para um arquivo de texto com o método <xref:System.IO.TextWriter.WriteLine%2A> da classe <xref:System.IO.StreamWriter> .  
  
## Exemplo  
 [!CODE [VbFileIOWrite#5](../CodeSnippet/VS_Snippets_VBCSharp/VbFileIOWrite#5)]  
  
## Programação robusta  
 As seguintes condições podem causar uma exceção:  
  
-   O arquivo existe e é somente leitura \(<xref:System.IO.IOException>\).  
  
-   O disco está cheio \(<xref:System.IO.IOException>\).  
  
-   O caminho é muito longo \(<xref:System.IO.PathTooLongException>\).  
  
## Segurança do .NET Framework  
 Este exemplo cria um novo arquivo, se o arquivo ainda não existir.  Se um aplicativo precisar criar um arquivo, o aplicativo precisa do acesso `Create` para a pasta.  Se o arquivo já existir, o aplicativo precisa apenas do acesso `Write`, um privilégio menor.  Quando possível, é mais seguro criar o arquivo durante a implantação e somente conceder acesso `Read` para um único arquivo, e não acesso `Create` para uma pasta.  
  
## Consulte também  
 <xref:System.IO.StreamWriter>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileWriter%2A>   
 [Como ler a partir de arquivos de texto](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files.md)   
 [Gravando em arquivos](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)