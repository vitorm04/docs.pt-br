---
title: Zero-based vs. One-based String Access
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], indexing
ms.assetid: 0ed39f35-d68e-421d-ae14-460a5c0373b8
ms.openlocfilehash: 97e60038bc7ec0f030939d0980b786bffebcfb9a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354295"
---
# <a name="zero-based-vs-one-based-string-access-in-visual-basic"></a><span data-ttu-id="b3634-102">Acesso à cadeia de caracteres com base em zero versus em um no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b3634-102">Zero-based vs. One-based String Access in Visual Basic</span></span>
<span data-ttu-id="b3634-103">This topic compares how Visual Basic and the .NET Framework provide access to the characters in a string.</span><span class="sxs-lookup"><span data-stu-id="b3634-103">This topic compares how Visual Basic and the .NET Framework provide access to the characters in a string.</span></span> <span data-ttu-id="b3634-104">The .NET Framework always provides zero-based access to the characters in a string, whereas Visual Basic provides zero-based and one-based access, depending on the function.</span><span class="sxs-lookup"><span data-stu-id="b3634-104">The .NET Framework always provides zero-based access to the characters in a string, whereas Visual Basic provides zero-based and one-based access, depending on the function.</span></span>  
  
## <a name="one-based"></a><span data-ttu-id="b3634-105">One-Based</span><span class="sxs-lookup"><span data-stu-id="b3634-105">One-Based</span></span>  
 <span data-ttu-id="b3634-106">For an example of a one-based Visual Basic function, consider the `Mid` function.</span><span class="sxs-lookup"><span data-stu-id="b3634-106">For an example of a one-based Visual Basic function, consider the `Mid` function.</span></span> <span data-ttu-id="b3634-107">It takes an argument that indicates the character position at which the substring will start, starting with position 1.</span><span class="sxs-lookup"><span data-stu-id="b3634-107">It takes an argument that indicates the character position at which the substring will start, starting with position 1.</span></span> <span data-ttu-id="b3634-108">The .NET Framework <xref:System.String.Substring%2A?displayProperty=nameWithType> method takes an index of the character in the string at which the substring is to start, starting with position 0.</span><span class="sxs-lookup"><span data-stu-id="b3634-108">The .NET Framework <xref:System.String.Substring%2A?displayProperty=nameWithType> method takes an index of the character in the string at which the substring is to start, starting with position 0.</span></span> <span data-ttu-id="b3634-109">Thus, if you have a string "ABCDE", the individual characters are numbered 1,2,3,4,5 for use with the `Mid` function, but 0,1,2,3,4 for use with the <xref:System.String.Substring%2A?displayProperty=nameWithType> method.</span><span class="sxs-lookup"><span data-stu-id="b3634-109">Thus, if you have a string "ABCDE", the individual characters are numbered 1,2,3,4,5 for use with the `Mid` function, but 0,1,2,3,4 for use with the <xref:System.String.Substring%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="zero-based"></a><span data-ttu-id="b3634-110">Zero-Based</span><span class="sxs-lookup"><span data-stu-id="b3634-110">Zero-Based</span></span>  
 <span data-ttu-id="b3634-111">For an example of a zero-based Visual Basic function, consider the `Split` function.</span><span class="sxs-lookup"><span data-stu-id="b3634-111">For an example of a zero-based Visual Basic function, consider the `Split` function.</span></span> <span data-ttu-id="b3634-112">It splits a string and returns an array containing the substrings.</span><span class="sxs-lookup"><span data-stu-id="b3634-112">It splits a string and returns an array containing the substrings.</span></span> <span data-ttu-id="b3634-113">The .NET Framework <xref:System.String.Split%2A?displayProperty=nameWithType> method also splits a string and returns an array containing the substrings.</span><span class="sxs-lookup"><span data-stu-id="b3634-113">The .NET Framework <xref:System.String.Split%2A?displayProperty=nameWithType> method also splits a string and returns an array containing the substrings.</span></span> <span data-ttu-id="b3634-114">Because the `Split` function and <xref:System.String.Split%2A> method return .NET Framework arrays, they must be zero-based.</span><span class="sxs-lookup"><span data-stu-id="b3634-114">Because the `Split` function and <xref:System.String.Split%2A> method return .NET Framework arrays, they must be zero-based.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3634-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b3634-115">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.Mid%2A>
- <xref:Microsoft.VisualBasic.Strings.Split%2A>
- <xref:System.String.Substring%2A>
- <xref:System.String.Split%2A>
- [<span data-ttu-id="b3634-116">Introdução às cadeias de caracteres no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b3634-116">Introduction to Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
