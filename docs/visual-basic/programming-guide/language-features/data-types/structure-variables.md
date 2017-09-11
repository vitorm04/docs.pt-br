---
title: "Estrutura variáveis (Visual Basic) | Documentos do Microsoft"
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
- structures, variables
- structures, structure variables
- variables [Visual Basic], structure variables
- structure variables
ms.assetid: 156872f8-aabc-4454-8e2d-f2253c3c13c9
caps.latest.revision: 11
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
ms.openlocfilehash: 5718887492c93ae3e6068d9ae3ddc181eadc62c3
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="structure-variables-visual-basic"></a><span data-ttu-id="878b6-102">Variáveis de estrutura (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="878b6-102">Structure Variables (Visual Basic)</span></span>
<span data-ttu-id="878b6-103">Depois de ter criado uma estrutura, você pode declarar variáveis de nível de procedimento e o nível de módulo como esse tipo.</span><span class="sxs-lookup"><span data-stu-id="878b6-103">Once you have created a structure, you can declare procedure-level and module-level variables as that type.</span></span> <span data-ttu-id="878b6-104">Por exemplo, você pode criar uma estrutura que registra informações sobre um sistema de computador.</span><span class="sxs-lookup"><span data-stu-id="878b6-104">For example, you can create a structure that records information about a computer system.</span></span> <span data-ttu-id="878b6-105">O exemplo a seguir demonstra isso.</span><span class="sxs-lookup"><span data-stu-id="878b6-105">The following example demonstrates this.</span></span>  
  
```  
Public Structure systemInfo  
    Public cPU As String  
    Public memory As Long  
    Public purchaseDate As Date  
End Structure  
```  
  
 <span data-ttu-id="878b6-106">Agora você pode declarar variáveis desse tipo.</span><span class="sxs-lookup"><span data-stu-id="878b6-106">You can now declare variables of that type.</span></span> <span data-ttu-id="878b6-107">A declaração a seguir ilustra isso.</span><span class="sxs-lookup"><span data-stu-id="878b6-107">The following declaration illustrates this.</span></span>  
  
```  
Dim mySystem, yourSystem As systemInfo  
```  
  
> [!NOTE]
>  <span data-ttu-id="878b6-108">Em módulos e classes, estruturas declaradas usando a [instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) padrão de acesso público.</span><span class="sxs-lookup"><span data-stu-id="878b6-108">In classes and modules, structures declared using the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) default to public access.</span></span> <span data-ttu-id="878b6-109">Se você pretende que uma estrutura seja particular, certifique-se de você declará-la usando o [particular](../../../../visual-basic/language-reference/modifiers/private.md) palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="878b6-109">If you intend a structure to be private, make sure you declare it using the [Private](../../../../visual-basic/language-reference/modifiers/private.md) keyword.</span></span>  
  
## <a name="access-to-structure-values"></a><span data-ttu-id="878b6-110">Acesso a valores de estrutura</span><span class="sxs-lookup"><span data-stu-id="878b6-110">Access to Structure Values</span></span>  
 <span data-ttu-id="878b6-111">Para atribuir e recuperar valores de elementos de uma variável de estrutura, você usar a mesma sintaxe que você usa para definir e obter as propriedades de um objeto.</span><span class="sxs-lookup"><span data-stu-id="878b6-111">To assign and retrieve values from the elements of a structure variable, you use the same syntax as you use to set and get properties on an object.</span></span> <span data-ttu-id="878b6-112">Coloque o operador de acesso de membro (`.`) entre o nome da variável de estrutura e o nome do elemento.</span><span class="sxs-lookup"><span data-stu-id="878b6-112">You place the member access operator (`.`) between the structure variable name and the element name.</span></span> <span data-ttu-id="878b6-113">O exemplo a seguir acessa elementos das variáveis previamente declaradas como do tipo `systemInfo`.</span><span class="sxs-lookup"><span data-stu-id="878b6-113">The following example accesses elements of the variables previously declared as type `systemInfo`.</span></span>  
  
```  
mySystem.cPU = "486"  
Dim tooOld As Boolean  
If yourSystem.purchaseDate < #1/1/1992# Then tooOld = True  
```  
  
## <a name="assigning-structure-variables"></a><span data-ttu-id="878b6-114">Atribuindo variáveis de estrutura</span><span class="sxs-lookup"><span data-stu-id="878b6-114">Assigning Structure Variables</span></span>  
 <span data-ttu-id="878b6-115">Você também pode atribuir uma variável a outra se ambas forem do mesmo tipo de estrutura.</span><span class="sxs-lookup"><span data-stu-id="878b6-115">You can also assign one variable to another if both are of the same structure type.</span></span> <span data-ttu-id="878b6-116">Isso copiará todos os elementos de uma estrutura para os elementos correspondentes no outro.</span><span class="sxs-lookup"><span data-stu-id="878b6-116">This copies all the elements of one structure to the corresponding elements in the other.</span></span> <span data-ttu-id="878b6-117">A declaração a seguir ilustra isso.</span><span class="sxs-lookup"><span data-stu-id="878b6-117">The following declaration illustrates this.</span></span>  
  
```  
yourSystem = mySystem  
```  
  
 <span data-ttu-id="878b6-118">Se um elemento de estrutura for um tipo de referência, como um `String`, `Object`, ou matriz, o ponteiro para os dados é copiado.</span><span class="sxs-lookup"><span data-stu-id="878b6-118">If a structure element is a reference type, such as a `String`, `Object`, or array, the pointer to the data is copied.</span></span> <span data-ttu-id="878b6-119">No exemplo anterior, se `systemInfo` tivesse incluído uma variável de objeto, em seguida, o exemplo anterior teria copiado o ponteiro de `mySystem` para `yourSystem`, e uma alteração nos dados do objeto através de uma estrutura teriam efeito quando acessados através da outra estrutura.</span><span class="sxs-lookup"><span data-stu-id="878b6-119">In the previous example, if `systemInfo` had included an object variable, then the preceding example would have copied the pointer from `mySystem` to `yourSystem`, and a change to the object's data through one structure would be in effect when accessed through the other structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="878b6-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="878b6-120">See Also</span></span>  
 <span data-ttu-id="878b6-121">[Tipos de dados](../../../../visual-basic/programming-guide/language-features/data-types/index.md) </span><span class="sxs-lookup"><span data-stu-id="878b6-121">[Data Types](../../../../visual-basic/programming-guide/language-features/data-types/index.md) </span></span>  
<span data-ttu-id="878b6-122"> [Tipos de dados elementares](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="878b6-122"> [Elementary Data Types](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md) </span></span>  
<span data-ttu-id="878b6-123"> [Tipos de dados compostos](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="878b6-123"> [Composite Data Types](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md) </span></span>  
<span data-ttu-id="878b6-124"> [Tipos de valor e tipos de referência](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md) </span><span class="sxs-lookup"><span data-stu-id="878b6-124"> [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md) </span></span>  
<span data-ttu-id="878b6-125"> [Estruturas](../../../../visual-basic/programming-guide/language-features/data-types/structures.md) </span><span class="sxs-lookup"><span data-stu-id="878b6-125"> [Structures](../../../../visual-basic/programming-guide/language-features/data-types/structures.md) </span></span>  
<span data-ttu-id="878b6-126"> [Solucionando problemas de tipos de dados](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="878b6-126"> [Troubleshooting Data Types](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md) </span></span>  
<span data-ttu-id="878b6-127"> [Como: declarar uma estrutura](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md) </span><span class="sxs-lookup"><span data-stu-id="878b6-127"> [How to: Declare a Structure](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md) </span></span>  
<span data-ttu-id="878b6-128"> [Estruturas e outros elementos de programação](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md) </span><span class="sxs-lookup"><span data-stu-id="878b6-128"> [Structures and Other Programming Elements](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md) </span></span>  
<span data-ttu-id="878b6-129"> [Estruturas e Classes](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md) </span><span class="sxs-lookup"><span data-stu-id="878b6-129"> [Structures and Classes](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md) </span></span>  
<span data-ttu-id="878b6-130"> [Instrução Structure](../../../../visual-basic/language-reference/statements/structure-statement.md)</span><span class="sxs-lookup"><span data-stu-id="878b6-130"> [Structure Statement](../../../../visual-basic/language-reference/statements/structure-statement.md)</span></span>
