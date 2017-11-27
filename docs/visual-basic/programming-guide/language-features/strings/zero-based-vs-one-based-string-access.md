---
title: Com base em zero vs. Acesso com base em uma cadeia de caracteres no Visual Basic
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: strings [Visual Basic], indexing
ms.assetid: 0ed39f35-d68e-421d-ae14-460a5c0373b8
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 911f063d6ca9a3f5d88a1f50d9df7f908a488f66
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="zero-based-vs-one-based-string-access-in-visual-basic"></a><span data-ttu-id="127be-102">Com base em zero vs. Acesso com base em uma cadeia de caracteres no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="127be-102">Zero-based vs. One-based String Access in Visual Basic</span></span>
<span data-ttu-id="127be-103">Este tópico compara como [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] e [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] fornecem acesso aos caracteres em uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="127be-103">This topic compares how [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] and the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] provide access to the characters in a string.</span></span> <span data-ttu-id="127be-104">O [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] sempre fornece acesso baseado em zero aos caracteres em uma cadeia de caracteres, enquanto [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] fornece acesso baseado em zero e um, dependendo da função.</span><span class="sxs-lookup"><span data-stu-id="127be-104">The [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] always provides zero-based access to the characters in a string, whereas [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] provides zero-based and one-based access, depending on the function.</span></span>  
  
## <a name="one-based"></a><span data-ttu-id="127be-105">Baseado em um</span><span class="sxs-lookup"><span data-stu-id="127be-105">One-Based</span></span>  
 <span data-ttu-id="127be-106">Para obter um exemplo de uma base de um [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] funcionar, considere o `Mid` função.</span><span class="sxs-lookup"><span data-stu-id="127be-106">For an example of a one-based [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] function, consider the `Mid` function.</span></span> <span data-ttu-id="127be-107">Ela tem um argumento que indica a posição do caractere no qual a subcadeia de caracteres será iniciada, começando pela posição 1.</span><span class="sxs-lookup"><span data-stu-id="127be-107">It takes an argument that indicates the character position at which the substring will start, starting with position 1.</span></span> <span data-ttu-id="127be-108">O [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.String.Substring%2A?displayProperty=nameWithType> método utiliza um índice de caractere na cadeia de caracteres na qual a subcadeia de caracteres é iniciada, começando pela posição 0.</span><span class="sxs-lookup"><span data-stu-id="127be-108">The [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.String.Substring%2A?displayProperty=nameWithType> method takes an index of the character in the string at which the substring is to start, starting with position 0.</span></span> <span data-ttu-id="127be-109">Portanto, se você tiver uma cadeia de caracteres "ABCDE", os caracteres individuais são numerados 1,2,3,4,5 para uso com o `Mid` função, mas 0,1,2,3,4 para uso com o <xref:System.String.Substring%2A?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="127be-109">Thus, if you have a string "ABCDE", the individual characters are numbered 1,2,3,4,5 for use with the `Mid` function, but 0,1,2,3,4 for use with the <xref:System.String.Substring%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="zero-based"></a><span data-ttu-id="127be-110">Com base em zero</span><span class="sxs-lookup"><span data-stu-id="127be-110">Zero-Based</span></span>  
 <span data-ttu-id="127be-111">Para obter um exemplo de uma base zero [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] funcionar, considere o `Split` função.</span><span class="sxs-lookup"><span data-stu-id="127be-111">For an example of a zero-based [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] function, consider the `Split` function.</span></span> <span data-ttu-id="127be-112">Ele divide uma cadeia de caracteres e retorna uma matriz que contém as subcadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="127be-112">It splits a string and returns an array containing the substrings.</span></span> <span data-ttu-id="127be-113">O [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.String.Split%2A?displayProperty=nameWithType> método também divide uma cadeia de caracteres e retorna uma matriz que contém as subcadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="127be-113">The [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.String.Split%2A?displayProperty=nameWithType> method also splits a string and returns an array containing the substrings.</span></span> <span data-ttu-id="127be-114">Porque o `Split` função e <xref:System.String.Split%2A> retorno do método [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] matrizes, eles devem ser com base em zero.</span><span class="sxs-lookup"><span data-stu-id="127be-114">Because the `Split` function and <xref:System.String.Split%2A> method return [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] arrays, they must be zero-based.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="127be-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="127be-115">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Strings.Mid%2A>  
 <xref:Microsoft.VisualBasic.Strings.Split%2A>  
 <xref:System.String.Substring%2A>  
 <xref:System.String.Split%2A>  
 [<span data-ttu-id="127be-116">Introdução às cadeias de caracteres no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="127be-116">Introduction to Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
