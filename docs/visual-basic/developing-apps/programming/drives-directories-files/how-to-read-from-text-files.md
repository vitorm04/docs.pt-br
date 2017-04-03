---
title: Como ler em arquivos de texto no Visual Basic | Microsoft Docs
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- extended characters, reading
- reading text files
- reading data, text files
- examples [Visual Basic], reading text files
- text files, reading
ms.assetid: 735fe9d7-0f7a-4185-ba02-f35e580ec4b8
caps.latest.revision: 27
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 362745101d1a8f7dd61b5e3aabe1c27190c46c07
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-read-from-text-files-in-visual-basic"></a>Como ler a partir de arquivos de texto no Visual Basic
O método <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.ReadAllText%2A> do objeto `My.Computer.FileSystem` permite que você leia em um arquivo de texto. A codificação do arquivo pode ser especificada se o conteúdo do arquivo usar uma codificação, como ASCII ou UTF-8.  
  
 Se você estiver lendo um arquivo com caracteres estendidos, será necessário especificar a codificação do arquivo.  
  
> [!NOTE]
>  Para ler uma linha de texto por vez em um arquivo, use o método <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.OpenTextFileReader%2A> do objeto `My.Computer.FileSystem`. O método `OpenTextFileReader` retorna um objeto <xref:System.IO.StreamReader>. Você pode usar o método <xref:System.IO.StreamReader.ReadLine%2A> do objeto `StreamReader` para ler um arquivo, uma linha por vez. Você pode testar para o final do arquivo usando o método <xref:System.IO.StreamReader.EndOfStream%2A> do objeto `StreamReader`.  
  
### <a name="to-read-from-a-text-file"></a>Para ler um arquivo de texto  
  
-   Use o método `ReadAllText` do objeto `My.Computer.FileSystem` para ler o conteúdo de um arquivo de texto em uma cadeia de caracteres, fornecendo o caminho. O exemplo a seguir lê o conteúdo de test.txt em uma cadeia de caracteres e o exibe em uma caixa de mensagem.  
  
     [!code-vb[VbFileIORead#2](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-text-files_1.vb)]  
  
### <a name="to-read-from-a-text-file-that-is-encoded"></a>Para ler de um arquivo de texto que está codificado  
  
-   Use o método `ReadAllText` do objeto `My.Computer.FileSystem` para ler o conteúdo de um arquivo de texto em uma cadeia de caracteres, fornecendo o caminho e o tipo da codificação do arquivo. O exemplo a seguir lê o conteúdo do arquivo test.txt UTF32 em uma cadeia de caracteres e depois o exibe em uma caixa de mensagem.  
  
     [!code-vb[VbFileIORead#3](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-text-files_2.vb)]  
  
## <a name="robust-programming"></a>Programação robusta  
 As seguintes condições podem causar uma exceção:  
  
-   O caminho não é válido por um dos seguintes motivos: é uma cadeia de caracteres de comprimento zero, contém apenas espaços em branco, contém caracteres inválidos ou é um caminho de dispositivo (<xref:System.ArgumentException>).  
  
-   O caminho não é válido, porque é `Nothing` (<xref:System.ArgumentNullException>).  
  
-   O arquivo não existe (<xref:System.IO.FileNotFoundException>).  
  
-   O arquivo está sendo usado por outro processo ou ocorre um erro de E/S (<xref:System.IO.IOException>).  
  
-   O caminho excede o comprimento máximo definido pelo sistema (<xref:System.IO.PathTooLongException>).  
  
-   Um nome de arquivo ou de diretório no caminho contém dois-pontos (:) ou está em um formato inválido (<xref:System.NotSupportedException>).  
  
-   Não há memória suficiente para gravar a cadeia de caracteres no buffer (<xref:System.OutOfMemoryException>).  
  
-   O usuário não tiver as permissões necessárias para exibir o caminho (<xref:System.Security.SecurityException>).  
  
 Não tome decisões sobre o conteúdo do arquivo com base no nome do arquivo. Por exemplo, o arquivo Form1.vb pode não ser um arquivo de código-fonte do [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
 Verifique todas as entradas antes de usar os dados no seu aplicativo. O conteúdo do arquivo pode não ser esperado, e os métodos para ler o arquivo podem falhar.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A>   
 [Leitura de Arquivos](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)   
 [Como ler com base em arquivos de texto separados por vírgulas](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)   
 [Como ler em arquivos de texto de largura fixa](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md)   
 [Como ler em arquivos de texto com vários formatos](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)   
 [Solução de Problemas: Lendo e Gravando em Arquivos de Texto](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)   
 [Passo a passo: manipulando arquivos e diretórios no Visual Basic](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)   
 [Codificações de Arquivo](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md)
