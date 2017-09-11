---
title: Propriedades (Visual Basic) autoimplementadas | Documentos do Microsoft
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.AutoProperty
- vb.AutoImplementedProperty
dev_langs:
- VB
helpviewer_keywords:
- properties [Visual Basic], auto-implemented
- properties, auto-implemented [Visual Basic]
- auto-implemented properties [Visual Basic]
ms.assetid: 5c669f0b-cf95-4b4e-ae84-9cc55212ca87
caps.latest.revision: 20
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
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: 4ae0004c793a267a494ca5515c20850a55ebe3be
ms.contentlocale: pt-br
ms.lasthandoff: 05/23/2017

---
# <a name="auto-implemented-properties-visual-basic"></a><span data-ttu-id="e2fe9-102">Propriedades autoimplementadas (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e2fe9-102">Auto-Implemented Properties (Visual Basic)</span></span>
<span data-ttu-id="e2fe9-103">*Propriedades autoimplementadas* permitem que você especificar uma propriedade de uma classe rapidamente sem precisar escrever código para `Get` e `Set` a propriedade.</span><span class="sxs-lookup"><span data-stu-id="e2fe9-103">*Auto-implemented properties* enable you to quickly specify a property of a class without having to write code to `Get` and `Set` the property.</span></span> <span data-ttu-id="e2fe9-104">Quando você escreve o código para uma propriedade implementada automaticamente, o compilador do Visual Basic cria automaticamente um campo particular para armazenar a variável de propriedade, além de criar associado `Get` e `Set` procedimentos.</span><span class="sxs-lookup"><span data-stu-id="e2fe9-104">When you write code for an auto-implemented property, the Visual Basic compiler automatically creates a private field to store the property variable in addition to creating the associated `Get` and `Set` procedures.</span></span>  
  
 <span data-ttu-id="e2fe9-105">Com as propriedades implementadas automaticamente, uma propriedade, incluindo um valor padrão, pode ser declarada em uma única linha.</span><span class="sxs-lookup"><span data-stu-id="e2fe9-105">With auto-implemented properties, a property, including a default value, can be declared in a single line.</span></span> <span data-ttu-id="e2fe9-106">O exemplo a seguir mostra três declarações de propriedade.</span><span class="sxs-lookup"><span data-stu-id="e2fe9-106">The following example shows three property declarations.</span></span>  
  
 <span data-ttu-id="e2fe9-107">[!code-vb[VbVbalrAutoImplementedProperties n º&1;](./codesnippet/VisualBasic/auto-implemented-properties_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="e2fe9-107">[!code-vb[VbVbalrAutoImplementedProperties#1](./codesnippet/VisualBasic/auto-implemented-properties_1.vb)]</span></span>  
  
 <span data-ttu-id="e2fe9-108">Uma propriedade autoimplementadas é equivalente a uma propriedade para a qual o valor da propriedade é armazenado em um campo particular.</span><span class="sxs-lookup"><span data-stu-id="e2fe9-108">An auto-implemented property is equivalent to a property for which the property value is stored in a private field.</span></span> <span data-ttu-id="e2fe9-109">O exemplo de código a seguir mostra uma propriedade implementada automaticamente.</span><span class="sxs-lookup"><span data-stu-id="e2fe9-109">The following code example shows an auto-implemented property.</span></span>  
  
 <span data-ttu-id="e2fe9-110">[!code-vb[VbVbalrAutoImplementedProperties n º&5;](./codesnippet/VisualBasic/auto-implemented-properties_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="e2fe9-110">[!code-vb[VbVbalrAutoImplementedProperties#5](./codesnippet/VisualBasic/auto-implemented-properties_2.vb)]</span></span>  
  
 <span data-ttu-id="e2fe9-111">O exemplo de código a seguir mostra o código equivalente no exemplo anterior de propriedades implementadas automaticamente.</span><span class="sxs-lookup"><span data-stu-id="e2fe9-111">The following code example shows the equivalent code for the previous auto-implemented property example.</span></span>  
  
 <span data-ttu-id="e2fe9-112">[!code-vb[VbVbalrAutoImplementedProperties n º&2;](./codesnippet/VisualBasic/auto-implemented-properties_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="e2fe9-112">[!code-vb[VbVbalrAutoImplementedProperties#2](./codesnippet/VisualBasic/auto-implemented-properties_3.vb)]</span></span>  
  
 <span data-ttu-id="e2fe9-113">O código a seguir mostram como implementar propriedades somente leitura:</span><span class="sxs-lookup"><span data-stu-id="e2fe9-113">The following code show implementing readonly properties:</span></span>  
  
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
  
 <span data-ttu-id="e2fe9-114">Você pode atribuir a propriedade com expressões de inicialização conforme mostrado no exemplo, ou você pode atribuir às propriedades no construtor do tipo recipiente.</span><span class="sxs-lookup"><span data-stu-id="e2fe9-114">You can assign to the property with initialization expressions as shown in the example, or you can assign to the properties in the containing type’s constructor.</span></span>  <span data-ttu-id="e2fe9-115">Você pode atribuir aos campos de apoio de propriedades somente leitura a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="e2fe9-115">You can assign to the backing fields of readonly properties at any time.</span></span>  
  
## <a name="backing-field"></a><span data-ttu-id="e2fe9-116">Campo de backup</span><span class="sxs-lookup"><span data-stu-id="e2fe9-116">Backing Field</span></span>  
 <span data-ttu-id="e2fe9-117">Quando você declara uma propriedade implementada automaticamente, o Visual Basic cria automaticamente um campo privado ocultado chamado de *campo de backup* para conter o valor da propriedade.</span><span class="sxs-lookup"><span data-stu-id="e2fe9-117">When you declare an auto-implemented property, Visual Basic automatically creates a hidden private field called the *backing field* to contain the property value.</span></span> <span data-ttu-id="e2fe9-118">O nome do campo de backup é o nome da propriedade autoimplementadas precedido por um sublinhado (_).</span><span class="sxs-lookup"><span data-stu-id="e2fe9-118">The backing field name is the auto-implemented property name preceded by an underscore (_).</span></span> <span data-ttu-id="e2fe9-119">Por exemplo, se você declarar uma propriedade autoimplementadas denominada `ID`, o campo de backup é chamado `_ID`.</span><span class="sxs-lookup"><span data-stu-id="e2fe9-119">For example, if you declare an auto-implemented property named `ID`, the backing field is named `_ID`.</span></span> <span data-ttu-id="e2fe9-120">Se você incluir um membro da sua classe também é chamado `_ID`, gerar um conflito de nomeação e Visual Basic relata um erro do compilador.</span><span class="sxs-lookup"><span data-stu-id="e2fe9-120">If you include a member of your class that is also named `_ID`, you produce a naming conflict and Visual Basic reports a compiler error.</span></span>  
  
 <span data-ttu-id="e2fe9-121">O campo de backup também tem as seguintes características:</span><span class="sxs-lookup"><span data-stu-id="e2fe9-121">The backing field also has the following characteristics:</span></span>  
  
-   <span data-ttu-id="e2fe9-122">O modificador de acesso para o campo de backup é sempre `Private`, mesmo quando a própria propriedade tem um nível de acesso diferente, como `Public`.</span><span class="sxs-lookup"><span data-stu-id="e2fe9-122">The access modifier for the backing field is always `Private`, even when the property itself has a different access level, such as `Public`.</span></span>  
  
-   <span data-ttu-id="e2fe9-123">Se a propriedade é marcada como `Shared`, o campo de suporte também é compartilhado.</span><span class="sxs-lookup"><span data-stu-id="e2fe9-123">If the property is marked as `Shared`, the backing field also is shared.</span></span>  
  
-   <span data-ttu-id="e2fe9-124">Atributos especificados para a propriedade não se aplicam ao campo existente.</span><span class="sxs-lookup"><span data-stu-id="e2fe9-124">Attributes specified for the property do not apply to the backing field.</span></span>  
  
-   <span data-ttu-id="e2fe9-125">O campo de backup pode ser acessado de código dentro da classe e de ferramentas de depuração, como a janela de observação.</span><span class="sxs-lookup"><span data-stu-id="e2fe9-125">The backing field can be accessed from code within the class and from debugging tools such as the Watch window.</span></span> <span data-ttu-id="e2fe9-126">No entanto, o campo existente não mostrar em uma lista de conclusão de palavras do IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="e2fe9-126">However, the backing field does not show in an IntelliSense word completion list.</span></span>  
  
## <a name="initializing-an-auto-implemented-property"></a><span data-ttu-id="e2fe9-127">Inicializando uma propriedade autoimplementadas</span><span class="sxs-lookup"><span data-stu-id="e2fe9-127">Initializing an Auto-Implemented Property</span></span>  
 <span data-ttu-id="e2fe9-128">Qualquer expressão que pode ser usado para inicializar um campo é válido para inicializar uma propriedade implementada automaticamente.</span><span class="sxs-lookup"><span data-stu-id="e2fe9-128">Any expression that can be used to initialize a field is valid for initializing an auto-implemented property.</span></span> <span data-ttu-id="e2fe9-129">Quando você inicializar uma propriedade implementada automaticamente, a expressão é avaliada e passada para o `Set` procedimento para a propriedade.</span><span class="sxs-lookup"><span data-stu-id="e2fe9-129">When you initialize an auto-implemented property, the expression is evaluated and passed to the `Set` procedure for the property.</span></span> <span data-ttu-id="e2fe9-130">Os exemplos de código a seguir mostram algumas propriedades implementadas automaticamente que incluem valores iniciais.</span><span class="sxs-lookup"><span data-stu-id="e2fe9-130">The following code examples show some auto-implemented properties that include initial values.</span></span>  
  
 <span data-ttu-id="e2fe9-131">[!code-vb[VbVbalrAutoImplementedProperties n º&3;](./codesnippet/VisualBasic/auto-implemented-properties_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="e2fe9-131">[!code-vb[VbVbalrAutoImplementedProperties#3](./codesnippet/VisualBasic/auto-implemented-properties_4.vb)]</span></span>  
  
 <span data-ttu-id="e2fe9-132">Você não pode inicializar uma propriedade autoimplementadas que seja membro de um `Interface`, ou que está marcado como `MustOverride`.</span><span class="sxs-lookup"><span data-stu-id="e2fe9-132">You cannot initialize an auto-implemented property that is a member of an `Interface`, or one that is marked `MustOverride`.</span></span>  
  
 <span data-ttu-id="e2fe9-133">Quando você declara uma propriedade implementada automaticamente como um membro de um `Structure`, você só pode inicializar a propriedade implementada automaticamente se ele está marcado como `Shared`.</span><span class="sxs-lookup"><span data-stu-id="e2fe9-133">When you declare an auto-implemented property as a member of a `Structure`, you can only initialize the auto-implemented property if it is marked as `Shared`.</span></span>  
  
 <span data-ttu-id="e2fe9-134">Quando você declara uma propriedade implementada automaticamente como uma matriz, você não pode especificar limites de matriz explícita.</span><span class="sxs-lookup"><span data-stu-id="e2fe9-134">When you declare an auto-implemented property as an array, you cannot specify explicit array bounds.</span></span> <span data-ttu-id="e2fe9-135">No entanto, você pode fornecer um valor usando um inicializador de matriz, como mostrado nos exemplos a seguir.</span><span class="sxs-lookup"><span data-stu-id="e2fe9-135">However, you can supply a value by using an array initializer, as shown in the following examples.</span></span>  
  
 <span data-ttu-id="e2fe9-136">[!code-vb[VbVbalrAutoImplementedProperties n º&4;](./codesnippet/VisualBasic/auto-implemented-properties_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="e2fe9-136">[!code-vb[VbVbalrAutoImplementedProperties#4](./codesnippet/VisualBasic/auto-implemented-properties_5.vb)]</span></span>  
  
## <a name="property-definitions-that-require-standard-syntax"></a><span data-ttu-id="e2fe9-137">Definições de propriedade que exigem uma sintaxe padrão</span><span class="sxs-lookup"><span data-stu-id="e2fe9-137">Property Definitions That Require Standard Syntax</span></span>  
 <span data-ttu-id="e2fe9-138">Propriedades autoimplementadas são convenientes e oferecer suporte a muitos cenários de programação.</span><span class="sxs-lookup"><span data-stu-id="e2fe9-138">Auto-implemented properties are convenient and support many programming scenarios.</span></span> <span data-ttu-id="e2fe9-139">No entanto, há situações nas quais você não pode usar uma propriedade implementada automaticamente e deve usar o padrão, ou *expandido*, sintaxe de propriedade.</span><span class="sxs-lookup"><span data-stu-id="e2fe9-139">However, there are situations in which you cannot use an auto-implemented property and must instead use standard, or *expanded*, property syntax.</span></span>  
  
 <span data-ttu-id="e2fe9-140">Você deve usar sintaxe de definição de propriedade expandido se você quiser fazer qualquer um destes procedimentos:</span><span class="sxs-lookup"><span data-stu-id="e2fe9-140">You have to use expanded property-definition syntax if you want to do any one of the following:</span></span>  
  
-   <span data-ttu-id="e2fe9-141">Adicione código para o `Get` ou `Set` procedimento de uma propriedade, como o código para validar os valores de entrada no `Set` procedimento.</span><span class="sxs-lookup"><span data-stu-id="e2fe9-141">Add code to the `Get` or `Set` procedure of a property, such as code to validate incoming values in the `Set` procedure.</span></span> <span data-ttu-id="e2fe9-142">Por exemplo, você talvez queira verificar se uma cadeia de caracteres que representa um número de telefone contém o número necessário de numerais antes de definir o valor da propriedade.</span><span class="sxs-lookup"><span data-stu-id="e2fe9-142">For example, you might want to verify that a string that represents a telephone number contains the required number of numerals before setting the property value.</span></span>  
  
-   <span data-ttu-id="e2fe9-143">Especifique diferente acessibilidade para o `Get` e `Set` procedimento.</span><span class="sxs-lookup"><span data-stu-id="e2fe9-143">Specify different accessibility for the `Get` and `Set` procedure.</span></span> <span data-ttu-id="e2fe9-144">Por exemplo, você talvez queira fazer a `Set` procedimento `Private` e `Get` procedimento `Public`.</span><span class="sxs-lookup"><span data-stu-id="e2fe9-144">For example, you might want to make the `Set` procedure `Private` and the `Get` procedure `Public`.</span></span>  
  
-   <span data-ttu-id="e2fe9-145">Criar propriedades `WriteOnly`.</span><span class="sxs-lookup"><span data-stu-id="e2fe9-145">Create properties that are `WriteOnly`.</span></span>  
  
-   <span data-ttu-id="e2fe9-146">Usar propriedades parametrizadas (incluindo `Default` propriedades).</span><span class="sxs-lookup"><span data-stu-id="e2fe9-146">Use parameterized properties (including `Default` properties).</span></span> <span data-ttu-id="e2fe9-147">Você deve declarar uma propriedade expandida para especificar um parâmetro para a propriedade, ou especifiquem parâmetros adicionais para o `Set` procedimento.</span><span class="sxs-lookup"><span data-stu-id="e2fe9-147">You must declare an expanded property in order to specify a parameter for the property, or to specify additional parameters for the `Set` procedure.</span></span>  
  
-   <span data-ttu-id="e2fe9-148">Colocar um atributo em um campo existente ou alterar o nível de acesso de campo existente.</span><span class="sxs-lookup"><span data-stu-id="e2fe9-148">Place an attribute on the backing field, or change the access level of the backing field.</span></span>  
  
-   <span data-ttu-id="e2fe9-149">Fornece comentários XML para o campo existente.</span><span class="sxs-lookup"><span data-stu-id="e2fe9-149">Provide XML comments for the backing field.</span></span>  
  
## <a name="expanding-an-auto-implemented-property"></a><span data-ttu-id="e2fe9-150">Expandindo uma propriedade autoimplementadas</span><span class="sxs-lookup"><span data-stu-id="e2fe9-150">Expanding an Auto-Implemented Property</span></span>  
 <span data-ttu-id="e2fe9-151">Se você precisar converter uma propriedade implementada automaticamente a uma propriedade expandida que contém um `Get` ou `Set` procedimento, o Editor de código do Visual Basic pode gerar automaticamente o `Get` e `Set` procedimentos e `End Property` declaração da propriedade.</span><span class="sxs-lookup"><span data-stu-id="e2fe9-151">If you have to convert an auto-implemented property to an expanded property that contains a `Get` or `Set` procedure, the Visual Basic Code Editor can automatically generate the `Get` and `Set` procedures and `End Property` statement for the property.</span></span> <span data-ttu-id="e2fe9-152">O código é gerado se você colocar o cursor em uma linha em branco seguinte o `Property` instrução, digite um `G` (para `Get`) ou um `S` (para `Set`) e pressione ENTER.</span><span class="sxs-lookup"><span data-stu-id="e2fe9-152">The code is generated if you put the cursor on a blank line following the `Property` statement, type a `G` (for `Get`) or an `S` (for `Set`) and press ENTER.</span></span> <span data-ttu-id="e2fe9-153">Editor de código do Visual Basic gera automaticamente o `Get` ou `Set` procedimento para propriedades somente leitura e somente gravação quando você pressiona ENTER ao final de uma `Property` instrução.</span><span class="sxs-lookup"><span data-stu-id="e2fe9-153">The Visual Basic Code Editor automatically generates the `Get` or `Set` procedure for read-only and write-only properties when you press ENTER at the end of a `Property` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2fe9-154">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e2fe9-154">See Also</span></span>  
 <span data-ttu-id="e2fe9-155">[Como: declarar e chamar uma propriedade padrão no Visual Basic](./how-to-declare-and-call-a-default-property.md) </span><span class="sxs-lookup"><span data-stu-id="e2fe9-155">[How to: Declare and Call a Default Property in Visual Basic](./how-to-declare-and-call-a-default-property.md) </span></span>  
<span data-ttu-id="e2fe9-156"> [Como: declarar uma propriedade com níveis de acesso mistos](./how-to-declare-a-property-with-mixed-access-levels.md) </span><span class="sxs-lookup"><span data-stu-id="e2fe9-156"> [How to: Declare a Property with Mixed Access Levels](./how-to-declare-a-property-with-mixed-access-levels.md) </span></span>  
<span data-ttu-id="e2fe9-157"> [Instrução Property](../../../../visual-basic/language-reference/statements/property-statement.md) </span><span class="sxs-lookup"><span data-stu-id="e2fe9-157"> [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md) </span></span>  
<span data-ttu-id="e2fe9-158"> [Somente leitura](../../../../visual-basic/language-reference/modifiers/readonly.md) </span><span class="sxs-lookup"><span data-stu-id="e2fe9-158"> [ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md) </span></span>  
<span data-ttu-id="e2fe9-159"> [WriteOnly](../../../../visual-basic/language-reference/modifiers/writeonly.md) </span><span class="sxs-lookup"><span data-stu-id="e2fe9-159"> [WriteOnly](../../../../visual-basic/language-reference/modifiers/writeonly.md) </span></span>  
<span data-ttu-id="e2fe9-160"> [Objetos e Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)</span><span class="sxs-lookup"><span data-stu-id="e2fe9-160"> [Objects and Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)</span></span>

