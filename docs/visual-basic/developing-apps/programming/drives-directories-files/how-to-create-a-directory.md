---
title: "Como criar um diretório no Visual Basic"
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
- directories [Visual Basic], creating
- folders [Visual Basic], creating
ms.assetid: 0351a2ca-24d8-43b5-bb39-9b99e6401cff
caps.latest.revision: 19
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 1a45a785916b480dcee6e36fd295390266eaa0a0
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-create-a-directory-in-visual-basic"></a>Como criar um diretório no Visual Basic
Use o método `CreateDirectory` do objeto `My.Computer.FileSystem` para criar diretórios.  
  
 Se o diretório já existir, nenhuma exceção será lançada.  
  
### <a name="to-create-a-directory"></a>Criar um diretório  
  
-   Use o método `CreateDirectory` especificando o caminho completo do local em que o diretório deverá ser criado. Este exemplo cria o diretório `NewDirectory` em `C:\Documents and Settings\All Users\Documents`.  
  
     [!code-vb[VbVbcnMyFileSystem#2](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-directory_1.vb)]  
  
## <a name="robust-programming"></a>Programação robusta  
 As seguintes condições podem causar uma exceção:  
  
-   O nome do diretório está malformado. Por exemplo, ele contém caracteres inválidos ou é somente um espaço em branco (<xref:System.ArgumentException>).  
  
-   O diretório pai do diretório a ser criado é somente leitura (<xref:System.IO.IOException>).  
  
-   O nome do diretório é `Nothing` (<xref:System.ArgumentNullException>).  
  
-   O nome do diretório é muito longo (<xref:System.IO.PathTooLongException>).  
  
-   O nome do diretório é um sinal de dois pontos ":" (<xref:System.NotSupportedException>).  
  
-   O usuário não tem permissão para criar o diretório (<xref:System.UnauthorizedAccessException>).  
  
-   O usuário não possui permissões em uma situação de confiança parcial (<xref:System.Security.SecurityException>).  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CreateDirectory%2A>   
 [Criando, excluindo e movendo arquivos e diretórios](../../../../visual-basic/developing-apps/programming/drives-directories-files/creating-deleting-and-moving-files-and-directories.md)

