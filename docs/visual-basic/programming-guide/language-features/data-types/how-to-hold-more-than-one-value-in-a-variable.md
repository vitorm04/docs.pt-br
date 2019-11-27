---
title: Como manter mais de um valor em uma variável
ms.date: 07/20/2015
helpviewer_keywords:
- classes [Visual Basic], composite data types
- composite types [Visual Basic]
- composite data types [Visual Basic]
- data types [Visual Basic], composite
- arrays [Visual Basic], composite data types
- structures [Visual Basic], composite data types
- arrays [Visual Basic], compilation errors
- types [Visual Basic], composite
ms.assetid: 5fe0e558-aac2-4a40-b7f2-7cfea7336917
ms.openlocfilehash: d452fbf35f9d200348234b38c40f8636f0ec4b4e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350017"
---
# <a name="how-to-hold-more-than-one-value-in-a-variable-visual-basic"></a><span data-ttu-id="db276-102">Como manter mais de um valor em uma variável (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="db276-102">How to: Hold More Than One Value in a Variable (Visual Basic)</span></span>

<span data-ttu-id="db276-103">Uma variável contém mais de um valor se você declará-lo para ser de um *tipo de dados composto*.</span><span class="sxs-lookup"><span data-stu-id="db276-103">A variable holds more than one value if you declare it to be of a *composite data type*.</span></span>

<span data-ttu-id="db276-104">[Os tipos de dados compostos](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md) incluem estruturas, matrizes e classes.</span><span class="sxs-lookup"><span data-stu-id="db276-104">[Composite Data Types](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md) include structures, arrays, and classes.</span></span> <span data-ttu-id="db276-105">Uma variável de um tipo de dados de composição pode conter uma combinação de tipos de dados elementares e outros tipos compostos.</span><span class="sxs-lookup"><span data-stu-id="db276-105">A variable of a composite data type can hold a combination of elementary data types and other composite types.</span></span> <span data-ttu-id="db276-106">Estruturas e classes podem conter código, bem como dados.</span><span class="sxs-lookup"><span data-stu-id="db276-106">Structures and classes can hold code as well as data.</span></span>

## <a name="to-hold-more-than-one-value-in-a-variable"></a><span data-ttu-id="db276-107">Para conter mais de um valor em uma variável</span><span class="sxs-lookup"><span data-stu-id="db276-107">To hold more than one value in a variable</span></span>

1. <span data-ttu-id="db276-108">Determine o tipo de dados composto que você deseja usar para a variável.</span><span class="sxs-lookup"><span data-stu-id="db276-108">Determine what composite data type you want to use for your variable.</span></span>

2. <span data-ttu-id="db276-109">Se o tipo de dados composto ainda não estiver definido, defina-o para que sua variável possa usá-lo.</span><span class="sxs-lookup"><span data-stu-id="db276-109">If the composite data type is not already defined, define it so that your variable can use it.</span></span>

    - <span data-ttu-id="db276-110">Defina uma estrutura com uma [instrução de estrutura](../../../../visual-basic/language-reference/statements/structure-statement.md).</span><span class="sxs-lookup"><span data-stu-id="db276-110">Define a structure with a [Structure Statement](../../../../visual-basic/language-reference/statements/structure-statement.md).</span></span>

    - <span data-ttu-id="db276-111">Defina uma matriz com uma [instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="db276-111">Define an array with a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md).</span></span>

    - <span data-ttu-id="db276-112">Defina uma classe com uma [instrução de classe](../../../../visual-basic/language-reference/statements/class-statement.md).</span><span class="sxs-lookup"><span data-stu-id="db276-112">Define a class with a [Class Statement](../../../../visual-basic/language-reference/statements/class-statement.md).</span></span>

3. <span data-ttu-id="db276-113">Declare sua variável com uma instrução `Dim`.</span><span class="sxs-lookup"><span data-stu-id="db276-113">Declare your variable with a `Dim` statement.</span></span>

4. <span data-ttu-id="db276-114">Siga o nome da variável com uma cláusula `As`.</span><span class="sxs-lookup"><span data-stu-id="db276-114">Follow the variable name with an `As` clause.</span></span>

5. <span data-ttu-id="db276-115">Siga a palavra-chave `As` com o nome do tipo de dados composto apropriado.</span><span class="sxs-lookup"><span data-stu-id="db276-115">Follow the `As` keyword with the name of the appropriate composite data type.</span></span>

## <a name="see-also"></a><span data-ttu-id="db276-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="db276-116">See also</span></span>

- [<span data-ttu-id="db276-117">Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="db276-117">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="db276-118">Caracteres de Tipo</span><span class="sxs-lookup"><span data-stu-id="db276-118">Type Characters</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
- [<span data-ttu-id="db276-119">Tipos de Dados Compostos</span><span class="sxs-lookup"><span data-stu-id="db276-119">Composite Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [<span data-ttu-id="db276-120">Estruturas</span><span class="sxs-lookup"><span data-stu-id="db276-120">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="db276-121">Matrizes</span><span class="sxs-lookup"><span data-stu-id="db276-121">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="db276-122">Objetos e Classes</span><span class="sxs-lookup"><span data-stu-id="db276-122">Objects and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [<span data-ttu-id="db276-123">Tipos de Valor e Tipos de Referência</span><span class="sxs-lookup"><span data-stu-id="db276-123">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
