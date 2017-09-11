---
title: 'Como: pesquisar em uma cadeia de caracteres (Visual Basic) | Documentos do Microsoft'
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
- strings [Visual Basic], finding
- strings [Visual Basic], searching
- examples [Visual Basic], strings
ms.assetid: ae4c79e0-08ea-489f-bdb2-5eb6d355f284
caps.latest.revision: 16
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
ms.openlocfilehash: 4d451dfa5e22c6ed490e2ded5fec4ea4db6f0b68
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-search-within-a-string-visual-basic"></a><span data-ttu-id="67f67-102">Como pesquisar em uma cadeia de caracteres (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="67f67-102">How to: Search Within a String (Visual Basic)</span></span>
<span data-ttu-id="67f67-103">Este exemplo chama o <xref:System.String.IndexOf%2A>método em uma <xref:System.String>objeto para relatar o índice da primeira ocorrência de uma subcadeia.</xref:System.String> </xref:System.String.IndexOf%2A></span><span class="sxs-lookup"><span data-stu-id="67f67-103">This example calls the <xref:System.String.IndexOf%2A> method on a <xref:System.String> object to report the index of the first occurrence of a substring.</span></span>  
  
## <a name="example"></a><span data-ttu-id="67f67-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="67f67-104">Example</span></span>  
 <span data-ttu-id="67f67-105">[!code-vb[VbVbalrStrings&#71;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-search-within-a-string_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="67f67-105">[!code-vb[VbVbalrStrings#71](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-search-within-a-string_1.vb)]</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="67f67-106">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="67f67-106">Compiling the Code</span></span>  
 <span data-ttu-id="67f67-107">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="67f67-107">This example requires:</span></span>  
  
-   <span data-ttu-id="67f67-108">Um `Imports` instrução especificando o <xref:System>namespace.</xref:System></span><span class="sxs-lookup"><span data-stu-id="67f67-108">An `Imports` statement specifying the <xref:System> namespace.</span></span> <span data-ttu-id="67f67-109">Para obter mais informações, consulte [instrução Imports (tipo e Namespace .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="67f67-109">For more information, see [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="67f67-110">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="67f67-110">Robust Programming</span></span>  
 <span data-ttu-id="67f67-111">O <xref:System.String.IndexOf%2A>método reporta a localização do primeiro caractere da primeira ocorrência da subsequência.</xref:System.String.IndexOf%2A></span><span class="sxs-lookup"><span data-stu-id="67f67-111">The <xref:System.String.IndexOf%2A> method reports the location of the first character of the first occurrence of the substring.</span></span> <span data-ttu-id="67f67-112">O índice é baseado em 0, o que significa que o primeiro caractere de uma cadeia de caracteres tem um índice 0.</span><span class="sxs-lookup"><span data-stu-id="67f67-112">The index is 0-based, which means the first character of a string has an index of 0.</span></span>  
  
 <span data-ttu-id="67f67-113">Se <xref:System.String.IndexOf%2A>não localizar a subcadeia de caracteres, ele retornará -1.</xref:System.String.IndexOf%2A></span><span class="sxs-lookup"><span data-stu-id="67f67-113">If <xref:System.String.IndexOf%2A> does not find the substring, it returns -1.</span></span>  
  
 <span data-ttu-id="67f67-114">O <xref:System.String.IndexOf%2A>método diferencia maiusculas de minúsculas e usa a cultura atual.</xref:System.String.IndexOf%2A></span><span class="sxs-lookup"><span data-stu-id="67f67-114">The <xref:System.String.IndexOf%2A> method is case-sensitive and uses the current culture.</span></span>  
  
 <span data-ttu-id="67f67-115">Para controle de erro ideal, talvez você queira incluir a pesquisa de cadeia de caracteres no `Try` bloco de um [Try... Catch... Instrução Finally](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) construção.</span><span class="sxs-lookup"><span data-stu-id="67f67-115">For optimal error control, you might want to enclose the string search in the `Try` block of a [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) construction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67f67-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="67f67-116">See Also</span></span>  
 <span data-ttu-id="67f67-117"><xref:System.String.IndexOf%2A></xref:System.String.IndexOf%2A></span><span class="sxs-lookup"><span data-stu-id="67f67-117"><xref:System.String.IndexOf%2A></span></span>   
<span data-ttu-id="67f67-118"> [Instrução Try...Catch...Finally](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) </span><span class="sxs-lookup"><span data-stu-id="67f67-118"> [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) </span></span>  
<span data-ttu-id="67f67-119"> [Introdução a cadeias de caracteres no Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md) </span><span class="sxs-lookup"><span data-stu-id="67f67-119"> [Introduction to Strings in Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md) </span></span>  
<span data-ttu-id="67f67-120"> [Cadeias de Caracteres](../../../../visual-basic/programming-guide/language-features/strings/index.md)</span><span class="sxs-lookup"><span data-stu-id="67f67-120"> [Strings](../../../../visual-basic/programming-guide/language-features/strings/index.md)</span></span>
