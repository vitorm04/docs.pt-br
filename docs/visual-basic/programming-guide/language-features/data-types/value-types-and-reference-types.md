---
title: "Tipos de valor e referência | Documentos do Microsoft"
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
- reference data types
- reference types
- value types
- value data types
- types [Visual Basic]
- data types [Visual Basic], value types
- data types [Visual Basic], reference types
ms.assetid: fc82ce15-5a40-4c5c-a1e1-a556830e7391
caps.latest.revision: 14
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
ms.openlocfilehash: 8136f58b2e7fce15e959e04b84b05f64d078d662
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="value-types-and-reference-types"></a><span data-ttu-id="ab510-102">Tipos de valor e referência</span><span class="sxs-lookup"><span data-stu-id="ab510-102">Value Types and Reference Types</span></span>
<span data-ttu-id="ab510-103">No Visual Basic, os tipos de dados são implementados com base em sua classificação.</span><span class="sxs-lookup"><span data-stu-id="ab510-103">In Visual Basic, data types are implemented based on their classification.</span></span> <span data-ttu-id="ab510-104">O [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] tipos de dados podem ser classificados de acordo com se uma variável de um determinado tipo armazena seus próprios dados ou um ponteiro para os dados.</span><span class="sxs-lookup"><span data-stu-id="ab510-104">The [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] data types can be classified according to whether a variable of a particular type stores its own data or a pointer to the data.</span></span> <span data-ttu-id="ab510-105">Se ela armazena seus próprios dados é um *tipo de valor*; se ela contém um ponteiro para os dados em outro lugar da memória é uma *tipo de referência*.</span><span class="sxs-lookup"><span data-stu-id="ab510-105">If it stores its own data it is a *value type*; if it holds a pointer to data elsewhere in memory it is a *reference type*.</span></span>  
  
## <a name="value-types"></a><span data-ttu-id="ab510-106">Tipos de valor</span><span class="sxs-lookup"><span data-stu-id="ab510-106">Value Types</span></span>  
 <span data-ttu-id="ab510-107">Um tipo de dados é uma *tipo de valor* se ele mantém os dados dentro sua própria alocação de memória.</span><span class="sxs-lookup"><span data-stu-id="ab510-107">A data type is a *value type* if it holds the data within its own memory allocation.</span></span> <span data-ttu-id="ab510-108">Tipos de valor incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="ab510-108">Value types include the following:</span></span>  
  
-   <span data-ttu-id="ab510-109">Todos os tipos de dados numéricos</span><span class="sxs-lookup"><span data-stu-id="ab510-109">All numeric data types</span></span>  
  
-   <span data-ttu-id="ab510-110">`Boolean`, `Char` e `Date`</span><span class="sxs-lookup"><span data-stu-id="ab510-110">`Boolean`, `Char`, and `Date`</span></span>  
  
-   <span data-ttu-id="ab510-111">Todas as estruturas, mesmo que seus membros são tipos de referência</span><span class="sxs-lookup"><span data-stu-id="ab510-111">All structures, even if their members are reference types</span></span>  
  
-   <span data-ttu-id="ab510-112">Enumerações, pois seu tipo base é sempre `SByte`, `Short`, `Integer`, `Long`, `Byte`, `UShort`, `UInteger`, ou`ULong`</span><span class="sxs-lookup"><span data-stu-id="ab510-112">Enumerations, since their underlying type is always `SByte`, `Short`, `Integer`, `Long`, `Byte`, `UShort`, `UInteger`, or `ULong`</span></span>  
  
 <span data-ttu-id="ab510-113">Cada estrutura é um tipo de valor, mesmo se ele contiver membros de tipo de referência.</span><span class="sxs-lookup"><span data-stu-id="ab510-113">Every structure is a value type, even if it contains reference type members.</span></span> <span data-ttu-id="ab510-114">Por esse motivo, tipos, como `Char` e `Integer` são implementados por estruturas do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ab510-114">For this reason, value types such as `Char` and `Integer` are implemented by .NET Framework structures.</span></span>  
  
 <span data-ttu-id="ab510-115">Você pode declarar um tipo de valor usando a palavra-chave reservada, por exemplo, `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="ab510-115">You can declare a value type by using the reserved keyword, for example, `Decimal`.</span></span> <span data-ttu-id="ab510-116">Você também pode usar o `New` palavra-chave para inicializar um tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="ab510-116">You can also use the `New` keyword to initialize a value type.</span></span> <span data-ttu-id="ab510-117">Isso é especialmente útil se o tipo tem um construtor que aceita parâmetros.</span><span class="sxs-lookup"><span data-stu-id="ab510-117">This is especially useful if the type has a constructor that takes parameters.</span></span> <span data-ttu-id="ab510-118">Um exemplo disso é o <xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29>construtor, que cria um novo `Decimal` valor a partir das partes fornecidas.</xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29></span><span class="sxs-lookup"><span data-stu-id="ab510-118">An example of this is the <xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29> constructor, which builds a new `Decimal` value from the supplied parts.</span></span>  
  
## <a name="reference-types"></a><span data-ttu-id="ab510-119">Tipos de referência</span><span class="sxs-lookup"><span data-stu-id="ab510-119">Reference Types</span></span>  
 <span data-ttu-id="ab510-120">A *tipo de referência* contém um ponteiro para outro local da memória que mantém os dados.</span><span class="sxs-lookup"><span data-stu-id="ab510-120">A *reference type* contains a pointer to another memory location that holds the data.</span></span> <span data-ttu-id="ab510-121">Tipos de referência incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="ab510-121">Reference types include the following:</span></span>  
  
-   `String`  
  
-   <span data-ttu-id="ab510-122">Todas as matrizes, mesmo se seus elementos são tipos de valor</span><span class="sxs-lookup"><span data-stu-id="ab510-122">All arrays, even if their elements are value types</span></span>  
  
-   <span data-ttu-id="ab510-123">Tipos de classe, como<xref:System.Windows.Forms.Form></xref:System.Windows.Forms.Form></span><span class="sxs-lookup"><span data-stu-id="ab510-123">Class types, such as <xref:System.Windows.Forms.Form></span></span>  
  
-   <span data-ttu-id="ab510-124">Delegados</span><span class="sxs-lookup"><span data-stu-id="ab510-124">Delegates</span></span>  
  
 <span data-ttu-id="ab510-125">Uma classe é um *tipo de referência*.</span><span class="sxs-lookup"><span data-stu-id="ab510-125">A class is a *reference type*.</span></span> <span data-ttu-id="ab510-126">Por esse motivo, tipos de referência como `Object` e `String` são suportados pelo [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] classes.</span><span class="sxs-lookup"><span data-stu-id="ab510-126">For this reason, reference types such as `Object` and `String` are supported by [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] classes.</span></span> <span data-ttu-id="ab510-127">Observe que cada matriz é um tipo de referência, mesmo se seus membros são tipos de valor.</span><span class="sxs-lookup"><span data-stu-id="ab510-127">Note that every array is a reference type, even if its members are value types.</span></span>  
  
 <span data-ttu-id="ab510-128">Como cada tipo de referência representa uma classe base do .NET Framework, você deve usar o [novo operador](../../../../visual-basic/language-reference/operators/new-operator.md) palavra-chave quando fizer a inicialização.</span><span class="sxs-lookup"><span data-stu-id="ab510-128">Since every reference type represents an underlying .NET Framework class, you must use the [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) keyword when you initialize it.</span></span> <span data-ttu-id="ab510-129">A instrução a seguir inicializa uma matriz.</span><span class="sxs-lookup"><span data-stu-id="ab510-129">The following statement initializes an array.</span></span>  
  
```  
Dim totals() As Single = New Single(8) {}  
```  
  
## <a name="elements-that-are-not-types"></a><span data-ttu-id="ab510-130">Elementos que não são de tipos</span><span class="sxs-lookup"><span data-stu-id="ab510-130">Elements That Are Not Types</span></span>  
 <span data-ttu-id="ab510-131">Os seguintes elementos de programação não se qualificam como tipos, porque você não pode especificar qualquer um deles como um tipo de dados de um elemento declarado:</span><span class="sxs-lookup"><span data-stu-id="ab510-131">The following programming elements do not qualify as types, because you cannot specify any of them as a data type for a declared element:</span></span>  
  
-   <span data-ttu-id="ab510-132">Namespaces</span><span class="sxs-lookup"><span data-stu-id="ab510-132">Namespaces</span></span>  
  
-   <span data-ttu-id="ab510-133">Módulos</span><span class="sxs-lookup"><span data-stu-id="ab510-133">Modules</span></span>  
  
-   <span data-ttu-id="ab510-134">Eventos</span><span class="sxs-lookup"><span data-stu-id="ab510-134">Events</span></span>  
  
-   <span data-ttu-id="ab510-135">Propriedades e procedimentos</span><span class="sxs-lookup"><span data-stu-id="ab510-135">Properties and procedures</span></span>  
  
-   <span data-ttu-id="ab510-136">Variáveis, constantes e campos</span><span class="sxs-lookup"><span data-stu-id="ab510-136">Variables, constants, and fields</span></span>  
  
## <a name="working-with-the-object-data-type"></a><span data-ttu-id="ab510-137">Trabalhando com o tipo de dados de objeto</span><span class="sxs-lookup"><span data-stu-id="ab510-137">Working with the Object Data Type</span></span>  
 <span data-ttu-id="ab510-138">Você pode atribuir um tipo de referência ou um tipo de valor a uma variável do `Object` tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="ab510-138">You can assign either a reference type or a value type to a variable of the `Object` data type.</span></span> <span data-ttu-id="ab510-139">Um `Object` variável sempre contém um ponteiro para os dados, nunca os dados propriamente ditos.</span><span class="sxs-lookup"><span data-stu-id="ab510-139">An `Object` variable always holds a pointer to the data, never the data itself.</span></span> <span data-ttu-id="ab510-140">No entanto, se você atribuir um tipo de valor para um `Object` variável, ele se comporta como se ele contém os seus próprios dados.</span><span class="sxs-lookup"><span data-stu-id="ab510-140">However, if you assign a value type to an `Object` variable, it behaves as if it holds its own data.</span></span> <span data-ttu-id="ab510-141">Para obter mais informações, consulte [tipo de dados do objeto](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="ab510-141">For more information, see [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span></span>  
  
 <span data-ttu-id="ab510-142">Você pode descobrir se um `Object` variável está atuando como um tipo de referência ou um tipo de valor, passando-o para o <xref:Microsoft.VisualBasic.Information.IsReference%2A>método o <xref:Microsoft.VisualBasic.Information>classe do <xref:Microsoft.VisualBasic?displayProperty=fullName>namespace.</xref:Microsoft.VisualBasic?displayProperty=fullName> </xref:Microsoft.VisualBasic.Information> </xref:Microsoft.VisualBasic.Information.IsReference%2A></span><span class="sxs-lookup"><span data-stu-id="ab510-142">You can find out whether an `Object` variable is acting as a reference type or a value type by passing it to the <xref:Microsoft.VisualBasic.Information.IsReference%2A> method in the <xref:Microsoft.VisualBasic.Information> class of the <xref:Microsoft.VisualBasic?displayProperty=fullName> namespace.</span></span> <span data-ttu-id="ab510-143"><xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=fullName>Retorna `True` se o conteúdo de `Object` variável representa um tipo de referência.</xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="ab510-143"><xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=fullName> returns `True` if the content of the `Object` variable represents a reference type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab510-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ab510-144">See Also</span></span>  
 <span data-ttu-id="ab510-145">[Tipos de valor anulável](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) </span><span class="sxs-lookup"><span data-stu-id="ab510-145">[Nullable Value Types](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) </span></span>  
<span data-ttu-id="ab510-146"> [Conversões de tipo no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md) </span><span class="sxs-lookup"><span data-stu-id="ab510-146"> [Type Conversions in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md) </span></span>  
<span data-ttu-id="ab510-147"> [Instrução Structure](../../../../visual-basic/language-reference/statements/structure-statement.md) </span><span class="sxs-lookup"><span data-stu-id="ab510-147"> [Structure Statement](../../../../visual-basic/language-reference/statements/structure-statement.md) </span></span>  
<span data-ttu-id="ab510-148"> [Uso eficiente de tipos de dados](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="ab510-148"> [Efficient Use of Data Types](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md) </span></span>  
<span data-ttu-id="ab510-149"> [Tipo de dados Object](../../../../visual-basic/language-reference/data-types/object-data-type.md) </span><span class="sxs-lookup"><span data-stu-id="ab510-149"> [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md) </span></span>  
<span data-ttu-id="ab510-150"> [Tipos de Dados](../../../../visual-basic/programming-guide/language-features/data-types/index.md)</span><span class="sxs-lookup"><span data-stu-id="ab510-150"> [Data Types](../../../../visual-basic/programming-guide/language-features/data-types/index.md)</span></span>
