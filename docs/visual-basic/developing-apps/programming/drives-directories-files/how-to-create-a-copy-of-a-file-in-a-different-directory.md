---
title: "Como Criar uma Cópia de um Arquivo em um Diretório Diferente no Visual Basic | Microsoft Docs"
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
- My.Computer.FileSystem.CopyFile method, copying files [Visual Basic]
- files, copying
- CopyFile method, copying files in Visual Basic
- I/O [Visual Basic], copying files
ms.assetid: 88e2145c-d414-45a5-ad03-6f5d58ecca26
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: 3f0bd4b0ebce8d8602853ed2076a2d1e616f29fd
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-create-a-copy-of-a-file-in-a-different-directory-in-visual-basic"></a>Como criar uma cópia de um arquivo em um diretório diferente no Visual Basic
O método `My.Computer.FileSystem.CopyFile` permite a cópia de arquivos. Os parâmetros desse método oferecem a capacidade de substituir os arquivos existentes, renomear o arquivo, mostrar o progresso da operação e permitir que o usuário cancele a operação.  
  
### <a name="to-copy-a-text-file-to-another-folder"></a>Copiar um arquivo de texto para outra pasta  
  
-   Use o método `CopyFile` para copiar um arquivo, especificando o arquivo de origem e o diretório de destino. O parâmetro `overwrite` permite especificar se os arquivos existentes devem ser sobrescritos ou não. Os exemplos de código a seguir demonstram como usar `CopyFile`.  
  
     [!code-vb[VbFileIOMisc#24](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-copy-of-a-file-in-a-different-directory_1.vb)]  
  
## <a name="robust-programming"></a>Programação robusta  
 As seguintes condições podem causar o lançamento de uma exceção:  
  
-   O caminho não é válido por um dos seguintes motivos: é uma cadeia de caracteres de comprimento zero, contém apenas espaços em branco, contém caracteres inválidos ou é um caminho de dispositivo (começa com \\\\.\\) (<xref:System.ArgumentException>).  
  
-   O sistema não pôde recuperar o caminho absoluto (<xref:System.ArgumentException>).  
  
-   O caminho não é válido, porque é `Nothing` (<xref:System.ArgumentNullException>).  
  
-   O arquivo de origem não é válido ou não existe (<xref:System.IO.FileNotFoundException>).  
  
-   O caminho combinado aponta para um diretório existente (<xref:System.IO.IOException>).  
  
-   O arquivo de destino já existe e `overwrite` é definido como `False` (<xref:System.IO.IOException>).  
  
-   O usuário não tem permissões suficientes para acessar o arquivo (<xref:System.IO.IOException>).  
  
-   Um arquivo na pasta de destino com o mesmo nome está em uso (<xref:System.IO.IOException>).  
  
-   Um nome de arquivo ou de pasta no caminho contém dois-pontos (:) ou está em um formato inválido (<xref:System.NotSupportedException>).  
  
-   `ShowUI` está definido como `True`, `onUserCancel` está definido como `ThrowException` e o usuário cancelou a operação (<xref:System.OperationCanceledException>).  
  
-   `ShowUI` está definido como `True`, `onUserCancel` está definido como `ThrowException` e um erro não especificado de E/S ocorreu (<xref:System.OperationCanceledException>).  
  
-   O caminho excede o comprimento máximo definido pelo sistema (<xref:System.IO.PathTooLongException>).  
  
-   O usuário não tem a permissão necessária (<xref:System.UnauthorizedAccessException>).  
  
-   O usuário não tiver as permissões necessárias para exibir o caminho (<xref:System.Security.SecurityException>).  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>   
 <xref:Microsoft.VisualBasic.FileIO.UICancelOption>   
 [Como Copiar Arquivos com um Padrão Específico para um Diretório](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-files-with-a-specific-pattern-to-a-directory.md)   
 [Como Criar uma Cópia de um Arquivo no Mesmo Diretório](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-the-same-directory.md)   
 [Como Copiar um Diretório para outro Diretório](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-a-directory-to-another-directory.md)   
 [Como renomear um arquivo](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)
