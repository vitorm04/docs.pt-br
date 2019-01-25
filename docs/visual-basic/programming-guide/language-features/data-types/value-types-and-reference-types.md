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
ms.openlocfilehash: 2f09a2842edfa9471267f294c9b64229ae824098
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54738742"
---
# <a name="value-types-and-reference-types"></a><span data-ttu-id="802c8-102">Tipos de valor e referência</span><span class="sxs-lookup"><span data-stu-id="802c8-102">Value Types and Reference Types</span></span>
<span data-ttu-id="802c8-103">No Visual Basic, os tipos de dados são implementados com base em sua classificação.</span><span class="sxs-lookup"><span data-stu-id="802c8-103">In Visual Basic, data types are implemented based on their classification.</span></span> <span data-ttu-id="802c8-104">Os tipos de dados do Visual Basic podem ser classificados de acordo com se uma variável de um determinado tipo armazena seus próprios dados ou um ponteiro para os dados.</span><span class="sxs-lookup"><span data-stu-id="802c8-104">The Visual Basic data types can be classified according to whether a variable of a particular type stores its own data or a pointer to the data.</span></span> <span data-ttu-id="802c8-105">Se ela armazena seus próprios dados é um *tipo de valor*; se ele contém um ponteiro para dados em outro lugar na memória é um *tipo de referência*.</span><span class="sxs-lookup"><span data-stu-id="802c8-105">If it stores its own data it is a *value type*; if it holds a pointer to data elsewhere in memory it is a *reference type*.</span></span>  
  
## <a name="value-types"></a><span data-ttu-id="802c8-106">Tipos de valor</span><span class="sxs-lookup"><span data-stu-id="802c8-106">Value Types</span></span>  
 <span data-ttu-id="802c8-107">Um tipo de dados é um *tipo de valor* se ele contém os dados dentro de sua própria alocação de memória.</span><span class="sxs-lookup"><span data-stu-id="802c8-107">A data type is a *value type* if it holds the data within its own memory allocation.</span></span> <span data-ttu-id="802c8-108">Tipos de valor incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="802c8-108">Value types include the following:</span></span>  
  
-   <span data-ttu-id="802c8-109">Todos os tipos de dados numéricos</span><span class="sxs-lookup"><span data-stu-id="802c8-109">All numeric data types</span></span>  
  
-   <span data-ttu-id="802c8-110">`Boolean`, `Char` e `Date`</span><span class="sxs-lookup"><span data-stu-id="802c8-110">`Boolean`, `Char`, and `Date`</span></span>  
  
-   <span data-ttu-id="802c8-111">Todas as estruturas, mesmo se seus membros são tipos de referência</span><span class="sxs-lookup"><span data-stu-id="802c8-111">All structures, even if their members are reference types</span></span>  
  
-   <span data-ttu-id="802c8-112">Enumerações, pois seu tipo subjacente é sempre `SByte`, `Short`, `Integer`, `Long`, `Byte`, `UShort`, `UInteger`, ou `ULong`</span><span class="sxs-lookup"><span data-stu-id="802c8-112">Enumerations, since their underlying type is always `SByte`, `Short`, `Integer`, `Long`, `Byte`, `UShort`, `UInteger`, or `ULong`</span></span>  
  
 <span data-ttu-id="802c8-113">Cada estrutura é um tipo de valor, mesmo que ele contenha membros de tipo de referência.</span><span class="sxs-lookup"><span data-stu-id="802c8-113">Every structure is a value type, even if it contains reference type members.</span></span> <span data-ttu-id="802c8-114">Por esse motivo, tipos de valor, tal como `Char` e `Integer` são implementados por estruturas do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="802c8-114">For this reason, value types such as `Char` and `Integer` are implemented by .NET Framework structures.</span></span>  
  
 <span data-ttu-id="802c8-115">Você pode declarar um tipo de valor usando a palavra-chave reservada, por exemplo, `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="802c8-115">You can declare a value type by using the reserved keyword, for example, `Decimal`.</span></span> <span data-ttu-id="802c8-116">Você também pode usar o `New` palavra-chave para inicializar um tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="802c8-116">You can also use the `New` keyword to initialize a value type.</span></span> <span data-ttu-id="802c8-117">Isso é especialmente útil se o tipo tem um construtor que aceita parâmetros.</span><span class="sxs-lookup"><span data-stu-id="802c8-117">This is especially useful if the type has a constructor that takes parameters.</span></span> <span data-ttu-id="802c8-118">Um exemplo disso é o <xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29> construtor, que cria um novo `Decimal` valor a partir das partes fornecidas.</span><span class="sxs-lookup"><span data-stu-id="802c8-118">An example of this is the <xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29> constructor, which builds a new `Decimal` value from the supplied parts.</span></span>  
  
## <a name="reference-types"></a><span data-ttu-id="802c8-119">Tipos de referência</span><span class="sxs-lookup"><span data-stu-id="802c8-119">Reference Types</span></span>  
 <span data-ttu-id="802c8-120">Um *tipo de referência* contém um ponteiro para outro local da memória que contém os dados.</span><span class="sxs-lookup"><span data-stu-id="802c8-120">A *reference type* contains a pointer to another memory location that holds the data.</span></span> <span data-ttu-id="802c8-121">Tipos de referência incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="802c8-121">Reference types include the following:</span></span>  
  
-   `String`  
  
-   <span data-ttu-id="802c8-122">Todas as matrizes, mesmo se seus elementos são tipos de valor</span><span class="sxs-lookup"><span data-stu-id="802c8-122">All arrays, even if their elements are value types</span></span>  
  
-   <span data-ttu-id="802c8-123">Tipos de classe, como <xref:System.Windows.Forms.Form></span><span class="sxs-lookup"><span data-stu-id="802c8-123">Class types, such as <xref:System.Windows.Forms.Form></span></span>  
  
-   <span data-ttu-id="802c8-124">Delegados</span><span class="sxs-lookup"><span data-stu-id="802c8-124">Delegates</span></span>  
  
 <span data-ttu-id="802c8-125">Uma classe é um *tipo de referência*.</span><span class="sxs-lookup"><span data-stu-id="802c8-125">A class is a *reference type*.</span></span> <span data-ttu-id="802c8-126">Por esse motivo, tipos de referência, como `Object` e `String` são compatíveis com [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] classes.</span><span class="sxs-lookup"><span data-stu-id="802c8-126">For this reason, reference types such as `Object` and `String` are supported by [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] classes.</span></span> <span data-ttu-id="802c8-127">Observe que cada matriz é um tipo de referência, mesmo se seus membros são tipos de valor.</span><span class="sxs-lookup"><span data-stu-id="802c8-127">Note that every array is a reference type, even if its members are value types.</span></span>  
  
 <span data-ttu-id="802c8-128">Como cada tipo de referência representa uma classe base do .NET Framework, você deve usar o [novo operador](../../../../visual-basic/language-reference/operators/new-operator.md) palavra-chave quando inicializá-la.</span><span class="sxs-lookup"><span data-stu-id="802c8-128">Since every reference type represents an underlying .NET Framework class, you must use the [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) keyword when you initialize it.</span></span> <span data-ttu-id="802c8-129">A instrução a seguir inicializa uma matriz.</span><span class="sxs-lookup"><span data-stu-id="802c8-129">The following statement initializes an array.</span></span>  
  
```  
Dim totals() As Single = New Single(8) {}  
```  
  
## <a name="elements-that-are-not-types"></a><span data-ttu-id="802c8-130">Elementos que não são de tipos</span><span class="sxs-lookup"><span data-stu-id="802c8-130">Elements That Are Not Types</span></span>  
 <span data-ttu-id="802c8-131">Os seguintes elementos de programação não se qualificam como tipos, porque você não pode especificar qualquer um deles como um tipo de dados para um elemento declarado:</span><span class="sxs-lookup"><span data-stu-id="802c8-131">The following programming elements do not qualify as types, because you cannot specify any of them as a data type for a declared element:</span></span>  
  
-   <span data-ttu-id="802c8-132">Namespaces</span><span class="sxs-lookup"><span data-stu-id="802c8-132">Namespaces</span></span>  
  
-   <span data-ttu-id="802c8-133">Módulos</span><span class="sxs-lookup"><span data-stu-id="802c8-133">Modules</span></span>  
  
-   <span data-ttu-id="802c8-134">Eventos</span><span class="sxs-lookup"><span data-stu-id="802c8-134">Events</span></span>  
  
-   <span data-ttu-id="802c8-135">Propriedades e procedimentos</span><span class="sxs-lookup"><span data-stu-id="802c8-135">Properties and procedures</span></span>  
  
-   <span data-ttu-id="802c8-136">Variáveis, constantes e campos</span><span class="sxs-lookup"><span data-stu-id="802c8-136">Variables, constants, and fields</span></span>  
  
## <a name="working-with-the-object-data-type"></a><span data-ttu-id="802c8-137">Trabalhando com o tipo de dados de objeto</span><span class="sxs-lookup"><span data-stu-id="802c8-137">Working with the Object Data Type</span></span>  
 <span data-ttu-id="802c8-138">Você pode atribuir um tipo de referência ou um tipo de valor a uma variável do `Object` tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="802c8-138">You can assign either a reference type or a value type to a variable of the `Object` data type.</span></span> <span data-ttu-id="802c8-139">Um `Object` variável sempre contém um ponteiro para os dados, nunca os dados em si.</span><span class="sxs-lookup"><span data-stu-id="802c8-139">An `Object` variable always holds a pointer to the data, never the data itself.</span></span> <span data-ttu-id="802c8-140">No entanto, se você atribuir um tipo de valor para um `Object` variável, ele se comporta como se ele contém seus próprios dados.</span><span class="sxs-lookup"><span data-stu-id="802c8-140">However, if you assign a value type to an `Object` variable, it behaves as if it holds its own data.</span></span> <span data-ttu-id="802c8-141">Para obter mais informações, consulte [tipo de dados do objeto](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="802c8-141">For more information, see [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span></span>  
  
 <span data-ttu-id="802c8-142">Você pode descobrir se um `Object` variável está atuando como um tipo de referência ou um tipo de valor, passando-o para o <xref:Microsoft.VisualBasic.Information.IsReference%2A> método na <xref:Microsoft.VisualBasic.Information> classe do <xref:Microsoft.VisualBasic?displayProperty=nameWithType> namespace.</span><span class="sxs-lookup"><span data-stu-id="802c8-142">You can find out whether an `Object` variable is acting as a reference type or a value type by passing it to the <xref:Microsoft.VisualBasic.Information.IsReference%2A> method in the <xref:Microsoft.VisualBasic.Information> class of the <xref:Microsoft.VisualBasic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="802c8-143"><xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=nameWithType> Retorna `True` se o conteúdo a `Object` variável representa um tipo de referência.</span><span class="sxs-lookup"><span data-stu-id="802c8-143"><xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=nameWithType> returns `True` if the content of the `Object` variable represents a reference type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="802c8-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="802c8-144">See also</span></span>
- [<span data-ttu-id="802c8-145">Tipos de Valor Anulável</span><span class="sxs-lookup"><span data-stu-id="802c8-145">Nullable Value Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="802c8-146">Conversões de tipo no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="802c8-146">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="802c8-147">Instrução Structure</span><span class="sxs-lookup"><span data-stu-id="802c8-147">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="802c8-148">Uso Eficiente de Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="802c8-148">Efficient Use of Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [<span data-ttu-id="802c8-149">Tipo de Dados Object</span><span class="sxs-lookup"><span data-stu-id="802c8-149">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="802c8-150">Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="802c8-150">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
