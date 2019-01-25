---
title: Determinando o tipo de objeto (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- classes [Visual Basic], discovering which an object belongs to
- types [Visual Basic], determining Visual Basic object types
- object variables [Visual Basic], testing values
- TypeOf...Is expression, object type at run time
- TypeName function
- objects [Visual Basic], type determining
ms.assetid: d95e7ad1-cd63-41d6-9a28-d7a1380d49c1
ms.openlocfilehash: 5980549dd063b2c7d5c60ebd4e9762284c072009
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54586612"
---
# <a name="determining-object-type-visual-basic"></a><span data-ttu-id="093b6-102">Determinando o tipo de objeto (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="093b6-102">Determining Object Type (Visual Basic)</span></span>
<span data-ttu-id="093b6-103">Variáveis de objeto genérico (ou seja, as variáveis que você declare como `Object`) pode conter objetos de qualquer classe.</span><span class="sxs-lookup"><span data-stu-id="093b6-103">Generic object variables (that is, variables you declare as `Object`) can hold objects from any class.</span></span> <span data-ttu-id="093b6-104">Ao usar as variáveis do tipo `Object`, talvez você precise executar ações diferentes com base na classe do objeto; por exemplo, alguns objetos podem não dar suporte a uma determinada propriedade ou método.</span><span class="sxs-lookup"><span data-stu-id="093b6-104">When using variables of type `Object`, you may need to take different actions based on the class of the object; for example, some objects might not support a particular property or method.</span></span> <span data-ttu-id="093b6-105">O Visual Basic fornece dois meios para determinar qual tipo de objeto é armazenado em uma variável de objeto: o `TypeName` função e o `TypeOf...Is` operador.</span><span class="sxs-lookup"><span data-stu-id="093b6-105">Visual Basic provides two means of determining which type of object is stored in an object variable: the `TypeName` function and the `TypeOf...Is` operator.</span></span>  
  
## <a name="typename-and-typeofis"></a><span data-ttu-id="093b6-106">TypeName e TypeOf... É</span><span class="sxs-lookup"><span data-stu-id="093b6-106">TypeName and TypeOf…Is</span></span>  
 <span data-ttu-id="093b6-107">O `TypeName` função retorna uma cadeia de caracteres e é a melhor opção quando você precisa armazenar ou exibir o nome de classe de um objeto, conforme mostrado no seguinte fragmento de código:</span><span class="sxs-lookup"><span data-stu-id="093b6-107">The `TypeName` function returns a string and is the best choice when you need to store or display the class name of an object, as shown in the following code fragment:</span></span>  
  
 [!code-vb[VbVbalrOOP#92](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_1.vb)]  
  
 <span data-ttu-id="093b6-108">O `TypeOf...Is` operador é a melhor opção para testar o tipo de um objeto, porque ele é muito mais rápido que uma comparação de cadeia de caracteres equivalente usando `TypeName`.</span><span class="sxs-lookup"><span data-stu-id="093b6-108">The `TypeOf...Is` operator is the best choice for testing an object's type, because it is much faster than an equivalent string comparison using `TypeName`.</span></span> <span data-ttu-id="093b6-109">O fragmento de código a seguir usa `TypeOf...Is` dentro de um `If...Then...Else` instrução:</span><span class="sxs-lookup"><span data-stu-id="093b6-109">The following code fragment uses `TypeOf...Is` within an `If...Then...Else` statement:</span></span>  
  
 [!code-vb[VbVbalrOOP#93](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_2.vb)]  
  
 <span data-ttu-id="093b6-110">Uma palavra de advertência aqui é devida.</span><span class="sxs-lookup"><span data-stu-id="093b6-110">A word of caution is due here.</span></span> <span data-ttu-id="093b6-111">O `TypeOf...Is` operador retorna `True` se um objeto é de um tipo específico, ou é derivado de um tipo específico.</span><span class="sxs-lookup"><span data-stu-id="093b6-111">The `TypeOf...Is` operator returns `True` if an object is of a specific type, or is derived from a specific type.</span></span> <span data-ttu-id="093b6-112">Quase tudo o que fazer com o Visual Basic envolve a objetos, que incluem alguns elementos que não são considerados normalmente objetos, como cadeias de caracteres e inteiros.</span><span class="sxs-lookup"><span data-stu-id="093b6-112">Almost everything you do with Visual Basic involves objects, which include some elements not normally thought of as objects, such as strings and integers.</span></span> <span data-ttu-id="093b6-113">Esses objetos são derivados e herdam os métodos de <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="093b6-113">These objects are derived from and inherit methods from <xref:System.Object>.</span></span> <span data-ttu-id="093b6-114">Quando passado um `Integer` e avaliados com `Object`, o `TypeOf...Is` operador retorna `True`.</span><span class="sxs-lookup"><span data-stu-id="093b6-114">When passed an `Integer` and evaluated with `Object`, the `TypeOf...Is` operator returns `True`.</span></span> <span data-ttu-id="093b6-115">O exemplo a seguir relata que o parâmetro `InParam` for tanto um `Object` e um `Integer`:</span><span class="sxs-lookup"><span data-stu-id="093b6-115">The following example reports that the parameter `InParam` is both an `Object` and an `Integer`:</span></span>  
  
 [!code-vb[VbVbalrOOP#94](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_3.vb)]  
  
 <span data-ttu-id="093b6-116">O exemplo a seguir usa ambos `TypeOf...Is` e `TypeName` para determinar o tipo de objeto passado para ele no `Ctrl` argumento.</span><span class="sxs-lookup"><span data-stu-id="093b6-116">The following example uses both `TypeOf...Is` and `TypeName` to determine the type of object passed to it in the `Ctrl` argument.</span></span> <span data-ttu-id="093b6-117">O `TestObject` chamadas de procedimento `ShowType` com três tipos diferentes de controles.</span><span class="sxs-lookup"><span data-stu-id="093b6-117">The `TestObject` procedure calls `ShowType` with three different kinds of controls.</span></span>  
  
#### <a name="to-run-the-example"></a><span data-ttu-id="093b6-118">Para executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="093b6-118">To run the example</span></span>  
  
1.  <span data-ttu-id="093b6-119">Criar um novo projeto de aplicativo do Windows e adicione uma <xref:System.Windows.Forms.Button> controle, um <xref:System.Windows.Forms.CheckBox> controle e um <xref:System.Windows.Forms.RadioButton> controle ao formulário.</span><span class="sxs-lookup"><span data-stu-id="093b6-119">Create a new Windows Application project and add a <xref:System.Windows.Forms.Button> control, a <xref:System.Windows.Forms.CheckBox> control, and a <xref:System.Windows.Forms.RadioButton> control to the form.</span></span>  
  
2.  <span data-ttu-id="093b6-120">Com o botão no formulário, chame o `TestObject` procedimento.</span><span class="sxs-lookup"><span data-stu-id="093b6-120">From the button on your form, call the `TestObject` procedure.</span></span>  
  
3.  <span data-ttu-id="093b6-121">Adicione o seguinte código ao seu formulário:</span><span class="sxs-lookup"><span data-stu-id="093b6-121">Add the following code to your form:</span></span>  
  
     [!code-vb[VbVbalrOOP#95](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_4.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="093b6-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="093b6-122">See also</span></span>
- <xref:Microsoft.VisualBasic.Information.TypeName%2A>
- [<span data-ttu-id="093b6-123">Chamando uma Propriedade ou um Método Usando o Nome de uma Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="093b6-123">Calling a Property or Method Using a String Name</span></span>](../../../../visual-basic/programming-guide/language-features/early-late-binding/calling-a-property-or-method-using-a-string-name.md)
- [<span data-ttu-id="093b6-124">Tipo de Dados Object</span><span class="sxs-lookup"><span data-stu-id="093b6-124">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="093b6-125">Instrução If...Then...Else</span><span class="sxs-lookup"><span data-stu-id="093b6-125">If...Then...Else Statement</span></span>](../../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [<span data-ttu-id="093b6-126">Tipo de Dados String</span><span class="sxs-lookup"><span data-stu-id="093b6-126">String Data Type</span></span>](../../../../visual-basic/language-reference/data-types/string-data-type.md)
- [<span data-ttu-id="093b6-127">Tipo de Dados Integer</span><span class="sxs-lookup"><span data-stu-id="093b6-127">Integer Data Type</span></span>](../../../../visual-basic/language-reference/data-types/integer-data-type.md)
