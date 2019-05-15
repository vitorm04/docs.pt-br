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
# <a name="how-to-retrieve-the-contents-of-the-my-documents-directory-in-visual-basic"></a><span data-ttu-id="79c72-102">Como: Recuperar o conteúdo do diretório Meus Documentos no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="79c72-102">How to: Retrieve the Contents of the My Documents Directory in Visual Basic</span></span>
<span data-ttu-id="79c72-103">O objeto <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories> pode ser usado para ler na maioria do diretórios de **Todos os Usuários**, como **Meus Documentos** ou **Área de Trabalho**.</span><span class="sxs-lookup"><span data-stu-id="79c72-103">The <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories> object can be used to read from many of the **All Users** directories, such as **My Documents** or **Desktop**.</span></span>  
  
### <a name="to-read-from-the-my-documents-folder"></a><span data-ttu-id="79c72-104">Para ler na pasta Meus Documentos</span><span class="sxs-lookup"><span data-stu-id="79c72-104">To read from the My Documents folder</span></span>  
  
- <span data-ttu-id="79c72-105">Use o método `ReadAllText` para ler o texto de cada arquivo em um diretório específico.</span><span class="sxs-lookup"><span data-stu-id="79c72-105">Use the `ReadAllText` method to read the text from each file in a specific directory.</span></span> <span data-ttu-id="79c72-106">O código a seguir especifica um diretório e um arquivo e, em seguida, usa o método `ReadAllText` para lê-los na cadeia de caracteres denominada `patients`.</span><span class="sxs-lookup"><span data-stu-id="79c72-106">The following code specifies a directory and file and then uses `ReadAllText` to read them into the string named `patients`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="79c72-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="79c72-107">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A>
