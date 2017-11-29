---
title: Como gravar texto em arquivos com um StreamWriter no Visual Basic
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- writing to files [Visual Basic], StreamWriter
ms.assetid: 99762e57-ef46-4dcc-8959-a8f79c22f067
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 874bb9cb88bbf25cb6208a0a33858855a7b26a49
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-text-to-files-with-a-streamwriter-in-visual-basic"></a><span data-ttu-id="00b37-102">Como gravar texto em arquivos com um StreamWriter no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="00b37-102">How to: Write Text to Files with a StreamWriter in Visual Basic</span></span>
<span data-ttu-id="00b37-103">Este exemplo abre um objeto <xref:System.IO.StreamWriter> com o método `My.Computer.FileSystem.OpenTextFileWriter` e o usa para gravar uma cadeia de caracteres em um arquivo de texto com o método <xref:System.IO.TextWriter.WriteLine%2A> da classe <xref:System.IO.StreamWriter>.</span><span class="sxs-lookup"><span data-stu-id="00b37-103">This example opens a <xref:System.IO.StreamWriter> object with the `My.Computer.FileSystem.OpenTextFileWriter` method and uses it to write a string to a text file with the <xref:System.IO.TextWriter.WriteLine%2A> method of the <xref:System.IO.StreamWriter> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="00b37-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="00b37-104">Example</span></span>  
 [!code-vb[VbFileIOWrite#5](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files-with-a-streamwriter_1.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="00b37-105">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="00b37-105">Robust Programming</span></span>  
 <span data-ttu-id="00b37-106">As seguintes condições podem causar uma exceção:</span><span class="sxs-lookup"><span data-stu-id="00b37-106">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="00b37-107">O arquivo existe e é somente leitura (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="00b37-107">The file exists and is read-only (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="00b37-108">O disco está cheio (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="00b37-108">The disk is full (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="00b37-109">O nome do caminho é muito longo (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="00b37-109">The pathname is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="00b37-110">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="00b37-110">.NET Framework Security</span></span>  
 <span data-ttu-id="00b37-111">Este exemplo cria um novo arquivo, se o arquivo ainda não existe.</span><span class="sxs-lookup"><span data-stu-id="00b37-111">This example creates a new file, if the file does not already exist.</span></span> <span data-ttu-id="00b37-112">Se um aplicativo precisar criar um arquivo, ele precisará de acesso `Create` para a pasta.</span><span class="sxs-lookup"><span data-stu-id="00b37-112">If an application needs to create a file, that application needs `Create` access for the folder.</span></span> <span data-ttu-id="00b37-113">Se o arquivo já existe, o aplicativo precisa apenas de acesso `Write`, um privilégio menor.</span><span class="sxs-lookup"><span data-stu-id="00b37-113">If the file already exists, the application needs only `Write` access, a lesser privilege.</span></span> <span data-ttu-id="00b37-114">Sempre que possível, é mais seguro criar o arquivo durante a implantação e somente conceder acesso `Read` a um único arquivo, em vez de acesso `Create` a uma pasta.</span><span class="sxs-lookup"><span data-stu-id="00b37-114">Where possible, it is more secure to create the file during deployment, and only grant `Read` access to a single file, rather than `Create` access for a folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00b37-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="00b37-115">See Also</span></span>  
 <xref:System.IO.StreamWriter>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileWriter%2A>  
 [<span data-ttu-id="00b37-116">Como ler em arquivos de texto</span><span class="sxs-lookup"><span data-stu-id="00b37-116">How to: Read from Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files.md)  
 [<span data-ttu-id="00b37-117">Gravando em arquivos</span><span class="sxs-lookup"><span data-stu-id="00b37-117">Writing to Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
