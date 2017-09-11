---
title: "Estruturas e outros elementos de programação (Visual Basic) | Documentos do Microsoft"
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
- structures, arrays
- procedures, structures as arguments to
- objects [Visual Basic], structure elements
- arrays [Visual Basic], structure elements
- nested structures
ms.assetid: 0f849313-ccd2-4c9a-acb9-69de6751c088
caps.latest.revision: 13
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
ms.openlocfilehash: e5dd1ac182afb7ba1d743b96a0d541da30cc3477
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="structures-and-other-programming-elements-visual-basic"></a><span data-ttu-id="178e0-102">Estruturas e outros elementos de programação (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="178e0-102">Structures and Other Programming Elements (Visual Basic)</span></span>
<span data-ttu-id="178e0-103">Você pode usar as estruturas em conjunto com matrizes, objetos e procedimentos, bem como entre si.</span><span class="sxs-lookup"><span data-stu-id="178e0-103">You can use structures in conjunction with arrays, objects, and procedures, as well as with each other.</span></span> <span data-ttu-id="178e0-104">As interações usam a mesma sintaxe que esses elementos usam individualmente.</span><span class="sxs-lookup"><span data-stu-id="178e0-104">The interactions use the same syntax as these elements use individually.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="178e0-105">Você não pode inicializar qualquer um dos elementos de estrutura na declaração da estrutura.</span><span class="sxs-lookup"><span data-stu-id="178e0-105">You cannot initialize any of the structure elements in the structure declaration.</span></span> <span data-ttu-id="178e0-106">Você pode atribuir valores somente para elementos de uma variável que foi declarada para ser de um tipo de estrutura.</span><span class="sxs-lookup"><span data-stu-id="178e0-106">You can assign values only to elements of a variable that has been declared to be of a structure type.</span></span>  
  
## <a name="structures-and-arrays"></a><span data-ttu-id="178e0-107">Estruturas e matrizes</span><span class="sxs-lookup"><span data-stu-id="178e0-107">Structures and Arrays</span></span>  
 <span data-ttu-id="178e0-108">Uma estrutura pode conter uma matriz como um ou mais dos seus elementos.</span><span class="sxs-lookup"><span data-stu-id="178e0-108">A structure can contain an array as one or more of its elements.</span></span> <span data-ttu-id="178e0-109">O exemplo a seguir ilustra essa situação.</span><span class="sxs-lookup"><span data-stu-id="178e0-109">The following example illustrates this.</span></span>  
  
```vb  
Public Structure systemInfo  
    Public cPU As String  
    Public memory As Long  
    Public diskDrives() As String  
    Public purchaseDate As Date  
End Structure   
```  
  
 <span data-ttu-id="178e0-110">Você acessa os valores de uma matriz em uma estrutura da mesma maneira que você acessa uma propriedade em um objeto.</span><span class="sxs-lookup"><span data-stu-id="178e0-110">You access the values of an array within a structure the same way you access a property on an object.</span></span> <span data-ttu-id="178e0-111">O exemplo a seguir ilustra essa situação.</span><span class="sxs-lookup"><span data-stu-id="178e0-111">The following example illustrates this.</span></span>  
  
```vb  
Dim mySystem As systemInfo  
ReDim mySystem.diskDrives(3)  
mySystem.diskDrives(0) = "1.44 MB"  
```  
  
 <span data-ttu-id="178e0-112">Você também pode declarar uma matriz de estruturas.</span><span class="sxs-lookup"><span data-stu-id="178e0-112">You can also declare an array of structures.</span></span> <span data-ttu-id="178e0-113">O exemplo a seguir ilustra essa situação.</span><span class="sxs-lookup"><span data-stu-id="178e0-113">The following example illustrates this.</span></span>  
  
```vb  
Dim allSystems(100) As systemInfo  
```  
  
 <span data-ttu-id="178e0-114">Siga as mesmas regras para acessar os componentes dessa arquitetura de dados.</span><span class="sxs-lookup"><span data-stu-id="178e0-114">You follow the same rules to access the components of this data architecture.</span></span> <span data-ttu-id="178e0-115">O exemplo a seguir ilustra essa situação.</span><span class="sxs-lookup"><span data-stu-id="178e0-115">The following example illustrates this.</span></span>  
  
```vb  
ReDim allSystems(5).diskDrives(3)  
allSystems(5).CPU = "386SX"  
allSystems(5).diskDrives(2) = "100M SCSI"  
```  
  
## <a name="structures-and-objects"></a><span data-ttu-id="178e0-116">Estruturas e objetos</span><span class="sxs-lookup"><span data-stu-id="178e0-116">Structures and Objects</span></span>  
 <span data-ttu-id="178e0-117">Uma estrutura pode conter um objeto como um ou mais dos seus elementos.</span><span class="sxs-lookup"><span data-stu-id="178e0-117">A structure can contain an object as one or more of its elements.</span></span> <span data-ttu-id="178e0-118">O exemplo a seguir ilustra essa situação.</span><span class="sxs-lookup"><span data-stu-id="178e0-118">The following example illustrates this.</span></span>  
  
```vb  
Protected Structure userInput  
    Public userName As String  
    Public inputForm As System.Windows.Forms.Form  
    Public userFileNumber As Integer  
End Structure  
```  
  
 <span data-ttu-id="178e0-119">Você deve usar uma classe de objeto específica em tal declaração, em vez de `Object`.</span><span class="sxs-lookup"><span data-stu-id="178e0-119">You should use a specific object class in such a declaration, rather than `Object`.</span></span>  
  
## <a name="structures-and-procedures"></a><span data-ttu-id="178e0-120">Estruturas e procedimentos</span><span class="sxs-lookup"><span data-stu-id="178e0-120">Structures and Procedures</span></span>  
 <span data-ttu-id="178e0-121">Você pode passar uma estrutura como um argumento de procedimento.</span><span class="sxs-lookup"><span data-stu-id="178e0-121">You can pass a structure as a procedure argument.</span></span> <span data-ttu-id="178e0-122">O exemplo a seguir ilustra essa situação.</span><span class="sxs-lookup"><span data-stu-id="178e0-122">The following example illustrates this.</span></span>  
  
```vb  
Public currentCPUName As String = "700MHz Pentium compatible"  
Public currentMemorySize As Long = 256  
Public Sub fillSystem(ByRef someSystem As systemInfo)  
    someSystem.cPU = currentCPUName  
    someSystem.memory = currentMemorySize  
    someSystem.purchaseDate = Now  
End Sub  
```  
  
 <span data-ttu-id="178e0-123">O exemplo anterior passa a estrutura *por referência*, que permite que o procedimento modifique seus elementos de modo que as alterações tenham efeito no código de chamada.</span><span class="sxs-lookup"><span data-stu-id="178e0-123">The preceding example passes the structure *by reference*, which allows the procedure to modify its elements so that the changes take effect in the calling code.</span></span> <span data-ttu-id="178e0-124">Se você quiser proteger uma estrutura contra tal modificação, passá-lo por valor.</span><span class="sxs-lookup"><span data-stu-id="178e0-124">If you want to protect a structure against such modification, pass it by value.</span></span>  
  
 <span data-ttu-id="178e0-125">Você também pode retornar uma estrutura de uma `Function` procedimento.</span><span class="sxs-lookup"><span data-stu-id="178e0-125">You can also return a structure from a `Function` procedure.</span></span> <span data-ttu-id="178e0-126">O exemplo a seguir ilustra essa situação.</span><span class="sxs-lookup"><span data-stu-id="178e0-126">The following example illustrates this.</span></span>  
  
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
  
## <a name="structures-within-structures"></a><span data-ttu-id="178e0-127">Estruturas dentro de estruturas</span><span class="sxs-lookup"><span data-stu-id="178e0-127">Structures Within Structures</span></span>  
 <span data-ttu-id="178e0-128">Estruturas podem conter outras estruturas.</span><span class="sxs-lookup"><span data-stu-id="178e0-128">Structures can contain other structures.</span></span> <span data-ttu-id="178e0-129">O exemplo a seguir ilustra essa situação.</span><span class="sxs-lookup"><span data-stu-id="178e0-129">The following example illustrates this.</span></span>  
  
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
  
 <span data-ttu-id="178e0-130">Você também pode usar essa técnica para encapsular uma estrutura definida em um módulo dentro de uma estrutura definida em um módulo diferente.</span><span class="sxs-lookup"><span data-stu-id="178e0-130">You can also use this technique to encapsulate a structure defined in one module within a structure defined in a different module.</span></span>  
  
 <span data-ttu-id="178e0-131">Estruturas podem conter outras estruturas a uma profundidade arbitrária.</span><span class="sxs-lookup"><span data-stu-id="178e0-131">Structures can contain other structures to an arbitrary depth.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="178e0-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="178e0-132">See Also</span></span>  
 <span data-ttu-id="178e0-133">[Tipos de dados](../../../../visual-basic/programming-guide/language-features/data-types/index.md) </span><span class="sxs-lookup"><span data-stu-id="178e0-133">[Data Types](../../../../visual-basic/programming-guide/language-features/data-types/index.md) </span></span>  
<span data-ttu-id="178e0-134"> [Tipos de dados elementares](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="178e0-134"> [Elementary Data Types](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md) </span></span>  
<span data-ttu-id="178e0-135"> [Tipos de dados compostos](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="178e0-135"> [Composite Data Types](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md) </span></span>  
<span data-ttu-id="178e0-136"> [Tipos de valor e tipos de referência](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md) </span><span class="sxs-lookup"><span data-stu-id="178e0-136"> [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md) </span></span>  
<span data-ttu-id="178e0-137"> [Estruturas](../../../../visual-basic/programming-guide/language-features/data-types/structures.md) </span><span class="sxs-lookup"><span data-stu-id="178e0-137"> [Structures](../../../../visual-basic/programming-guide/language-features/data-types/structures.md) </span></span>  
<span data-ttu-id="178e0-138"> [Solucionando problemas de tipos de dados](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="178e0-138"> [Troubleshooting Data Types](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md) </span></span>  
<span data-ttu-id="178e0-139"> [Como: declarar uma estrutura](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md) </span><span class="sxs-lookup"><span data-stu-id="178e0-139"> [How to: Declare a Structure](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md) </span></span>  
<span data-ttu-id="178e0-140"> [Variáveis de estrutura](../../../../visual-basic/programming-guide/language-features/data-types/structure-variables.md) </span><span class="sxs-lookup"><span data-stu-id="178e0-140"> [Structure Variables](../../../../visual-basic/programming-guide/language-features/data-types/structure-variables.md) </span></span>  
<span data-ttu-id="178e0-141"> [Estruturas e Classes](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md) </span><span class="sxs-lookup"><span data-stu-id="178e0-141"> [Structures and Classes](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md) </span></span>  
<span data-ttu-id="178e0-142"> [Instrução Structure](../../../../visual-basic/language-reference/statements/structure-statement.md)</span><span class="sxs-lookup"><span data-stu-id="178e0-142"> [Structure Statement](../../../../visual-basic/language-reference/statements/structure-statement.md)</span></span>
