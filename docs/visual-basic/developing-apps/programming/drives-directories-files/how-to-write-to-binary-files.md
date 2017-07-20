---
title: "Como gravar em arquivos binários no Visual Basic | Microsoft Docs"
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
- files, binary access
- WriteAllBytes method
- binary files, writing in Visual Basic
ms.assetid: 59fae125-de5b-4c96-883c-209f4a55112c
caps.latest.revision: 16
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 0d86e39b7150b4ae8fc4de0498b0b786c5669bb4
ms.contentlocale: pt-br
ms.lasthandoff: 05/22/2017

---
# <a name="how-to-write-to-binary-files-in-visual-basic"></a>Como gravar em arquivos binários no Visual Basic
O método <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A> grava dados em um arquivo binário. Se o parâmetro `append` for `True`, ele acrescentará os dados ao arquivo; caso contrário, os dados no arquivo serão substituídos.  
  
 Se o caminho especificado, excluindo o nome de arquivo, não for válido, uma exceção <xref:System.IO.DirectoryNotFoundException> será lançada. Se o caminho for válido, mas o arquivo não existir, o arquivo será criado.  
  
### <a name="to-write-to-a-binary-file"></a>Para gravar em um arquivo binário  
  
-   Use o método `WriteAllBytes`, fornecendo o nome e o caminho do arquivo e os bytes a serem gravados. Este exemplo acrescenta a matriz de dados `CustomerData` ao arquivo chamado `CollectedData.dat`.  
  
     [!code-vb[VbVbcnMyFileSystem#27](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-to-binary-files_1.vb)]  
  
## <a name="robust-programming"></a>Programação robusta  
 As seguintes condições podem criar uma exceção:  
  
-   O caminho não é válido por um destes motivos: é uma cadeia de caracteres de comprimento zero; contém somente espaço em branco ou contém caracteres inválidos. (<xref:System.ArgumentException>).  
  
-   O caminho não é válido porque é `Nothing` (<xref:System.ArgumentNullException>).  
  
-   `File` aponta para um caminho que não existe (<xref:System.IO.FileNotFoundException> ou <xref:System.IO.DirectoryNotFoundException>).  
  
-   O arquivo está sendo usado por outro processo, ou ocorre um erro de E/S (<xref:System.IO.IOException>).  
  
-   O caminho excede o comprimento máximo definido pelo sistema (<xref:System.IO.PathTooLongException>).  
  
-   Um nome de arquivo ou de diretório no caminho contém dois-pontos (:) ou está em um formato inválido (<xref:System.NotSupportedException>).  
  
-   O usuário não possui permissões necessárias para exibir o caminho (<xref:System.Security.SecurityException>).  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A>   
 [Como gravar texto em arquivos](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-write-text-to-files.md)
