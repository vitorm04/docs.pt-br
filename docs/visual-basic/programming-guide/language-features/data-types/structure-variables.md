---
title: Variáveis de estrutura
ms.date: 07/20/2015
helpviewer_keywords:
- structures [Visual Basic], variables
- structures [Visual Basic], structure variables
- variables [Visual Basic], structure variables
- structure variables [Visual Basic]
ms.assetid: 156872f8-aabc-4454-8e2d-f2253c3c13c9
ms.openlocfilehash: 270e8ca26185e4a68def3b95f4ce6ab4c57a629c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84393579"
---
# <a name="structure-variables-visual-basic"></a><span data-ttu-id="52df7-102">Variáveis de estrutura (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="52df7-102">Structure Variables (Visual Basic)</span></span>

<span data-ttu-id="52df7-103">Depois de criar uma estrutura, você pode declarar variáveis em nível de procedimento e de módulo como esse tipo.</span><span class="sxs-lookup"><span data-stu-id="52df7-103">Once you have created a structure, you can declare procedure-level and module-level variables as that type.</span></span> <span data-ttu-id="52df7-104">Por exemplo, você pode criar uma estrutura que registra informações sobre um sistema de computador.</span><span class="sxs-lookup"><span data-stu-id="52df7-104">For example, you can create a structure that records information about a computer system.</span></span> <span data-ttu-id="52df7-105">O exemplo a seguir demonstra isso.</span><span class="sxs-lookup"><span data-stu-id="52df7-105">The following example demonstrates this.</span></span>

```vb
Public Structure systemInfo
    Public cPU As String
    Public memory As Long
    Public purchaseDate As Date
End Structure
```

<span data-ttu-id="52df7-106">Agora você pode declarar variáveis desse tipo.</span><span class="sxs-lookup"><span data-stu-id="52df7-106">You can now declare variables of that type.</span></span> <span data-ttu-id="52df7-107">A declaração a seguir ilustra isso.</span><span class="sxs-lookup"><span data-stu-id="52df7-107">The following declaration illustrates this.</span></span>

```vb
Dim mySystem, yourSystem As systemInfo
```

> [!NOTE]
> <span data-ttu-id="52df7-108">Em classes e módulos, as estruturas declaradas usando a [instrução Dim](../../../language-reference/statements/dim-statement.md) assumem o acesso público como padrão.</span><span class="sxs-lookup"><span data-stu-id="52df7-108">In classes and modules, structures declared using the [Dim Statement](../../../language-reference/statements/dim-statement.md) default to public access.</span></span> <span data-ttu-id="52df7-109">Se você pretende que uma estrutura seja privada, certifique-se de declará-la usando a palavra-chave [Private](../../../language-reference/modifiers/private.md) .</span><span class="sxs-lookup"><span data-stu-id="52df7-109">If you intend a structure to be private, make sure you declare it using the [Private](../../../language-reference/modifiers/private.md) keyword.</span></span>

## <a name="access-to-structure-values"></a><span data-ttu-id="52df7-110">Acesso a valores de estrutura</span><span class="sxs-lookup"><span data-stu-id="52df7-110">Access to Structure Values</span></span>

<span data-ttu-id="52df7-111">Para atribuir e recuperar valores dos elementos de uma variável de estrutura, use a mesma sintaxe usada para definir e obter propriedades em um objeto.</span><span class="sxs-lookup"><span data-stu-id="52df7-111">To assign and retrieve values from the elements of a structure variable, you use the same syntax as you use to set and get properties on an object.</span></span> <span data-ttu-id="52df7-112">Você coloca o operador de acesso de membro ( `.` ) entre o nome da variável de estrutura e o nome do elemento.</span><span class="sxs-lookup"><span data-stu-id="52df7-112">You place the member access operator (`.`) between the structure variable name and the element name.</span></span> <span data-ttu-id="52df7-113">O exemplo a seguir acessa os elementos das variáveis declaradas anteriormente como tipo `systemInfo` .</span><span class="sxs-lookup"><span data-stu-id="52df7-113">The following example accesses elements of the variables previously declared as type `systemInfo`.</span></span>

```vb
mySystem.cPU = "486"
Dim tooOld As Boolean
If yourSystem.purchaseDate < #1/1/1992# Then tooOld = True
```

## <a name="assigning-structure-variables"></a><span data-ttu-id="52df7-114">Atribuindo variáveis de estrutura</span><span class="sxs-lookup"><span data-stu-id="52df7-114">Assigning Structure Variables</span></span>

<span data-ttu-id="52df7-115">Você também pode atribuir uma variável a outra se ambas forem do mesmo tipo de estrutura.</span><span class="sxs-lookup"><span data-stu-id="52df7-115">You can also assign one variable to another if both are of the same structure type.</span></span> <span data-ttu-id="52df7-116">Isso copia todos os elementos de uma estrutura para os elementos correspondentes no outro.</span><span class="sxs-lookup"><span data-stu-id="52df7-116">This copies all the elements of one structure to the corresponding elements in the other.</span></span> <span data-ttu-id="52df7-117">A declaração a seguir ilustra isso.</span><span class="sxs-lookup"><span data-stu-id="52df7-117">The following declaration illustrates this.</span></span>

```vb
yourSystem = mySystem
```

<span data-ttu-id="52df7-118">Se um elemento de estrutura for um tipo de referência, como `String` uma `Object` matriz, ou, o ponteiro para os dados será copiado.</span><span class="sxs-lookup"><span data-stu-id="52df7-118">If a structure element is a reference type, such as a `String`, `Object`, or array, the pointer to the data is copied.</span></span> <span data-ttu-id="52df7-119">No exemplo anterior, se `systemInfo` tiver incluído uma variável de objeto, o exemplo anterior teria copiado o ponteiro de `mySystem` para `yourSystem` , e uma alteração nos dados do objeto por meio de uma estrutura estaria em vigor quando acessada por meio da outra estrutura.</span><span class="sxs-lookup"><span data-stu-id="52df7-119">In the previous example, if `systemInfo` had included an object variable, then the preceding example would have copied the pointer from `mySystem` to `yourSystem`, and a change to the object's data through one structure would be in effect when accessed through the other structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="52df7-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="52df7-120">See also</span></span>

- [<span data-ttu-id="52df7-121">Tipos de dados</span><span class="sxs-lookup"><span data-stu-id="52df7-121">Data Types</span></span>](index.md)
- [<span data-ttu-id="52df7-122">Tipos de dados elementares</span><span class="sxs-lookup"><span data-stu-id="52df7-122">Elementary Data Types</span></span>](elementary-data-types.md)
- [<span data-ttu-id="52df7-123">Tipos de dados compostos</span><span class="sxs-lookup"><span data-stu-id="52df7-123">Composite Data Types</span></span>](composite-data-types.md)
- [<span data-ttu-id="52df7-124">Tipos de valor e referência</span><span class="sxs-lookup"><span data-stu-id="52df7-124">Value Types and Reference Types</span></span>](value-types-and-reference-types.md)
- [<span data-ttu-id="52df7-125">Estruturas</span><span class="sxs-lookup"><span data-stu-id="52df7-125">Structures</span></span>](structures.md)
- [<span data-ttu-id="52df7-126">Solução de problemas de tipos de dados</span><span class="sxs-lookup"><span data-stu-id="52df7-126">Troubleshooting Data Types</span></span>](troubleshooting-data-types.md)
- [<span data-ttu-id="52df7-127">Como: Declarar uma estrutura</span><span class="sxs-lookup"><span data-stu-id="52df7-127">How to: Declare a Structure</span></span>](how-to-declare-a-structure.md)
- [<span data-ttu-id="52df7-128">Estruturas e outros elementos de programação</span><span class="sxs-lookup"><span data-stu-id="52df7-128">Structures and Other Programming Elements</span></span>](structures-and-other-programming-elements.md)
- [<span data-ttu-id="52df7-129">Estruturas e classes</span><span class="sxs-lookup"><span data-stu-id="52df7-129">Structures and Classes</span></span>](structures-and-classes.md)
- [<span data-ttu-id="52df7-130">Instrução Structure</span><span class="sxs-lookup"><span data-stu-id="52df7-130">Structure Statement</span></span>](../../../language-reference/statements/structure-statement.md)
