---
title: Tipos de dados de caractere
ms.date: 07/20/2015
helpviewer_keywords:
- data types [Visual Basic], character
- String data type [Visual Basic], character data types
- character data types [Visual Basic]
- Char data type [Visual Basic], character data types
- data types [Visual Basic], choosing
ms.assetid: 902479ef-1679-47fc-9911-0c1c5008226c
ms.openlocfilehash: edd1d3a41dd878649aa422256b7858d7bce366e1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346389"
---
# <a name="character-data-types-visual-basic"></a><span data-ttu-id="f049c-102">Tipos de dados de caractere (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f049c-102">Character Data Types (Visual Basic)</span></span>
<span data-ttu-id="f049c-103">Visual Basic fornece *tipos de dados de caractere* para lidar com caracteres imprimíveis e exibíveis.</span><span class="sxs-lookup"><span data-stu-id="f049c-103">Visual Basic provides *character data types* to deal with printable and displayable characters.</span></span> <span data-ttu-id="f049c-104">Embora ambos lidem com caracteres Unicode, `Char` mantém um único caractere, enquanto `String` contém um número indefinido de caracteres.</span><span class="sxs-lookup"><span data-stu-id="f049c-104">While they both deal with Unicode characters, `Char` holds a single character whereas `String` contains an indefinite number of characters.</span></span>  
  
 <span data-ttu-id="f049c-105">Para uma tabela que exibe uma comparação lado a lado do Visual Basic tipos de dados, consulte tipos de [dados](../../../../visual-basic/language-reference/data-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="f049c-105">For a table that displays a side-by-side comparison of the Visual Basic data types, see [Data Types](../../../../visual-basic/language-reference/data-types/index.md).</span></span>  
  
## <a name="char-type"></a><span data-ttu-id="f049c-106">Tipo de caractere</span><span class="sxs-lookup"><span data-stu-id="f049c-106">Char Type</span></span>  
 <span data-ttu-id="f049c-107">O tipo de dados `Char` é um caractere Unicode único de dois bytes (16 bits).</span><span class="sxs-lookup"><span data-stu-id="f049c-107">The `Char` data type is a single two-byte (16-bit) Unicode character.</span></span> <span data-ttu-id="f049c-108">Se uma variável sempre armazenar exatamente um caractere, declare-a como `Char`.</span><span class="sxs-lookup"><span data-stu-id="f049c-108">If a variable always stores exactly one character, declare it as `Char`.</span></span> <span data-ttu-id="f049c-109">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="f049c-109">For example:</span></span>  
  
 [!code-vb[VbVbalrCharTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#1)]
  
 <span data-ttu-id="f049c-110">Cada valor possível em uma variável `Char` ou `String` é um *ponto de código*, ou código de caractere, no conjunto de caracteres Unicode.</span><span class="sxs-lookup"><span data-stu-id="f049c-110">Each possible value in a `Char` or `String` variable is a *code point*, or character code, in the Unicode character set.</span></span> <span data-ttu-id="f049c-111">Os caracteres Unicode incluem o conjunto de caracteres ASCII básico, várias outras letras do alfabeto, acentos, símbolos monetários, frações, sinais diacríticos e símbolos matemáticos e técnicos.</span><span class="sxs-lookup"><span data-stu-id="f049c-111">Unicode characters include the basic ASCII character set, various other alphabet letters, accents, currency symbols, fractions, diacritics, and mathematical and technical symbols.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f049c-112">O conjunto de caracteres Unicode reserva os pontos de código D800 por meio de DFFF (55296 a 55551 decimal) para *pares substitutos*, que exigem valores de 2 16 bits para representar um único ponto de código.</span><span class="sxs-lookup"><span data-stu-id="f049c-112">The Unicode character set reserves the code points D800 through DFFF (55296 through 55551 decimal) for *surrogate pairs*, which require two 16-bit values to represent a single code point.</span></span> <span data-ttu-id="f049c-113">Uma variável `Char` não pode conter um par substituto e uma `String` usa duas posições para manter esse par.</span><span class="sxs-lookup"><span data-stu-id="f049c-113">A `Char` variable cannot hold a surrogate pair, and a `String` uses two positions to hold such a pair.</span></span>  
  
 <span data-ttu-id="f049c-114">Para obter mais informações, consulte [Char Data Type](../../../../visual-basic/language-reference/data-types/char-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="f049c-114">For more information, see [Char Data Type](../../../../visual-basic/language-reference/data-types/char-data-type.md).</span></span>  
  
## <a name="string-type"></a><span data-ttu-id="f049c-115">Tipo de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="f049c-115">String Type</span></span>  
 <span data-ttu-id="f049c-116">O tipo de dados `String` é uma sequência de zero ou mais caracteres Unicode de dois bytes (16 bits).</span><span class="sxs-lookup"><span data-stu-id="f049c-116">The `String` data type is a sequence of zero or more two-byte (16-bit) Unicode characters.</span></span> <span data-ttu-id="f049c-117">Se uma variável puder conter um número indefinido de caracteres, declare-a como `String`.</span><span class="sxs-lookup"><span data-stu-id="f049c-117">If a variable can contain an indefinite number of characters, declare it as `String`.</span></span> <span data-ttu-id="f049c-118">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="f049c-118">For example:</span></span>  
  
 [!code-vb[VbVbalrCharTypes#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#2)]
  
 <span data-ttu-id="f049c-119">Para obter mais informações, consulte [cadeia de caracteres tipo de dados](../../../../visual-basic/language-reference/data-types/string-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="f049c-119">For more information, see [String Data Type](../../../../visual-basic/language-reference/data-types/string-data-type.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f049c-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f049c-120">See also</span></span>

- [<span data-ttu-id="f049c-121">Tipos de Dados Elementares</span><span class="sxs-lookup"><span data-stu-id="f049c-121">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [<span data-ttu-id="f049c-122">Tipos de Dados Compostos</span><span class="sxs-lookup"><span data-stu-id="f049c-122">Composite Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [<span data-ttu-id="f049c-123">Tipos genéricos no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f049c-123">Generic Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="f049c-124">Tipos de Valor e Tipos de Referência</span><span class="sxs-lookup"><span data-stu-id="f049c-124">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [<span data-ttu-id="f049c-125">Conversões de tipo no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f049c-125">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="f049c-126">Solução de problemas de Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="f049c-126">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="f049c-127">Caracteres de Tipo</span><span class="sxs-lookup"><span data-stu-id="f049c-127">Type Characters</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
