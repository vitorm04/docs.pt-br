---
title: 'Como: Analisar caminhos de arquivo no Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- file names [Visual Basic], parsing [Visual Basic]
- parsing, file paths [Visual Basic]
ms.assetid: c1bd99c9-8160-456a-b5ab-60a49139b923
ms.openlocfilehash: 2b31dedbdd33ddfb3c15863a45b93148fd722faa
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54707746"
---
# <a name="how-to-parse-file-paths-in-visual-basic"></a><span data-ttu-id="395ea-102">Como: Analisar caminhos de arquivo no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="395ea-102">How to: Parse File Paths in Visual Basic</span></span>
<span data-ttu-id="395ea-103">O objeto <xref:Microsoft.VisualBasic.FileIO.FileSystem> oferece uma série de métodos úteis ao analisar os caminhos de arquivo.</span><span class="sxs-lookup"><span data-stu-id="395ea-103">The <xref:Microsoft.VisualBasic.FileIO.FileSystem> object offers a number of useful methods when parsing file paths.</span></span>  
  
-   <span data-ttu-id="395ea-104">O método <xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A> usa dois caminhos e retorna um caminho combinado formatado corretamente.</span><span class="sxs-lookup"><span data-stu-id="395ea-104">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A> method takes two paths and returns a properly formatted combined path.</span></span>  
  
-   <span data-ttu-id="395ea-105">O método <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetParentPath%2A> retorna o caminho absoluto do pai do caminho fornecido.</span><span class="sxs-lookup"><span data-stu-id="395ea-105">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetParentPath%2A> method returns the absolute path of the parent of the provided path.</span></span>  
  
-   <span data-ttu-id="395ea-106">O método <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> retorna um objeto <xref:System.IO.FileInfo> que pode ser consultado para determinar as propriedades do arquivo, como seu nome e caminho.</span><span class="sxs-lookup"><span data-stu-id="395ea-106">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> method returns a <xref:System.IO.FileInfo> object that can be queried to determine the file's properties, such as its name and path.</span></span>  
  
 <span data-ttu-id="395ea-107">Não tome decisões sobre os conteúdos do arquivo com base na extensão de nome de arquivo.</span><span class="sxs-lookup"><span data-stu-id="395ea-107">Do not make decisions about the contents of the file based on the file name extension.</span></span> <span data-ttu-id="395ea-108">Por exemplo, o arquivo Form1.vb pode não ser um arquivo de código-fonte do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="395ea-108">For example, the file Form1.vb may not be a Visual Basic source file.</span></span>  
  
### <a name="to-determine-a-files-name-and-path"></a><span data-ttu-id="395ea-109">Determinar o nome e o caminho de um arquivo</span><span class="sxs-lookup"><span data-stu-id="395ea-109">To determine a file's name and path</span></span>  
  
-   <span data-ttu-id="395ea-110">Use as propriedades <xref:System.IO.FileInfo.DirectoryName%2A> e <xref:System.IO.FileInfo.Name%2A> do objeto <xref:System.IO.FileInfo> para determinar o nome e o caminho do arquivo.</span><span class="sxs-lookup"><span data-stu-id="395ea-110">Use the <xref:System.IO.FileInfo.DirectoryName%2A> and <xref:System.IO.FileInfo.Name%2A> properties of the <xref:System.IO.FileInfo> object to determine a file's name and path.</span></span> <span data-ttu-id="395ea-111">Este exemplo determina o nome e o caminho e os exibe.</span><span class="sxs-lookup"><span data-stu-id="395ea-111">This example determines the name and path and displays them.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#54](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-parse-file-paths_1.vb)]  
  
### <a name="to-combine-a-files-name-and-directory-to-create-the-full-path"></a><span data-ttu-id="395ea-112">Combinar o nome e o diretório de um arquivo para criar o caminho completo</span><span class="sxs-lookup"><span data-stu-id="395ea-112">To combine a file's name and directory to create the full path</span></span>  
  
-   <span data-ttu-id="395ea-113">Use o método `CombinePath`, fornecendo o diretório e o nome.</span><span class="sxs-lookup"><span data-stu-id="395ea-113">Use the `CombinePath` method, supplying the directory and name.</span></span> <span data-ttu-id="395ea-114">Este exemplo usa as cadeias de caracteres `folderPath` e `fileName`, criadas no exemplo anterior, as combina e exibe o resultado.</span><span class="sxs-lookup"><span data-stu-id="395ea-114">This example takes the strings `folderPath` and `fileName` created in the previous example, combines them, and displays the result.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#55](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-parse-file-paths_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="395ea-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="395ea-115">See also</span></span>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A>
- <xref:System.IO.FileInfo>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A>
- [<span data-ttu-id="395ea-116">Como: Obter a coleção de arquivos em um diretório</span><span class="sxs-lookup"><span data-stu-id="395ea-116">How to: Get the Collection of Files in a Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
