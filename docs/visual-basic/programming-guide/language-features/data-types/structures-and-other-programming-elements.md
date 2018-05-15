---
title: Estruturas e outros elementos de programação (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- structures [Visual Basic], arrays
- procedures [Visual Basic], structures as arguments to
- objects [Visual Basic], structure elements
- arrays [Visual Basic], structure elements
- nested structures [Visual Basic]
ms.assetid: 0f849313-ccd2-4c9a-acb9-69de6751c088
ms.openlocfilehash: 7b375c5a45998fc0bd06f7c075f23a30dd377295
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="structures-and-other-programming-elements-visual-basic"></a><span data-ttu-id="011ac-102">Estruturas e outros elementos de programação (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="011ac-102">Structures and Other Programming Elements (Visual Basic)</span></span>
<span data-ttu-id="011ac-103">Você pode usar as estruturas em conjunto com matrizes, objetos e procedimentos, bem como entre si.</span><span class="sxs-lookup"><span data-stu-id="011ac-103">You can use structures in conjunction with arrays, objects, and procedures, as well as with each other.</span></span> <span data-ttu-id="011ac-104">As interações usam a mesma sintaxe que esses elementos usam individualmente.</span><span class="sxs-lookup"><span data-stu-id="011ac-104">The interactions use the same syntax as these elements use individually.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="011ac-105">Você não pode inicializar qualquer um dos elementos de estrutura na declaração da estrutura.</span><span class="sxs-lookup"><span data-stu-id="011ac-105">You cannot initialize any of the structure elements in the structure declaration.</span></span> <span data-ttu-id="011ac-106">Você pode atribuir valores somente para elementos de uma variável que foi declarada com um tipo de estrutura.</span><span class="sxs-lookup"><span data-stu-id="011ac-106">You can assign values only to elements of a variable that has been declared to be of a structure type.</span></span>  
  
## <a name="structures-and-arrays"></a><span data-ttu-id="011ac-107">Estruturas e matrizes</span><span class="sxs-lookup"><span data-stu-id="011ac-107">Structures and Arrays</span></span>  
 <span data-ttu-id="011ac-108">Uma estrutura pode conter uma matriz como um ou mais dos seus elementos.</span><span class="sxs-lookup"><span data-stu-id="011ac-108">A structure can contain an array as one or more of its elements.</span></span> <span data-ttu-id="011ac-109">O exemplo a seguir ilustra essa situação.</span><span class="sxs-lookup"><span data-stu-id="011ac-109">The following example illustrates this.</span></span>  
  
```vb  
Public Structure systemInfo  
    Public cPU As String  
    Public memory As Long  
    Public diskDrives() As String  
    Public purchaseDate As Date  
End Structure   
```  
  
 <span data-ttu-id="011ac-110">Você acessa os valores de uma matriz em uma estrutura da mesma maneira que você acessa uma propriedade em um objeto.</span><span class="sxs-lookup"><span data-stu-id="011ac-110">You access the values of an array within a structure the same way you access a property on an object.</span></span> <span data-ttu-id="011ac-111">O exemplo a seguir ilustra essa situação.</span><span class="sxs-lookup"><span data-stu-id="011ac-111">The following example illustrates this.</span></span>  
  
```vb  
Dim mySystem As systemInfo  
ReDim mySystem.diskDrives(3)  
mySystem.diskDrives(0) = "1.44 MB"  
```  
  
 <span data-ttu-id="011ac-112">Você também pode declarar uma matriz de estruturas.</span><span class="sxs-lookup"><span data-stu-id="011ac-112">You can also declare an array of structures.</span></span> <span data-ttu-id="011ac-113">O exemplo a seguir ilustra essa situação.</span><span class="sxs-lookup"><span data-stu-id="011ac-113">The following example illustrates this.</span></span>  
  
```vb  
Dim allSystems(100) As systemInfo  
```  
  
 <span data-ttu-id="011ac-114">Você seguir as mesmas regras para acessar os componentes dessa arquitetura de dados.</span><span class="sxs-lookup"><span data-stu-id="011ac-114">You follow the same rules to access the components of this data architecture.</span></span> <span data-ttu-id="011ac-115">O exemplo a seguir ilustra essa situação.</span><span class="sxs-lookup"><span data-stu-id="011ac-115">The following example illustrates this.</span></span>  
  
```vb  
ReDim allSystems(5).diskDrives(3)  
allSystems(5).CPU = "386SX"  
allSystems(5).diskDrives(2) = "100M SCSI"  
```  
  
## <a name="structures-and-objects"></a><span data-ttu-id="011ac-116">Estruturas e objetos</span><span class="sxs-lookup"><span data-stu-id="011ac-116">Structures and Objects</span></span>  
 <span data-ttu-id="011ac-117">Uma estrutura pode conter um objeto como um ou mais dos seus elementos.</span><span class="sxs-lookup"><span data-stu-id="011ac-117">A structure can contain an object as one or more of its elements.</span></span> <span data-ttu-id="011ac-118">O exemplo a seguir ilustra essa situação.</span><span class="sxs-lookup"><span data-stu-id="011ac-118">The following example illustrates this.</span></span>  
  
```vb  
Protected Structure userInput  
    Public userName As String  
    Public inputForm As System.Windows.Forms.Form  
    Public userFileNumber As Integer  
End Structure  
```  
  
 <span data-ttu-id="011ac-119">Você deve usar uma classe de objeto específica em tal declaração, em vez de `Object`.</span><span class="sxs-lookup"><span data-stu-id="011ac-119">You should use a specific object class in such a declaration, rather than `Object`.</span></span>  
  
## <a name="structures-and-procedures"></a><span data-ttu-id="011ac-120">Estruturas e procedimentos</span><span class="sxs-lookup"><span data-stu-id="011ac-120">Structures and Procedures</span></span>  
 <span data-ttu-id="011ac-121">Você pode passar uma estrutura como um argumento de procedimento.</span><span class="sxs-lookup"><span data-stu-id="011ac-121">You can pass a structure as a procedure argument.</span></span> <span data-ttu-id="011ac-122">O exemplo a seguir ilustra essa situação.</span><span class="sxs-lookup"><span data-stu-id="011ac-122">The following example illustrates this.</span></span>  
  
```vb  
Public currentCPUName As String = "700MHz Pentium compatible"  
Public currentMemorySize As Long = 256  
Public Sub fillSystem(ByRef someSystem As systemInfo)  
    someSystem.cPU = currentCPUName  
    someSystem.memory = currentMemorySize  
    someSystem.purchaseDate = Now  
End Sub  
```  
  
 <span data-ttu-id="011ac-123">O exemplo anterior passa a estrutura *por referência*, que permite que o procedimento para modificar seus elementos para que as alterações tenham efeito no código de chamada.</span><span class="sxs-lookup"><span data-stu-id="011ac-123">The preceding example passes the structure *by reference*, which allows the procedure to modify its elements so that the changes take effect in the calling code.</span></span> <span data-ttu-id="011ac-124">Se você quiser proteger uma estrutura contra tal modificação, passá-lo por valor.</span><span class="sxs-lookup"><span data-stu-id="011ac-124">If you want to protect a structure against such modification, pass it by value.</span></span>  
  
 <span data-ttu-id="011ac-125">Você também pode retornar uma estrutura de uma `Function` procedimento.</span><span class="sxs-lookup"><span data-stu-id="011ac-125">You can also return a structure from a `Function` procedure.</span></span> <span data-ttu-id="011ac-126">O exemplo a seguir ilustra essa situação.</span><span class="sxs-lookup"><span data-stu-id="011ac-126">The following example illustrates this.</span></span>  
  
```vb  
Dim allSystems(100) As systemInfo  
Function findByDate(ByVal searchDate As Date) As systemInfo  
    Dim i As Integer  
    For i = 1 To 100  
        If allSystems(i).purchaseDate = searchDate Then Return allSystems(i)  
    Next i  
   ' Process error: system with desired purchase date not found.  
End Function  
```  
  
## <a name="structures-within-structures"></a><span data-ttu-id="011ac-127">Estruturas dentro de estruturas</span><span class="sxs-lookup"><span data-stu-id="011ac-127">Structures Within Structures</span></span>  
 <span data-ttu-id="011ac-128">As estruturas podem conter outras estruturas.</span><span class="sxs-lookup"><span data-stu-id="011ac-128">Structures can contain other structures.</span></span> <span data-ttu-id="011ac-129">O exemplo a seguir ilustra essa situação.</span><span class="sxs-lookup"><span data-stu-id="011ac-129">The following example illustrates this.</span></span>  
  
```vb  
Public Structure driveInfo  
    Public type As String  
    Public size As Long  
End Structure  
Public Structure systemInfo  
    Public cPU As String  
    Public memory As Long  
    Public diskDrives() As driveInfo  
    Public purchaseDate As Date  
End Structure  
```  
  
```vb  
Dim allSystems(100) As systemInfo  
ReDim allSystems(1).diskDrives(3)  
allSystems(1).diskDrives(0).type = "Floppy"  
```  
  
 <span data-ttu-id="011ac-130">Você também pode usar essa técnica para encapsular uma estrutura definida em um módulo dentro de uma estrutura definida em um módulo diferente.</span><span class="sxs-lookup"><span data-stu-id="011ac-130">You can also use this technique to encapsulate a structure defined in one module within a structure defined in a different module.</span></span>  
  
 <span data-ttu-id="011ac-131">As estruturas podem conter outras estruturas a uma profundidade arbitrária.</span><span class="sxs-lookup"><span data-stu-id="011ac-131">Structures can contain other structures to an arbitrary depth.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="011ac-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="011ac-132">See Also</span></span>  
 [<span data-ttu-id="011ac-133">Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="011ac-133">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [<span data-ttu-id="011ac-134">Tipos de Dados Elementares</span><span class="sxs-lookup"><span data-stu-id="011ac-134">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [<span data-ttu-id="011ac-135">Tipos de Dados Compostos</span><span class="sxs-lookup"><span data-stu-id="011ac-135">Composite Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)  
 [<span data-ttu-id="011ac-136">Tipos de Valor e Tipos de Referência</span><span class="sxs-lookup"><span data-stu-id="011ac-136">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [<span data-ttu-id="011ac-137">Estruturas</span><span class="sxs-lookup"><span data-stu-id="011ac-137">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="011ac-138">Solução de problemas de Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="011ac-138">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [<span data-ttu-id="011ac-139">Como declarar uma estrutura</span><span class="sxs-lookup"><span data-stu-id="011ac-139">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [<span data-ttu-id="011ac-140">Variáveis de Estrutura</span><span class="sxs-lookup"><span data-stu-id="011ac-140">Structure Variables</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structure-variables.md)  
 [<span data-ttu-id="011ac-141">Estruturas e Classes</span><span class="sxs-lookup"><span data-stu-id="011ac-141">Structures and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)  
 [<span data-ttu-id="011ac-142">Instrução Structure</span><span class="sxs-lookup"><span data-stu-id="011ac-142">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)
