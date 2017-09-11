---
title: "Como criar um diretório no Visual Basic"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- directories [Visual Basic], creating
- folders [Visual Basic], creating
ms.assetid: 0351a2ca-24d8-43b5-bb39-9b99e6401cff
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 1a45a785916b480dcee6e36fd295390266eaa0a0
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-create-a-directory-in-visual-basic"></a><span data-ttu-id="80323-102">Como criar um diretório no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="80323-102">How to: Create a Directory in Visual Basic</span></span>
<span data-ttu-id="80323-103">Use o método `CreateDirectory` do objeto `My.Computer.FileSystem` para criar diretórios.</span><span class="sxs-lookup"><span data-stu-id="80323-103">Use the `CreateDirectory` method of the `My.Computer.FileSystem` object to create directories.</span></span>  
  
 <span data-ttu-id="80323-104">Se o diretório já existir, nenhuma exceção será lançada.</span><span class="sxs-lookup"><span data-stu-id="80323-104">If the directory already exists, no exception is thrown.</span></span>  
  
### <a name="to-create-a-directory"></a><span data-ttu-id="80323-105">Criar um diretório</span><span class="sxs-lookup"><span data-stu-id="80323-105">To create a directory</span></span>  
  
-   <span data-ttu-id="80323-106">Use o método `CreateDirectory` especificando o caminho completo do local em que o diretório deverá ser criado.</span><span class="sxs-lookup"><span data-stu-id="80323-106">Use the `CreateDirectory` method by specifying the full path of the location where the directory should be created.</span></span> <span data-ttu-id="80323-107">Este exemplo cria o diretório `NewDirectory` em `C:\Documents and Settings\All Users\Documents`.</span><span class="sxs-lookup"><span data-stu-id="80323-107">This example creates the directory `NewDirectory` in `C:\Documents and Settings\All Users\Documents`.</span></span>  
  
     <span data-ttu-id="80323-108">[!code-vb[VbVbcnMyFileSystem#2](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-directory_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="80323-108">[!code-vb[VbVbcnMyFileSystem#2](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-directory_1.vb)]</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="80323-109">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="80323-109">Robust Programming</span></span>  
 <span data-ttu-id="80323-110">As seguintes condições podem causar uma exceção:</span><span class="sxs-lookup"><span data-stu-id="80323-110">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="80323-111">O nome do diretório está malformado.</span><span class="sxs-lookup"><span data-stu-id="80323-111">The directory name is malformed.</span></span> <span data-ttu-id="80323-112">Por exemplo, ele contém caracteres inválidos ou é somente um espaço em branco (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="80323-112">For example, it contains illegal characters or is only white space (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="80323-113">O diretório pai do diretório a ser criado é somente leitura (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="80323-113">The parent directory of the directory to be created is read-only (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="80323-114">O nome do diretório é `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="80323-114">The directory name is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="80323-115">O nome do diretório é muito longo (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="80323-115">The directory name is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="80323-116">O nome do diretório é um sinal de dois pontos ":" (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="80323-116">The directory name is a colon ":" (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="80323-117">O usuário não tem permissão para criar o diretório (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="80323-117">The user does not have permission to create the directory (<xref:System.UnauthorizedAccessException>).</span></span>  
  
-   <span data-ttu-id="80323-118">O usuário não possui permissões em uma situação de confiança parcial (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="80323-118">The user lacks permissions in a partial-trust situation (<xref:System.Security.SecurityException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80323-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="80323-119">See Also</span></span>  
 <span data-ttu-id="80323-120"><xref:Microsoft.VisualBasic.FileIO.FileSystem.CreateDirectory%2A></span><span class="sxs-lookup"><span data-stu-id="80323-120"><xref:Microsoft.VisualBasic.FileIO.FileSystem.CreateDirectory%2A></span></span>   
 [<span data-ttu-id="80323-121">Criando, excluindo e movendo arquivos e diretórios</span><span class="sxs-lookup"><span data-stu-id="80323-121">Creating, Deleting, and Moving Files and Directories</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/creating-deleting-and-moving-files-and-directories.md)

