---
title: Como validar nomes de arquivo e caminhos no Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- file names [Visual Basic], validating
- strings [Visual Basic], validating
- Boolean values [Visual Basic]
- paths [Visual Basic], validating
ms.assetid: f673462d-57b7-4120-b13a-6a7592f7ab2c
ms.openlocfilehash: ab3df335bc5bba21d386bb69b12d840990e629fe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-validate-file-names-and-paths-in-visual-basic"></a>Como validar nomes de arquivo e caminhos no Visual Basic
Este exemplo retorna um `Boolean` valor que indica se uma cadeia de caracteres representa um nome de arquivo ou caminho. A validação verifica se o nome contém caracteres que não são permitidos pelo sistema de arquivos.  
  
## <a name="example"></a>Exemplo  
 [!code-vb[VbVbcnRegEx#4](../../../../visual-basic/programming-guide/language-features/strings/codesnippet/VisualBasic/how-to-validate-file-names-and-paths_1.vb)]  
  
 Este exemplo não verifica se o nome tiver colocado incorretamente dois-pontos ou diretórios sem nome, ou se o comprimento do nome excede o comprimento máximo definido pelo sistema. Ele também não verifica se o aplicativo tem permissão para acessar o recurso de sistema de arquivos com o nome especificado.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.IO.Path.GetInvalidPathChars%2A>  
 [Validando cadeias de caracteres no Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
