---
title: Tipos de dados de caractere (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- data types [Visual Basic], character
- String data type [Visual Basic], character data types
- character data types [Visual Basic]
- Char data type [Visual Basic], character data types
- data types [Visual Basic], choosing
ms.assetid: 902479ef-1679-47fc-9911-0c1c5008226c
ms.openlocfilehash: d29e8771d61c04cf35aa71b5ba7fbba0d308c730
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965684"
---
# <a name="character-data-types-visual-basic"></a><span data-ttu-id="9b993-102">Tipos de dados de caractere (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9b993-102">Character Data Types (Visual Basic)</span></span>
<span data-ttu-id="9b993-103">Visual Basic fornece *tipos de dados de caractere* para lidar com caracteres imprimíveis e exibíveis.</span><span class="sxs-lookup"><span data-stu-id="9b993-103">Visual Basic provides *character data types* to deal with printable and displayable characters.</span></span> <span data-ttu-id="9b993-104">Embora ambos lidem com caracteres Unicode, `Char` o mantém um único caractere `String` , enquanto contém um número indefinido de caracteres.</span><span class="sxs-lookup"><span data-stu-id="9b993-104">While they both deal with Unicode characters, `Char` holds a single character whereas `String` contains an indefinite number of characters.</span></span>  
  
 <span data-ttu-id="9b993-105">Para uma tabela que exibe uma comparação lado a lado do Visual Basic tipos de dados, consulte tipos de [dados](../../../../visual-basic/language-reference/data-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="9b993-105">For a table that displays a side-by-side comparison of the Visual Basic data types, see [Data Types](../../../../visual-basic/language-reference/data-types/index.md).</span></span>  
  
## <a name="char-type"></a><span data-ttu-id="9b993-106">Tipo de caractere</span><span class="sxs-lookup"><span data-stu-id="9b993-106">Char Type</span></span>  
 <span data-ttu-id="9b993-107">O `Char` tipo de dados é um caractere Unicode único de dois bytes (16 bits).</span><span class="sxs-lookup"><span data-stu-id="9b993-107">The `Char` data type is a single two-byte (16-bit) Unicode character.</span></span> <span data-ttu-id="9b993-108">Se uma variável sempre armazenar exatamente um caractere, declare-a `Char`como.</span><span class="sxs-lookup"><span data-stu-id="9b993-108">If a variable always stores exactly one character, declare it as `Char`.</span></span> <span data-ttu-id="9b993-109">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="9b993-109">For example:</span></span>  
  
 [!code-vb[VbVbalrCharTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#1)]
  
 <span data-ttu-id="9b993-110">Cada valor possível em uma `Char` variável `String` ou é um *ponto de código*, ou código de caractere, no conjunto de caracteres Unicode.</span><span class="sxs-lookup"><span data-stu-id="9b993-110">Each possible value in a `Char` or `String` variable is a *code point*, or character code, in the Unicode character set.</span></span> <span data-ttu-id="9b993-111">Os caracteres Unicode incluem o conjunto de caracteres ASCII básico, várias outras letras do alfabeto, acentos, símbolos monetários, frações, sinais diacríticos e símbolos matemáticos e técnicos.</span><span class="sxs-lookup"><span data-stu-id="9b993-111">Unicode characters include the basic ASCII character set, various other alphabet letters, accents, currency symbols, fractions, diacritics, and mathematical and technical symbols.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9b993-112">O conjunto de caracteres Unicode reserva os pontos de código D800 por meio de DFFF (55296 a 55551 decimal) para *pares substitutos*, que exigem valores de 2 16 bits para representar um único ponto de código.</span><span class="sxs-lookup"><span data-stu-id="9b993-112">The Unicode character set reserves the code points D800 through DFFF (55296 through 55551 decimal) for *surrogate pairs*, which require two 16-bit values to represent a single code point.</span></span> <span data-ttu-id="9b993-113">Uma `Char` variável não pode conter um par alternativo e uma `String` usa duas posições para manter esse par.</span><span class="sxs-lookup"><span data-stu-id="9b993-113">A `Char` variable cannot hold a surrogate pair, and a `String` uses two positions to hold such a pair.</span></span>  
  
 <span data-ttu-id="9b993-114">Para obter mais informações, consulte [Char Data Type](../../../../visual-basic/language-reference/data-types/char-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="9b993-114">For more information, see [Char Data Type](../../../../visual-basic/language-reference/data-types/char-data-type.md).</span></span>  
  
## <a name="string-type"></a><span data-ttu-id="9b993-115">Tipo de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="9b993-115">String Type</span></span>  
 <span data-ttu-id="9b993-116">O `String` tipo de dados é uma sequência de zero ou mais caracteres Unicode de dois bytes (16 bits).</span><span class="sxs-lookup"><span data-stu-id="9b993-116">The `String` data type is a sequence of zero or more two-byte (16-bit) Unicode characters.</span></span> <span data-ttu-id="9b993-117">Se uma variável puder conter um número indefinido de caracteres, declare- `String`a como.</span><span class="sxs-lookup"><span data-stu-id="9b993-117">If a variable can contain an indefinite number of characters, declare it as `String`.</span></span> <span data-ttu-id="9b993-118">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="9b993-118">For example:</span></span>  
  
 [!code-vb[VbVbalrCharTypes#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#2)]
  
 <span data-ttu-id="9b993-119">Para obter mais informações, consulte [cadeia de caracteres tipo de dados](../../../../visual-basic/language-reference/data-types/string-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="9b993-119">For more information, see [String Data Type](../../../../visual-basic/language-reference/data-types/string-data-type.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b993-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9b993-120">See also</span></span>

- [<span data-ttu-id="9b993-121">Tipos de Dados Elementares</span><span class="sxs-lookup"><span data-stu-id="9b993-121">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [<span data-ttu-id="9b993-122">Tipos de Dados Compostos</span><span class="sxs-lookup"><span data-stu-id="9b993-122">Composite Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [<span data-ttu-id="9b993-123">Tipos genéricos no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9b993-123">Generic Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="9b993-124">Tipos de Valor e Tipos de Referência</span><span class="sxs-lookup"><span data-stu-id="9b993-124">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [<span data-ttu-id="9b993-125">Conversões de tipo no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9b993-125">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="9b993-126">Solução de problemas de Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="9b993-126">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="9b993-127">Caracteres de Tipo</span><span class="sxs-lookup"><span data-stu-id="9b993-127">Type Characters</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
