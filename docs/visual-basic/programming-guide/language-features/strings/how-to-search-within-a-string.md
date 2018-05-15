---
title: Como pesquisar em uma cadeia de caracteres (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], finding
- strings [Visual Basic], searching
- examples [Visual Basic], strings
ms.assetid: ae4c79e0-08ea-489f-bdb2-5eb6d355f284
ms.openlocfilehash: 08a005f2927a76c9b29c1ff0092ea8282188b2b2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-search-within-a-string-visual-basic"></a><span data-ttu-id="64c93-102">Como pesquisar em uma cadeia de caracteres (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="64c93-102">How to: Search Within a String (Visual Basic)</span></span>
<span data-ttu-id="64c93-103">Este exemplo chama o <xref:System.String.IndexOf%2A> método em um <xref:System.String> objeto para relatar o índice da primeira ocorrência de uma subcadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="64c93-103">This example calls the <xref:System.String.IndexOf%2A> method on a <xref:System.String> object to report the index of the first occurrence of a substring.</span></span>  
  
## <a name="example"></a><span data-ttu-id="64c93-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="64c93-104">Example</span></span>  
 [!code-vb[VbVbalrStrings#71](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-search-within-a-string_1.vb)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="64c93-105">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="64c93-105">Compiling the Code</span></span>  
 <span data-ttu-id="64c93-106">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="64c93-106">This example requires:</span></span>  
  
-   <span data-ttu-id="64c93-107">Um `Imports` instrução especificando o <xref:System> namespace.</span><span class="sxs-lookup"><span data-stu-id="64c93-107">An `Imports` statement specifying the <xref:System> namespace.</span></span> <span data-ttu-id="64c93-108">Para obter mais informações, consulte [Instrução Imports (tipo e namespace .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="64c93-108">For more information, see [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="64c93-109">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="64c93-109">Robust Programming</span></span>  
 <span data-ttu-id="64c93-110">O <xref:System.String.IndexOf%2A> método reporta a localização do primeiro caractere da primeira ocorrência da subcadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="64c93-110">The <xref:System.String.IndexOf%2A> method reports the location of the first character of the first occurrence of the substring.</span></span> <span data-ttu-id="64c93-111">O índice é baseado em 0, o que significa que o primeiro caractere de uma cadeia de caracteres tem um índice de 0.</span><span class="sxs-lookup"><span data-stu-id="64c93-111">The index is 0-based, which means the first character of a string has an index of 0.</span></span>  
  
 <span data-ttu-id="64c93-112">Se <xref:System.String.IndexOf%2A> não encontre a subcadeia de caracteres, ele retornará -1.</span><span class="sxs-lookup"><span data-stu-id="64c93-112">If <xref:System.String.IndexOf%2A> does not find the substring, it returns -1.</span></span>  
  
 <span data-ttu-id="64c93-113">O <xref:System.String.IndexOf%2A> método diferencia maiusculas de minúsculas e usa a cultura atual.</span><span class="sxs-lookup"><span data-stu-id="64c93-113">The <xref:System.String.IndexOf%2A> method is case-sensitive and uses the current culture.</span></span>  
  
 <span data-ttu-id="64c93-114">Para o controle de erro ideal, talvez você queira colocar a pesquisa de cadeia de caracteres no `Try` block de um [tente... Catch... Instrução Finally](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) construção.</span><span class="sxs-lookup"><span data-stu-id="64c93-114">For optimal error control, you might want to enclose the string search in the `Try` block of a [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) construction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64c93-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="64c93-115">See Also</span></span>  
 <xref:System.String.IndexOf%2A>  
 [<span data-ttu-id="64c93-116">Instrução Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="64c93-116">Try...Catch...Finally Statement</span></span>](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [<span data-ttu-id="64c93-117">Introdução às cadeias de caracteres no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="64c93-117">Introduction to Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)  
 [<span data-ttu-id="64c93-118">Cadeias de Caracteres</span><span class="sxs-lookup"><span data-stu-id="64c93-118">Strings</span></span>](../../../../visual-basic/programming-guide/language-features/strings/index.md)
