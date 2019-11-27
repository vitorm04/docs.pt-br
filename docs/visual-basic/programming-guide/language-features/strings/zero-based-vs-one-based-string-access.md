---
title: Acesso de cadeia de caracteres baseado em zero versus um
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
# <a name="zero-based-vs-one-based-string-access-in-visual-basic"></a><span data-ttu-id="ac66c-102">Acesso à cadeia de caracteres com base em zero versus em um no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ac66c-102">Zero-based vs. One-based String Access in Visual Basic</span></span>
<span data-ttu-id="ac66c-103">Este tópico compara como Visual Basic e o .NET Framework fornecem acesso aos caracteres em uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="ac66c-103">This topic compares how Visual Basic and the .NET Framework provide access to the characters in a string.</span></span> <span data-ttu-id="ac66c-104">O .NET Framework sempre fornece acesso baseado em zero aos caracteres em uma cadeia de caracteres, enquanto Visual Basic fornece acesso baseado em zero e um baseado em um, dependendo da função.</span><span class="sxs-lookup"><span data-stu-id="ac66c-104">The .NET Framework always provides zero-based access to the characters in a string, whereas Visual Basic provides zero-based and one-based access, depending on the function.</span></span>  
  
## <a name="one-based"></a><span data-ttu-id="ac66c-105">Baseado em um</span><span class="sxs-lookup"><span data-stu-id="ac66c-105">One-Based</span></span>  
 <span data-ttu-id="ac66c-106">Para obter um exemplo de uma função de Visual Basic baseada em um, considere a função `Mid`.</span><span class="sxs-lookup"><span data-stu-id="ac66c-106">For an example of a one-based Visual Basic function, consider the `Mid` function.</span></span> <span data-ttu-id="ac66c-107">Ele usa um argumento que indica a posição do caractere na qual a subcadeia de caracteres será iniciada, começando com a posição 1.</span><span class="sxs-lookup"><span data-stu-id="ac66c-107">It takes an argument that indicates the character position at which the substring will start, starting with position 1.</span></span> <span data-ttu-id="ac66c-108">O método .NET Framework <xref:System.String.Substring%2A?displayProperty=nameWithType> usa um índice do caractere na cadeia de caracteres na qual a subcadeia de caracteres é iniciada, começando com a posição 0.</span><span class="sxs-lookup"><span data-stu-id="ac66c-108">The .NET Framework <xref:System.String.Substring%2A?displayProperty=nameWithType> method takes an index of the character in the string at which the substring is to start, starting with position 0.</span></span> <span data-ttu-id="ac66c-109">Portanto, se você tiver uma cadeia de caracteres "ABCDE", os caracteres individuais serão numerados como 1, 2, 3, 4, 5 para uso com a função `Mid`, mas 0, 1, 2, 3, 4 para uso com o método <xref:System.String.Substring%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ac66c-109">Thus, if you have a string "ABCDE", the individual characters are numbered 1,2,3,4,5 for use with the `Mid` function, but 0,1,2,3,4 for use with the <xref:System.String.Substring%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="zero-based"></a><span data-ttu-id="ac66c-110">Baseado em zero</span><span class="sxs-lookup"><span data-stu-id="ac66c-110">Zero-Based</span></span>  
 <span data-ttu-id="ac66c-111">Para obter um exemplo de uma função de Visual Basic com base em zero, considere a função `Split`.</span><span class="sxs-lookup"><span data-stu-id="ac66c-111">For an example of a zero-based Visual Basic function, consider the `Split` function.</span></span> <span data-ttu-id="ac66c-112">Ele divide uma cadeia de caracteres e retorna uma matriz que contém as subcadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="ac66c-112">It splits a string and returns an array containing the substrings.</span></span> <span data-ttu-id="ac66c-113">O método .NET Framework <xref:System.String.Split%2A?displayProperty=nameWithType> também divide uma cadeia de caracteres e retorna uma matriz que contém as subcadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="ac66c-113">The .NET Framework <xref:System.String.Split%2A?displayProperty=nameWithType> method also splits a string and returns an array containing the substrings.</span></span> <span data-ttu-id="ac66c-114">Como a função `Split` e o método <xref:System.String.Split%2A> retornam .NET Framework matrizes, elas devem ser baseadas em zero.</span><span class="sxs-lookup"><span data-stu-id="ac66c-114">Because the `Split` function and <xref:System.String.Split%2A> method return .NET Framework arrays, they must be zero-based.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac66c-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ac66c-115">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.Mid%2A>
- <xref:Microsoft.VisualBasic.Strings.Split%2A>
- <xref:System.String.Substring%2A>
- <xref:System.String.Split%2A>
- [<span data-ttu-id="ac66c-116">Introdução às cadeias de caracteres no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ac66c-116">Introduction to Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
