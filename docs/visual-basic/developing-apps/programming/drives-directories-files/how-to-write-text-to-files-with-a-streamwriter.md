---
title: Como gravar texto em arquivos com um StreamWriter no Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- writing to files [Visual Basic], StreamWriter
ms.assetid: 99762e57-ef46-4dcc-8959-a8f79c22f067
ms.openlocfilehash: 4cb589125286082b9c7d5886a51b0ef8d998474e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33583338"
---
# <a name="how-to-write-text-to-files-with-a-streamwriter-in-visual-basic"></a><span data-ttu-id="947b0-102">Como gravar texto em arquivos com um StreamWriter no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="947b0-102">How to: Write Text to Files with a StreamWriter in Visual Basic</span></span>
<span data-ttu-id="947b0-103">Este exemplo abre um objeto <xref:System.IO.StreamWriter> com o método `My.Computer.FileSystem.OpenTextFileWriter` e o usa para gravar uma cadeia de caracteres em um arquivo de texto com o método <xref:System.IO.TextWriter.WriteLine%2A> da classe <xref:System.IO.StreamWriter>.</span><span class="sxs-lookup"><span data-stu-id="947b0-103">This example opens a <xref:System.IO.StreamWriter> object with the `My.Computer.FileSystem.OpenTextFileWriter` method and uses it to write a string to a text file with the <xref:System.IO.TextWriter.WriteLine%2A> method of the <xref:System.IO.StreamWriter> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="947b0-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="947b0-104">Example</span></span>  
 [!code-vb[VbFileIOWrite#5](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files-with-a-streamwriter_1.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="947b0-105">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="947b0-105">Robust Programming</span></span>  
 <span data-ttu-id="947b0-106">As seguintes condições podem causar uma exceção:</span><span class="sxs-lookup"><span data-stu-id="947b0-106">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="947b0-107">O arquivo existe e é somente leitura (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="947b0-107">The file exists and is read-only (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="947b0-108">O disco está cheio (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="947b0-108">The disk is full (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="947b0-109">O nome do caminho é muito longo (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="947b0-109">The pathname is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="947b0-110">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="947b0-110">.NET Framework Security</span></span>  
 <span data-ttu-id="947b0-111">Este exemplo cria um novo arquivo, se o arquivo ainda não existe.</span><span class="sxs-lookup"><span data-stu-id="947b0-111">This example creates a new file, if the file does not already exist.</span></span> <span data-ttu-id="947b0-112">Se um aplicativo precisar criar um arquivo, ele precisará de acesso `Create` para a pasta.</span><span class="sxs-lookup"><span data-stu-id="947b0-112">If an application needs to create a file, that application needs `Create` access for the folder.</span></span> <span data-ttu-id="947b0-113">Se o arquivo já existe, o aplicativo precisa apenas de acesso `Write`, um privilégio menor.</span><span class="sxs-lookup"><span data-stu-id="947b0-113">If the file already exists, the application needs only `Write` access, a lesser privilege.</span></span> <span data-ttu-id="947b0-114">Sempre que possível, é mais seguro criar o arquivo durante a implantação e somente conceder acesso `Read` a um único arquivo, em vez de acesso `Create` a uma pasta.</span><span class="sxs-lookup"><span data-stu-id="947b0-114">Where possible, it is more secure to create the file during deployment, and only grant `Read` access to a single file, rather than `Create` access for a folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="947b0-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="947b0-115">See Also</span></span>  
 <xref:System.IO.StreamWriter>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileWriter%2A>  
 [<span data-ttu-id="947b0-116">Como ler em arquivos de texto</span><span class="sxs-lookup"><span data-stu-id="947b0-116">How to: Read from Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files.md)  
 [<span data-ttu-id="947b0-117">Gravando em arquivos</span><span class="sxs-lookup"><span data-stu-id="947b0-117">Writing to Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
