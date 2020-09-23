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
ms.openlocfilehash: 72cb1455300e1ff00d9d558aa5a9df95f32aa7b0
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91090112"
---
# <a name="value-types-and-reference-types"></a><span data-ttu-id="11093-102">Tipos de valor e referência</span><span class="sxs-lookup"><span data-stu-id="11093-102">Value Types and Reference Types</span></span>

<span data-ttu-id="11093-103">Há dois tipos de tipo em Visual Basic: tipos de referência e tipos de valor.</span><span class="sxs-lookup"><span data-stu-id="11093-103">There are two kinds of types in Visual Basic: reference types and value types.</span></span> <span data-ttu-id="11093-104">Variáveis de tipos de referência armazenam referências em seus dados (objetos) enquanto que variáveis de tipos de valor contém diretamente seus dados.</span><span class="sxs-lookup"><span data-stu-id="11093-104">Variables of reference types store references to their data (objects), while variables of value types directly contain their data.</span></span> <span data-ttu-id="11093-105">Com tipos de referência, duas variáveis podem fazer referência ao mesmo objeto; portanto, operações em uma variável podem afetar o objeto referenciado pela outra variável.</span><span class="sxs-lookup"><span data-stu-id="11093-105">With reference types, two variables can reference the same object; therefore, operations on one variable can affect the object referenced by the other variable.</span></span> <span data-ttu-id="11093-106">Com tipos de valor, cada variável tem sua própria cópia dos dados e não é possível que as operações em uma variável afetem a outra (exceto no caso do [modificador ByRef nos parâmetros](../../../language-reference/modifiers/byref.md)).</span><span class="sxs-lookup"><span data-stu-id="11093-106">With value types, each variable has its own copy of the data, and it is not possible for operations on one variable to affect the other (except in the case of the [ByRef modifier on parameters](../../../language-reference/modifiers/byref.md)).</span></span>
  
## <a name="value-types"></a><span data-ttu-id="11093-107">Tipos de valor</span><span class="sxs-lookup"><span data-stu-id="11093-107">Value Types</span></span>  

 <span data-ttu-id="11093-108">Um tipo de dados é um *tipo de valor* se ele mantém os dados dentro de sua própria alocação de memória.</span><span class="sxs-lookup"><span data-stu-id="11093-108">A data type is a *value type* if it holds the data within its own memory allocation.</span></span> <span data-ttu-id="11093-109">Os tipos de valor incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="11093-109">Value types include the following:</span></span>  
  
- <span data-ttu-id="11093-110">Todos os tipos de dados numéricos</span><span class="sxs-lookup"><span data-stu-id="11093-110">All numeric data types</span></span>  
  
- <span data-ttu-id="11093-111">`Boolean`, `Char`, e `Date`</span><span class="sxs-lookup"><span data-stu-id="11093-111">`Boolean`, `Char`, and `Date`</span></span>  
  
- <span data-ttu-id="11093-112">Todas as estruturas, mesmo que seus membros sejam tipos de referência</span><span class="sxs-lookup"><span data-stu-id="11093-112">All structures, even if their members are reference types</span></span>  
  
- <span data-ttu-id="11093-113">Enumerações, já que seu tipo subjacente é sempre,,,,,, `SByte` `Short` `Integer` `Long` `Byte` `UShort` `UInteger` ou `ULong`</span><span class="sxs-lookup"><span data-stu-id="11093-113">Enumerations, since their underlying type is always `SByte`, `Short`, `Integer`, `Long`, `Byte`, `UShort`, `UInteger`, or `ULong`</span></span>  
  
 <span data-ttu-id="11093-114">Cada estrutura é um tipo de valor, mesmo que contenha membros de tipo de referência.</span><span class="sxs-lookup"><span data-stu-id="11093-114">Every structure is a value type, even if it contains reference type members.</span></span> <span data-ttu-id="11093-115">Por esse motivo, tipos de valor como `Char` e `Integer` são implementados por estruturas .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="11093-115">For this reason, value types such as `Char` and `Integer` are implemented by .NET Framework structures.</span></span>  
  
 <span data-ttu-id="11093-116">Você pode declarar um tipo de valor usando a palavra-chave reservada, por exemplo, `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="11093-116">You can declare a value type by using the reserved keyword, for example, `Decimal`.</span></span> <span data-ttu-id="11093-117">Você também pode usar a `New` palavra-chave para inicializar um tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="11093-117">You can also use the `New` keyword to initialize a value type.</span></span> <span data-ttu-id="11093-118">Isso é especialmente útil se o tipo tiver um construtor que aceite parâmetros.</span><span class="sxs-lookup"><span data-stu-id="11093-118">This is especially useful if the type has a constructor that takes parameters.</span></span> <span data-ttu-id="11093-119">Um exemplo disso é o <xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29> Construtor, que cria um novo `Decimal` valor a partir das partes fornecidas.</span><span class="sxs-lookup"><span data-stu-id="11093-119">An example of this is the <xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29> constructor, which builds a new `Decimal` value from the supplied parts.</span></span>  
  
## <a name="reference-types"></a><span data-ttu-id="11093-120">Tipos de referência</span><span class="sxs-lookup"><span data-stu-id="11093-120">Reference Types</span></span>  

 <span data-ttu-id="11093-121">Um *tipo de referência* armazena uma referência a seus dados.</span><span class="sxs-lookup"><span data-stu-id="11093-121">A *reference type* stores a reference to its data.</span></span> <span data-ttu-id="11093-122">Os tipos de referência incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="11093-122">Reference types include the following:</span></span>  
  
- `String`  
  
- <span data-ttu-id="11093-123">Todas as matrizes, mesmo que seus elementos sejam de tipos de valor</span><span class="sxs-lookup"><span data-stu-id="11093-123">All arrays, even if their elements are value types</span></span>  
  
- <span data-ttu-id="11093-124">Tipos de classe, como <xref:System.Windows.Forms.Form></span><span class="sxs-lookup"><span data-stu-id="11093-124">Class types, such as <xref:System.Windows.Forms.Form></span></span>  
  
- <span data-ttu-id="11093-125">Delegados</span><span class="sxs-lookup"><span data-stu-id="11093-125">Delegates</span></span>  
  
 <span data-ttu-id="11093-126">Uma classe é um *tipo de referência*.</span><span class="sxs-lookup"><span data-stu-id="11093-126">A class is a *reference type*.</span></span> <span data-ttu-id="11093-127">Observe que cada matriz é um tipo de referência, mesmo que seus membros sejam de tipos de valor.</span><span class="sxs-lookup"><span data-stu-id="11093-127">Note that every array is a reference type, even if its members are value types.</span></span>  
  
 <span data-ttu-id="11093-128">Como cada tipo de referência representa uma classe de .NET Framework subjacente, você deve usar a palavra-chave [New Operator](../../../language-reference/operators/new-operator.md) ao inicializá-la.</span><span class="sxs-lookup"><span data-stu-id="11093-128">Since every reference type represents an underlying .NET Framework class, you must use the [New Operator](../../../language-reference/operators/new-operator.md) keyword when you initialize it.</span></span> <span data-ttu-id="11093-129">A instrução a seguir inicializa uma matriz.</span><span class="sxs-lookup"><span data-stu-id="11093-129">The following statement initializes an array.</span></span>  
  
```vb  
Dim totals() As Single = New Single(8) {}  
```  
  
## <a name="elements-that-are-not-types"></a><span data-ttu-id="11093-130">Elementos que não são tipos</span><span class="sxs-lookup"><span data-stu-id="11093-130">Elements That Are Not Types</span></span>  

 <span data-ttu-id="11093-131">Os seguintes elementos de programação não se qualificam como tipos, porque você não pode especificar nenhum deles como um tipo de dados para um elemento declarado:</span><span class="sxs-lookup"><span data-stu-id="11093-131">The following programming elements do not qualify as types, because you cannot specify any of them as a data type for a declared element:</span></span>  
  
- <span data-ttu-id="11093-132">Namespaces</span><span class="sxs-lookup"><span data-stu-id="11093-132">Namespaces</span></span>  
  
- <span data-ttu-id="11093-133">Módulos</span><span class="sxs-lookup"><span data-stu-id="11093-133">Modules</span></span>  
  
- <span data-ttu-id="11093-134">Eventos</span><span class="sxs-lookup"><span data-stu-id="11093-134">Events</span></span>  
  
- <span data-ttu-id="11093-135">Propriedades e procedimentos</span><span class="sxs-lookup"><span data-stu-id="11093-135">Properties and procedures</span></span>  
  
- <span data-ttu-id="11093-136">Variáveis, constantes e campos</span><span class="sxs-lookup"><span data-stu-id="11093-136">Variables, constants, and fields</span></span>  
  
## <a name="working-with-the-object-data-type"></a><span data-ttu-id="11093-137">Trabalhando com o tipo de dados Object</span><span class="sxs-lookup"><span data-stu-id="11093-137">Working with the Object Data Type</span></span>  

 <span data-ttu-id="11093-138">Você pode atribuir um tipo de referência ou um tipo de valor a uma variável do `Object` tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="11093-138">You can assign either a reference type or a value type to a variable of the `Object` data type.</span></span> <span data-ttu-id="11093-139">Uma `Object` variável sempre mantém uma referência aos dados, nunca os dados em si.</span><span class="sxs-lookup"><span data-stu-id="11093-139">An `Object` variable always holds a reference to the data, never the data itself.</span></span> <span data-ttu-id="11093-140">No entanto, se você atribuir um tipo de valor a uma `Object` variável, ele se comparecerá como se ele mantiver seus próprios dados.</span><span class="sxs-lookup"><span data-stu-id="11093-140">However, if you assign a value type to an `Object` variable, it behaves as if it holds its own data.</span></span> <span data-ttu-id="11093-141">Para obter mais informações, consulte [Object Data Type](../../../language-reference/data-types/object-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="11093-141">For more information, see [Object Data Type](../../../language-reference/data-types/object-data-type.md).</span></span>  
  
 <span data-ttu-id="11093-142">Você pode descobrir se uma `Object` variável está agindo como um tipo de referência ou um tipo de valor passando-a para o <xref:Microsoft.VisualBasic.Information.IsReference%2A> método na <xref:Microsoft.VisualBasic.Information> classe do <xref:Microsoft.VisualBasic?displayProperty=nameWithType> namespace.</span><span class="sxs-lookup"><span data-stu-id="11093-142">You can find out whether an `Object` variable is acting as a reference type or a value type by passing it to the <xref:Microsoft.VisualBasic.Information.IsReference%2A> method in the <xref:Microsoft.VisualBasic.Information> class of the <xref:Microsoft.VisualBasic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="11093-143"><xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=nameWithType> retorna `True` se o conteúdo da `Object` variável representa um tipo de referência.</span><span class="sxs-lookup"><span data-stu-id="11093-143"><xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=nameWithType> returns `True` if the content of the `Object` variable represents a reference type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11093-144">Confira também</span><span class="sxs-lookup"><span data-stu-id="11093-144">See also</span></span>

- [<span data-ttu-id="11093-145">Tipos de valor anulável</span><span class="sxs-lookup"><span data-stu-id="11093-145">Nullable Value Types</span></span>](nullable-value-types.md)
- [<span data-ttu-id="11093-146">Conversões de tipo no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="11093-146">Type Conversions in Visual Basic</span></span>](type-conversions.md)
- [<span data-ttu-id="11093-147">Instrução Structure</span><span class="sxs-lookup"><span data-stu-id="11093-147">Structure Statement</span></span>](../../../language-reference/statements/structure-statement.md)
- [<span data-ttu-id="11093-148">Uso eficiente de tipos de dados</span><span class="sxs-lookup"><span data-stu-id="11093-148">Efficient Use of Data Types</span></span>](efficient-use-of-data-types.md)
- [<span data-ttu-id="11093-149">Tipo de dados Object</span><span class="sxs-lookup"><span data-stu-id="11093-149">Object Data Type</span></span>](../../../language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="11093-150">Data Types</span><span class="sxs-lookup"><span data-stu-id="11093-150">Data Types</span></span>](index.md)
