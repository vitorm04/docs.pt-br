---
title: Como retirar caracteres inválidos de uma cadeia de caracteres
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- regular expressions, examples
- cleaning input
- user input, examples
- .NET Framework regular expressions, examples
- regular expressions [.NET Framework], examples
- Regex.Replace method
- stripping invalid characters
- Replace method
- validating user input
ms.assetid: b4319c8a-9032-4129-a9d5-6f6fc28e7f32
ms.openlocfilehash: cc90e6609f9335b7e2f08271e5540b182901e8c9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127648"
---
# <a name="how-to-strip-invalid-characters-from-a-string"></a><span data-ttu-id="f67fb-102">Como retirar caracteres inválidos de uma cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="f67fb-102">How to: Strip Invalid Characters from a String</span></span>
<span data-ttu-id="f67fb-103">O exemplo a seguir usa o método <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> estático para retirar caracteres inválidos de uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="f67fb-103">The following example uses the static <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> method to strip invalid characters from a string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f67fb-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f67fb-104">Example</span></span>  
 <span data-ttu-id="f67fb-105">Você pode usar o método `CleanInput` definido neste exemplo para retirar caracteres potencialmente prejudiciais que tenham sido inseridos em um campo de texto que aceita entrada do usuário.</span><span class="sxs-lookup"><span data-stu-id="f67fb-105">You can use the `CleanInput` method defined in this example to strip potentially harmful characters that have been entered into a text field that accepts user input.</span></span> <span data-ttu-id="f67fb-106">Nesse caso, o `CleanInput` remove todos os caracteres não alfanuméricos, exceto pontos (.), arrobas (@) e hifens (-) e retorna a cadeia de caracteres restante.</span><span class="sxs-lookup"><span data-stu-id="f67fb-106">In this case, `CleanInput` strips out all nonalphanumeric characters except periods (.), at symbols (@), and hyphens (-), and returns the remaining string.</span></span> <span data-ttu-id="f67fb-107">No entanto, você pode modificar o padrão da expressão regular para que ela elimine qualquer caractere que não deve ser incluído em uma cadeia de caracteres de entrada.</span><span class="sxs-lookup"><span data-stu-id="f67fb-107">However, you can modify the regular expression pattern so that it strips out any characters that should not be included in an input string.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.StripChars#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.StripChars/cs/Example.cs#1)]
 [!code-vb[RegularExpressions.Examples.StripChars#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.StripChars/vb/Example.vb#1)]  
  
 <span data-ttu-id="f67fb-108">O padrão da expressão regular `[^\w\.@-]` corresponde a qualquer caractere que não seja um caractere de palavra, um ponto, um símbolo de @ ou um hífen.</span><span class="sxs-lookup"><span data-stu-id="f67fb-108">The regular expression pattern `[^\w\.@-]` matches any character that is not a word character, a period, an @ symbol, or a hyphen.</span></span> <span data-ttu-id="f67fb-109">Um caractere de palavra é qualquer letra, dígito decimal ou conector de pontuação, como um sublinhado.</span><span class="sxs-lookup"><span data-stu-id="f67fb-109">A word character is any letter, decimal digit, or punctuation connector such as an underscore.</span></span> <span data-ttu-id="f67fb-110">Qualquer caractere que corresponde a esse padrão é substituído pelo <xref:System.String.Empty?displayProperty=nameWithType>, que é a cadeia de caracteres definida pelo padrão de substituição.</span><span class="sxs-lookup"><span data-stu-id="f67fb-110">Any character that matches this pattern is replaced by <xref:System.String.Empty?displayProperty=nameWithType>, which is the string defined by the replacement pattern.</span></span> <span data-ttu-id="f67fb-111">Para permitir caracteres adicionais na entrada do usuário, adicione esses caracteres à classe de caractere no padrão de expressão regular.</span><span class="sxs-lookup"><span data-stu-id="f67fb-111">To allow additional characters in user input, add those characters to the character class in the regular expression pattern.</span></span> <span data-ttu-id="f67fb-112">Por exemplo, o padrão de expressão regular `[^\w\.@-\\%]` também permite um símbolo percentual e uma barra invertida em uma cadeia de caracteres de entrada.</span><span class="sxs-lookup"><span data-stu-id="f67fb-112">For example, the regular expression pattern `[^\w\.@-\\%]` also allows a percentage symbol and a backslash in an input string.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f67fb-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f67fb-113">See also</span></span>

- [<span data-ttu-id="f67fb-114">Expressões regulares do .NET</span><span class="sxs-lookup"><span data-stu-id="f67fb-114">.NET Regular Expressions</span></span>](../../../docs/standard/base-types/regular-expressions.md)
