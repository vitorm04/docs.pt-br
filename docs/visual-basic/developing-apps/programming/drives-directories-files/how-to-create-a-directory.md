---
title: Como criar um diretório no Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- directories [Visual Basic], creating
- folders [Visual Basic], creating
ms.assetid: 0351a2ca-24d8-43b5-bb39-9b99e6401cff
ms.openlocfilehash: ec9ee01e17f116e80708dbcb34e4d804bf3d7a6e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33583949"
---
# <a name="how-to-create-a-directory-in-visual-basic"></a><span data-ttu-id="88d6c-102">Como criar um diretório no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="88d6c-102">How to: Create a Directory in Visual Basic</span></span>
<span data-ttu-id="88d6c-103">Use o método `CreateDirectory` do objeto `My.Computer.FileSystem` para criar diretórios.</span><span class="sxs-lookup"><span data-stu-id="88d6c-103">Use the `CreateDirectory` method of the `My.Computer.FileSystem` object to create directories.</span></span>  
  
 <span data-ttu-id="88d6c-104">Se o diretório já existir, nenhuma exceção será lançada.</span><span class="sxs-lookup"><span data-stu-id="88d6c-104">If the directory already exists, no exception is thrown.</span></span>  
  
### <a name="to-create-a-directory"></a><span data-ttu-id="88d6c-105">Criar um diretório</span><span class="sxs-lookup"><span data-stu-id="88d6c-105">To create a directory</span></span>  
  
-   <span data-ttu-id="88d6c-106">Use o método `CreateDirectory` especificando o caminho completo do local em que o diretório deverá ser criado.</span><span class="sxs-lookup"><span data-stu-id="88d6c-106">Use the `CreateDirectory` method by specifying the full path of the location where the directory should be created.</span></span> <span data-ttu-id="88d6c-107">Este exemplo cria o diretório `NewDirectory` em `C:\Documents and Settings\All Users\Documents`.</span><span class="sxs-lookup"><span data-stu-id="88d6c-107">This example creates the directory `NewDirectory` in `C:\Documents and Settings\All Users\Documents`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#2](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-directory_1.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="88d6c-108">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="88d6c-108">Robust Programming</span></span>  
 <span data-ttu-id="88d6c-109">As seguintes condições podem causar uma exceção:</span><span class="sxs-lookup"><span data-stu-id="88d6c-109">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="88d6c-110">O nome do diretório está malformado.</span><span class="sxs-lookup"><span data-stu-id="88d6c-110">The directory name is malformed.</span></span> <span data-ttu-id="88d6c-111">Por exemplo, ele contém caracteres inválidos ou é somente um espaço em branco (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="88d6c-111">For example, it contains illegal characters or is only white space (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="88d6c-112">O diretório pai do diretório a ser criado é somente leitura (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="88d6c-112">The parent directory of the directory to be created is read-only (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="88d6c-113">O nome do diretório é `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="88d6c-113">The directory name is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="88d6c-114">O nome do diretório é muito longo (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="88d6c-114">The directory name is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="88d6c-115">O nome do diretório é um sinal de dois pontos ":" (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="88d6c-115">The directory name is a colon ":" (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="88d6c-116">O usuário não tem permissão para criar o diretório (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="88d6c-116">The user does not have permission to create the directory (<xref:System.UnauthorizedAccessException>).</span></span>  
  
-   <span data-ttu-id="88d6c-117">O usuário não possui permissões em uma situação de confiança parcial (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="88d6c-117">The user lacks permissions in a partial-trust situation (<xref:System.Security.SecurityException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88d6c-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="88d6c-118">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CreateDirectory%2A>  
 [<span data-ttu-id="88d6c-119">Criando, excluindo e movendo arquivos e diretórios</span><span class="sxs-lookup"><span data-stu-id="88d6c-119">Creating, Deleting, and Moving Files and Directories</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/creating-deleting-and-moving-files-and-directories.md)
