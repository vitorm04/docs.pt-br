---
title: 'Como: validar nomes de arquivo e caminhos no Visual Basic | Documentos do Microsoft'
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
- file names, validating
- strings [Visual Basic], validating
- Boolean values
- paths, validating
ms.assetid: f673462d-57b7-4120-b13a-6a7592f7ab2c
caps.latest.revision: 7
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 1f9a96ebad94d3416431defafdacb2bbb110f199
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-validate-file-names-and-paths-in-visual-basic"></a><span data-ttu-id="e47c6-102">Como validar nomes de arquivo e demarcadores no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e47c6-102">How to: Validate File Names and Paths in Visual Basic</span></span>
<span data-ttu-id="e47c6-103">Este exemplo retorna um `Boolean` valor que indica se uma cadeia de caracteres representa um nome de arquivo ou caminho.</span><span class="sxs-lookup"><span data-stu-id="e47c6-103">This example returns a `Boolean` value that indicates whether a string represents a file name or path.</span></span> <span data-ttu-id="e47c6-104">A validação verifica se o nome contém caracteres que não são permitidos pelo sistema de arquivos.</span><span class="sxs-lookup"><span data-stu-id="e47c6-104">The validation checks if the name contains characters that are not allowed by the file system.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e47c6-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e47c6-105">Example</span></span>  
 <span data-ttu-id="e47c6-106">[!code-vb[VbVbcnRegEx n º&4;](../../../../visual-basic/programming-guide/language-features/strings/codesnippet/VisualBasic/how-to-validate-file-names-and-paths_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="e47c6-106">[!code-vb[VbVbcnRegEx#4](../../../../visual-basic/programming-guide/language-features/strings/codesnippet/VisualBasic/how-to-validate-file-names-and-paths_1.vb)]</span></span>  
  
 <span data-ttu-id="e47c6-107">Este exemplo verifica se o nome tiver colocado incorretamente dois-pontos ou diretórios sem nome, ou se o comprimento do nome excede o comprimento máximo definido pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="e47c6-107">This example does not check if the name has incorrectly placed colons, or directories with no name, or if the length of the name exceeds the system-defined maximum length.</span></span> <span data-ttu-id="e47c6-108">Ele também verifica se o aplicativo tem permissão para acessar o recurso de sistema de arquivos com o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="e47c6-108">It also does not check if the application has permission to access the file-system resource with the specified name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e47c6-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e47c6-109">See Also</span></span>  
 <span data-ttu-id="e47c6-110"><xref:System.IO.Path.GetInvalidPathChars%2A></xref:System.IO.Path.GetInvalidPathChars%2A></span><span class="sxs-lookup"><span data-stu-id="e47c6-110"><xref:System.IO.Path.GetInvalidPathChars%2A></span></span>   
<span data-ttu-id="e47c6-111"> [Validando cadeias de caracteres no Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)</span><span class="sxs-lookup"><span data-stu-id="e47c6-111"> [Validating Strings in Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)</span></span>
