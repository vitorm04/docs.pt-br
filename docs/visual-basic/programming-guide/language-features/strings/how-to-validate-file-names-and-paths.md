---
title: 'Como: Validar nomes de arquivo e caminhos no Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- file names [Visual Basic], validating
- strings [Visual Basic], validating
- Boolean values [Visual Basic]
- paths [Visual Basic], validating
ms.assetid: f673462d-57b7-4120-b13a-6a7592f7ab2c
ms.openlocfilehash: d29553071d68319d754406b3104da6e096f908fd
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56975518"
---
# <a name="how-to-validate-file-names-and-paths-in-visual-basic"></a><span data-ttu-id="821b8-102">Como: Validar nomes de arquivo e caminhos no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="821b8-102">How to: Validate File Names and Paths in Visual Basic</span></span>
<span data-ttu-id="821b8-103">Este exemplo retorna um `Boolean` valor que indica se uma cadeia de caracteres representa um nome de arquivo ou caminho.</span><span class="sxs-lookup"><span data-stu-id="821b8-103">This example returns a `Boolean` value that indicates whether a string represents a file name or path.</span></span> <span data-ttu-id="821b8-104">A validação verifica se o nome contém caracteres que não são permitidos pelo sistema de arquivos.</span><span class="sxs-lookup"><span data-stu-id="821b8-104">The validation checks if the name contains characters that are not allowed by the file system.</span></span>  
  
## <a name="example"></a><span data-ttu-id="821b8-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="821b8-105">Example</span></span>  
 [!code-vb[VbVbcnRegEx#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#4)]  
  
 <span data-ttu-id="821b8-106">Este exemplo verifica se o nome tiver colocado incorretamente dois-pontos ou diretórios sem nome ou se o comprimento do nome excede o comprimento máximo definido pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="821b8-106">This example does not check if the name has incorrectly placed colons, or directories with no name, or if the length of the name exceeds the system-defined maximum length.</span></span> <span data-ttu-id="821b8-107">Ele também verifica se o aplicativo tem permissão para acessar o recurso de sistema de arquivos com o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="821b8-107">It also does not check if the application has permission to access the file-system resource with the specified name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="821b8-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="821b8-108">See also</span></span>
- <xref:System.IO.Path.GetInvalidPathChars%2A>
- [<span data-ttu-id="821b8-109">Validando cadeias de caracteres no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="821b8-109">Validating Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
