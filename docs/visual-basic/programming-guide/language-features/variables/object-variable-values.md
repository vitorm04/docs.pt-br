---
title: Valores de variável de objeto
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], values
- values [Visual Basic], of object variables
- data types [Visual Basic], object variable
- variables [Visual Basic], object
ms.assetid: 31555704-58a3-49f1-9a0a-6421f605664f
ms.openlocfilehash: 8b93063d2d97802b1a7fdbc93e01040ff3337753
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351797"
---
# <a name="object-variable-values-visual-basic"></a><span data-ttu-id="ed8a3-102">Valores de variável de objeto (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ed8a3-102">Object Variable Values (Visual Basic)</span></span>
<span data-ttu-id="ed8a3-103">Uma variável do [tipo de dados Object](../../../../visual-basic/language-reference/data-types/object-data-type.md) pode se referir a dados de qualquer tipo.</span><span class="sxs-lookup"><span data-stu-id="ed8a3-103">A variable of the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md) can refer to data of any type.</span></span> <span data-ttu-id="ed8a3-104">O valor que você armazena em uma variável `Object` é mantido em outro lugar na memória, enquanto a própria variável contém um ponteiro para os dados.</span><span class="sxs-lookup"><span data-stu-id="ed8a3-104">The value you store in an `Object` variable is kept elsewhere in memory, while the variable itself holds a pointer to the data.</span></span>  
  
## <a name="object-classifier-functions"></a><span data-ttu-id="ed8a3-105">Funções de classificação de objeto</span><span class="sxs-lookup"><span data-stu-id="ed8a3-105">Object Classifier Functions</span></span>  
 <span data-ttu-id="ed8a3-106">Visual Basic fornece funções que retornam informações sobre a qual uma variável `Object` se refere, conforme mostrado na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="ed8a3-106">Visual Basic supplies functions that return information about what an `Object` variable refers to, as shown in the following table.</span></span>  
  
|<span data-ttu-id="ed8a3-107">Função</span><span class="sxs-lookup"><span data-stu-id="ed8a3-107">Function</span></span>|<span data-ttu-id="ed8a3-108">Retornará true se a variável de objeto se referir a</span><span class="sxs-lookup"><span data-stu-id="ed8a3-108">Returns True if the Object variable refers to</span></span>|  
|--------------|---------------------------------------------------|  
|<xref:Microsoft.VisualBasic.Information.IsArray%2A>|<span data-ttu-id="ed8a3-109">Uma matriz de valores, em vez de um único valor</span><span class="sxs-lookup"><span data-stu-id="ed8a3-109">An array of values, rather than a single value</span></span>|  
|<xref:Microsoft.VisualBasic.Information.IsDate%2A>|<span data-ttu-id="ed8a3-110">Um valor de [tipo de dados Date](../../../../visual-basic/language-reference/data-types/date-data-type.md) ou uma cadeia de caracteres que pode ser interpretada como um valor de data e hora</span><span class="sxs-lookup"><span data-stu-id="ed8a3-110">A [Date Data Type](../../../../visual-basic/language-reference/data-types/date-data-type.md) value, or a string that can be interpreted as a date and time value</span></span>|  
|<xref:Microsoft.VisualBasic.Information.IsDBNull%2A>|<span data-ttu-id="ed8a3-111">Um objeto do tipo <xref:System.DBNull>, que representa dados ausentes ou inexistentes</span><span class="sxs-lookup"><span data-stu-id="ed8a3-111">An object of type <xref:System.DBNull>, which represents missing or nonexistent data</span></span>|  
|<xref:Microsoft.VisualBasic.Information.IsError%2A>|<span data-ttu-id="ed8a3-112">Um objeto de exceção, que deriva de <xref:System.Exception></span><span class="sxs-lookup"><span data-stu-id="ed8a3-112">An exception object, which derives from <xref:System.Exception></span></span>|  
|<xref:Microsoft.VisualBasic.Information.IsNothing%2A>|<span data-ttu-id="ed8a3-113">[Nada](../../../../visual-basic/language-reference/nothing.md), ou seja, nenhum objeto está atribuído atualmente à variável</span><span class="sxs-lookup"><span data-stu-id="ed8a3-113">[Nothing](../../../../visual-basic/language-reference/nothing.md), that is, no object is currently assigned to the variable</span></span>|  
|<xref:Microsoft.VisualBasic.Information.IsNumeric%2A>|<span data-ttu-id="ed8a3-114">Um número ou uma cadeia de caracteres que pode ser interpretada como um número</span><span class="sxs-lookup"><span data-stu-id="ed8a3-114">A number, or a string that can be interpreted as a number</span></span>|  
|<xref:Microsoft.VisualBasic.Information.IsReference%2A>|<span data-ttu-id="ed8a3-115">Um tipo de referência (como uma cadeia de caracteres, matriz, delegado ou tipo de classe)</span><span class="sxs-lookup"><span data-stu-id="ed8a3-115">A reference type (such as a string, array, delegate, or class type)</span></span>|  
  
 <span data-ttu-id="ed8a3-116">Você pode usar essas funções para evitar o envio de um valor inválido para uma operação ou um procedimento.</span><span class="sxs-lookup"><span data-stu-id="ed8a3-116">You can use these functions to avoid submitting an invalid value to an operation or a procedure.</span></span>  
  
## <a name="typeof-operator"></a><span data-ttu-id="ed8a3-117">Operador TypeOf</span><span class="sxs-lookup"><span data-stu-id="ed8a3-117">TypeOf Operator</span></span>  
 <span data-ttu-id="ed8a3-118">Você também pode usar o [operador typeof](../../../../visual-basic/language-reference/operators/typeof-operator.md) para determinar se uma variável de objeto atualmente se refere a um tipo de dados específico.</span><span class="sxs-lookup"><span data-stu-id="ed8a3-118">You can also use the [TypeOf Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md) to determine whether an object variable currently refers to a specific data type.</span></span> <span data-ttu-id="ed8a3-119">A expressão `TypeOf`...`Is` é avaliada como `True` se o tipo de tempo de execução do operando é derivado de ou implementa o tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="ed8a3-119">The `TypeOf`...`Is` expression evaluates to `True` if the run-time type of the operand is derived from or implements the specified type.</span></span>  
  
 <span data-ttu-id="ed8a3-120">O exemplo a seguir usa `TypeOf` em variáveis de objeto referindo-se a tipos de referência e valor.</span><span class="sxs-lookup"><span data-stu-id="ed8a3-120">The following example uses `TypeOf` on object variables referring to value and reference types.</span></span>  
  
```vb  
' The following statement puts a value type (Integer) in an Object variable.  
Dim num As Object = 10  
' The following statement puts a reference type (Form) in an Object variable.  
Dim frm As Object = New Form()  
If TypeOf num Is Long Then Debug.WriteLine("num is Long")  
If TypeOf num Is Integer Then Debug.WriteLine("num is Integer")  
If TypeOf num Is Short Then Debug.WriteLine("num is Short")  
If TypeOf num Is Object Then Debug.WriteLine("num is Object")  
If TypeOf frm Is Form Then Debug.WriteLine("frm is Form")  
If TypeOf frm Is Label Then Debug.WriteLine("frm is Label")  
If TypeOf frm Is Object Then Debug.WriteLine("frm is Object")  
```  
  
 <span data-ttu-id="ed8a3-121">O exemplo anterior grava as seguintes linhas na janela de **depuração** :</span><span class="sxs-lookup"><span data-stu-id="ed8a3-121">The preceding example writes the following lines to the **Debug** window:</span></span>  
  
 `num is Integer`  
  
 `num is Object`  
  
 `frm is Form`  
  
 `frm is Object`  
  
 <span data-ttu-id="ed8a3-122">A variável de objeto `num` refere-se a dados do tipo `Integer`e `frm` se refere a um objeto da classe <xref:System.Windows.Forms.Form>.</span><span class="sxs-lookup"><span data-stu-id="ed8a3-122">The object variable `num` refers to data of type `Integer`, and `frm` refers to an object of class <xref:System.Windows.Forms.Form>.</span></span>  
  
## <a name="object-arrays"></a><span data-ttu-id="ed8a3-123">Matrizes de objetos</span><span class="sxs-lookup"><span data-stu-id="ed8a3-123">Object Arrays</span></span>  
 <span data-ttu-id="ed8a3-124">Você pode declarar e usar uma matriz de variáveis de `Object`.</span><span class="sxs-lookup"><span data-stu-id="ed8a3-124">You can declare and use an array of `Object` variables.</span></span> <span data-ttu-id="ed8a3-125">Isso é útil quando você precisa lidar com uma variedade de tipos de dados e classes de objeto.</span><span class="sxs-lookup"><span data-stu-id="ed8a3-125">This is useful when you need to handle a variety of data types and object classes.</span></span> <span data-ttu-id="ed8a3-126">Todos os elementos em uma matriz devem ter o mesmo tipo de dados declarado.</span><span class="sxs-lookup"><span data-stu-id="ed8a3-126">All the elements in an array must have the same declared data type.</span></span> <span data-ttu-id="ed8a3-127">Declarar esse tipo de dados como `Object` permite que você armazene objetos e instâncias de classe junto com outros tipos de dados na matriz.</span><span class="sxs-lookup"><span data-stu-id="ed8a3-127">Declaring this data type as `Object` allows you to store objects and class instances alongside other data types in the array.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed8a3-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ed8a3-128">See also</span></span>

- [<span data-ttu-id="ed8a3-129">Variáveis de Objeto</span><span class="sxs-lookup"><span data-stu-id="ed8a3-129">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="ed8a3-130">Declaração de Variável do Objeto</span><span class="sxs-lookup"><span data-stu-id="ed8a3-130">Object Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [<span data-ttu-id="ed8a3-131">Atribuição de variável do objeto</span><span class="sxs-lookup"><span data-stu-id="ed8a3-131">Object Variable Assignment</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [<span data-ttu-id="ed8a3-132">Como fazer referência à instância atual de um objeto</span><span class="sxs-lookup"><span data-stu-id="ed8a3-132">How to: Refer to the Current Instance of an Object</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md)
- [<span data-ttu-id="ed8a3-133">Como determinar a que tipo uma variável de objeto se refere</span><span class="sxs-lookup"><span data-stu-id="ed8a3-133">How to: Determine What Type an Object Variable Refers To</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-what-type-an-object-variable-refers-to.md)
- [<span data-ttu-id="ed8a3-134">Como determinar se dois objetos estão relacionados</span><span class="sxs-lookup"><span data-stu-id="ed8a3-134">How to: Determine Whether Two Objects Are Related</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)
- [<span data-ttu-id="ed8a3-135">Como determinar se dois objetos são idênticos</span><span class="sxs-lookup"><span data-stu-id="ed8a3-135">How to: Determine Whether Two Objects Are Identical</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
- [<span data-ttu-id="ed8a3-136">Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="ed8a3-136">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
