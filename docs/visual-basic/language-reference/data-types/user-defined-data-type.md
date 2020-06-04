---
title: Tipo de dados definido pelo usuário
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
ms.openlocfilehash: fbd9536a54d7fb471d6cb2e130b14a84e40a4940
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415486"
---
# <a name="user-defined-data-type"></a><span data-ttu-id="832e9-102">Tipo de dados definido pelo usuário</span><span class="sxs-lookup"><span data-stu-id="832e9-102">User-Defined Data Type</span></span>

<span data-ttu-id="832e9-103">Contém dados em um formato que você define.</span><span class="sxs-lookup"><span data-stu-id="832e9-103">Holds data in a format you define.</span></span> <span data-ttu-id="832e9-104">A `Structure` instrução define o formato.</span><span class="sxs-lookup"><span data-stu-id="832e9-104">The `Structure` statement defines the format.</span></span>

<span data-ttu-id="832e9-105">As versões anteriores do Visual Basic dão suporte ao tipo definido pelo usuário (UDT).</span><span class="sxs-lookup"><span data-stu-id="832e9-105">Previous versions of Visual Basic support the user-defined type (UDT).</span></span> <span data-ttu-id="832e9-106">A versão atual expande o UDT para uma *estrutura*.</span><span class="sxs-lookup"><span data-stu-id="832e9-106">The current version expands the UDT to a *structure*.</span></span> <span data-ttu-id="832e9-107">Uma estrutura é uma concatenação de um ou mais *Membros* de vários tipos de dados.</span><span class="sxs-lookup"><span data-stu-id="832e9-107">A structure is a concatenation of one or more *members* of various data types.</span></span> <span data-ttu-id="832e9-108">Visual Basic trata uma estrutura como uma única unidade, embora você também possa acessar seus membros individualmente.</span><span class="sxs-lookup"><span data-stu-id="832e9-108">Visual Basic treats a structure as a single unit, although you can also access its members individually.</span></span>

## <a name="remarks"></a><span data-ttu-id="832e9-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="832e9-109">Remarks</span></span>

<span data-ttu-id="832e9-110">Defina e use um tipo de dados de estrutura quando for necessário combinar vários tipos de dados em uma única unidade ou quando nenhum dos tipos de dados elementares atender às suas necessidades.</span><span class="sxs-lookup"><span data-stu-id="832e9-110">Define and use a structure data type when you need to combine various data types into a single unit, or when none of the elementary data types serve your needs.</span></span>

<span data-ttu-id="832e9-111">O valor padrão de um tipo de dados de estrutura consiste na combinação dos valores padrão de cada um de seus membros.</span><span class="sxs-lookup"><span data-stu-id="832e9-111">The default value of a structure data type consists of the combination of the default values of each of its members.</span></span>

## <a name="declaration-format"></a><span data-ttu-id="832e9-112">Formato de declaração</span><span class="sxs-lookup"><span data-stu-id="832e9-112">Declaration Format</span></span>

<span data-ttu-id="832e9-113">Uma declaração de estrutura começa com a [instrução Structure](../statements/structure-statement.md) e termina com a `End Structure` instrução.</span><span class="sxs-lookup"><span data-stu-id="832e9-113">A structure declaration starts with the [Structure Statement](../statements/structure-statement.md) and ends with the `End Structure` statement.</span></span> <span data-ttu-id="832e9-114">A `Structure` instrução fornece o nome da estrutura, que também é o identificador do tipo de dados que a estrutura está definindo.</span><span class="sxs-lookup"><span data-stu-id="832e9-114">The `Structure` statement supplies the name of the structure, which is also the identifier of the data type the structure is defining.</span></span> <span data-ttu-id="832e9-115">Outras partes do código podem usar esse identificador para declarar variáveis, parâmetros e valores de retorno de função para serem do tipo de dados dessa estrutura.</span><span class="sxs-lookup"><span data-stu-id="832e9-115">Other parts of the code can use this identifier to declare variables, parameters, and function return values to be of this structure's data type.</span></span>

<span data-ttu-id="832e9-116">As declarações entre as `Structure` `End Structure` instruções e definem os membros da estrutura.</span><span class="sxs-lookup"><span data-stu-id="832e9-116">The declarations between the `Structure` and `End Structure` statements define the members of the structure.</span></span>

## <a name="member-access-levels"></a><span data-ttu-id="832e9-117">Níveis de acesso de membro</span><span class="sxs-lookup"><span data-stu-id="832e9-117">Member Access Levels</span></span>

<span data-ttu-id="832e9-118">Você deve declarar todos os membros usando uma [instrução Dim](../statements/dim-statement.md) ou uma instrução que especifique o nível de acesso, como [Public](../modifiers/public.md), [Friend](../modifiers/friend.md)ou [Private](../modifiers/private.md).</span><span class="sxs-lookup"><span data-stu-id="832e9-118">You must declare every member using a [Dim Statement](../statements/dim-statement.md) or a statement that specifies access level, such as [Public](../modifiers/public.md), [Friend](../modifiers/friend.md), or [Private](../modifiers/private.md).</span></span> <span data-ttu-id="832e9-119">Se você usar uma `Dim` instrução, o nível de acesso padrão será público.</span><span class="sxs-lookup"><span data-stu-id="832e9-119">If you use a `Dim` statement, the access level defaults to public.</span></span>

## <a name="programming-tips"></a><span data-ttu-id="832e9-120">Dicas de programação</span><span class="sxs-lookup"><span data-stu-id="832e9-120">Programming Tips</span></span>

- <span data-ttu-id="832e9-121">**Consumo de memória.**</span><span class="sxs-lookup"><span data-stu-id="832e9-121">**Memory Consumption.**</span></span> <span data-ttu-id="832e9-122">Assim como acontece com todos os tipos de dados compostos, você não pode calcular com segurança o consumo total de memória de uma estrutura adicionando as alocações de armazenamento nominal de seus membros.</span><span class="sxs-lookup"><span data-stu-id="832e9-122">As with all composite data types, you cannot safely calculate the total memory consumption of a structure by adding together the nominal storage allocations of its members.</span></span> <span data-ttu-id="832e9-123">Além disso, você não pode supor com segurança que a ordem de armazenamento na memória é igual à sua ordem de declaração.</span><span class="sxs-lookup"><span data-stu-id="832e9-123">Furthermore, you cannot safely assume that the order of storage in memory is the same as your order of declaration.</span></span> <span data-ttu-id="832e9-124">Se você precisar controlar o layout de armazenamento de uma estrutura, poderá aplicar o <xref:System.Runtime.InteropServices.StructLayoutAttribute> atributo à `Structure` instrução.</span><span class="sxs-lookup"><span data-stu-id="832e9-124">If you need to control the storage layout of a structure, you can apply the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute to the `Structure` statement.</span></span>

- <span data-ttu-id="832e9-125">**Considerações sobre interoperabilidade.**</span><span class="sxs-lookup"><span data-stu-id="832e9-125">**Interop Considerations.**</span></span> <span data-ttu-id="832e9-126">Se você estiver fazendo a interface com componentes não escritos para o .NET Framework, por exemplo, automação ou objetos COM, tenha em mente que os tipos definidos pelo usuário em outros ambientes não são compatíveis com Visual Basic tipos de estrutura.</span><span class="sxs-lookup"><span data-stu-id="832e9-126">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that user-defined types in other environments are not compatible with Visual Basic structure types.</span></span>

- <span data-ttu-id="832e9-127">**Ampliação.**</span><span class="sxs-lookup"><span data-stu-id="832e9-127">**Widening.**</span></span> <span data-ttu-id="832e9-128">Não há conversão automática de ou para nenhum tipo de dados de estrutura.</span><span class="sxs-lookup"><span data-stu-id="832e9-128">There is no automatic conversion to or from any structure data type.</span></span> <span data-ttu-id="832e9-129">Você pode definir operadores de conversão em sua estrutura usando a [instrução Operator](../statements/operator-statement.md)e pode declarar cada operador de conversão como `Widening` ou `Narrowing` .</span><span class="sxs-lookup"><span data-stu-id="832e9-129">You can define conversion operators on your structure using the [Operator Statement](../statements/operator-statement.md), and you can declare each conversion operator to be `Widening` or `Narrowing`.</span></span>

- <span data-ttu-id="832e9-130">**Digite os caracteres.**</span><span class="sxs-lookup"><span data-stu-id="832e9-130">**Type Characters.**</span></span> <span data-ttu-id="832e9-131">Os tipos de dados de estrutura não têm nenhum caractere de tipo literal ou caractere de tipo de identificador.</span><span class="sxs-lookup"><span data-stu-id="832e9-131">Structure data types have no literal type character or identifier type character.</span></span>

- <span data-ttu-id="832e9-132">**Tipo de estrutura.**</span><span class="sxs-lookup"><span data-stu-id="832e9-132">**Framework Type.**</span></span> <span data-ttu-id="832e9-133">Não há nenhum tipo correspondente no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="832e9-133">There is no corresponding type in the .NET Framework.</span></span> <span data-ttu-id="832e9-134">Todas as estruturas herdam da classe .NET Framework <xref:System.ValueType?displayProperty=nameWithType> , mas nenhuma estrutura individual corresponde a <xref:System.ValueType?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="832e9-134">All structures inherit from the .NET Framework class <xref:System.ValueType?displayProperty=nameWithType>, but no individual structure corresponds to <xref:System.ValueType?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="832e9-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="832e9-135">Example</span></span>

<span data-ttu-id="832e9-136">O paradigma a seguir mostra o contorno da declaração de uma estrutura.</span><span class="sxs-lookup"><span data-stu-id="832e9-136">The following paradigm shows the outline of the declaration of a structure.</span></span>

```vb
[Public | Protected | Friend | Protected Friend | Private] Structure structname
    {Dim | Public | Friend | Private} member1 As datatype1
    ' ...
    {Dim | Public | Friend | Private} memberN As datatypeN
End Structure
```

## <a name="see-also"></a><span data-ttu-id="832e9-137">Confira também</span><span class="sxs-lookup"><span data-stu-id="832e9-137">See also</span></span>

- <xref:System.ValueType>
- <xref:System.Runtime.InteropServices.StructLayoutAttribute>
- [<span data-ttu-id="832e9-138">Tipos de dados</span><span class="sxs-lookup"><span data-stu-id="832e9-138">Data Types</span></span>](index.md)
- [<span data-ttu-id="832e9-139">Funções de conversão do tipo</span><span class="sxs-lookup"><span data-stu-id="832e9-139">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="832e9-140">Resumo da Conversão</span><span class="sxs-lookup"><span data-stu-id="832e9-140">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="832e9-141">Instrução Structure</span><span class="sxs-lookup"><span data-stu-id="832e9-141">Structure Statement</span></span>](../statements/structure-statement.md)
- [<span data-ttu-id="832e9-142">Widening</span><span class="sxs-lookup"><span data-stu-id="832e9-142">Widening</span></span>](../modifiers/widening.md)
- [<span data-ttu-id="832e9-143">Narrowing</span><span class="sxs-lookup"><span data-stu-id="832e9-143">Narrowing</span></span>](../modifiers/narrowing.md)
- [<span data-ttu-id="832e9-144">Estruturas</span><span class="sxs-lookup"><span data-stu-id="832e9-144">Structures</span></span>](../../programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="832e9-145">Uso eficiente de tipos de dados</span><span class="sxs-lookup"><span data-stu-id="832e9-145">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
