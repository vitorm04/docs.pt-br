---
title: Determinando o tipo de objeto
ms.date: 07/20/2015
helpviewer_keywords:
- classes [Visual Basic], discovering which an object belongs to
- types [Visual Basic], determining Visual Basic object types
- object variables [Visual Basic], testing values
- TypeOf...Is expression, object type at run time
- TypeName function
- objects [Visual Basic], type determining
ms.assetid: d95e7ad1-cd63-41d6-9a28-d7a1380d49c1
ms.openlocfilehash: a77cc0603a0b61f58a4aa703c4b1e6ef4c26729c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345194"
---
# <a name="determining-object-type-visual-basic"></a><span data-ttu-id="7bfc6-102">Determinando o tipo de objeto (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7bfc6-102">Determining Object Type (Visual Basic)</span></span>
<span data-ttu-id="7bfc6-103">Variáveis de objeto genérico (ou seja, variáveis que você declara como `Object`) podem conter objetos de qualquer classe.</span><span class="sxs-lookup"><span data-stu-id="7bfc6-103">Generic object variables (that is, variables you declare as `Object`) can hold objects from any class.</span></span> <span data-ttu-id="7bfc6-104">Ao usar variáveis do tipo `Object`, talvez seja necessário executar ações diferentes com base na classe do objeto; por exemplo, alguns objetos podem não dar suporte a uma propriedade ou um método específico.</span><span class="sxs-lookup"><span data-stu-id="7bfc6-104">When using variables of type `Object`, you may need to take different actions based on the class of the object; for example, some objects might not support a particular property or method.</span></span> <span data-ttu-id="7bfc6-105">Visual Basic fornece dois meios de determinar qual tipo de objeto é armazenado em uma variável de objeto: a função `TypeName` e o operador de `TypeOf...Is`.</span><span class="sxs-lookup"><span data-stu-id="7bfc6-105">Visual Basic provides two means of determining which type of object is stored in an object variable: the `TypeName` function and the `TypeOf...Is` operator.</span></span>  
  
## <a name="typename-and-typeofis"></a><span data-ttu-id="7bfc6-106">TypeName e TypeOf... For</span><span class="sxs-lookup"><span data-stu-id="7bfc6-106">TypeName and TypeOf…Is</span></span>  
 <span data-ttu-id="7bfc6-107">A função `TypeName` retorna uma cadeia de caracteres e é a melhor opção quando você precisa armazenar ou exibir o nome de classe de um objeto, conforme mostrado no fragmento de código a seguir:</span><span class="sxs-lookup"><span data-stu-id="7bfc6-107">The `TypeName` function returns a string and is the best choice when you need to store or display the class name of an object, as shown in the following code fragment:</span></span>  
  
 [!code-vb[VbVbalrOOP#92](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#92)]  
  
 <span data-ttu-id="7bfc6-108">O operador de `TypeOf...Is` é a melhor opção para testar o tipo de um objeto, pois é muito mais rápido do que uma comparação de cadeia de caracteres equivalente usando `TypeName`.</span><span class="sxs-lookup"><span data-stu-id="7bfc6-108">The `TypeOf...Is` operator is the best choice for testing an object's type, because it is much faster than an equivalent string comparison using `TypeName`.</span></span> <span data-ttu-id="7bfc6-109">O fragmento de código a seguir usa `TypeOf...Is` em uma instrução `If...Then...Else`:</span><span class="sxs-lookup"><span data-stu-id="7bfc6-109">The following code fragment uses `TypeOf...Is` within an `If...Then...Else` statement:</span></span>  
  
 [!code-vb[VbVbalrOOP#93](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#93)]  
  
 <span data-ttu-id="7bfc6-110">Uma palavra de atenção é devida aqui.</span><span class="sxs-lookup"><span data-stu-id="7bfc6-110">A word of caution is due here.</span></span> <span data-ttu-id="7bfc6-111">O operador `TypeOf...Is` retornará `True` se um objeto for de um tipo específico ou for derivado de um tipo específico.</span><span class="sxs-lookup"><span data-stu-id="7bfc6-111">The `TypeOf...Is` operator returns `True` if an object is of a specific type, or is derived from a specific type.</span></span> <span data-ttu-id="7bfc6-112">Quase tudo o que você faz com Visual Basic envolve objetos, que incluem alguns elementos que normalmente não são considerados objetos como, por exemplo, cadeias de caracteres e inteiros.</span><span class="sxs-lookup"><span data-stu-id="7bfc6-112">Almost everything you do with Visual Basic involves objects, which include some elements not normally thought of as objects, such as strings and integers.</span></span> <span data-ttu-id="7bfc6-113">Esses objetos são derivados de e herdam métodos de <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="7bfc6-113">These objects are derived from and inherit methods from <xref:System.Object>.</span></span> <span data-ttu-id="7bfc6-114">Quando passado um `Integer` e avaliado com `Object`, o operador `TypeOf...Is` retorna `True`.</span><span class="sxs-lookup"><span data-stu-id="7bfc6-114">When passed an `Integer` and evaluated with `Object`, the `TypeOf...Is` operator returns `True`.</span></span> <span data-ttu-id="7bfc6-115">O exemplo a seguir relata que o parâmetro `InParam` é um `Object` e um `Integer`:</span><span class="sxs-lookup"><span data-stu-id="7bfc6-115">The following example reports that the parameter `InParam` is both an `Object` and an `Integer`:</span></span>  
  
 [!code-vb[VbVbalrOOP#94](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#94)]  
  
 <span data-ttu-id="7bfc6-116">O exemplo a seguir usa `TypeOf...Is` e `TypeName` para determinar o tipo de objeto passado para ele no argumento `Ctrl`.</span><span class="sxs-lookup"><span data-stu-id="7bfc6-116">The following example uses both `TypeOf...Is` and `TypeName` to determine the type of object passed to it in the `Ctrl` argument.</span></span> <span data-ttu-id="7bfc6-117">O procedimento `TestObject` chama `ShowType` com três tipos diferentes de controles.</span><span class="sxs-lookup"><span data-stu-id="7bfc6-117">The `TestObject` procedure calls `ShowType` with three different kinds of controls.</span></span>  
  
#### <a name="to-run-the-example"></a><span data-ttu-id="7bfc6-118">Para executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="7bfc6-118">To run the example</span></span>  
  
1. <span data-ttu-id="7bfc6-119">Crie um novo projeto de aplicativo do Windows e adicione um controle de <xref:System.Windows.Forms.Button>, um controle de <xref:System.Windows.Forms.CheckBox> e um controle de <xref:System.Windows.Forms.RadioButton> ao formulário.</span><span class="sxs-lookup"><span data-stu-id="7bfc6-119">Create a new Windows Application project and add a <xref:System.Windows.Forms.Button> control, a <xref:System.Windows.Forms.CheckBox> control, and a <xref:System.Windows.Forms.RadioButton> control to the form.</span></span>  
  
2. <span data-ttu-id="7bfc6-120">No botão do formulário, chame o procedimento de `TestObject`.</span><span class="sxs-lookup"><span data-stu-id="7bfc6-120">From the button on your form, call the `TestObject` procedure.</span></span>  
  
3. <span data-ttu-id="7bfc6-121">Adicione o seguinte código ao seu formulário:</span><span class="sxs-lookup"><span data-stu-id="7bfc6-121">Add the following code to your form:</span></span>  
  
     [!code-vb[VbVbalrOOP#95](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#95)]  
  
## <a name="see-also"></a><span data-ttu-id="7bfc6-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7bfc6-122">See also</span></span>

- <xref:Microsoft.VisualBasic.Information.TypeName%2A>
- [<span data-ttu-id="7bfc6-123">Chamando uma Propriedade ou um Método Usando o Nome de uma Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="7bfc6-123">Calling a Property or Method Using a String Name</span></span>](../../../../visual-basic/programming-guide/language-features/early-late-binding/calling-a-property-or-method-using-a-string-name.md)
- [<span data-ttu-id="7bfc6-124">Tipo de Dados Object</span><span class="sxs-lookup"><span data-stu-id="7bfc6-124">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="7bfc6-125">Instrução If...Then...Else</span><span class="sxs-lookup"><span data-stu-id="7bfc6-125">If...Then...Else Statement</span></span>](../../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [<span data-ttu-id="7bfc6-126">Tipo de Dados String</span><span class="sxs-lookup"><span data-stu-id="7bfc6-126">String Data Type</span></span>](../../../../visual-basic/language-reference/data-types/string-data-type.md)
- [<span data-ttu-id="7bfc6-127">Tipo de Dados Integer</span><span class="sxs-lookup"><span data-stu-id="7bfc6-127">Integer Data Type</span></span>](../../../../visual-basic/language-reference/data-types/integer-data-type.md)
