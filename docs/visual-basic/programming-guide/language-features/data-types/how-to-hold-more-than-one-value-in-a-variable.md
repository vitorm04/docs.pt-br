---
title: "Como: armazenar mais de um valor em uma variável (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- classes [Visual Basic], composite data types
- composite types
- composite data types
- data types [Visual Basic], composite
- arrays [Visual Basic], composite data types
- structures, composite data types
- arrays [Visual Basic], compilation errors
- types [Visual Basic], composite
ms.assetid: 5fe0e558-aac2-4a40-b7f2-7cfea7336917
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 4f8367b1a7ac0d5cc272b9a1ae53523b7ffa3e12
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-hold-more-than-one-value-in-a-variable-visual-basic"></a><span data-ttu-id="61f3c-102">Como manter mais de um valor em uma variável (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="61f3c-102">How to: Hold More Than One Value in a Variable (Visual Basic)</span></span>
<span data-ttu-id="61f3c-103">Uma variável contém mais de um valor se você declará-la para ser de um *tipo de dados composto*.</span><span class="sxs-lookup"><span data-stu-id="61f3c-103">A variable holds more than one value if you declare it to be of a *composite data type*.</span></span>  
  
 <span data-ttu-id="61f3c-104">[Tipos de dados compostos](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md) incluem classes, matrizes e estruturas.</span><span class="sxs-lookup"><span data-stu-id="61f3c-104">[Composite Data Types](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md) include structures, arrays, and classes.</span></span> <span data-ttu-id="61f3c-105">Uma variável de um tipo de dados composto pode conter uma combinação de tipos de dados elementares e outros tipos compostos.</span><span class="sxs-lookup"><span data-stu-id="61f3c-105">A variable of a composite data type can hold a combination of elementary data types and other composite types.</span></span> <span data-ttu-id="61f3c-106">Estruturas e classes podem armazenar código bem como dados.</span><span class="sxs-lookup"><span data-stu-id="61f3c-106">Structures and classes can hold code as well as data.</span></span>  
  
### <a name="to-hold-more-than-one-value-in-a-variable"></a><span data-ttu-id="61f3c-107">Para manter mais de um valor em uma variável</span><span class="sxs-lookup"><span data-stu-id="61f3c-107">To hold more than one value in a variable</span></span>  
  
1.  <span data-ttu-id="61f3c-108">Determine que tipo de dados compostos que você deseja usar para sua variável.</span><span class="sxs-lookup"><span data-stu-id="61f3c-108">Determine what composite data type you want to use for your variable.</span></span>  
  
2.  <span data-ttu-id="61f3c-109">Se o tipo de dados compostos já não estiver definido, defini-lo para que sua variável possa usá-lo.</span><span class="sxs-lookup"><span data-stu-id="61f3c-109">If the composite data type is not already defined, define it so that your variable can use it.</span></span>  
  
    -   <span data-ttu-id="61f3c-110">Defina uma estrutura com um [declaração de estrutura](../../../../visual-basic/language-reference/statements/structure-statement.md).</span><span class="sxs-lookup"><span data-stu-id="61f3c-110">Define a structure with a [Structure Statement](../../../../visual-basic/language-reference/statements/structure-statement.md).</span></span>  
  
    -   <span data-ttu-id="61f3c-111">Definir uma matriz com um [instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="61f3c-111">Define an array with a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md).</span></span>  
  
    -   <span data-ttu-id="61f3c-112">Definir uma classe com um [instrução Class](../../../../visual-basic/language-reference/statements/class-statement.md).</span><span class="sxs-lookup"><span data-stu-id="61f3c-112">Define a class with a [Class Statement](../../../../visual-basic/language-reference/statements/class-statement.md).</span></span>  
  
3.  <span data-ttu-id="61f3c-113">Declare a variável com um `Dim` instrução.</span><span class="sxs-lookup"><span data-stu-id="61f3c-113">Declare your variable with a `Dim` statement.</span></span>  
  
4.  <span data-ttu-id="61f3c-114">Siga o nome da variável com um `As` cláusula.</span><span class="sxs-lookup"><span data-stu-id="61f3c-114">Follow the variable name with an `As` clause.</span></span>  
  
5.  <span data-ttu-id="61f3c-115">Execute o `As` palavra-chave com o nome do tipo de dados compostos apropriado.</span><span class="sxs-lookup"><span data-stu-id="61f3c-115">Follow the `As` keyword with the name of the appropriate composite data type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61f3c-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="61f3c-116">See Also</span></span>  
 <span data-ttu-id="61f3c-117">[Tipos de dados](../../../../visual-basic/language-reference/data-types/data-type-summary.md) </span><span class="sxs-lookup"><span data-stu-id="61f3c-117">[Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md) </span></span>  
<span data-ttu-id="61f3c-118"> [Caracteres de tipo](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md) </span><span class="sxs-lookup"><span data-stu-id="61f3c-118"> [Type Characters](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md) </span></span>  
<span data-ttu-id="61f3c-119"> [Tipos de dados compostos](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="61f3c-119"> [Composite Data Types](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md) </span></span>  
<span data-ttu-id="61f3c-120"> [Estruturas](../../../../visual-basic/programming-guide/language-features/data-types/structures.md) </span><span class="sxs-lookup"><span data-stu-id="61f3c-120"> [Structures](../../../../visual-basic/programming-guide/language-features/data-types/structures.md) </span></span>  
<span data-ttu-id="61f3c-121"> [Matrizes](../../../../visual-basic/programming-guide/language-features/arrays/index.md) </span><span class="sxs-lookup"><span data-stu-id="61f3c-121"> [Arrays](../../../../visual-basic/programming-guide/language-features/arrays/index.md) </span></span>  
<span data-ttu-id="61f3c-122"> [Objetos e Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md) </span><span class="sxs-lookup"><span data-stu-id="61f3c-122"> [Objects and Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md) </span></span>  
<span data-ttu-id="61f3c-123"> [Tipos de Valor e Tipos de Referência](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)</span><span class="sxs-lookup"><span data-stu-id="61f3c-123"> [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)</span></span>
