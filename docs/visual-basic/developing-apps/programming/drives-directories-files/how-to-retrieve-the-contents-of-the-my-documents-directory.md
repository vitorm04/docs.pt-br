---
title: 'Como: Recuperar o conteúdo do diretório Meus Documentos no Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- My Documents directory
ms.assetid: 26560d01-7dda-4457-8e95-21db23d71aea
ms.openlocfilehash: f03dbe1811dd5367dab2d32d94ba35ff05fad198
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64623144"
---
# <a name="how-to-retrieve-the-contents-of-the-my-documents-directory-in-visual-basic"></a>Como: Recuperar o conteúdo do diretório Meus Documentos no Visual Basic
O objeto <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories> pode ser usado para ler na maioria do diretórios de **Todos os Usuários**, como **Meus Documentos** ou **Área de Trabalho**.  
  
### <a name="to-read-from-the-my-documents-folder"></a>Para ler na pasta Meus Documentos  
  
- Use o método `ReadAllText` para ler o texto de cada arquivo em um diretório específico. O código a seguir especifica um diretório e um arquivo e, em seguida, usa o método `ReadAllText` para lê-los na cadeia de caracteres denominada `patients`.  
  
     [!code-vb[VbVbcnMyFileSystem#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#15)]  
  
## <a name="see-also"></a>Consulte também

- <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A>
