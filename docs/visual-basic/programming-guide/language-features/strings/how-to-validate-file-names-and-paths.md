---
title: 'Como: Validar nomes de arquivo e caminhos no Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- file names [Visual Basic], validating
- strings [Visual Basic], validating
- Boolean values [Visual Basic]
- paths [Visual Basic], validating
ms.assetid: f673462d-57b7-4120-b13a-6a7592f7ab2c
ms.openlocfilehash: c8e01a0f5a3f99fdbc424d6cd7d224367c7bad08
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62032169"
---
# <a name="how-to-validate-file-names-and-paths-in-visual-basic"></a>Como: Validar nomes de arquivo e caminhos no Visual Basic
Este exemplo retorna um `Boolean` valor que indica se uma cadeia de caracteres representa um nome de arquivo ou caminho. A validação verifica se o nome contém caracteres que não são permitidos pelo sistema de arquivos.  
  
## <a name="example"></a>Exemplo  
 [!code-vb[VbVbcnRegEx#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#4)]  
  
 Este exemplo verifica se o nome tiver colocado incorretamente dois-pontos ou diretórios sem nome ou se o comprimento do nome excede o comprimento máximo definido pelo sistema. Ele também verifica se o aplicativo tem permissão para acessar o recurso de sistema de arquivos com o nome especificado.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.IO.Path.GetInvalidPathChars%2A>
- [Validando cadeias de caracteres no Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
