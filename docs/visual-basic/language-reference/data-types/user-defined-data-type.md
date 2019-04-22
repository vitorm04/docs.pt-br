---
title: Tipo de dados definido pelo usuário (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- UserDefined
- UDT
- vb.UDT
- User-Defined
- vb.UserDefined
- vb.User-Defined
helpviewer_keywords:
- user-defined data types [Visual Basic], Visual Basic
- user-defined types
- structures [Visual Basic], as user-defined data types
- user-defined types [Visual Basic], Visual Basic
- user-defined types [Visual Basic], structure declaration
- user-defined types [Visual Basic], structures in Visual Basic
- user-defined data types [Visual Basic], structure declaration
- data types [Visual Basic], assigning
- Structure statement [Visual Basic]
- data types [Visual Basic], user-defined
- user-defined data types [Visual Basic], structures in Visual Basic
- user-defined data types
- types [Visual Basic], user-defined
ms.assetid: be913dca-a364-4a51-96a1-549a1b390b0a
ms.openlocfilehash: 5fe12d18c7f403c1a50ed548a260ba39e83280eb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58814181"
---
# <a name="user-defined-data-type"></a><span data-ttu-id="b1079-102">Tipo de dados definido pelo usuário</span><span class="sxs-lookup"><span data-stu-id="b1079-102">User-Defined Data Type</span></span>
<span data-ttu-id="b1079-103">Contém os dados em um formato que você definir.</span><span class="sxs-lookup"><span data-stu-id="b1079-103">Holds data in a format you define.</span></span> <span data-ttu-id="b1079-104">O `Structure` instrução define o formato.</span><span class="sxs-lookup"><span data-stu-id="b1079-104">The `Structure` statement defines the format.</span></span>  
  
 <span data-ttu-id="b1079-105">As versões anteriores do Visual Basic suportam o tipo definido pelo usuário (UDT).</span><span class="sxs-lookup"><span data-stu-id="b1079-105">Previous versions of Visual Basic support the user-defined type (UDT).</span></span> <span data-ttu-id="b1079-106">A versão atual expande o UDT para um *estrutura*.</span><span class="sxs-lookup"><span data-stu-id="b1079-106">The current version expands the UDT to a *structure*.</span></span> <span data-ttu-id="b1079-107">Uma estrutura é uma concatenação de um ou mais *membros* de vários tipos de dados.</span><span class="sxs-lookup"><span data-stu-id="b1079-107">A structure is a concatenation of one or more *members* of various data types.</span></span> <span data-ttu-id="b1079-108">Visual Basic trata uma estrutura como uma única unidade, embora você também pode acessar seus membros individualmente.</span><span class="sxs-lookup"><span data-stu-id="b1079-108">Visual Basic treats a structure as a single unit, although you can also access its members individually.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b1079-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="b1079-109">Remarks</span></span>  
 <span data-ttu-id="b1079-110">Definir e usar um tipo de dados de estrutura quando você precisa combinar vários tipos de dados em uma única unidade, ou quando nenhum dos tipos de dados elementares atender às suas necessidades.</span><span class="sxs-lookup"><span data-stu-id="b1079-110">Define and use a structure data type when you need to combine various data types into a single unit, or when none of the elementary data types serve your needs.</span></span>  
  
 <span data-ttu-id="b1079-111">O valor padrão de um tipo de dados de estrutura consiste na combinação dos valores padrão de cada um dos seus membros.</span><span class="sxs-lookup"><span data-stu-id="b1079-111">The default value of a structure data type consists of the combination of the default values of each of its members.</span></span>  
  
## <a name="declaration-format"></a><span data-ttu-id="b1079-112">Formato de declaração</span><span class="sxs-lookup"><span data-stu-id="b1079-112">Declaration Format</span></span>  
 <span data-ttu-id="b1079-113">Uma declaração de estrutura começa com o [instrução Structure](../../../visual-basic/language-reference/statements/structure-statement.md) e termina com o `End Structure` instrução.</span><span class="sxs-lookup"><span data-stu-id="b1079-113">A structure declaration starts with the [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md) and ends with the `End Structure` statement.</span></span> <span data-ttu-id="b1079-114">O `Structure` instrução fornece o nome da estrutura, que também é o identificador do tipo de dados é que define a estrutura.</span><span class="sxs-lookup"><span data-stu-id="b1079-114">The `Structure` statement supplies the name of the structure, which is also the identifier of the data type the structure is defining.</span></span> <span data-ttu-id="b1079-115">Outras partes do código podem usar esse identificador para declarar variáveis, parâmetros e função de valores de retorno para ser do tipo de dados dessa estrutura.</span><span class="sxs-lookup"><span data-stu-id="b1079-115">Other parts of the code can use this identifier to declare variables, parameters, and function return values to be of this structure's data type.</span></span>  
  
 <span data-ttu-id="b1079-116">As declarações entre o `Structure` e `End Structure` instruções definem os membros da estrutura.</span><span class="sxs-lookup"><span data-stu-id="b1079-116">The declarations between the `Structure` and `End Structure` statements define the members of the structure.</span></span>  
  
## <a name="member-access-levels"></a><span data-ttu-id="b1079-117">Níveis de acesso de membro</span><span class="sxs-lookup"><span data-stu-id="b1079-117">Member Access Levels</span></span>  
 <span data-ttu-id="b1079-118">Você deve declarar cada membro usando um [instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md) ou uma declaração que especifica o nível de acesso, como [pública](../../../visual-basic/language-reference/modifiers/public.md), [amigo](../../../visual-basic/language-reference/modifiers/friend.md), ou [privada](../../../visual-basic/language-reference/modifiers/private.md).</span><span class="sxs-lookup"><span data-stu-id="b1079-118">You must declare every member using a [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md) or a statement that specifies access level, such as [Public](../../../visual-basic/language-reference/modifiers/public.md), [Friend](../../../visual-basic/language-reference/modifiers/friend.md), or [Private](../../../visual-basic/language-reference/modifiers/private.md).</span></span> <span data-ttu-id="b1079-119">Se você usar um `Dim` instrução, os padrões de nível de acesso para público.</span><span class="sxs-lookup"><span data-stu-id="b1079-119">If you use a `Dim` statement, the access level defaults to public.</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="b1079-120">Dicas de programação</span><span class="sxs-lookup"><span data-stu-id="b1079-120">Programming Tips</span></span>  
  
-   <span data-ttu-id="b1079-121">**Consumo de memória.**</span><span class="sxs-lookup"><span data-stu-id="b1079-121">**Memory Consumption.**</span></span> <span data-ttu-id="b1079-122">Assim como acontece com todos os tipos de dados compostos, você não pode calcular com segurança o consumo de memória total de uma estrutura somando as alocações de armazenamento nominais de seus membros.</span><span class="sxs-lookup"><span data-stu-id="b1079-122">As with all composite data types, you cannot safely calculate the total memory consumption of a structure by adding together the nominal storage allocations of its members.</span></span> <span data-ttu-id="b1079-123">Além disso, você não pode presumir com segurança que a ordem de armazenamento na memória é a mesma que sua ordem de declaração.</span><span class="sxs-lookup"><span data-stu-id="b1079-123">Furthermore, you cannot safely assume that the order of storage in memory is the same as your order of declaration.</span></span> <span data-ttu-id="b1079-124">Se você precisar controlar o layout de armazenamento de uma estrutura, você pode aplicar a <xref:System.Runtime.InteropServices.StructLayoutAttribute> de atributo para o `Structure` instrução.</span><span class="sxs-lookup"><span data-stu-id="b1079-124">If you need to control the storage layout of a structure, you can apply the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute to the `Structure` statement.</span></span>  
  
-   <span data-ttu-id="b1079-125">**Considerações de interoperabilidade.**</span><span class="sxs-lookup"><span data-stu-id="b1079-125">**Interop Considerations.**</span></span> <span data-ttu-id="b1079-126">Se você estiver fazendo interface com componentes não escritos para o .NET Framework, por exemplo objetos de automação ou COM, lembre-se de que os tipos definidos pelo usuário em outros ambientes não são compatíveis com o Visual Basic estruturam tipos.</span><span class="sxs-lookup"><span data-stu-id="b1079-126">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that user-defined types in other environments are not compatible with Visual Basic structure types.</span></span>  
  
-   <span data-ttu-id="b1079-127">**Ampliação.**</span><span class="sxs-lookup"><span data-stu-id="b1079-127">**Widening.**</span></span> <span data-ttu-id="b1079-128">Não há nenhuma conversão automática de ou para qualquer tipo de dados de estrutura.</span><span class="sxs-lookup"><span data-stu-id="b1079-128">There is no automatic conversion to or from any structure data type.</span></span> <span data-ttu-id="b1079-129">Você pode definir operadores de conversão em sua estrutura usando o [instrução Operator](../../../visual-basic/language-reference/statements/operator-statement.md), e você pode declarar cada operador de conversão para ser `Widening` ou `Narrowing`.</span><span class="sxs-lookup"><span data-stu-id="b1079-129">You can define conversion operators on your structure using the [Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md), and you can declare each conversion operator to be `Widening` or `Narrowing`.</span></span>  
  
-   <span data-ttu-id="b1079-130">**Caracteres de tipo.**</span><span class="sxs-lookup"><span data-stu-id="b1079-130">**Type Characters.**</span></span> <span data-ttu-id="b1079-131">Tipos de dados de estrutura não têm nenhum caractere de tipo literal ou um caractere de tipo identificador.</span><span class="sxs-lookup"><span data-stu-id="b1079-131">Structure data types have no literal type character or identifier type character.</span></span>  
  
-   <span data-ttu-id="b1079-132">**Tipo de estrutura.**</span><span class="sxs-lookup"><span data-stu-id="b1079-132">**Framework Type.**</span></span> <span data-ttu-id="b1079-133">Não há nenhum tipo correspondente no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b1079-133">There is no corresponding type in the .NET Framework.</span></span> <span data-ttu-id="b1079-134">Todas as estruturas herdam da classe do .NET Framework <xref:System.ValueType?displayProperty=nameWithType>, mas nenhuma estrutura individual corresponde ao <xref:System.ValueType?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b1079-134">All structures inherit from the .NET Framework class <xref:System.ValueType?displayProperty=nameWithType>, but no individual structure corresponds to <xref:System.ValueType?displayProperty=nameWithType>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b1079-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b1079-135">Example</span></span>  
 <span data-ttu-id="b1079-136">O paradigma a seguir mostra a estrutura da declaração de uma estrutura.</span><span class="sxs-lookup"><span data-stu-id="b1079-136">The following paradigm shows the outline of the declaration of a structure.</span></span>  
  
```  
[Public | Protected | Friend | Protected Friend | Private] Structure structname  
    {Dim | Public | Friend | Private} member1 As datatype1  
    ' ...  
    {Dim | Public | Friend | Private} memberN As datatypeN  
End Structure  
```  
  
## <a name="see-also"></a><span data-ttu-id="b1079-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b1079-137">See also</span></span>

- <xref:System.ValueType>
- <xref:System.Runtime.InteropServices.StructLayoutAttribute>
- [<span data-ttu-id="b1079-138">Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="b1079-138">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="b1079-139">Funções de Conversão do Tipo</span><span class="sxs-lookup"><span data-stu-id="b1079-139">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="b1079-140">Resumo da Conversão</span><span class="sxs-lookup"><span data-stu-id="b1079-140">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="b1079-141">Instrução Structure</span><span class="sxs-lookup"><span data-stu-id="b1079-141">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="b1079-142">Ampliação</span><span class="sxs-lookup"><span data-stu-id="b1079-142">Widening</span></span>](../../../visual-basic/language-reference/modifiers/widening.md)
- [<span data-ttu-id="b1079-143">Narrowing</span><span class="sxs-lookup"><span data-stu-id="b1079-143">Narrowing</span></span>](../../../visual-basic/language-reference/modifiers/narrowing.md)
- [<span data-ttu-id="b1079-144">Estruturas</span><span class="sxs-lookup"><span data-stu-id="b1079-144">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="b1079-145">Uso Eficiente de Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="b1079-145">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
