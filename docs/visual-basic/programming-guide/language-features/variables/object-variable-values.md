---
title: Valores de variável de objeto (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], values
- values [Visual Basic], of object variables
- data types [Visual Basic], object variable
- variables [Visual Basic], object
ms.assetid: 31555704-58a3-49f1-9a0a-6421f605664f
ms.openlocfilehash: ce38089e91b25cf50e738d956881f3a44bfa3306
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54588711"
---
# <a name="object-variable-values-visual-basic"></a><span data-ttu-id="f66b9-102">Valores de variável de objeto (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f66b9-102">Object Variable Values (Visual Basic)</span></span>
<span data-ttu-id="f66b9-103">Uma variável do [tipo de dados de objeto](../../../../visual-basic/language-reference/data-types/object-data-type.md) pode se referir a qualquer tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="f66b9-103">A variable of the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md) can refer to data of any type.</span></span> <span data-ttu-id="f66b9-104">O valor que você armazene em um `Object` variável é mantida em outro lugar na memória, enquanto a variável contém um ponteiro para os dados.</span><span class="sxs-lookup"><span data-stu-id="f66b9-104">The value you store in an `Object` variable is kept elsewhere in memory, while the variable itself holds a pointer to the data.</span></span>  
  
## <a name="object-classifier-functions"></a><span data-ttu-id="f66b9-105">Funções de classificação do objeto</span><span class="sxs-lookup"><span data-stu-id="f66b9-105">Object Classifier Functions</span></span>  
 <span data-ttu-id="f66b9-106">Visual Basic fornece funções que retornam informações sobre o que um `Object` variável refere-se a, conforme mostrado na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="f66b9-106">Visual Basic supplies functions that return information about what an `Object` variable refers to, as shown in the following table.</span></span>  
  
|<span data-ttu-id="f66b9-107">Função</span><span class="sxs-lookup"><span data-stu-id="f66b9-107">Function</span></span>|<span data-ttu-id="f66b9-108">Retorna VERDADEIRO se a variável de objeto se refere a</span><span class="sxs-lookup"><span data-stu-id="f66b9-108">Returns True if the Object variable refers to</span></span>|  
|--------------|---------------------------------------------------|  
|<xref:Microsoft.VisualBasic.Information.IsArray%2A>|<span data-ttu-id="f66b9-109">Uma matriz de valores, em vez de um único valor</span><span class="sxs-lookup"><span data-stu-id="f66b9-109">An array of values, rather than a single value</span></span>|  
|<xref:Microsoft.VisualBasic.Information.IsDate%2A>|<span data-ttu-id="f66b9-110">Um [tipo de dados Date](../../../../visual-basic/language-reference/data-types/date-data-type.md) valor ou uma cadeia de caracteres que pode ser interpretada como um valor de data e hora</span><span class="sxs-lookup"><span data-stu-id="f66b9-110">A [Date Data Type](../../../../visual-basic/language-reference/data-types/date-data-type.md) value, or a string that can be interpreted as a date and time value</span></span>|  
|<xref:Microsoft.VisualBasic.Information.IsDBNull%2A>|<span data-ttu-id="f66b9-111">Um objeto do tipo <xref:System.DBNull>, que representa dados ausentes ou inexistentes</span><span class="sxs-lookup"><span data-stu-id="f66b9-111">An object of type <xref:System.DBNull>, which represents missing or nonexistent data</span></span>|  
|<xref:Microsoft.VisualBasic.Information.IsError%2A>|<span data-ttu-id="f66b9-112">Um objeto de exceção, que deriva de <xref:System.Exception></span><span class="sxs-lookup"><span data-stu-id="f66b9-112">An exception object, which derives from <xref:System.Exception></span></span>|  
|<xref:Microsoft.VisualBasic.Information.IsNothing%2A>|<span data-ttu-id="f66b9-113">[Nada](../../../../visual-basic/language-reference/nothing.md), ou seja, nenhum objeto atualmente atribuído à variável</span><span class="sxs-lookup"><span data-stu-id="f66b9-113">[Nothing](../../../../visual-basic/language-reference/nothing.md), that is, no object is currently assigned to the variable</span></span>|  
|<xref:Microsoft.VisualBasic.Information.IsNumeric%2A>|<span data-ttu-id="f66b9-114">Um número ou uma cadeia de caracteres que pode ser interpretada como um número</span><span class="sxs-lookup"><span data-stu-id="f66b9-114">A number, or a string that can be interpreted as a number</span></span>|  
|<xref:Microsoft.VisualBasic.Information.IsReference%2A>|<span data-ttu-id="f66b9-115">Um tipo de referência (como uma cadeia de caracteres, matriz, delegado ou tipo de classe)</span><span class="sxs-lookup"><span data-stu-id="f66b9-115">A reference type (such as a string, array, delegate, or class type)</span></span>|  
  
 <span data-ttu-id="f66b9-116">Você pode usar essas funções para evitar enviar um valor inválido para uma operação ou um procedimento.</span><span class="sxs-lookup"><span data-stu-id="f66b9-116">You can use these functions to avoid submitting an invalid value to an operation or a procedure.</span></span>  
  
## <a name="typeof-operator"></a><span data-ttu-id="f66b9-117">Operador TypeOf</span><span class="sxs-lookup"><span data-stu-id="f66b9-117">TypeOf Operator</span></span>  
 <span data-ttu-id="f66b9-118">Você também pode usar o [operador TypeOf](../../../../visual-basic/language-reference/operators/typeof-operator.md) para determinar se uma variável de objeto no momento se refere a um tipo de dados específico.</span><span class="sxs-lookup"><span data-stu-id="f66b9-118">You can also use the [TypeOf Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md) to determine whether an object variable currently refers to a specific data type.</span></span> <span data-ttu-id="f66b9-119">O `TypeOf`... `Is` expressão é avaliada como `True` se o tipo de tempo de execução do operando é derivado de ou implementa o tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="f66b9-119">The `TypeOf`...`Is` expression evaluates to `True` if the run-time type of the operand is derived from or implements the specified type.</span></span>  
  
 <span data-ttu-id="f66b9-120">O exemplo a seguir usa `TypeOf` em variáveis de objeto fazendo referência aos tipos de valor e referência.</span><span class="sxs-lookup"><span data-stu-id="f66b9-120">The following example uses `TypeOf` on object variables referring to value and reference types.</span></span>  
  
```  
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
  
 <span data-ttu-id="f66b9-121">O exemplo anterior grava as seguintes linhas para o **depurar** janela:</span><span class="sxs-lookup"><span data-stu-id="f66b9-121">The preceding example writes the following lines to the **Debug** window:</span></span>  
  
 `num is Integer`  
  
 `num is Object`  
  
 `frm is Form`  
  
 `frm is Object`  
  
 <span data-ttu-id="f66b9-122">A variável de objeto `num` refere-se ao tipo de dados `Integer`, e `frm` refere-se a um objeto da classe <xref:System.Windows.Forms.Form>.</span><span class="sxs-lookup"><span data-stu-id="f66b9-122">The object variable `num` refers to data of type `Integer`, and `frm` refers to an object of class <xref:System.Windows.Forms.Form>.</span></span>  
  
## <a name="object-arrays"></a><span data-ttu-id="f66b9-123">Matrizes de objetos</span><span class="sxs-lookup"><span data-stu-id="f66b9-123">Object Arrays</span></span>  
 <span data-ttu-id="f66b9-124">Você pode declarar e usar uma matriz de `Object` variáveis.</span><span class="sxs-lookup"><span data-stu-id="f66b9-124">You can declare and use an array of `Object` variables.</span></span> <span data-ttu-id="f66b9-125">Isso é útil quando você precisar manipular uma variedade de tipos de dados e classes de objeto.</span><span class="sxs-lookup"><span data-stu-id="f66b9-125">This is useful when you need to handle a variety of data types and object classes.</span></span> <span data-ttu-id="f66b9-126">Todos os elementos em uma matriz devem ter os mesmos dados declarados de tipo.</span><span class="sxs-lookup"><span data-stu-id="f66b9-126">All the elements in an array must have the same declared data type.</span></span> <span data-ttu-id="f66b9-127">Declarando esse tipo de dados como `Object` permite armazenar objetos e instâncias juntamente com outros tipos de dados na matriz de classe.</span><span class="sxs-lookup"><span data-stu-id="f66b9-127">Declaring this data type as `Object` allows you to store objects and class instances alongside other data types in the array.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f66b9-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f66b9-128">See also</span></span>
- [<span data-ttu-id="f66b9-129">Variáveis de Objeto</span><span class="sxs-lookup"><span data-stu-id="f66b9-129">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="f66b9-130">Declaração de Variável do Objeto</span><span class="sxs-lookup"><span data-stu-id="f66b9-130">Object Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [<span data-ttu-id="f66b9-131">Atribuição de variável do objeto</span><span class="sxs-lookup"><span data-stu-id="f66b9-131">Object Variable Assignment</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [<span data-ttu-id="f66b9-132">Como: Fazer referência à instância atual de um objeto</span><span class="sxs-lookup"><span data-stu-id="f66b9-132">How to: Refer to the Current Instance of an Object</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md)
- [<span data-ttu-id="f66b9-133">Como: Determinar que tipo uma variável de objeto se refere a</span><span class="sxs-lookup"><span data-stu-id="f66b9-133">How to: Determine What Type an Object Variable Refers To</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-what-type-an-object-variable-refers-to.md)
- [<span data-ttu-id="f66b9-134">Como: Determinar se dois objetos estão relacionados</span><span class="sxs-lookup"><span data-stu-id="f66b9-134">How to: Determine Whether Two Objects Are Related</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)
- [<span data-ttu-id="f66b9-135">Como: Determinar se dois objetos são idênticos</span><span class="sxs-lookup"><span data-stu-id="f66b9-135">How to: Determine Whether Two Objects Are Identical</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
- [<span data-ttu-id="f66b9-136">Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="f66b9-136">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
