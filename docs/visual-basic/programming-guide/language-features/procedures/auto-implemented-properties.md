---
title: Propriedades autoimplementadas (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.AutoProperty
- vb.AutoImplementedProperty
helpviewer_keywords:
- properties [Visual Basic], auto-implemented
- properties [Visual Basic], auto-implemented
- auto-implemented properties [Visual Basic]
ms.assetid: 5c669f0b-cf95-4b4e-ae84-9cc55212ca87
ms.openlocfilehash: bc83163a024bd50d3e256b4eb49861669f8c02c3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33656302"
---
# <a name="auto-implemented-properties-visual-basic"></a><span data-ttu-id="c3f51-102">Propriedades autoimplementadas (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c3f51-102">Auto-Implemented Properties (Visual Basic)</span></span>
<span data-ttu-id="c3f51-103">*Propriedades autoimplementadas* permitem que você especifique uma propriedade de uma classe rapidamente sem a necessidade de escrever código para as propriedades `Get` e `Set` .</span><span class="sxs-lookup"><span data-stu-id="c3f51-103">*Auto-implemented properties* enable you to quickly specify a property of a class without having to write code to `Get` and `Set` the property.</span></span> <span data-ttu-id="c3f51-104">uando você escreve código criando uma propriedade implementada automaticamente, o compilador do Visual Basic cria automaticamente um campo *private* para armazenar a variável de propriedade, além de criar os procedimentos `Get` e `Set` associados.</span><span class="sxs-lookup"><span data-stu-id="c3f51-104">When you write code for an auto-implemented property, the Visual Basic compiler automatically creates a private field to store the property variable in addition to creating the associated `Get` and `Set` procedures.</span></span>  
  
 <span data-ttu-id="c3f51-105">Com Propriedades autoimplementadas, uma propriedade, incluindo um valor padrão, pode ser declarada em uma única linha.</span><span class="sxs-lookup"><span data-stu-id="c3f51-105">With auto-implemented properties, a property, including a default value, can be declared in a single line.</span></span> <span data-ttu-id="c3f51-106">O exemplo a seguir mostra três declarações de propriedade.</span><span class="sxs-lookup"><span data-stu-id="c3f51-106">The following example shows three property declarations.</span></span>  
  
 [!code-vb[VbVbalrAutoImplementedProperties#1](./codesnippet/VisualBasic/auto-implemented-properties_1.vb)]  
  
 <span data-ttu-id="c3f51-107">Uma propriedade implementada automaticamente é equivalente a uma propriedade para o qual o valor da propriedade é armazenado em um campo particular.</span><span class="sxs-lookup"><span data-stu-id="c3f51-107">An auto-implemented property is equivalent to a property for which the property value is stored in a private field.</span></span> <span data-ttu-id="c3f51-108">O exemplo de código a seguir mostra uma propriedade implementada automaticamente.</span><span class="sxs-lookup"><span data-stu-id="c3f51-108">The following code example shows an auto-implemented property.</span></span>  
  
 [!code-vb[VbVbalrAutoImplementedProperties#5](./codesnippet/VisualBasic/auto-implemented-properties_2.vb)]  
  
 <span data-ttu-id="c3f51-109">O exemplo de código a seguir mostra o código equivalente para o exemplo anterior da propriedade implementada automaticamente.</span><span class="sxs-lookup"><span data-stu-id="c3f51-109">The following code example shows the equivalent code for the previous auto-implemented property example.</span></span>  
  
 [!code-vb[VbVbalrAutoImplementedProperties#2](./codesnippet/VisualBasic/auto-implemented-properties_3.vb)]  
  
 <span data-ttu-id="c3f51-110">O código a seguir mostra como implementar propriedades somente leitura:</span><span class="sxs-lookup"><span data-stu-id="c3f51-110">The following code show implementing readonly properties:</span></span>  
  
```vb  
Class Customer  
   Public ReadOnly Property Tags As New List(Of String)  
   Public ReadOnly Property Name As String = ""  
   Public ReadOnly Property File As String  
  
   Sub New(file As String)  
      Me.File = file  
   End Sub  
End Class  
```  
  
 <span data-ttu-id="c3f51-111">Você pode atribuir a propriedade com expressões de inicialização, conforme mostrado no exemplo, ou você pode atribuir às propriedades do construtor do tipo recipiente.</span><span class="sxs-lookup"><span data-stu-id="c3f51-111">You can assign to the property with initialization expressions as shown in the example, or you can assign to the properties in the containing type’s constructor.</span></span>  <span data-ttu-id="c3f51-112">Você pode atribuir aos campos de backup propriedades somente leitura a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="c3f51-112">You can assign to the backing fields of readonly properties at any time.</span></span>  
  
## <a name="backing-field"></a><span data-ttu-id="c3f51-113">Campo de backup</span><span class="sxs-lookup"><span data-stu-id="c3f51-113">Backing Field</span></span>  
 <span data-ttu-id="c3f51-114">Quando você declara uma propriedade implementada automaticamente, o Visual Basic cria automaticamente um campo particular oculto chamado o *campo existente* para conter o valor da propriedade.</span><span class="sxs-lookup"><span data-stu-id="c3f51-114">When you declare an auto-implemented property, Visual Basic automatically creates a hidden private field called the *backing field* to contain the property value.</span></span> <span data-ttu-id="c3f51-115">O nome do campo de backup é o nome da propriedade implementada automaticamente precedido por um sublinhado (_).</span><span class="sxs-lookup"><span data-stu-id="c3f51-115">The backing field name is the auto-implemented property name preceded by an underscore (_).</span></span> <span data-ttu-id="c3f51-116">Por exemplo, se você declarar uma propriedade implementada automaticamente denominada `ID`, o campo de backup é denominado `_ID`.</span><span class="sxs-lookup"><span data-stu-id="c3f51-116">For example, if you declare an auto-implemented property named `ID`, the backing field is named `_ID`.</span></span> <span data-ttu-id="c3f51-117">Se você incluir um membro da sua classe que também é denominada `_ID`, produzir um conflito de nomeação e Visual Basic relata um erro do compilador.</span><span class="sxs-lookup"><span data-stu-id="c3f51-117">If you include a member of your class that is also named `_ID`, you produce a naming conflict and Visual Basic reports a compiler error.</span></span>  
  
 <span data-ttu-id="c3f51-118">O campo de suporte também tem as seguintes características:</span><span class="sxs-lookup"><span data-stu-id="c3f51-118">The backing field also has the following characteristics:</span></span>  
  
-   <span data-ttu-id="c3f51-119">O modificador de acesso para o campo de backup é sempre `Private`, mesmo quando a própria propriedade tem um nível de acesso diferentes, como `Public`.</span><span class="sxs-lookup"><span data-stu-id="c3f51-119">The access modifier for the backing field is always `Private`, even when the property itself has a different access level, such as `Public`.</span></span>  
  
-   <span data-ttu-id="c3f51-120">Se a propriedade é marcada como `Shared`, o campo de reforço também é compartilhado.</span><span class="sxs-lookup"><span data-stu-id="c3f51-120">If the property is marked as `Shared`, the backing field also is shared.</span></span>  
  
-   <span data-ttu-id="c3f51-121">Atributos especificados para a propriedade não se aplicam ao campo de backup.</span><span class="sxs-lookup"><span data-stu-id="c3f51-121">Attributes specified for the property do not apply to the backing field.</span></span>  
  
-   <span data-ttu-id="c3f51-122">O campo de suporte pode ser acessado do código dentro da classe e de ferramentas de depuração, como a janela de inspeção.</span><span class="sxs-lookup"><span data-stu-id="c3f51-122">The backing field can be accessed from code within the class and from debugging tools such as the Watch window.</span></span> <span data-ttu-id="c3f51-123">No entanto, o campo de suporte não aparece na lista de conclusão do IntelliSense word.</span><span class="sxs-lookup"><span data-stu-id="c3f51-123">However, the backing field does not show in an IntelliSense word completion list.</span></span>  
  
## <a name="initializing-an-auto-implemented-property"></a><span data-ttu-id="c3f51-124">Inicializando uma propriedade implementada automaticamente</span><span class="sxs-lookup"><span data-stu-id="c3f51-124">Initializing an Auto-Implemented Property</span></span>  
 <span data-ttu-id="c3f51-125">Qualquer expressão que pode ser usada para inicializar um campo é válida para a inicialização de uma propriedade implementada automaticamente.</span><span class="sxs-lookup"><span data-stu-id="c3f51-125">Any expression that can be used to initialize a field is valid for initializing an auto-implemented property.</span></span> <span data-ttu-id="c3f51-126">Quando você inicializa uma propriedade implementada automaticamente, a expressão é avaliada e passada para o `Set` procedimento para a propriedade.</span><span class="sxs-lookup"><span data-stu-id="c3f51-126">When you initialize an auto-implemented property, the expression is evaluated and passed to the `Set` procedure for the property.</span></span> <span data-ttu-id="c3f51-127">Os exemplos de código a seguir mostram algumas propriedades autoimplementadas que incluem valores iniciais.</span><span class="sxs-lookup"><span data-stu-id="c3f51-127">The following code examples show some auto-implemented properties that include initial values.</span></span>  
  
 [!code-vb[VbVbalrAutoImplementedProperties#3](./codesnippet/VisualBasic/auto-implemented-properties_4.vb)]  
  
 <span data-ttu-id="c3f51-128">Não é possível inicializar uma propriedade implementada automaticamente que é um membro de um `Interface`, ou que está marcado como `MustOverride`.</span><span class="sxs-lookup"><span data-stu-id="c3f51-128">You cannot initialize an auto-implemented property that is a member of an `Interface`, or one that is marked `MustOverride`.</span></span>  
  
 <span data-ttu-id="c3f51-129">Quando você declara uma propriedade implementada automaticamente como um membro de um `Structure`, só é possível inicializar a propriedade implementada automaticamente, se ele está marcado como `Shared`.</span><span class="sxs-lookup"><span data-stu-id="c3f51-129">When you declare an auto-implemented property as a member of a `Structure`, you can only initialize the auto-implemented property if it is marked as `Shared`.</span></span>  
  
 <span data-ttu-id="c3f51-130">Quando você declara uma propriedade implementada automaticamente como uma matriz, você não pode especificar limites de matriz explícita.</span><span class="sxs-lookup"><span data-stu-id="c3f51-130">When you declare an auto-implemented property as an array, you cannot specify explicit array bounds.</span></span> <span data-ttu-id="c3f51-131">No entanto, você pode fornecer um valor usando um inicializador de matriz, conforme mostrado nos exemplos a seguir.</span><span class="sxs-lookup"><span data-stu-id="c3f51-131">However, you can supply a value by using an array initializer, as shown in the following examples.</span></span>  
  
 [!code-vb[VbVbalrAutoImplementedProperties#4](./codesnippet/VisualBasic/auto-implemented-properties_5.vb)]  
  
## <a name="property-definitions-that-require-standard-syntax"></a><span data-ttu-id="c3f51-132">Definições de propriedade que exigem a sintaxe padrão</span><span class="sxs-lookup"><span data-stu-id="c3f51-132">Property Definitions That Require Standard Syntax</span></span>  
 <span data-ttu-id="c3f51-133">Propriedades autoimplementadas são convenientes e dar suporte a vários cenários de programação.</span><span class="sxs-lookup"><span data-stu-id="c3f51-133">Auto-implemented properties are convenient and support many programming scenarios.</span></span> <span data-ttu-id="c3f51-134">No entanto, há situações nas quais você não pode usar uma propriedade implementada automaticamente e deve usar o padrão, ou *expandido*, sintaxe de propriedade.</span><span class="sxs-lookup"><span data-stu-id="c3f51-134">However, there are situations in which you cannot use an auto-implemented property and must instead use standard, or *expanded*, property syntax.</span></span>  
  
 <span data-ttu-id="c3f51-135">Você deve usar a sintaxe de definição de propriedade expandido se quiser fazer qualquer um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="c3f51-135">You have to use expanded property-definition syntax if you want to do any one of the following:</span></span>  
  
-   <span data-ttu-id="c3f51-136">Adicione código para o `Get` ou `Set` procedimento de uma propriedade, como o código para validar valores de entrada no `Set` procedimento.</span><span class="sxs-lookup"><span data-stu-id="c3f51-136">Add code to the `Get` or `Set` procedure of a property, such as code to validate incoming values in the `Set` procedure.</span></span> <span data-ttu-id="c3f51-137">Por exemplo, convém verificar se uma cadeia de caracteres que representa um número de telefone contém o número necessário de numerais antes de definir o valor da propriedade.</span><span class="sxs-lookup"><span data-stu-id="c3f51-137">For example, you might want to verify that a string that represents a telephone number contains the required number of numerals before setting the property value.</span></span>  
  
-   <span data-ttu-id="c3f51-138">Especificar diferente acessibilidade para o `Get` e `Set` procedimento.</span><span class="sxs-lookup"><span data-stu-id="c3f51-138">Specify different accessibility for the `Get` and `Set` procedure.</span></span> <span data-ttu-id="c3f51-139">Por exemplo, talvez você queira fazer a `Set` procedimento `Private` e `Get` procedimento `Public`.</span><span class="sxs-lookup"><span data-stu-id="c3f51-139">For example, you might want to make the `Set` procedure `Private` and the `Get` procedure `Public`.</span></span>  
  
-   <span data-ttu-id="c3f51-140">Criar propriedades `WriteOnly`.</span><span class="sxs-lookup"><span data-stu-id="c3f51-140">Create properties that are `WriteOnly`.</span></span>  
  
-   <span data-ttu-id="c3f51-141">Usar propriedades com parâmetros (incluindo `Default` propriedades).</span><span class="sxs-lookup"><span data-stu-id="c3f51-141">Use parameterized properties (including `Default` properties).</span></span> <span data-ttu-id="c3f51-142">Você deve declarar uma propriedade expandida para especificar um parâmetro para a propriedade ou para especificar parâmetros adicionais para o `Set` procedimento.</span><span class="sxs-lookup"><span data-stu-id="c3f51-142">You must declare an expanded property in order to specify a parameter for the property, or to specify additional parameters for the `Set` procedure.</span></span>  
  
-   <span data-ttu-id="c3f51-143">Coloque um atributo em um campo existente ou alterar o nível de acesso de campo existente.</span><span class="sxs-lookup"><span data-stu-id="c3f51-143">Place an attribute on the backing field, or change the access level of the backing field.</span></span>  
  
-   <span data-ttu-id="c3f51-144">Fornece comentários XML para o campo de backup.</span><span class="sxs-lookup"><span data-stu-id="c3f51-144">Provide XML comments for the backing field.</span></span>  
  
## <a name="expanding-an-auto-implemented-property"></a><span data-ttu-id="c3f51-145">Expandindo uma propriedade implementada automaticamente</span><span class="sxs-lookup"><span data-stu-id="c3f51-145">Expanding an Auto-Implemented Property</span></span>  
 <span data-ttu-id="c3f51-146">Se você precisar converter uma propriedade implementada automaticamente para uma propriedade expandida que contém um `Get` ou `Set` procedimento, o Editor de código do Visual Basic pode gerar automaticamente o `Get` e `Set` procedimentos e `End Property`instrução para a propriedade.</span><span class="sxs-lookup"><span data-stu-id="c3f51-146">If you have to convert an auto-implemented property to an expanded property that contains a `Get` or `Set` procedure, the Visual Basic Code Editor can automatically generate the `Get` and `Set` procedures and `End Property` statement for the property.</span></span> <span data-ttu-id="c3f51-147">O código é gerado se você colocar o cursor em uma linha em branco após o `Property` instrução, digite um `G` (para `Get`) ou um `S` (para `Set`) e pressione ENTER.</span><span class="sxs-lookup"><span data-stu-id="c3f51-147">The code is generated if you put the cursor on a blank line following the `Property` statement, type a `G` (for `Get`) or an `S` (for `Set`) and press ENTER.</span></span> <span data-ttu-id="c3f51-148">Editor de código do Visual Basic gera automaticamente o `Get` ou `Set` procedimento para propriedades somente leitura e gravação ao pressionar ENTER no final de um `Property` instrução.</span><span class="sxs-lookup"><span data-stu-id="c3f51-148">The Visual Basic Code Editor automatically generates the `Get` or `Set` procedure for read-only and write-only properties when you press ENTER at the end of a `Property` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3f51-149">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c3f51-149">See Also</span></span>  
 [<span data-ttu-id="c3f51-150">Como: declarar e chamar uma propriedade padrão no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c3f51-150">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)  
 [<span data-ttu-id="c3f51-151">Como declarar uma propriedade com níveis de acesso mistos</span><span class="sxs-lookup"><span data-stu-id="c3f51-151">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)  
 [<span data-ttu-id="c3f51-152">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="c3f51-152">Property Statement</span></span>](../../../../visual-basic/language-reference/statements/property-statement.md)  
 [<span data-ttu-id="c3f51-153">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="c3f51-153">ReadOnly</span></span>](../../../../visual-basic/language-reference/modifiers/readonly.md)  
 [<span data-ttu-id="c3f51-154">WriteOnly</span><span class="sxs-lookup"><span data-stu-id="c3f51-154">WriteOnly</span></span>](../../../../visual-basic/language-reference/modifiers/writeonly.md)  
 [<span data-ttu-id="c3f51-155">Objetos e Classes</span><span class="sxs-lookup"><span data-stu-id="c3f51-155">Objects and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
