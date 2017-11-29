---
title: "Como ler a partir de arquivos binários no Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- binary files [Visual Basic], reading from
- I/O [Visual Basic], reading from binary files
- ReadAllBytes method [Visual Basic], reading from binary files
- My.Computer.FileSystem object, reading from binary files
ms.assetid: d2b1269e-24b6-42e0-9414-ae708db282d8
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ea6056f7d33b1137abb19b24246ce6874ff4d008
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-read-from-binary-files-in-visual-basic"></a>Como ler a partir de arquivos binários no Visual Basic
O objeto `My.Computer.FileSystem` fornece o método `ReadAllBytes` para ler arquivos binários.  
  
### <a name="to-read-from-a-binary-file"></a>Para ler em um arquivo binário  
  
-   Use o método `ReadAllBytes`, que retorna o conteúdo de um arquivo como uma matriz de bytes. Este exemplo lê do arquivo `C:/Documents and Settings/selfportrait.jpg`.  
  
     [!code-vb[VbVbcnMyFileSystem#78](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-binary-files_1.vb)]  
  
-   Para arquivos binários grandes, é possível usar o método <xref:System.IO.FileStream.Read%2A> do objeto <xref:System.IO.FileStream> para ler apenas uma quantidade especificada do arquivo por vez. Assim, é possível limitar quanto do arquivo é carregado na memória para cada operação de leitura. O exemplo de código a seguir copia um arquivo e permite que o chamador especifique quanto do arquivo é lido na memória por operação de leitura.  
  
     [!code-vb[VbVbcnMyFileSystem#91](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-binary-files_2.vb)]  
  
## <a name="robust-programming"></a>Programação robusta  
 As seguintes condições podem causar o lançamento de uma exceção:  
  
-   O caminho não é válido por um destes motivos: é uma cadeia de caracteres de comprimento zero, contém somente espaço em branco, contém caracteres inválidos ou é um caminho de dispositivo (<xref:System.ArgumentException>).  
  
-   O caminho não é válido porque é `Nothing` (<xref:System.ArgumentNullException>).  
  
-   O arquivo não existe (<xref:System.IO.FileNotFoundException>).  
  
-   O arquivo está sendo usado por outro processo, ou ocorre um erro de E/S (<xref:System.IO.IOException>).  
  
-   O caminho excede o comprimento máximo definido pelo sistema (<xref:System.IO.PathTooLongException>).  
  
-   Um nome de arquivo ou de diretório no caminho contém dois-pontos (:) ou está em um formato inválido (<xref:System.NotSupportedException>).  
  
-   Não há memória suficiente para gravar a cadeia de caracteres no buffer (<xref:System.OutOfMemoryException>).  
  
-   O usuário não possui permissões necessárias para exibir o caminho (<xref:System.Security.SecurityException>).  
  
 Não tome decisões sobre o conteúdo do arquivo com base no nome do arquivo. Por exemplo, o arquivo Form1.vb pode não ser um arquivo de código-fonte do Visual Basic.  
  
 Verifique todas as entradas antes de usar os dados no seu aplicativo. O conteúdo do arquivo pode não ser esperado, e os métodos para ler o arquivo podem falhar.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllBytes%2A>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A>  
 [Leitura de arquivos](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)  
 [Como ler a partir de arquivos de texto com vários formatos](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)  
 [Armazenando Dados e Lendo da Área de Transferência](../../../../visual-basic/developing-apps/programming/computer-resources/storing-data-to-and-reading-from-the-clipboard.md)
