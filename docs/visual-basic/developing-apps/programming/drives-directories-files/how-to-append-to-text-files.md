---
title: 'Como: Acrescentar a arquivos de texto no Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [Visual Basic], appending to files
- I/O [Visual Basic], My.Computer.FileSystem.WriteAllText method
- I/O [Visual Basic], WriteAllText method
ms.assetid: bbbd7fb5-f169-41a9-b53f-520ea9613913
ms.openlocfilehash: 83f34e9cb669e8d2e841b13875b5237626164dd9
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58819834"
---
# <a name="how-to-append-to-text-files-in-visual-basic"></a><span data-ttu-id="b1d1b-102">Como: Acrescentar a arquivos de texto no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b1d1b-102">How to: Append to Text Files in Visual Basic</span></span>
<span data-ttu-id="b1d1b-103">O método <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> pode ser usado para anexar a um arquivo de texto especificando que o parâmetro `append` seja definido como `True`.</span><span class="sxs-lookup"><span data-stu-id="b1d1b-103">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> method can be used to append to a text file by specifying that the `append` parameter is set to `True`.</span></span>  
  
### <a name="to-append-to-a-text-file"></a><span data-ttu-id="b1d1b-104">Para acrescentar um arquivo de texto</span><span class="sxs-lookup"><span data-stu-id="b1d1b-104">To append to a text file</span></span>  
  
-   <span data-ttu-id="b1d1b-105">Use o método `WriteAllText`, especificando o arquivo de destino e a cadeia de caracteres a ser acrescentada e configuração o parâmetro `append` como `True`.</span><span class="sxs-lookup"><span data-stu-id="b1d1b-105">Use the `WriteAllText` method, specifying the target file and string to be appended and setting the `append` parameter to `True`.</span></span>  
  
     <span data-ttu-id="b1d1b-106">Este exemplo grava cadeia de caracteres `"This is a test string."` no nomeado `Testfile.txt`.</span><span class="sxs-lookup"><span data-stu-id="b1d1b-106">This example writes the string `"This is a test string."` to the file named `Testfile.txt`.</span></span>  
  
     [!code-vb[VbFileIOWrite#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#6)]  
  
## <a name="robust-programming"></a><span data-ttu-id="b1d1b-107">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="b1d1b-107">Robust Programming</span></span>  
 <span data-ttu-id="b1d1b-108">As seguintes condições podem causar uma exceção:</span><span class="sxs-lookup"><span data-stu-id="b1d1b-108">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="b1d1b-109">O caminho não é válido por um dos seguintes motivos: é uma cadeia de comprimento zero, contém apenas espaços em branco, contém caracteres inválidos ou é um caminho de dispositivo (começa com \\\\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="b1d1b-109">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="b1d1b-110">O caminho não é válido porque é `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="b1d1b-110">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="b1d1b-111">`File` aponta para um caminho que não existe (<xref:System.IO.FileNotFoundException> ou <xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="b1d1b-111">`File` points to a path that does not exist (<xref:System.IO.FileNotFoundException> or <xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
-   <span data-ttu-id="b1d1b-112">O arquivo está sendo usado por outro processo, ou ocorre um erro de E/S (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="b1d1b-112">The file is in use by another process, or an I/O error occurs (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="b1d1b-113">O caminho excede o comprimento máximo definido pelo sistema (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="b1d1b-113">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="b1d1b-114">Um nome de arquivo ou de diretório no caminho contém dois-pontos (:) ou está em um formato inválido (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="b1d1b-114">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="b1d1b-115">O usuário não possui permissões necessárias para exibir o caminho (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="b1d1b-115">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1d1b-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b1d1b-116">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- [<span data-ttu-id="b1d1b-117">Gravando em arquivos</span><span class="sxs-lookup"><span data-stu-id="b1d1b-117">Writing to Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
