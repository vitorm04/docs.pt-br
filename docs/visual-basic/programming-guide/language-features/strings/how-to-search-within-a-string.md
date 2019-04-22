---
title: 'Como: Pesquisar em uma cadeia de caracteres (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], finding
- strings [Visual Basic], searching
- examples [Visual Basic], strings
ms.assetid: ae4c79e0-08ea-489f-bdb2-5eb6d355f284
ms.openlocfilehash: b690aa78a2cf07b0db5bdd28d7d71ed4a79fbf61
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58823292"
---
# <a name="how-to-search-within-a-string-visual-basic"></a><span data-ttu-id="b7591-102">Como: Pesquisar em uma cadeia de caracteres (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b7591-102">How to: Search Within a String (Visual Basic)</span></span>
<span data-ttu-id="b7591-103">Este exemplo chama o <xref:System.String.IndexOf%2A> método em um <xref:System.String> objeto para relatar o índice da primeira ocorrência de uma subcadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="b7591-103">This example calls the <xref:System.String.IndexOf%2A> method on a <xref:System.String> object to report the index of the first occurrence of a substring.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b7591-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b7591-104">Example</span></span>  
 [!code-vb[VbVbalrStrings#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#71)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b7591-105">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="b7591-105">Compiling the Code</span></span>  
 <span data-ttu-id="b7591-106">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="b7591-106">This example requires:</span></span>  
  
-   <span data-ttu-id="b7591-107">Uma `Imports` instrução que especifica o <xref:System> namespace.</span><span class="sxs-lookup"><span data-stu-id="b7591-107">An `Imports` statement specifying the <xref:System> namespace.</span></span> <span data-ttu-id="b7591-108">Para obter mais informações, consulte [Instrução Imports (tipo e namespace .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="b7591-108">For more information, see [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="b7591-109">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="b7591-109">Robust Programming</span></span>  
 <span data-ttu-id="b7591-110">O <xref:System.String.IndexOf%2A> método relata o local do primeiro caractere da primeira ocorrência da subcadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="b7591-110">The <xref:System.String.IndexOf%2A> method reports the location of the first character of the first occurrence of the substring.</span></span> <span data-ttu-id="b7591-111">O índice é baseado em 0, o que significa que o primeiro caractere de uma cadeia de caracteres tem um índice de 0.</span><span class="sxs-lookup"><span data-stu-id="b7591-111">The index is 0-based, which means the first character of a string has an index of 0.</span></span>  
  
 <span data-ttu-id="b7591-112">Se <xref:System.String.IndexOf%2A> não localizar a subcadeia de caracteres, ele retornará -1.</span><span class="sxs-lookup"><span data-stu-id="b7591-112">If <xref:System.String.IndexOf%2A> does not find the substring, it returns -1.</span></span>  
  
 <span data-ttu-id="b7591-113">O <xref:System.String.IndexOf%2A> método diferencia maiusculas de minúsculas e usa a cultura atual.</span><span class="sxs-lookup"><span data-stu-id="b7591-113">The <xref:System.String.IndexOf%2A> method is case-sensitive and uses the current culture.</span></span>  
  
 <span data-ttu-id="b7591-114">Para controle de erro ideal, você talvez queira incluir a pesquisa de cadeia de caracteres na `Try` block de um [tente... Catch... Instrução Finally](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) construção.</span><span class="sxs-lookup"><span data-stu-id="b7591-114">For optimal error control, you might want to enclose the string search in the `Try` block of a [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) construction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7591-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b7591-115">See also</span></span>

- <xref:System.String.IndexOf%2A>
- [<span data-ttu-id="b7591-116">Instrução Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="b7591-116">Try...Catch...Finally Statement</span></span>](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="b7591-117">Introdução às cadeias de caracteres no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b7591-117">Introduction to Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
- [<span data-ttu-id="b7591-118">Cadeias de Caracteres</span><span class="sxs-lookup"><span data-stu-id="b7591-118">Strings</span></span>](../../../../visual-basic/programming-guide/language-features/strings/index.md)
