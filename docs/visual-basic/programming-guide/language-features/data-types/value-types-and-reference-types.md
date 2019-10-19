---
title: Tipos de valor e referência
ms.date: 07/20/2015
helpviewer_keywords:
- reference data types [Visual Basic]
- reference types [Visual Basic]
- value types [Visual Basic]
- value data types [Visual Basic]
- types [Visual Basic]
- data types [Visual Basic], value types
- data types [Visual Basic], reference types
ms.assetid: fc82ce15-5a40-4c5c-a1e1-a556830e7391
ms.openlocfilehash: 466bb5386235917705344d35c5141c8bf779218d
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582644"
---
# <a name="value-types-and-reference-types"></a><span data-ttu-id="42bf2-102">Tipos de valor e referência</span><span class="sxs-lookup"><span data-stu-id="42bf2-102">Value Types and Reference Types</span></span>
<span data-ttu-id="42bf2-103">Há dois tipos de tipo em Visual Basic: tipos de referência e tipos de valor.</span><span class="sxs-lookup"><span data-stu-id="42bf2-103">There are two kinds of types in Visual Basic: reference types and value types.</span></span> <span data-ttu-id="42bf2-104">Variáveis de tipos de referência armazenam referências em seus dados (objetos) enquanto que variáveis de tipos de valor contém diretamente seus dados.</span><span class="sxs-lookup"><span data-stu-id="42bf2-104">Variables of reference types store references to their data (objects), while variables of value types directly contain their data.</span></span> <span data-ttu-id="42bf2-105">Com tipos de referência, duas variáveis podem fazer referência ao mesmo objeto; portanto, operações em uma variável podem afetar o objeto referenciado pela outra variável.</span><span class="sxs-lookup"><span data-stu-id="42bf2-105">With reference types, two variables can reference the same object; therefore, operations on one variable can affect the object referenced by the other variable.</span></span> <span data-ttu-id="42bf2-106">Com tipos de valor, cada variável tem sua própria cópia dos dados e não é possível que as operações em uma variável afetem a outra (exceto no caso do [modificador ByRef nos parâmetros](../../../language-reference/modifiers/byref.md)).</span><span class="sxs-lookup"><span data-stu-id="42bf2-106">With value types, each variable has its own copy of the data, and it is not possible for operations on one variable to affect the other (except in the case of the [ByRef modifier on parameters](../../../language-reference/modifiers/byref.md)).</span></span>
  
## <a name="value-types"></a><span data-ttu-id="42bf2-107">Tipos de valor</span><span class="sxs-lookup"><span data-stu-id="42bf2-107">Value Types</span></span>  
 <span data-ttu-id="42bf2-108">Um tipo de dados é um *tipo de valor* se ele mantém os dados dentro de sua própria alocação de memória.</span><span class="sxs-lookup"><span data-stu-id="42bf2-108">A data type is a *value type* if it holds the data within its own memory allocation.</span></span> <span data-ttu-id="42bf2-109">Os tipos de valor incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="42bf2-109">Value types include the following:</span></span>  
  
- <span data-ttu-id="42bf2-110">Todos os tipos de dados numéricos</span><span class="sxs-lookup"><span data-stu-id="42bf2-110">All numeric data types</span></span>  
  
- <span data-ttu-id="42bf2-111">`Boolean`, `Char` e `Date`</span><span class="sxs-lookup"><span data-stu-id="42bf2-111">`Boolean`, `Char`, and `Date`</span></span>  
  
- <span data-ttu-id="42bf2-112">Todas as estruturas, mesmo que seus membros sejam tipos de referência</span><span class="sxs-lookup"><span data-stu-id="42bf2-112">All structures, even if their members are reference types</span></span>  
  
- <span data-ttu-id="42bf2-113">As enumerações, já que seu tipo subjacente é sempre `SByte`, `Short`, `Integer`, `Long`, `Byte`, `UShort`, `UInteger` ou `ULong`</span><span class="sxs-lookup"><span data-stu-id="42bf2-113">Enumerations, since their underlying type is always `SByte`, `Short`, `Integer`, `Long`, `Byte`, `UShort`, `UInteger`, or `ULong`</span></span>  
  
 <span data-ttu-id="42bf2-114">Cada estrutura é um tipo de valor, mesmo que contenha membros de tipo de referência.</span><span class="sxs-lookup"><span data-stu-id="42bf2-114">Every structure is a value type, even if it contains reference type members.</span></span> <span data-ttu-id="42bf2-115">Por esse motivo, tipos de valor como `Char` e `Integer` são implementados por estruturas de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="42bf2-115">For this reason, value types such as `Char` and `Integer` are implemented by .NET Framework structures.</span></span>  
  
 <span data-ttu-id="42bf2-116">Você pode declarar um tipo de valor usando a palavra-chave reservada, por exemplo, `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="42bf2-116">You can declare a value type by using the reserved keyword, for example, `Decimal`.</span></span> <span data-ttu-id="42bf2-117">Você também pode usar a palavra-chave `New` para inicializar um tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="42bf2-117">You can also use the `New` keyword to initialize a value type.</span></span> <span data-ttu-id="42bf2-118">Isso é especialmente útil se o tipo tiver um construtor que aceite parâmetros.</span><span class="sxs-lookup"><span data-stu-id="42bf2-118">This is especially useful if the type has a constructor that takes parameters.</span></span> <span data-ttu-id="42bf2-119">Um exemplo disso é o Construtor <xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29>, que cria um novo valor de `Decimal` a partir das partes fornecidas.</span><span class="sxs-lookup"><span data-stu-id="42bf2-119">An example of this is the <xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29> constructor, which builds a new `Decimal` value from the supplied parts.</span></span>  
  
## <a name="reference-types"></a><span data-ttu-id="42bf2-120">Tipos de referência</span><span class="sxs-lookup"><span data-stu-id="42bf2-120">Reference Types</span></span>  
 <span data-ttu-id="42bf2-121">Um *tipo de referência* armazena uma referência a seus dados.</span><span class="sxs-lookup"><span data-stu-id="42bf2-121">A *reference type* stores a reference to its data.</span></span> <span data-ttu-id="42bf2-122">Os tipos de referência incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="42bf2-122">Reference types include the following:</span></span>  
  
- `String`  
  
- <span data-ttu-id="42bf2-123">Todas as matrizes, mesmo que seus elementos sejam de tipos de valor</span><span class="sxs-lookup"><span data-stu-id="42bf2-123">All arrays, even if their elements are value types</span></span>  
  
- <span data-ttu-id="42bf2-124">Tipos de classe, como <xref:System.Windows.Forms.Form></span><span class="sxs-lookup"><span data-stu-id="42bf2-124">Class types, such as <xref:System.Windows.Forms.Form></span></span>  
  
- <span data-ttu-id="42bf2-125">Delegados</span><span class="sxs-lookup"><span data-stu-id="42bf2-125">Delegates</span></span>  
  
 <span data-ttu-id="42bf2-126">Uma classe é um *tipo de referência*.</span><span class="sxs-lookup"><span data-stu-id="42bf2-126">A class is a *reference type*.</span></span> <span data-ttu-id="42bf2-127">Observe que cada matriz é um tipo de referência, mesmo que seus membros sejam de tipos de valor.</span><span class="sxs-lookup"><span data-stu-id="42bf2-127">Note that every array is a reference type, even if its members are value types.</span></span>  
  
 <span data-ttu-id="42bf2-128">Como cada tipo de referência representa uma classe de .NET Framework subjacente, você deve usar a palavra-chave [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) ao inicializá-la.</span><span class="sxs-lookup"><span data-stu-id="42bf2-128">Since every reference type represents an underlying .NET Framework class, you must use the [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) keyword when you initialize it.</span></span> <span data-ttu-id="42bf2-129">A instrução a seguir inicializa uma matriz.</span><span class="sxs-lookup"><span data-stu-id="42bf2-129">The following statement initializes an array.</span></span>  
  
```vb  
Dim totals() As Single = New Single(8) {}  
```  
  
## <a name="elements-that-are-not-types"></a><span data-ttu-id="42bf2-130">Elementos que não são tipos</span><span class="sxs-lookup"><span data-stu-id="42bf2-130">Elements That Are Not Types</span></span>  
 <span data-ttu-id="42bf2-131">Os seguintes elementos de programação não se qualificam como tipos, porque você não pode especificar nenhum deles como um tipo de dados para um elemento declarado:</span><span class="sxs-lookup"><span data-stu-id="42bf2-131">The following programming elements do not qualify as types, because you cannot specify any of them as a data type for a declared element:</span></span>  
  
- <span data-ttu-id="42bf2-132">Namespaces</span><span class="sxs-lookup"><span data-stu-id="42bf2-132">Namespaces</span></span>  
  
- <span data-ttu-id="42bf2-133">Módulos</span><span class="sxs-lookup"><span data-stu-id="42bf2-133">Modules</span></span>  
  
- <span data-ttu-id="42bf2-134">Eventos</span><span class="sxs-lookup"><span data-stu-id="42bf2-134">Events</span></span>  
  
- <span data-ttu-id="42bf2-135">Propriedades e procedimentos</span><span class="sxs-lookup"><span data-stu-id="42bf2-135">Properties and procedures</span></span>  
  
- <span data-ttu-id="42bf2-136">Variáveis, constantes e campos</span><span class="sxs-lookup"><span data-stu-id="42bf2-136">Variables, constants, and fields</span></span>  
  
## <a name="working-with-the-object-data-type"></a><span data-ttu-id="42bf2-137">Trabalhando com o tipo de dados Object</span><span class="sxs-lookup"><span data-stu-id="42bf2-137">Working with the Object Data Type</span></span>  
 <span data-ttu-id="42bf2-138">Você pode atribuir um tipo de referência ou um tipo de valor a uma variável do tipo de dados `Object`.</span><span class="sxs-lookup"><span data-stu-id="42bf2-138">You can assign either a reference type or a value type to a variable of the `Object` data type.</span></span> <span data-ttu-id="42bf2-139">Uma variável `Object` sempre mantém uma referência aos dados, nunca os dados em si.</span><span class="sxs-lookup"><span data-stu-id="42bf2-139">An `Object` variable always holds a reference to the data, never the data itself.</span></span> <span data-ttu-id="42bf2-140">No entanto, se você atribuir um tipo de valor a uma variável `Object`, ela se comporta como se ela contiver seus próprios dados.</span><span class="sxs-lookup"><span data-stu-id="42bf2-140">However, if you assign a value type to an `Object` variable, it behaves as if it holds its own data.</span></span> <span data-ttu-id="42bf2-141">Para obter mais informações, consulte [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="42bf2-141">For more information, see [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span></span>  
  
 <span data-ttu-id="42bf2-142">Você pode descobrir se uma variável `Object` está agindo como um tipo de referência ou um tipo de valor passando-a para o método <xref:Microsoft.VisualBasic.Information.IsReference%2A> na classe <xref:Microsoft.VisualBasic.Information> do namespace <xref:Microsoft.VisualBasic?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="42bf2-142">You can find out whether an `Object` variable is acting as a reference type or a value type by passing it to the <xref:Microsoft.VisualBasic.Information.IsReference%2A> method in the <xref:Microsoft.VisualBasic.Information> class of the <xref:Microsoft.VisualBasic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="42bf2-143"><xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=nameWithType> retornará `True` se o conteúdo da variável `Object` representar um tipo de referência.</span><span class="sxs-lookup"><span data-stu-id="42bf2-143"><xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=nameWithType> returns `True` if the content of the `Object` variable represents a reference type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42bf2-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="42bf2-144">See also</span></span>

- [<span data-ttu-id="42bf2-145">Tipos de Valor Anulável</span><span class="sxs-lookup"><span data-stu-id="42bf2-145">Nullable Value Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="42bf2-146">Conversões de tipo no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="42bf2-146">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="42bf2-147">Instrução Structure</span><span class="sxs-lookup"><span data-stu-id="42bf2-147">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="42bf2-148">Uso Eficiente de Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="42bf2-148">Efficient Use of Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [<span data-ttu-id="42bf2-149">Tipo de Dados Object</span><span class="sxs-lookup"><span data-stu-id="42bf2-149">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="42bf2-150">Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="42bf2-150">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
