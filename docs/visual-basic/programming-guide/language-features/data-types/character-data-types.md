---
title: Tipos de dados de caractere (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- data types [Visual Basic], character
- String data type [Visual Basic], character data types
- character data types [Visual Basic]
- Char data type [Visual Basic], character data types
- data types [Visual Basic], choosing
ms.assetid: 902479ef-1679-47fc-9911-0c1c5008226c
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d1066444ba3a98f26fc2a35135a50b2954c6b992
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="character-data-types-visual-basic"></a><span data-ttu-id="4abd6-102">Tipos de dados de caractere (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4abd6-102">Character Data Types (Visual Basic)</span></span>
[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="4abd6-103">Fornece *tipos de dados de caractere* para lidar com caracteres imprimível e pode ser exibido.</span><span class="sxs-lookup"><span data-stu-id="4abd6-103"> provides *character data types* to deal with printable and displayable characters.</span></span> <span data-ttu-id="4abd6-104">Enquanto ambos lidem com caracteres Unicode, `Char` contém um único caractere enquanto `String` contém um número indefinido de caracteres.</span><span class="sxs-lookup"><span data-stu-id="4abd6-104">While they both deal with Unicode characters, `Char` holds a single character whereas `String` contains an indefinite number of characters.</span></span>  
  
 <span data-ttu-id="4abd6-105">Para uma tabela que exibe uma comparação lado a lado do [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] tipos de dados, consulte [tipos de dados](../../../../visual-basic/language-reference/data-types/data-type-summary.md).</span><span class="sxs-lookup"><span data-stu-id="4abd6-105">For a table that displays a side-by-side comparison of the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] data types, see [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md).</span></span>  
  
## <a name="char-type"></a><span data-ttu-id="4abd6-106">Tipo char</span><span class="sxs-lookup"><span data-stu-id="4abd6-106">Char Type</span></span>  
 <span data-ttu-id="4abd6-107">O `Char` tipo de dados é um único caractere de Unicode de dois bytes (16 bits).</span><span class="sxs-lookup"><span data-stu-id="4abd6-107">The `Char` data type is a single two-byte (16-bit) Unicode character.</span></span> <span data-ttu-id="4abd6-108">Se uma variável sempre armazena exatamente um caractere, declare-o como `Char`.</span><span class="sxs-lookup"><span data-stu-id="4abd6-108">If a variable always stores exactly one character, declare it as `Char`.</span></span> <span data-ttu-id="4abd6-109">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="4abd6-109">For example:</span></span>  
  
 [!code-vb[VbVbalrCharTypes#1](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/character-data-types_1.vb)]  
  
 <span data-ttu-id="4abd6-110">Cada valor possível em um `Char` ou `String` variável é uma *ponto de código*, ou código de caractere no conjunto de caracteres Unicode.</span><span class="sxs-lookup"><span data-stu-id="4abd6-110">Each possible value in a `Char` or `String` variable is a *code point*, or character code, in the Unicode character set.</span></span> <span data-ttu-id="4abd6-111">Caracteres Unicode incluem o conjunto de caracteres ASCII básico, várias outras letras do alfabeto, acentos, símbolos de moeda, frações, diacríticos e símbolos matemáticos e técnicos.</span><span class="sxs-lookup"><span data-stu-id="4abd6-111">Unicode characters include the basic ASCII character set, various other alphabet letters, accents, currency symbols, fractions, diacritics, and mathematical and technical symbols.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4abd6-112">O caractere Unicode definir os pontos de código D800 e DFFF (55296 até 55551 em decimal) para as reservas *pares substitutos*, que exigem dois valores de 16 bits para representar um único ponto de código.</span><span class="sxs-lookup"><span data-stu-id="4abd6-112">The Unicode character set reserves the code points D800 through DFFF (55296 through 55551 decimal) for *surrogate pairs*, which require two 16-bit values to represent a single code point.</span></span> <span data-ttu-id="4abd6-113">Um `Char` variável não pode conter um par substituto e um `String` usa duas posições para armazenar tal par.</span><span class="sxs-lookup"><span data-stu-id="4abd6-113">A `Char` variable cannot hold a surrogate pair, and a `String` uses two positions to hold such a pair.</span></span>  
  
 <span data-ttu-id="4abd6-114">Para obter mais informações, consulte [tipo de dados Char](../../../../visual-basic/language-reference/data-types/char-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="4abd6-114">For more information, see [Char Data Type](../../../../visual-basic/language-reference/data-types/char-data-type.md).</span></span>  
  
## <a name="string-type"></a><span data-ttu-id="4abd6-115">Tipo de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="4abd6-115">String Type</span></span>  
 <span data-ttu-id="4abd6-116">O `String` tipo de dados é uma sequência de caracteres de Unicode do zero ou mais de dois bytes (16 bits).</span><span class="sxs-lookup"><span data-stu-id="4abd6-116">The `String` data type is a sequence of zero or more two-byte (16-bit) Unicode characters.</span></span> <span data-ttu-id="4abd6-117">Se uma variável pode conter um número indefinido de caracteres, declare-o como `String`.</span><span class="sxs-lookup"><span data-stu-id="4abd6-117">If a variable can contain an indefinite number of characters, declare it as `String`.</span></span> <span data-ttu-id="4abd6-118">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="4abd6-118">For example:</span></span>  
  
 [!code-vb[VbVbalrCharTypes#2](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/character-data-types_2.vb)]  
  
 <span data-ttu-id="4abd6-119">Para obter mais informações, consulte [tipo de dados de cadeia de caracteres](../../../../visual-basic/language-reference/data-types/string-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="4abd6-119">For more information, see [String Data Type](../../../../visual-basic/language-reference/data-types/string-data-type.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4abd6-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4abd6-120">See Also</span></span>  
 [<span data-ttu-id="4abd6-121">Tipos de Dados Elementares</span><span class="sxs-lookup"><span data-stu-id="4abd6-121">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [<span data-ttu-id="4abd6-122">Tipos de Dados Compostos</span><span class="sxs-lookup"><span data-stu-id="4abd6-122">Composite Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)  
 [<span data-ttu-id="4abd6-123">Tipos genéricos no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4abd6-123">Generic Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [<span data-ttu-id="4abd6-124">Tipos de Valor e Tipos de Referência</span><span class="sxs-lookup"><span data-stu-id="4abd6-124">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [<span data-ttu-id="4abd6-125">Conversões de tipo no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4abd6-125">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [<span data-ttu-id="4abd6-126">Solução de problemas de Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="4abd6-126">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [<span data-ttu-id="4abd6-127">Caracteres de Tipo</span><span class="sxs-lookup"><span data-stu-id="4abd6-127">Type Characters</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
