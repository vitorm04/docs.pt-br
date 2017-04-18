---
title: 'Como: validar nomes de arquivo e caminhos no Visual Basic | Documentos do Microsoft'
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
- file names, validating
- strings [Visual Basic], validating
- Boolean values
- paths, validating
ms.assetid: f673462d-57b7-4120-b13a-6a7592f7ab2c
caps.latest.revision: 7
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 9b11e2e9dc5ae4c0bbeee947f18422f5f142b7af
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-validate-file-names-and-paths-in-visual-basic"></a>Como validar nomes de arquivo e demarcadores no Visual Basic
Este exemplo retorna um `Boolean` valor que indica se uma cadeia de caracteres representa um nome de arquivo ou caminho. A validação verifica se o nome contém caracteres que não são permitidos pelo sistema de arquivos.  
  
## <a name="example"></a>Exemplo  
 [!code-vb[VbVbcnRegEx n º&4;](../../../../visual-basic/programming-guide/language-features/strings/codesnippet/VisualBasic/how-to-validate-file-names-and-paths_1.vb)]  
  
 Este exemplo verifica se o nome tiver colocado incorretamente dois-pontos ou diretórios sem nome, ou se o comprimento do nome excede o comprimento máximo definido pelo sistema. Ele também verifica se o aplicativo tem permissão para acessar o recurso de sistema de arquivos com o nome especificado.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.IO.Path.GetInvalidPathChars%2A></xref:System.IO.Path.GetInvalidPathChars%2A>   
 [Validando cadeias de caracteres no Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
