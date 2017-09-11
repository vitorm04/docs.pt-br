---
title: "Valores de variável (Visual Basic) do objeto | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- object variables, values
- values, of object variables
- data types [Visual Basic], object variable
- variables [Visual Basic], object
ms.assetid: 31555704-58a3-49f1-9a0a-6421f605664f
caps.latest.revision: 18
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
ms.openlocfilehash: 5f42706a79212ae523b08ee336fdcacb3f761af6
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="object-variable-values-visual-basic"></a><span data-ttu-id="61aa8-102">Valores de variável de objeto (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="61aa8-102">Object Variable Values (Visual Basic)</span></span>
<span data-ttu-id="61aa8-103">Uma variável do [tipo de dados Object](../../../../visual-basic/language-reference/data-types/object-data-type.md) pode se referir a qualquer tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="61aa8-103">A variable of the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md) can refer to data of any type.</span></span> <span data-ttu-id="61aa8-104">O valor que armazenamos em uma `Object` variável é mantida em outro lugar na memória, enquanto a variável contém um ponteiro para os dados.</span><span class="sxs-lookup"><span data-stu-id="61aa8-104">The value you store in an `Object` variable is kept elsewhere in memory, while the variable itself holds a pointer to the data.</span></span>  
  
## <a name="object-classifier-functions"></a><span data-ttu-id="61aa8-105">Funções de classificação de objeto</span><span class="sxs-lookup"><span data-stu-id="61aa8-105">Object Classifier Functions</span></span>  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="61aa8-106">fornece funções que retornam informações sobre o que um `Object` variável refere-se a, conforme mostrado na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="61aa8-106"> supplies functions that return information about what an `Object` variable refers to, as shown in the following table.</span></span>  
  
|<span data-ttu-id="61aa8-107">Função</span><span class="sxs-lookup"><span data-stu-id="61aa8-107">Function</span></span>|<span data-ttu-id="61aa8-108">Retorna VERDADEIRO se a variável de objeto refere-se a</span><span class="sxs-lookup"><span data-stu-id="61aa8-108">Returns True if the Object variable refers to</span></span>|  
|--------------|---------------------------------------------------|  
|<span data-ttu-id="61aa8-109"><xref:Microsoft.VisualBasic.Information.IsArray%2A></xref:Microsoft.VisualBasic.Information.IsArray%2A></span><span class="sxs-lookup"><span data-stu-id="61aa8-109"><xref:Microsoft.VisualBasic.Information.IsArray%2A></span></span>|<span data-ttu-id="61aa8-110">Uma matriz de valores, em vez de um único valor</span><span class="sxs-lookup"><span data-stu-id="61aa8-110">An array of values, rather than a single value</span></span>|  
|<span data-ttu-id="61aa8-111"><xref:Microsoft.VisualBasic.Information.IsDate%2A></xref:Microsoft.VisualBasic.Information.IsDate%2A></span><span class="sxs-lookup"><span data-stu-id="61aa8-111"><xref:Microsoft.VisualBasic.Information.IsDate%2A></span></span>|<span data-ttu-id="61aa8-112">A [tipo de dados data](../../../../visual-basic/language-reference/data-types/date-data-type.md) valor ou uma cadeia de caracteres que pode ser interpretada como um valor de data e hora</span><span class="sxs-lookup"><span data-stu-id="61aa8-112">A [Date Data Type](../../../../visual-basic/language-reference/data-types/date-data-type.md) value, or a string that can be interpreted as a date and time value</span></span>|  
|<span data-ttu-id="61aa8-113"><xref:Microsoft.VisualBasic.Information.IsDBNull%2A></xref:Microsoft.VisualBasic.Information.IsDBNull%2A></span><span class="sxs-lookup"><span data-stu-id="61aa8-113"><xref:Microsoft.VisualBasic.Information.IsDBNull%2A></span></span>|<span data-ttu-id="61aa8-114">Um objeto de tipo <xref:System.DBNull>que representa dados ausentes ou inexistentes</xref:System.DBNull></span><span class="sxs-lookup"><span data-stu-id="61aa8-114">An object of type <xref:System.DBNull>, which represents missing or nonexistent data</span></span>|  
|<span data-ttu-id="61aa8-115"><xref:Microsoft.VisualBasic.Information.IsError%2A></xref:Microsoft.VisualBasic.Information.IsError%2A></span><span class="sxs-lookup"><span data-stu-id="61aa8-115"><xref:Microsoft.VisualBasic.Information.IsError%2A></span></span>|<span data-ttu-id="61aa8-116">Um objeto de exceção, que é derivada de<xref:System.Exception></xref:System.Exception></span><span class="sxs-lookup"><span data-stu-id="61aa8-116">An exception object, which derives from <xref:System.Exception></span></span>|  
|<span data-ttu-id="61aa8-117"><xref:Microsoft.VisualBasic.Information.IsNothing%2A></xref:Microsoft.VisualBasic.Information.IsNothing%2A></span><span class="sxs-lookup"><span data-stu-id="61aa8-117"><xref:Microsoft.VisualBasic.Information.IsNothing%2A></span></span>|<span data-ttu-id="61aa8-118">[Nada](../../../../visual-basic/language-reference/nothing.md), ou seja, nenhum objeto atualmente atribuído à variável</span><span class="sxs-lookup"><span data-stu-id="61aa8-118">[Nothing](../../../../visual-basic/language-reference/nothing.md), that is, no object is currently assigned to the variable</span></span>|  
|<span data-ttu-id="61aa8-119"><xref:Microsoft.VisualBasic.Information.IsNumeric%2A></xref:Microsoft.VisualBasic.Information.IsNumeric%2A></span><span class="sxs-lookup"><span data-stu-id="61aa8-119"><xref:Microsoft.VisualBasic.Information.IsNumeric%2A></span></span>|<span data-ttu-id="61aa8-120">Um número ou uma cadeia de caracteres que pode ser interpretada como um número</span><span class="sxs-lookup"><span data-stu-id="61aa8-120">A number, or a string that can be interpreted as a number</span></span>|  
|<span data-ttu-id="61aa8-121"><xref:Microsoft.VisualBasic.Information.IsReference%2A></xref:Microsoft.VisualBasic.Information.IsReference%2A></span><span class="sxs-lookup"><span data-stu-id="61aa8-121"><xref:Microsoft.VisualBasic.Information.IsReference%2A></span></span>|<span data-ttu-id="61aa8-122">Um tipo de referência (como uma cadeia de caracteres, matriz, representante ou tipo de classe)</span><span class="sxs-lookup"><span data-stu-id="61aa8-122">A reference type (such as a string, array, delegate, or class type)</span></span>|  
  
 <span data-ttu-id="61aa8-123">Você pode usar essas funções para evitar enviar um valor inválido para uma operação ou um procedimento.</span><span class="sxs-lookup"><span data-stu-id="61aa8-123">You can use these functions to avoid submitting an invalid value to an operation or a procedure.</span></span>  
  
## <a name="typeof-operator"></a><span data-ttu-id="61aa8-124">Operador TypeOf</span><span class="sxs-lookup"><span data-stu-id="61aa8-124">TypeOf Operator</span></span>  
 <span data-ttu-id="61aa8-125">Você também pode usar o [operador TypeOf](../../../../visual-basic/language-reference/operators/typeof-operator.md) para determinar se uma variável de objeto no momento se refere a um tipo de dados específico.</span><span class="sxs-lookup"><span data-stu-id="61aa8-125">You can also use the [TypeOf Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md) to determine whether an object variable currently refers to a specific data type.</span></span> <span data-ttu-id="61aa8-126">The `TypeOf`... `Is` expressão é avaliada como `True` se o tipo de tempo de execução do operando é derivado de ou implementa o tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="61aa8-126">The `TypeOf`...`Is` expression evaluates to `True` if the run-time type of the operand is derived from or implements the specified type.</span></span>  
  
 <span data-ttu-id="61aa8-127">O exemplo a seguir usa `TypeOf` em variáveis de objeto referindo-se a tipos de referência e valor.</span><span class="sxs-lookup"><span data-stu-id="61aa8-127">The following example uses `TypeOf` on object variables referring to value and reference types.</span></span>  
  
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
  
 <span data-ttu-id="61aa8-128">O exemplo anterior grava as seguintes linhas para o **depurar** janela:</span><span class="sxs-lookup"><span data-stu-id="61aa8-128">The preceding example writes the following lines to the **Debug** window:</span></span>  
  
 `num is Integer`  
  
 `num is Object`  
  
 `frm is Form`  
  
 `frm is Object`  
  
 <span data-ttu-id="61aa8-129">A variável de objeto `num` refere-se ao tipo de dados `Integer`, e `frm` refere-se a um objeto da classe <xref:System.Windows.Forms.Form>.</xref:System.Windows.Forms.Form></span><span class="sxs-lookup"><span data-stu-id="61aa8-129">The object variable `num` refers to data of type `Integer`, and `frm` refers to an object of class <xref:System.Windows.Forms.Form>.</span></span>  
  
## <a name="object-arrays"></a><span data-ttu-id="61aa8-130">Matrizes de objetos</span><span class="sxs-lookup"><span data-stu-id="61aa8-130">Object Arrays</span></span>  
 <span data-ttu-id="61aa8-131">Você pode declarar e usar uma matriz de `Object` variáveis.</span><span class="sxs-lookup"><span data-stu-id="61aa8-131">You can declare and use an array of `Object` variables.</span></span> <span data-ttu-id="61aa8-132">Isso é útil quando você precisar manipular uma variedade de tipos de dados e classes de objeto.</span><span class="sxs-lookup"><span data-stu-id="61aa8-132">This is useful when you need to handle a variety of data types and object classes.</span></span> <span data-ttu-id="61aa8-133">Todos os elementos em uma matriz devem ter os mesmos dados declarados tipo.</span><span class="sxs-lookup"><span data-stu-id="61aa8-133">All the elements in an array must have the same declared data type.</span></span> <span data-ttu-id="61aa8-134">Declarando esse tipo de dados como `Object` permite armazenar objetos e instâncias juntamente com outros tipos de dados na matriz de classe.</span><span class="sxs-lookup"><span data-stu-id="61aa8-134">Declaring this data type as `Object` allows you to store objects and class instances alongside other data types in the array.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61aa8-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="61aa8-135">See Also</span></span>  
 <span data-ttu-id="61aa8-136">[Variáveis de objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md) </span><span class="sxs-lookup"><span data-stu-id="61aa8-136">[Object Variables](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md) </span></span>  
<span data-ttu-id="61aa8-137"> [Declaração de variável de objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md) </span><span class="sxs-lookup"><span data-stu-id="61aa8-137"> [Object Variable Declaration](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md) </span></span>  
<span data-ttu-id="61aa8-138"> [Atribuição de variável de objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md) </span><span class="sxs-lookup"><span data-stu-id="61aa8-138"> [Object Variable Assignment](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md) </span></span>  
<span data-ttu-id="61aa8-139"> [Como: fazer referência à instância atual de um objeto](../../../../visual-basic/programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md) </span><span class="sxs-lookup"><span data-stu-id="61aa8-139"> [How to: Refer to the Current Instance of an Object](../../../../visual-basic/programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md) </span></span>  
<span data-ttu-id="61aa8-140"> [Como: determinar que tipo uma variável de objeto se refere](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-what-type-an-object-variable-refers-to.md) </span><span class="sxs-lookup"><span data-stu-id="61aa8-140"> [How to: Determine What Type an Object Variable Refers To](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-what-type-an-object-variable-refers-to.md) </span></span>  
<span data-ttu-id="61aa8-141"> [Como: determinar se dois objetos estão relacionados](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md) </span><span class="sxs-lookup"><span data-stu-id="61aa8-141"> [How to: Determine Whether Two Objects Are Related](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md) </span></span>  
<span data-ttu-id="61aa8-142"> [Como: determinar se dois objetos são idênticos](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md) </span><span class="sxs-lookup"><span data-stu-id="61aa8-142"> [How to: Determine Whether Two Objects Are Identical](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md) </span></span>  
<span data-ttu-id="61aa8-143"> [Tipos de Dados](../../../../visual-basic/programming-guide/language-features/data-types/index.md)</span><span class="sxs-lookup"><span data-stu-id="61aa8-143"> [Data Types](../../../../visual-basic/programming-guide/language-features/data-types/index.md)</span></span>
