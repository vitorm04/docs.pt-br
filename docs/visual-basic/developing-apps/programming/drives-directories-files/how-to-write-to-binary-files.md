---
title: Como gravar em arquivos binários
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], binary access
- WriteAllBytes method [Visual Basic]
- binary files [Visual Basic], writing in Visual Basic
ms.assetid: 59fae125-de5b-4c96-883c-209f4a55112c
ms.openlocfilehash: 72d019f5f49868bd84d0507535e8ebc547b50e25
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74334425"
---
# <a name="how-to-write-to-binary-files-in-visual-basic"></a>Como gravar em arquivos binários no Visual Basic

O método <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A> grava dados em um arquivo binário. Se o parâmetro `append` for `True`, ele acrescentará os dados ao arquivo; caso contrário, os dados no arquivo serão substituídos.

Se o caminho especificado, excluindo o nome de arquivo, não for válido, uma exceção <xref:System.IO.DirectoryNotFoundException> será lançada. Se o caminho for válido, mas o arquivo não existir, o arquivo será criado.

## <a name="to-write-to-a-binary-file"></a>Para gravar em um arquivo binário

Use o método `WriteAllBytes`, fornecendo o nome e o caminho do arquivo e os bytes a serem gravados. Este exemplo acrescenta a matriz de dados `CustomerData` ao arquivo chamado `CollectedData.dat`.

[!code-vb[VbVbcnMyFileSystem#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#27)]

## <a name="robust-programming"></a>Programação Robusta

As seguintes condições podem criar uma exceção:

- O caminho não é válido por um destes motivos: é uma cadeia de caracteres de comprimento zero; contém somente espaço em branco ou contém caracteres inválidos. (<xref:System.ArgumentException>).

- O caminho não é válido porque é `Nothing` (<xref:System.ArgumentNullException>).

- `File` aponta para um caminho que não existe (<xref:System.IO.FileNotFoundException> ou <xref:System.IO.DirectoryNotFoundException>).

- O arquivo está sendo usado por outro processo, ou ocorre um erro de E/S (<xref:System.IO.IOException>).

- O caminho excede o comprimento máximo definido pelo sistema (<xref:System.IO.PathTooLongException>).

- Um nome de arquivo ou de diretório no caminho contém dois-pontos (:) ou está em um formato inválido (<xref:System.NotSupportedException>).

- O usuário não possui permissões necessárias para exibir o caminho (<xref:System.Security.SecurityException>).

## <a name="see-also"></a>Consulte também

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A>
- [Como gravar texto em arquivos](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-write-text-to-files.md)
