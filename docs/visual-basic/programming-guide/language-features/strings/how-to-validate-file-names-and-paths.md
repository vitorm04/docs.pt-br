---
title: Como validar nomes de arquivo e caminhos
ms.date: 07/20/2015
helpviewer_keywords:
- file names [Visual Basic], validating
- strings [Visual Basic], validating
- Boolean values [Visual Basic]
- paths [Visual Basic], validating
ms.assetid: f673462d-57b7-4120-b13a-6a7592f7ab2c
ms.openlocfilehash: cc4d275d469860aa19c45ca0fe0401b709b42d82
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344360"
---
# <a name="how-to-validate-file-names-and-paths-in-visual-basic"></a>Como validar nomes de arquivo e caminhos no Visual Basic
Este exemplo retorna um valor `Boolean` que indica se uma cadeia de caracteres representa um nome de arquivo ou caminho. A validação verifica se o nome contém caracteres que não são permitidos pelo sistema de arquivos.  
  
## <a name="example"></a>Exemplo  
 [!code-vb[VbVbcnRegEx#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#4)]  
  
 Este exemplo não verifica se o nome tem dois-pontos inseridos incorretamente ou diretórios sem nome ou se o comprimento do nome excede o comprimento máximo definido pelo sistema. Ele também não verifica se o aplicativo tem permissão para acessar o recurso do sistema de arquivos com o nome especificado.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.IO.Path.GetInvalidPathChars%2A>
- [Validando cadeias de caracteres no Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
