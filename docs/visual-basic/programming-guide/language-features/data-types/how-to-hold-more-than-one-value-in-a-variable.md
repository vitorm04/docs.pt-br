---
title: 'Como: Manter mais de um valor em uma variável'
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
ms.openlocfilehash: 399c5909ee6988f96bcc85260b0401f3bd18a0f2
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84393890"
---
# <a name="how-to-hold-more-than-one-value-in-a-variable-visual-basic"></a><span data-ttu-id="a5977-102">Como manter mais de um valor em uma variável (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a5977-102">How to: Hold More Than One Value in a Variable (Visual Basic)</span></span>

<span data-ttu-id="a5977-103">Uma variável contém mais de um valor se você declará-lo para ser de um *tipo de dados composto*.</span><span class="sxs-lookup"><span data-stu-id="a5977-103">A variable holds more than one value if you declare it to be of a *composite data type*.</span></span>

<span data-ttu-id="a5977-104">[Os tipos de dados compostos](composite-data-types.md) incluem estruturas, matrizes e classes.</span><span class="sxs-lookup"><span data-stu-id="a5977-104">[Composite Data Types](composite-data-types.md) include structures, arrays, and classes.</span></span> <span data-ttu-id="a5977-105">Uma variável de um tipo de dados de composição pode conter uma combinação de tipos de dados elementares e outros tipos compostos.</span><span class="sxs-lookup"><span data-stu-id="a5977-105">A variable of a composite data type can hold a combination of elementary data types and other composite types.</span></span> <span data-ttu-id="a5977-106">Estruturas e classes podem conter código, bem como dados.</span><span class="sxs-lookup"><span data-stu-id="a5977-106">Structures and classes can hold code as well as data.</span></span>

## <a name="to-hold-more-than-one-value-in-a-variable"></a><span data-ttu-id="a5977-107">Para conter mais de um valor em uma variável</span><span class="sxs-lookup"><span data-stu-id="a5977-107">To hold more than one value in a variable</span></span>

1. <span data-ttu-id="a5977-108">Determine o tipo de dados composto que você deseja usar para a variável.</span><span class="sxs-lookup"><span data-stu-id="a5977-108">Determine what composite data type you want to use for your variable.</span></span>

2. <span data-ttu-id="a5977-109">Se o tipo de dados composto ainda não estiver definido, defina-o para que sua variável possa usá-lo.</span><span class="sxs-lookup"><span data-stu-id="a5977-109">If the composite data type is not already defined, define it so that your variable can use it.</span></span>

    - <span data-ttu-id="a5977-110">Defina uma estrutura com uma [instrução de estrutura](../../../language-reference/statements/structure-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a5977-110">Define a structure with a [Structure Statement](../../../language-reference/statements/structure-statement.md).</span></span>

    - <span data-ttu-id="a5977-111">Defina uma matriz com uma [instrução Dim](../../../language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a5977-111">Define an array with a [Dim Statement](../../../language-reference/statements/dim-statement.md).</span></span>

    - <span data-ttu-id="a5977-112">Defina uma classe com uma [instrução de classe](../../../language-reference/statements/class-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a5977-112">Define a class with a [Class Statement](../../../language-reference/statements/class-statement.md).</span></span>

3. <span data-ttu-id="a5977-113">Declare sua variável com uma `Dim` instrução.</span><span class="sxs-lookup"><span data-stu-id="a5977-113">Declare your variable with a `Dim` statement.</span></span>

4. <span data-ttu-id="a5977-114">Siga o nome da variável com uma `As` cláusula.</span><span class="sxs-lookup"><span data-stu-id="a5977-114">Follow the variable name with an `As` clause.</span></span>

5. <span data-ttu-id="a5977-115">Siga a `As` palavra-chave com o nome do tipo de dados composto apropriado.</span><span class="sxs-lookup"><span data-stu-id="a5977-115">Follow the `As` keyword with the name of the appropriate composite data type.</span></span>

## <a name="see-also"></a><span data-ttu-id="a5977-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="a5977-116">See also</span></span>

- [<span data-ttu-id="a5977-117">Tipos de dados</span><span class="sxs-lookup"><span data-stu-id="a5977-117">Data Types</span></span>](../../../language-reference/data-types/index.md)
- [<span data-ttu-id="a5977-118">Caracteres de tipo</span><span class="sxs-lookup"><span data-stu-id="a5977-118">Type Characters</span></span>](type-characters.md)
- [<span data-ttu-id="a5977-119">Tipos de dados compostos</span><span class="sxs-lookup"><span data-stu-id="a5977-119">Composite Data Types</span></span>](composite-data-types.md)
- [<span data-ttu-id="a5977-120">Estruturas</span><span class="sxs-lookup"><span data-stu-id="a5977-120">Structures</span></span>](structures.md)
- [<span data-ttu-id="a5977-121">Matrizes</span><span class="sxs-lookup"><span data-stu-id="a5977-121">Arrays</span></span>](../arrays/index.md)
- [<span data-ttu-id="a5977-122">Objetos e classes</span><span class="sxs-lookup"><span data-stu-id="a5977-122">Objects and Classes</span></span>](../objects-and-classes/index.md)
- [<span data-ttu-id="a5977-123">Tipos de valor e referência</span><span class="sxs-lookup"><span data-stu-id="a5977-123">Value Types and Reference Types</span></span>](value-types-and-reference-types.md)
