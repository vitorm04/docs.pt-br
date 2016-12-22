---
title: "Como gravar texto em arquivos no Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "exemplos [Visual Basic], arquivos de texto"
  - "Arquivos , gravando em"
  - "texto, escrevendo em arquivos"
  - "escrevendo em arquivos"
ms.assetid: 304956eb-530d-4df7-b48f-9b4d1f2581a0
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como gravar texto em arquivos no Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

O <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> método pode ser usado para gravar arquivos de texto.  Se o arquivo especificado não existir, ele é criado.  
  
## Procedimento  
  
#### Para Escrever Texto em um Arquivo  
  
-   Use o método `WriteAllText` para gravar texto em um arquivo, especificando o arquivo e o texto a ser gravado.  Este exemplo grava a linha `"This is new text."` no arquivo chamado `test.txt`, anexando o texto a qualquer texto existente no arquivo.  
  
     [!CODE [VbFileIOWrite#3](../CodeSnippet/VS_Snippets_VBCSharp/VbFileIOWrite#3)]  
  
#### Para gravar uma série de sequências de caracteres em um arquivo  
  
-   Faça um loop através da coleção da sequência de caracteres.  Use o método `WriteAllText` para gravar texto em um arquivo, especificando o arquivo de destino e a sequência de caracteres a ser adicionada e definindo `append` como `True`.  
  
     Este exemplo grava os nomes dos arquivos no diretório `Documents and Settings` para `FileList.txt`, inserindo um retorno de carro entre cada um para melhor legibilidade.  
  
     [!CODE [VbFileIOWrite#4](../CodeSnippet/VS_Snippets_VBCSharp/VbFileIOWrite#4)]  
  
## Programação robusta  
 As seguintes condições podem causar uma exceção:  
  
-   O caminho não é válido para uma das seguintes razões: ele é uma seqüência de comprimento zero, ele contém somente espaços em branco, ele contém caracteres inválidos ou é um caminho de dispositivo \(começa com \\ \\.  \\\) \(<xref:System.ArgumentException>\).  
  
-   O caminho não é válido porque ele é `Nothing` \(<xref:System.ArgumentNullException>\).  
  
-   `File` aponta para um caminho que não existe \(<xref:System.IO.FileNotFoundException> ou <xref:System.IO.DirectoryNotFoundException>\).  
  
-   O arquivo está em uso por outro processo, ou ocorre um erro de I\/O \(<xref:System.IO.IOException>\).  
  
-   O caminho excede o comprimento máximo definido pelo sistema \(<xref:System.IO.PathTooLongException>\).  
  
-   Um nome de arquivo ou de diretório no caminho contém dois\-pontos \(:\) ou está em um formato inválido \(<xref:System.NotSupportedException>\).  
  
-   O usuário não possui permissões necessárias para exibir o caminho \(<xref:System.Security.SecurityException>\).  
  
-   O disco está cheio e a chamada a `WriteAllText` falha \(<xref:System.IO.IOException>\).  
  
 Se você estiver executando em um contexto parcialmente confiável, o código pode lançar uma exceção devido a privilégios insuficientes.  Para obter mais informações, consulte [Noções básicas da segurança de acesso do código](../Topic/Code%20Access%20Security%20Basics.md).  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>   
 [Como ler a partir de arquivos de texto](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files.md)