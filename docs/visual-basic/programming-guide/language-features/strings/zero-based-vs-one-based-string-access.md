---
title: Acesso a cadeias de caracteres baseado em Acesso com base em uma cadeia de caracteres no Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], indexing
ms.assetid: 0ed39f35-d68e-421d-ae14-460a5c0373b8
ms.openlocfilehash: cc8f286de41d7e44225e889e73ff3c7b1fdbd881
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591755"
---
# <a name="zero-based-vs-one-based-string-access-in-visual-basic"></a><span data-ttu-id="3fe69-102">Acesso a cadeias de caracteres baseado em Acesso com base em uma cadeia de caracteres no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3fe69-102">Zero-based vs. One-based String Access in Visual Basic</span></span>
<span data-ttu-id="3fe69-103">Este tópico compara como Visual Basic e o .NET Framework fornecem acesso aos caracteres em uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="3fe69-103">This topic compares how Visual Basic and the .NET Framework provide access to the characters in a string.</span></span> <span data-ttu-id="3fe69-104">O .NET Framework sempre fornece acesso baseado em zero para os caracteres em uma cadeia de caracteres, enquanto o Visual Basic fornece acesso baseado em zero e um, dependendo da função.</span><span class="sxs-lookup"><span data-stu-id="3fe69-104">The .NET Framework always provides zero-based access to the characters in a string, whereas Visual Basic provides zero-based and one-based access, depending on the function.</span></span>  
  
## <a name="one-based"></a><span data-ttu-id="3fe69-105">Baseado em um</span><span class="sxs-lookup"><span data-stu-id="3fe69-105">One-Based</span></span>  
 <span data-ttu-id="3fe69-106">Para obter um exemplo de uma função do Visual Basic baseado em um, considere o `Mid` função.</span><span class="sxs-lookup"><span data-stu-id="3fe69-106">For an example of a one-based Visual Basic function, consider the `Mid` function.</span></span> <span data-ttu-id="3fe69-107">Ele usa um argumento que indica a posição do caractere no qual será iniciada a subcadeia de caracteres, começando pela posição 1.</span><span class="sxs-lookup"><span data-stu-id="3fe69-107">It takes an argument that indicates the character position at which the substring will start, starting with position 1.</span></span> <span data-ttu-id="3fe69-108">O .NET Framework <xref:System.String.Substring%2A?displayProperty=nameWithType> método utiliza um índice do caractere na cadeia de caracteres no qual a subcadeia de caracteres deve começar, começando pela posição 0.</span><span class="sxs-lookup"><span data-stu-id="3fe69-108">The .NET Framework <xref:System.String.Substring%2A?displayProperty=nameWithType> method takes an index of the character in the string at which the substring is to start, starting with position 0.</span></span> <span data-ttu-id="3fe69-109">Portanto, se você tiver uma cadeia de caracteres "ABCDE", os caracteres individuais são numerados 1,2,3,4,5 para uso com o `Mid` função, mas 0,1,2,3,4 para uso com o <xref:System.String.Substring%2A?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="3fe69-109">Thus, if you have a string "ABCDE", the individual characters are numbered 1,2,3,4,5 for use with the `Mid` function, but 0,1,2,3,4 for use with the <xref:System.String.Substring%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="zero-based"></a><span data-ttu-id="3fe69-110">Com base em zero</span><span class="sxs-lookup"><span data-stu-id="3fe69-110">Zero-Based</span></span>  
 <span data-ttu-id="3fe69-111">Para obter um exemplo de uma função do Visual Basic com base em zero, considere o `Split` função.</span><span class="sxs-lookup"><span data-stu-id="3fe69-111">For an example of a zero-based Visual Basic function, consider the `Split` function.</span></span> <span data-ttu-id="3fe69-112">Ele divide uma cadeia de caracteres e retorna uma matriz que contém as subcadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="3fe69-112">It splits a string and returns an array containing the substrings.</span></span> <span data-ttu-id="3fe69-113">O .NET Framework <xref:System.String.Split%2A?displayProperty=nameWithType> método também divide uma cadeia de caracteres e retorna uma matriz que contém as subcadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="3fe69-113">The .NET Framework <xref:System.String.Split%2A?displayProperty=nameWithType> method also splits a string and returns an array containing the substrings.</span></span> <span data-ttu-id="3fe69-114">Porque o `Split` função e <xref:System.String.Split%2A> método retornam matrizes do .NET Framework, eles devem ser baseado em zero.</span><span class="sxs-lookup"><span data-stu-id="3fe69-114">Because the `Split` function and <xref:System.String.Split%2A> method return .NET Framework arrays, they must be zero-based.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fe69-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3fe69-115">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.Mid%2A>
- <xref:Microsoft.VisualBasic.Strings.Split%2A>
- <xref:System.String.Substring%2A>
- <xref:System.String.Split%2A>
- [<span data-ttu-id="3fe69-116">Introdução às cadeias de caracteres no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3fe69-116">Introduction to Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
