---
title: Como manter mais de um valor em uma variável (Visual Basic)
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
ms.openlocfilehash: 781f56c7e710f5130d821ca4796398379dfa4c6e
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43456484"
---
# <a name="how-to-hold-more-than-one-value-in-a-variable-visual-basic"></a><span data-ttu-id="3d030-102">Como manter mais de um valor em uma variável (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3d030-102">How to: Hold More Than One Value in a Variable (Visual Basic)</span></span>
<span data-ttu-id="3d030-103">Uma variável contém mais de um valor se você declará-la para ser de um *tipo de dados composto*.</span><span class="sxs-lookup"><span data-stu-id="3d030-103">A variable holds more than one value if you declare it to be of a *composite data type*.</span></span>  
  
 <span data-ttu-id="3d030-104">[Tipos de dados compostos](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md) incluem classes, matrizes e estruturas.</span><span class="sxs-lookup"><span data-stu-id="3d030-104">[Composite Data Types](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md) include structures, arrays, and classes.</span></span> <span data-ttu-id="3d030-105">Uma variável de um tipo de dados composto pode conter uma combinação de tipos de dados elementares e outros tipos compostos.</span><span class="sxs-lookup"><span data-stu-id="3d030-105">A variable of a composite data type can hold a combination of elementary data types and other composite types.</span></span> <span data-ttu-id="3d030-106">Estruturas e classes podem conter código, bem como dados.</span><span class="sxs-lookup"><span data-stu-id="3d030-106">Structures and classes can hold code as well as data.</span></span>  
  
### <a name="to-hold-more-than-one-value-in-a-variable"></a><span data-ttu-id="3d030-107">Para manter mais de um valor em uma variável</span><span class="sxs-lookup"><span data-stu-id="3d030-107">To hold more than one value in a variable</span></span>  
  
1.  <span data-ttu-id="3d030-108">Determine que tipo de dados compostos que você deseja usar para sua variável.</span><span class="sxs-lookup"><span data-stu-id="3d030-108">Determine what composite data type you want to use for your variable.</span></span>  
  
2.  <span data-ttu-id="3d030-109">Se o tipo de dados compostos já não estiver definido, defini-lo para que sua variável possa usá-lo.</span><span class="sxs-lookup"><span data-stu-id="3d030-109">If the composite data type is not already defined, define it so that your variable can use it.</span></span>  
  
    -   <span data-ttu-id="3d030-110">Definir uma estrutura com um [instrução Structure](../../../../visual-basic/language-reference/statements/structure-statement.md).</span><span class="sxs-lookup"><span data-stu-id="3d030-110">Define a structure with a [Structure Statement](../../../../visual-basic/language-reference/statements/structure-statement.md).</span></span>  
  
    -   <span data-ttu-id="3d030-111">Definir uma matriz com um [instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="3d030-111">Define an array with a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md).</span></span>  
  
    -   <span data-ttu-id="3d030-112">Defina uma classe com um [declaração de classe](../../../../visual-basic/language-reference/statements/class-statement.md).</span><span class="sxs-lookup"><span data-stu-id="3d030-112">Define a class with a [Class Statement](../../../../visual-basic/language-reference/statements/class-statement.md).</span></span>  
  
3.  <span data-ttu-id="3d030-113">Declare a variável com um `Dim` instrução.</span><span class="sxs-lookup"><span data-stu-id="3d030-113">Declare your variable with a `Dim` statement.</span></span>  
  
4.  <span data-ttu-id="3d030-114">Siga o nome da variável com um `As` cláusula.</span><span class="sxs-lookup"><span data-stu-id="3d030-114">Follow the variable name with an `As` clause.</span></span>  
  
5.  <span data-ttu-id="3d030-115">Siga o `As` palavra-chave com o nome do tipo de dados compostos apropriado.</span><span class="sxs-lookup"><span data-stu-id="3d030-115">Follow the `As` keyword with the name of the appropriate composite data type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d030-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3d030-116">See Also</span></span>  
 [<span data-ttu-id="3d030-117">Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="3d030-117">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/index.md)  
 [<span data-ttu-id="3d030-118">Caracteres de Tipo</span><span class="sxs-lookup"><span data-stu-id="3d030-118">Type Characters</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)  
 [<span data-ttu-id="3d030-119">Tipos de Dados Compostos</span><span class="sxs-lookup"><span data-stu-id="3d030-119">Composite Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)  
 [<span data-ttu-id="3d030-120">Estruturas</span><span class="sxs-lookup"><span data-stu-id="3d030-120">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="3d030-121">Matrizes</span><span class="sxs-lookup"><span data-stu-id="3d030-121">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [<span data-ttu-id="3d030-122">Objetos e Classes</span><span class="sxs-lookup"><span data-stu-id="3d030-122">Objects and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [<span data-ttu-id="3d030-123">Tipos de Valor e Tipos de Referência</span><span class="sxs-lookup"><span data-stu-id="3d030-123">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
