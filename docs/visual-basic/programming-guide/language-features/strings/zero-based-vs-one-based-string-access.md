---
title: Acesso de cadeia de caracteres baseado em zero versus um
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], indexing
ms.assetid: 0ed39f35-d68e-421d-ae14-460a5c0373b8
ms.openlocfilehash: 91d3fb9d7bfdf3d5af27fc6499583640946a802f
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91072282"
---
# <a name="zero-based-vs-one-based-string-access-in-visual-basic"></a><span data-ttu-id="623ad-102">Acesso à cadeia de caracteres com base em zero versus em um no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="623ad-102">Zero-based vs. One-based String Access in Visual Basic</span></span>

<span data-ttu-id="623ad-103">Este tópico compara como Visual Basic e o .NET Framework fornecem acesso aos caracteres em uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="623ad-103">This topic compares how Visual Basic and the .NET Framework provide access to the characters in a string.</span></span> <span data-ttu-id="623ad-104">O .NET Framework sempre fornece acesso baseado em zero aos caracteres em uma cadeia de caracteres, enquanto Visual Basic fornece acesso baseado em zero e um baseado em um, dependendo da função.</span><span class="sxs-lookup"><span data-stu-id="623ad-104">The .NET Framework always provides zero-based access to the characters in a string, whereas Visual Basic provides zero-based and one-based access, depending on the function.</span></span>  
  
## <a name="one-based"></a><span data-ttu-id="623ad-105">Baseado em um</span><span class="sxs-lookup"><span data-stu-id="623ad-105">One-Based</span></span>  

 <span data-ttu-id="623ad-106">Para obter um exemplo de uma função de Visual Basic baseada em um, considere a `Mid` função.</span><span class="sxs-lookup"><span data-stu-id="623ad-106">For an example of a one-based Visual Basic function, consider the `Mid` function.</span></span> <span data-ttu-id="623ad-107">Ele usa um argumento que indica a posição do caractere na qual a subcadeia de caracteres será iniciada, começando com a posição 1.</span><span class="sxs-lookup"><span data-stu-id="623ad-107">It takes an argument that indicates the character position at which the substring will start, starting with position 1.</span></span> <span data-ttu-id="623ad-108">O <xref:System.String.Substring%2A?displayProperty=nameWithType> método .NET Framework usa um índice do caractere na cadeia de caracteres na qual a subcadeia de caracteres é iniciada, começando com a posição 0.</span><span class="sxs-lookup"><span data-stu-id="623ad-108">The .NET Framework <xref:System.String.Substring%2A?displayProperty=nameWithType> method takes an index of the character in the string at which the substring is to start, starting with position 0.</span></span> <span data-ttu-id="623ad-109">Portanto, se você tiver uma cadeia de caracteres "ABCDE", os caracteres individuais serão numerados como 1, 2, 3, 4, 5 para uso com a `Mid` função, mas 0, 1, 2, 3, 4 para uso com o <xref:System.String.Substring%2A?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="623ad-109">Thus, if you have a string "ABCDE", the individual characters are numbered 1,2,3,4,5 for use with the `Mid` function, but 0,1,2,3,4 for use with the <xref:System.String.Substring%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="zero-based"></a><span data-ttu-id="623ad-110">Baseado em zero</span><span class="sxs-lookup"><span data-stu-id="623ad-110">Zero-Based</span></span>  

 <span data-ttu-id="623ad-111">Para obter um exemplo de uma função de Visual Basic com base em zero, considere a `Split` função.</span><span class="sxs-lookup"><span data-stu-id="623ad-111">For an example of a zero-based Visual Basic function, consider the `Split` function.</span></span> <span data-ttu-id="623ad-112">Ele divide uma cadeia de caracteres e retorna uma matriz que contém as subcadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="623ad-112">It splits a string and returns an array containing the substrings.</span></span> <span data-ttu-id="623ad-113">O <xref:System.String.Split%2A?displayProperty=nameWithType> método .NET Framework também divide uma cadeia de caracteres e retorna uma matriz que contém as subcadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="623ad-113">The .NET Framework <xref:System.String.Split%2A?displayProperty=nameWithType> method also splits a string and returns an array containing the substrings.</span></span> <span data-ttu-id="623ad-114">Como a `Split` função e o <xref:System.String.Split%2A> método retornam .NET Framework matrizes, eles devem ser baseados em zero.</span><span class="sxs-lookup"><span data-stu-id="623ad-114">Because the `Split` function and <xref:System.String.Split%2A> method return .NET Framework arrays, they must be zero-based.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="623ad-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="623ad-115">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.Mid%2A>
- <xref:Microsoft.VisualBasic.Strings.Split%2A>
- <xref:System.String.Substring%2A>
- <xref:System.String.Split%2A>
- [<span data-ttu-id="623ad-116">Introdução a cadeias de caracteres no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="623ad-116">Introduction to Strings in Visual Basic</span></span>](introduction-to-strings.md)
