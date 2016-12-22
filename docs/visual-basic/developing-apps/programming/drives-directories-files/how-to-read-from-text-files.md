---
title: "Como ler a partir de arquivos de texto no Visual Basic | Microsoft Docs"
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
  - "exemplos [Visual Basic], lendo arquivos de texto"
  - "caracteres estendidos, lendo"
  - "lendo dados, arquivos de texto"
  - "lendo arquivos de texto"
  - "arquivos de texto, lendo"
ms.assetid: 735fe9d7-0f7a-4185-ba02-f35e580ec4b8
caps.latest.revision: 27
caps.handback.revision: 27
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como ler a partir de arquivos de texto no Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

O método <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.ReadAllText%2A> do objeto `My.Computer.FileSystem` permite que você leia um arquivo de texto.  A codificação do arquivo pode ser especificada se o conteúdo do arquivo usar uma codificação, como ASCII ou UTF\-8.  
  
 Se você estiver lendo um arquivo com caracteres estendidos, será necessário especificar a codificação do arquivo.  
  
> [!NOTE]
>  Para ler em um arquivo uma linha de texto por vez, use o método <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.OpenTextFileReader%2A> do objeto `My.Computer.FileSystem`.  O método `OpenTextFileReader` retorna um objeto <xref:System.IO.StreamReader>.  Você pode usar o método <xref:System.IO.StreamReader.ReadLine%2A> do objeto `StreamReader` para ler o arquivo uma linha por vez.  Você pode testar o final do arquivo usando o método <xref:System.IO.StreamReader.EndOfStream%2A> do objeto `StreamReader`.  
  
### Para ler um arquivo de texto  
  
-   Use o método `ReadAllText` do objeto `My.Computer.FileSystem` para ler o conteúdo de um arquivo de texto em uma cadeia de caracteres, fornecendo o caminho.  O exemplo a seguir lê o conteúdo de test.txt em uma cadeia de caracteres e o exibe em uma caixa de mensagem.  
  
     [!code-vb[VbFileIORead#2](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-text-files_1.vb)]  
  
### Para ler de um arquivo de texto que está codificado  
  
-   Use o método `ReadAllText` do objeto `My.Computer.FileSystem` para ler o conteúdo de um arquivo de texto em uma cadeia de caracteres, fornecendo o caminho e o tipo da codificação do arquivo.  O exemplo a seguir lê o conteúdo do arquivo test.txt UTF32 em uma cadeia de caracteres e depois o exibe em uma caixa de mensagem.  
  
     [!code-vb[VbFileIORead#3](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-text-files_2.vb)]  
  
## Programação robusta  
 As seguintes condições podem causar uma exceção:  
  
-   O caminho não é válido por um destes motivos: é uma cadeia de caracteres de comprimento zero, contém somente espaço em branco, contém caracteres inválidos ou é um caminho de dispositivo \(<xref:System.ArgumentException>\).  
  
-   O caminho não é válido porque é `Nothing` \(<xref:System.ArgumentNullException>\).  
  
-   O arquivo não existe \(<xref:System.IO.FileNotFoundException>\).  
  
-   O arquivo está em uso por outro processo, ou ocorre um erro de E\/S \(<xref:System.IO.IOException>\).  
  
-   O caminho excede o comprimento máximo definido pelo sistema \(<xref:System.IO.PathTooLongException>\).  
  
-   Um nome de arquivo ou de diretório no caminho contém dois\-pontos \(:\) ou está em um formato inválido \(<xref:System.NotSupportedException>\).  
  
-   Não há memória suficiente para gravar a cadeia de caracteres no buffer \(<xref:System.OutOfMemoryException>\).  
  
-   O usuário não possui permissões necessárias para exibir o caminho \(<xref:System.Security.SecurityException>\).  
  
 Não tome decisões sobre o conteúdo do arquivo com base no nome do arquivo.  Por exemplo, o arquivo Form1.vb pode não ser um arquivo de código\-fonte do [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
 Verifique todas as entradas antes de usar os dados no seu aplicativo.  O conteúdo do arquivo pode não ser esperado, e os métodos para ler o arquivo podem falhar.  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A>   
 [Lendo a partir de arquivos](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)   
 [Como ler a partir de arquivos de texto separados por vírgulas](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)   
 [Como ler a partir de arquivos de texto de largura fixa](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md)   
 [Como ler a partir de arquivos de texto com vários formatos](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)   
 [Solucionando problemas: lendo e gravando em arquivos de texto](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)   
 [Instruções passo a passo: manipulando arquivos e diretórios no Visual Basic](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)   
 [Codificações de arquivo](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md)