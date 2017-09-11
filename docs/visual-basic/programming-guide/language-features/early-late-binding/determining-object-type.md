---
title: Determinando o tipo de objeto (Visual Basic) | Documentos do Microsoft
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
- classes [Visual Basic], discovering which an object belongs to
- types [Visual Basic], determining Visual Basic object types
- object variables, testing values
- TypeOf...Is expression, object type at run time
- TypeName function
- objects [Visual Basic], type determining
ms.assetid: d95e7ad1-cd63-41d6-9a28-d7a1380d49c1
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
ms.openlocfilehash: fec7a275029dde469425b651d5b1220cb21ddbf6
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="determining-object-type-visual-basic"></a><span data-ttu-id="0f6c1-102">Determinando o tipo de objeto (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0f6c1-102">Determining Object Type (Visual Basic)</span></span>
<span data-ttu-id="0f6c1-103">Variáveis de objeto genérico (ou seja, variáveis que você declara como `Object`) pode conter objetos de qualquer classe.</span><span class="sxs-lookup"><span data-stu-id="0f6c1-103">Generic object variables (that is, variables you declare as `Object`) can hold objects from any class.</span></span> <span data-ttu-id="0f6c1-104">Ao usar variáveis do tipo `Object`, talvez você precise executar ações diferentes com base na classe de objeto; por exemplo, alguns objetos podem não oferecer suporte a uma determinada propriedade ou método.</span><span class="sxs-lookup"><span data-stu-id="0f6c1-104">When using variables of type `Object`, you may need to take different actions based on the class of the object; for example, some objects might not support a particular property or method.</span></span> [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="0f6c1-105">fornece dois meios de determinar qual tipo de objeto é armazenado em uma variável de objeto: o `TypeName` função e o `TypeOf...Is` operador.</span><span class="sxs-lookup"><span data-stu-id="0f6c1-105"> provides two means of determining which type of object is stored in an object variable: the `TypeName` function and the `TypeOf...Is` operator.</span></span>  
  
## <a name="typename-and-typeofis"></a><span data-ttu-id="0f6c1-106">TypeName e TypeOf... É</span><span class="sxs-lookup"><span data-stu-id="0f6c1-106">TypeName and TypeOf…Is</span></span>  
 <span data-ttu-id="0f6c1-107">O `TypeName` função retorna uma cadeia de caracteres e é a melhor opção quando você precisa armazenar ou exibir o nome da classe de um objeto, conforme mostrado no fragmento de código a seguir:</span><span class="sxs-lookup"><span data-stu-id="0f6c1-107">The `TypeName` function returns a string and is the best choice when you need to store or display the class name of an object, as shown in the following code fragment:</span></span>  
  
 <span data-ttu-id="0f6c1-108">[!code-vb[VbVbalrOOP&#92;](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="0f6c1-108">[!code-vb[VbVbalrOOP#92](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_1.vb)]</span></span>  
  
 <span data-ttu-id="0f6c1-109">O `TypeOf...Is` operador é a melhor opção para testar tipo de um objeto, pois é muito mais rápido do que uma comparação de cadeia de caracteres equivalente usando `TypeName`.</span><span class="sxs-lookup"><span data-stu-id="0f6c1-109">The `TypeOf...Is` operator is the best choice for testing an object's type, because it is much faster than an equivalent string comparison using `TypeName`.</span></span> <span data-ttu-id="0f6c1-110">O fragmento de código a seguir usa `TypeOf...Is` dentro de um `If...Then...Else` instrução:</span><span class="sxs-lookup"><span data-stu-id="0f6c1-110">The following code fragment uses `TypeOf...Is` within an `If...Then...Else` statement:</span></span>  
  
 <span data-ttu-id="0f6c1-111">[!code-vb[VbVbalrOOP&#93;](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="0f6c1-111">[!code-vb[VbVbalrOOP#93](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_2.vb)]</span></span>  
  
 <span data-ttu-id="0f6c1-112">Uma nota de advertência aqui é devida.</span><span class="sxs-lookup"><span data-stu-id="0f6c1-112">A word of caution is due here.</span></span> <span data-ttu-id="0f6c1-113">O `TypeOf...Is` operador retorna `True` se um objeto for de um tipo específico, ou é derivado de um tipo específico.</span><span class="sxs-lookup"><span data-stu-id="0f6c1-113">The `TypeOf...Is` operator returns `True` if an object is of a specific type, or is derived from a specific type.</span></span> <span data-ttu-id="0f6c1-114">Quase tudo o que fazer com [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] envolve objetos, que incluem alguns elementos que normalmente não são considerados objetos, como cadeias de caracteres e inteiros.</span><span class="sxs-lookup"><span data-stu-id="0f6c1-114">Almost everything you do with [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] involves objects, which include some elements not normally thought of as objects, such as strings and integers.</span></span> <span data-ttu-id="0f6c1-115">Esses objetos são derivados de e herdam métodos de <xref:System.Object>.</xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="0f6c1-115">These objects are derived from and inherit methods from <xref:System.Object>.</span></span> <span data-ttu-id="0f6c1-116">Quando passado um `Integer` e avaliadas com `Object`, o `TypeOf...Is` retornará `True`.</span><span class="sxs-lookup"><span data-stu-id="0f6c1-116">When passed an `Integer` and evaluated with `Object`, the `TypeOf...Is` operator returns `True`.</span></span> <span data-ttu-id="0f6c1-117">O exemplo a seguir relata que o parâmetro `InParam` tanto uma `Object` e um `Integer`:</span><span class="sxs-lookup"><span data-stu-id="0f6c1-117">The following example reports that the parameter `InParam` is both an `Object` and an `Integer`:</span></span>  
  
 <span data-ttu-id="0f6c1-118">[!code-vb[VbVbalrOOP&#94;](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="0f6c1-118">[!code-vb[VbVbalrOOP#94](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_3.vb)]</span></span>  
  
 <span data-ttu-id="0f6c1-119">O exemplo a seguir usa `TypeOf...Is` e `TypeName` para determinar o tipo de objeto passado para ele no `Ctrl` argumento.</span><span class="sxs-lookup"><span data-stu-id="0f6c1-119">The following example uses both `TypeOf...Is` and `TypeName` to determine the type of object passed to it in the `Ctrl` argument.</span></span> <span data-ttu-id="0f6c1-120">O `TestObject` chamadas de procedimento `ShowType` com três tipos diferentes de controles.</span><span class="sxs-lookup"><span data-stu-id="0f6c1-120">The `TestObject` procedure calls `ShowType` with three different kinds of controls.</span></span>  
  
#### <a name="to-run-the-example"></a><span data-ttu-id="0f6c1-121">Para executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="0f6c1-121">To run the example</span></span>  
  
1.  <span data-ttu-id="0f6c1-122">Criar um novo projeto de aplicativo do Windows e adicionar um <xref:System.Windows.Forms.Button>controle, um <xref:System.Windows.Forms.CheckBox>controle e um <xref:System.Windows.Forms.RadioButton>controle ao formulário.</xref:System.Windows.Forms.RadioButton> </xref:System.Windows.Forms.CheckBox> </xref:System.Windows.Forms.Button></span><span class="sxs-lookup"><span data-stu-id="0f6c1-122">Create a new Windows Application project and add a <xref:System.Windows.Forms.Button> control, a <xref:System.Windows.Forms.CheckBox> control, and a <xref:System.Windows.Forms.RadioButton> control to the form.</span></span>  
  
2.  <span data-ttu-id="0f6c1-123">Com o botão no formulário, chame o `TestObject` procedimento.</span><span class="sxs-lookup"><span data-stu-id="0f6c1-123">From the button on your form, call the `TestObject` procedure.</span></span>  
  
3.  <span data-ttu-id="0f6c1-124">Adicione o seguinte código ao seu formulário:</span><span class="sxs-lookup"><span data-stu-id="0f6c1-124">Add the following code to your form:</span></span>  
  
     <span data-ttu-id="0f6c1-125">[!code-vb[VbVbalrOOP&#95;](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="0f6c1-125">[!code-vb[VbVbalrOOP#95](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_4.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f6c1-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0f6c1-126">See Also</span></span>  
 <span data-ttu-id="0f6c1-127"><xref:Microsoft.VisualBasic.Information.TypeName%2A></xref:Microsoft.VisualBasic.Information.TypeName%2A></span><span class="sxs-lookup"><span data-stu-id="0f6c1-127"><xref:Microsoft.VisualBasic.Information.TypeName%2A></span></span>   
<span data-ttu-id="0f6c1-128"> [Chamando uma propriedade ou método usando um nome de cadeia de caracteres](../../../../visual-basic/programming-guide/language-features/early-late-binding/calling-a-property-or-method-using-a-string-name.md) </span><span class="sxs-lookup"><span data-stu-id="0f6c1-128"> [Calling a Property or Method Using a String Name](../../../../visual-basic/programming-guide/language-features/early-late-binding/calling-a-property-or-method-using-a-string-name.md) </span></span>  
<span data-ttu-id="0f6c1-129"> [Tipo de dados Object](../../../../visual-basic/language-reference/data-types/object-data-type.md) </span><span class="sxs-lookup"><span data-stu-id="0f6c1-129"> [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md) </span></span>  
<span data-ttu-id="0f6c1-130"> [If... Then... Instrução else](../../../../visual-basic/language-reference/statements/if-then-else-statement.md) </span><span class="sxs-lookup"><span data-stu-id="0f6c1-130"> [If...Then...Else Statement](../../../../visual-basic/language-reference/statements/if-then-else-statement.md) </span></span>  
<span data-ttu-id="0f6c1-131"> [Tipo de dados String](../../../../visual-basic/language-reference/data-types/string-data-type.md) </span><span class="sxs-lookup"><span data-stu-id="0f6c1-131"> [String Data Type](../../../../visual-basic/language-reference/data-types/string-data-type.md) </span></span>  
<span data-ttu-id="0f6c1-132"> [Tipo de Dados Integer](../../../../visual-basic/language-reference/data-types/integer-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="0f6c1-132"> [Integer Data Type](../../../../visual-basic/language-reference/data-types/integer-data-type.md)</span></span>
