---
title: Variáveis de estrutura (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- structures [Visual Basic], variables
- structures [Visual Basic], structure variables
- variables [Visual Basic], structure variables
- structure variables [Visual Basic]
ms.assetid: 156872f8-aabc-4454-8e2d-f2253c3c13c9
ms.openlocfilehash: 9a6e542e297a17f44d929235530ae6058cf13a36
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61663382"
---
# <a name="structure-variables-visual-basic"></a><span data-ttu-id="275ee-102">Variáveis de estrutura (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="275ee-102">Structure Variables (Visual Basic)</span></span>
<span data-ttu-id="275ee-103">Depois de criar uma estrutura, você pode declarar variáveis de nível de procedimento e o nível de módulo como esse tipo.</span><span class="sxs-lookup"><span data-stu-id="275ee-103">Once you have created a structure, you can declare procedure-level and module-level variables as that type.</span></span> <span data-ttu-id="275ee-104">Por exemplo, você pode criar uma estrutura que registra informações sobre um sistema de computador.</span><span class="sxs-lookup"><span data-stu-id="275ee-104">For example, you can create a structure that records information about a computer system.</span></span> <span data-ttu-id="275ee-105">O exemplo a seguir demonstra isso.</span><span class="sxs-lookup"><span data-stu-id="275ee-105">The following example demonstrates this.</span></span>  
  
```  
Public Structure systemInfo  
    Public cPU As String  
    Public memory As Long  
    Public purchaseDate As Date  
End Structure  
```  
  
 <span data-ttu-id="275ee-106">Agora você pode declarar variáveis desse tipo.</span><span class="sxs-lookup"><span data-stu-id="275ee-106">You can now declare variables of that type.</span></span> <span data-ttu-id="275ee-107">A declaração a seguir ilustra isso.</span><span class="sxs-lookup"><span data-stu-id="275ee-107">The following declaration illustrates this.</span></span>  
  
```  
Dim mySystem, yourSystem As systemInfo  
```  
  
> [!NOTE]
>  <span data-ttu-id="275ee-108">Em módulos e classes, estruturas declaradas usando o [instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) padrão de acesso público.</span><span class="sxs-lookup"><span data-stu-id="275ee-108">In classes and modules, structures declared using the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) default to public access.</span></span> <span data-ttu-id="275ee-109">Se você pretende que uma estrutura seja particular, verifique se você declará-la usando o [privada](../../../../visual-basic/language-reference/modifiers/private.md) palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="275ee-109">If you intend a structure to be private, make sure you declare it using the [Private](../../../../visual-basic/language-reference/modifiers/private.md) keyword.</span></span>  
  
## <a name="access-to-structure-values"></a><span data-ttu-id="275ee-110">Acesso aos valores de estrutura</span><span class="sxs-lookup"><span data-stu-id="275ee-110">Access to Structure Values</span></span>  
 <span data-ttu-id="275ee-111">Para atribuir e recuperar valores de elementos de uma variável de estrutura, você usar a mesma sintaxe que você use para definir e obter as propriedades de um objeto.</span><span class="sxs-lookup"><span data-stu-id="275ee-111">To assign and retrieve values from the elements of a structure variable, you use the same syntax as you use to set and get properties on an object.</span></span> <span data-ttu-id="275ee-112">Você coloca o operador de acesso de membro (`.`) entre o nome da variável de estrutura e o nome do elemento.</span><span class="sxs-lookup"><span data-stu-id="275ee-112">You place the member access operator (`.`) between the structure variable name and the element name.</span></span> <span data-ttu-id="275ee-113">O exemplo a seguir acessa elementos das variáveis declarados anteriormente como tipo `systemInfo`.</span><span class="sxs-lookup"><span data-stu-id="275ee-113">The following example accesses elements of the variables previously declared as type `systemInfo`.</span></span>  
  
```  
mySystem.cPU = "486"  
Dim tooOld As Boolean  
If yourSystem.purchaseDate < #1/1/1992# Then tooOld = True  
```  
  
## <a name="assigning-structure-variables"></a><span data-ttu-id="275ee-114">Atribuindo variáveis de estrutura</span><span class="sxs-lookup"><span data-stu-id="275ee-114">Assigning Structure Variables</span></span>  
 <span data-ttu-id="275ee-115">Você também pode atribuir uma variável para outra se ambas forem do mesmo tipo de estrutura.</span><span class="sxs-lookup"><span data-stu-id="275ee-115">You can also assign one variable to another if both are of the same structure type.</span></span> <span data-ttu-id="275ee-116">Isso copiará todos os elementos de uma estrutura para os elementos correspondentes no outro.</span><span class="sxs-lookup"><span data-stu-id="275ee-116">This copies all the elements of one structure to the corresponding elements in the other.</span></span> <span data-ttu-id="275ee-117">A declaração a seguir ilustra isso.</span><span class="sxs-lookup"><span data-stu-id="275ee-117">The following declaration illustrates this.</span></span>  
  
```  
yourSystem = mySystem  
```  
  
 <span data-ttu-id="275ee-118">Se um elemento de estrutura é um tipo de referência, como uma `String`, `Object`, ou matriz, o ponteiro para os dados é copiado.</span><span class="sxs-lookup"><span data-stu-id="275ee-118">If a structure element is a reference type, such as a `String`, `Object`, or array, the pointer to the data is copied.</span></span> <span data-ttu-id="275ee-119">No exemplo anterior, se `systemInfo` tivesse incluído uma variável de objeto, em seguida, o exemplo anterior seria ter copiado o ponteiro de `mySystem` para `yourSystem`, e uma alteração nos dados do objeto através de uma estrutura teriam efeito quando acessados através da estrutura.</span><span class="sxs-lookup"><span data-stu-id="275ee-119">In the previous example, if `systemInfo` had included an object variable, then the preceding example would have copied the pointer from `mySystem` to `yourSystem`, and a change to the object's data through one structure would be in effect when accessed through the other structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="275ee-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="275ee-120">See also</span></span>

- [<span data-ttu-id="275ee-121">Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="275ee-121">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [<span data-ttu-id="275ee-122">Tipos de Dados Elementares</span><span class="sxs-lookup"><span data-stu-id="275ee-122">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [<span data-ttu-id="275ee-123">Tipos de Dados Compostos</span><span class="sxs-lookup"><span data-stu-id="275ee-123">Composite Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [<span data-ttu-id="275ee-124">Tipos de Valor e Tipos de Referência</span><span class="sxs-lookup"><span data-stu-id="275ee-124">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [<span data-ttu-id="275ee-125">Estruturas</span><span class="sxs-lookup"><span data-stu-id="275ee-125">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="275ee-126">Solução de problemas de Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="275ee-126">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="275ee-127">Como: declarar uma estrutura</span><span class="sxs-lookup"><span data-stu-id="275ee-127">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="275ee-128">Estruturas e Outros Elementos de Programação</span><span class="sxs-lookup"><span data-stu-id="275ee-128">Structures and Other Programming Elements</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)
- [<span data-ttu-id="275ee-129">Estruturas e Classes</span><span class="sxs-lookup"><span data-stu-id="275ee-129">Structures and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)
- [<span data-ttu-id="275ee-130">Instrução Structure</span><span class="sxs-lookup"><span data-stu-id="275ee-130">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)
