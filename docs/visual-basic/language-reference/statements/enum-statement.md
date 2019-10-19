---
title: Instrução Enum (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Enum
helpviewer_keywords:
- enumerated constants [Visual Basic]
- Enum statement [Visual Basic]
- Private keyword [Visual Basic], Enum statements
- Public keyword [Visual Basic], in Enum statement
- variables [Visual Basic], enumeration
- constants [Visual Basic], enumerated
ms.assetid: a45e51f1-65ff-48e1-bf32-79130f137377
ms.openlocfilehash: be1780b00b4d58964e1de5ec199cb80dc0f9dba5
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583402"
---
# <a name="enum-statement-visual-basic"></a><span data-ttu-id="cd7e3-102">Instrução Enum (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cd7e3-102">Enum Statement (Visual Basic)</span></span>

<span data-ttu-id="cd7e3-103">Declara uma enumeração e define os valores de seus membros.</span><span class="sxs-lookup"><span data-stu-id="cd7e3-103">Declares an enumeration and defines the values of its members.</span></span>

## <a name="syntax"></a><span data-ttu-id="cd7e3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cd7e3-104">Syntax</span></span>

```vb
[ <attributelist> ] [ accessmodifier ]  [ Shadows ]
Enum enumerationname [ As datatype ]
   memberlist
End Enum
```

## <a name="parts"></a><span data-ttu-id="cd7e3-105">Partes</span><span class="sxs-lookup"><span data-stu-id="cd7e3-105">Parts</span></span>

- `attributelist`

  <span data-ttu-id="cd7e3-106">Opcional.</span><span class="sxs-lookup"><span data-stu-id="cd7e3-106">Optional.</span></span> <span data-ttu-id="cd7e3-107">Lista de atributos que se aplicam a essa enumeração.</span><span class="sxs-lookup"><span data-stu-id="cd7e3-107">List of attributes that apply to this enumeration.</span></span> <span data-ttu-id="cd7e3-108">Você deve colocar a [lista de atributos](../../../visual-basic/language-reference/statements/attribute-list.md) entre colchetes angulares ("`<`" e "`>`").</span><span class="sxs-lookup"><span data-stu-id="cd7e3-108">You must enclose the [attribute list](../../../visual-basic/language-reference/statements/attribute-list.md) in angle brackets ("`<`" and "`>`").</span></span>

  <span data-ttu-id="cd7e3-109">O atributo <xref:System.FlagsAttribute> indica que o valor de uma instância da enumeração pode incluir vários membros de enumeração e que cada membro representa um campo de bits no valor de enumeração.</span><span class="sxs-lookup"><span data-stu-id="cd7e3-109">The <xref:System.FlagsAttribute> attribute indicates that the value of an instance of the enumeration can include multiple enumeration members, and that each member represents a bit field in the enumeration value.</span></span>

- `accessmodifier`

  <span data-ttu-id="cd7e3-110">Opcional.</span><span class="sxs-lookup"><span data-stu-id="cd7e3-110">Optional.</span></span> <span data-ttu-id="cd7e3-111">Especifica qual código pode acessar essa enumeração.</span><span class="sxs-lookup"><span data-stu-id="cd7e3-111">Specifies what code can access this enumeration.</span></span> <span data-ttu-id="cd7e3-112">Pode ser um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="cd7e3-112">Can be one of the following:</span></span>

  - [<span data-ttu-id="cd7e3-113">Público</span><span class="sxs-lookup"><span data-stu-id="cd7e3-113">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)

  - [<span data-ttu-id="cd7e3-114">Protegido</span><span class="sxs-lookup"><span data-stu-id="cd7e3-114">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)

  - [<span data-ttu-id="cd7e3-115">Friend</span><span class="sxs-lookup"><span data-stu-id="cd7e3-115">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)

  - [<span data-ttu-id="cd7e3-116">Privado</span><span class="sxs-lookup"><span data-stu-id="cd7e3-116">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)

  - [<span data-ttu-id="cd7e3-117">Amigo Protegido</span><span class="sxs-lookup"><span data-stu-id="cd7e3-117">Protected Friend</span></span>](../../language-reference/modifiers/protected-friend.md)

  - [<span data-ttu-id="cd7e3-118">Particular Protegido</span><span class="sxs-lookup"><span data-stu-id="cd7e3-118">Private Protected</span></span>](../../language-reference/modifiers/private-protected.md)

- `Shadows`

  <span data-ttu-id="cd7e3-119">Opcional.</span><span class="sxs-lookup"><span data-stu-id="cd7e3-119">Optional.</span></span> <span data-ttu-id="cd7e3-120">Especifica que essa enumeração redeclara e oculta um elemento de programação nomeado de forma idêntica, ou conjunto de elementos sobrecarregados, em uma classe base.</span><span class="sxs-lookup"><span data-stu-id="cd7e3-120">Specifies that this enumeration redeclares and hides an identically named programming element, or set of overloaded elements, in a base class.</span></span> <span data-ttu-id="cd7e3-121">Você pode especificar [sombras](../../../visual-basic/language-reference/modifiers/shadows.md) apenas na enumeração, não em nenhum de seus membros.</span><span class="sxs-lookup"><span data-stu-id="cd7e3-121">You can specify [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md) only on the enumeration itself, not on any of its members.</span></span>

- `enumerationname`

  <span data-ttu-id="cd7e3-122">Necessário.</span><span class="sxs-lookup"><span data-stu-id="cd7e3-122">Required.</span></span> <span data-ttu-id="cd7e3-123">Nome da enumeração.</span><span class="sxs-lookup"><span data-stu-id="cd7e3-123">Name of the enumeration.</span></span> <span data-ttu-id="cd7e3-124">Para obter informações sobre nomes válidos, consulte [nomes de elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="cd7e3-124">For information on valid names, see [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>

- `datatype`

  <span data-ttu-id="cd7e3-125">Opcional.</span><span class="sxs-lookup"><span data-stu-id="cd7e3-125">Optional.</span></span> <span data-ttu-id="cd7e3-126">Tipo de dados da enumeração e todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="cd7e3-126">Data type of the enumeration and all its members.</span></span>

- `memberlist`

  <span data-ttu-id="cd7e3-127">Necessário.</span><span class="sxs-lookup"><span data-stu-id="cd7e3-127">Required.</span></span> <span data-ttu-id="cd7e3-128">Lista de constantes de membro sendo declarada nesta instrução.</span><span class="sxs-lookup"><span data-stu-id="cd7e3-128">List of member constants being declared in this statement.</span></span> <span data-ttu-id="cd7e3-129">Vários membros aparecem em linhas de código-fonte individuais.</span><span class="sxs-lookup"><span data-stu-id="cd7e3-129">Multiple members appear on individual source code lines.</span></span>

  <span data-ttu-id="cd7e3-130">Cada `member` tem a seguinte sintaxe e partes: `[<attribute list>] member name [ = initializer ]`</span><span class="sxs-lookup"><span data-stu-id="cd7e3-130">Each `member` has the following syntax and parts: `[<attribute list>] member name [ = initializer ]`</span></span>

  |<span data-ttu-id="cd7e3-131">Parte</span><span class="sxs-lookup"><span data-stu-id="cd7e3-131">Part</span></span>|<span data-ttu-id="cd7e3-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="cd7e3-132">Description</span></span>|
  |---|---|
  |`membername`|<span data-ttu-id="cd7e3-133">Necessário.</span><span class="sxs-lookup"><span data-stu-id="cd7e3-133">Required.</span></span> <span data-ttu-id="cd7e3-134">Nome deste membro.</span><span class="sxs-lookup"><span data-stu-id="cd7e3-134">Name of this member.</span></span>|
  |`initializer`|<span data-ttu-id="cd7e3-135">Opcional.</span><span class="sxs-lookup"><span data-stu-id="cd7e3-135">Optional.</span></span> <span data-ttu-id="cd7e3-136">Expressão que é avaliada em tempo de compilação e atribuída a este membro.</span><span class="sxs-lookup"><span data-stu-id="cd7e3-136">Expression that is evaluated at compile time and assigned to this member.</span></span>|

- <span data-ttu-id="cd7e3-137">`End` `Enum`</span><span class="sxs-lookup"><span data-stu-id="cd7e3-137">`End` `Enum`</span></span>

  <span data-ttu-id="cd7e3-138">Encerra o bloco de `Enum`.</span><span class="sxs-lookup"><span data-stu-id="cd7e3-138">Terminates the `Enum` block.</span></span>

## <a name="remarks"></a><span data-ttu-id="cd7e3-139">Comentários</span><span class="sxs-lookup"><span data-stu-id="cd7e3-139">Remarks</span></span>

<span data-ttu-id="cd7e3-140">Se você tiver um conjunto de valores inalteráveis logicamente relacionados entre si, você poderá defini-los juntos em uma enumeração.</span><span class="sxs-lookup"><span data-stu-id="cd7e3-140">If you have a set of unchanging values that are logically related to each other, you can define them together in an enumeration.</span></span> <span data-ttu-id="cd7e3-141">Isso fornece nomes significativos para a enumeração e seus membros, que são mais fáceis de lembrar do que seus valores.</span><span class="sxs-lookup"><span data-stu-id="cd7e3-141">This provides meaningful names for the enumeration and its members, which are easier to remember than their values.</span></span> <span data-ttu-id="cd7e3-142">Você pode usar os membros de enumeração em muitos locais em seu código.</span><span class="sxs-lookup"><span data-stu-id="cd7e3-142">You can then use the enumeration members in many places in your code.</span></span>

<span data-ttu-id="cd7e3-143">Os benefícios do uso de enumerações incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="cd7e3-143">The benefits of using enumerations include the following:</span></span>

- <span data-ttu-id="cd7e3-144">Reduz os erros causados pela transposição ou números incorretas de digitação.</span><span class="sxs-lookup"><span data-stu-id="cd7e3-144">Reduces errors caused by transposing or mistyping numbers.</span></span>

- <span data-ttu-id="cd7e3-145">Torna mais fácil alterar valores no futuro.</span><span class="sxs-lookup"><span data-stu-id="cd7e3-145">Makes it easy to change values in the future.</span></span>

- <span data-ttu-id="cd7e3-146">Torna o código mais fácil de ler, o que significa que é menos provável que os erros sejam introduzidos.</span><span class="sxs-lookup"><span data-stu-id="cd7e3-146">Makes code easier to read, which means it is less likely that errors will be introduced.</span></span>

- <span data-ttu-id="cd7e3-147">Garante a compatibilidade com o futuro.</span><span class="sxs-lookup"><span data-stu-id="cd7e3-147">Ensures forward compatibility.</span></span> <span data-ttu-id="cd7e3-148">Se você usar enumerações, o código terá menos probabilidade de falhar se, em outras pessoas, alterar os valores correspondentes aos nomes dos membros.</span><span class="sxs-lookup"><span data-stu-id="cd7e3-148">If you use enumerations, your code is less likely to fail if in the future someone changes the values corresponding to the member names.</span></span>

<span data-ttu-id="cd7e3-149">Uma enumeração tem um nome, um tipo de dados subjacente e um conjunto de membros.</span><span class="sxs-lookup"><span data-stu-id="cd7e3-149">An enumeration has a name, an underlying data type, and a set of members.</span></span> <span data-ttu-id="cd7e3-150">Cada membro representa uma constante.</span><span class="sxs-lookup"><span data-stu-id="cd7e3-150">Each member represents a constant.</span></span>

<span data-ttu-id="cd7e3-151">Uma enumeração declarada na classe, estrutura, módulo ou nível de interface, fora de qualquer procedimento, é uma *enumeração de membro*.</span><span class="sxs-lookup"><span data-stu-id="cd7e3-151">An enumeration declared at class, structure, module, or interface level, outside any procedure, is a *member enumeration*.</span></span> <span data-ttu-id="cd7e3-152">É um membro da classe, da estrutura, do módulo ou da interface que o declara.</span><span class="sxs-lookup"><span data-stu-id="cd7e3-152">It is a member of the class, structure, module, or interface that declares it.</span></span>

<span data-ttu-id="cd7e3-153">As enumerações de membro podem ser acessadas de qualquer lugar dentro de sua classe, estrutura, módulo ou interface.</span><span class="sxs-lookup"><span data-stu-id="cd7e3-153">Member enumerations can be accessed from anywhere within their class, structure, module, or interface.</span></span> <span data-ttu-id="cd7e3-154">O código fora de uma classe, estrutura ou módulo deve qualificar o nome de uma enumeração de membro com o nome dessa classe, estrutura ou módulo.</span><span class="sxs-lookup"><span data-stu-id="cd7e3-154">Code outside a class, structure, or module must qualify a member enumeration's name with the name of that class, structure, or module.</span></span> <span data-ttu-id="cd7e3-155">Você pode evitar a necessidade de usar nomes totalmente qualificados adicionando uma instrução [Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) ao arquivo de origem.</span><span class="sxs-lookup"><span data-stu-id="cd7e3-155">You can avoid the need to use fully qualified names by adding an [Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) statement to the source file.</span></span>

<span data-ttu-id="cd7e3-156">Uma enumeração declarada no nível de namespace, fora de qualquer classe, estrutura, módulo ou interface, é um membro do namespace no qual ela aparece.</span><span class="sxs-lookup"><span data-stu-id="cd7e3-156">An enumeration declared at namespace level, outside any class, structure, module, or interface, is a member of the namespace in which it appears.</span></span>

<span data-ttu-id="cd7e3-157">O *contexto de declaração* para uma enumeração deve ser um arquivo de origem, namespace, classe, estrutura, módulo ou interface, e não pode ser um procedimento.</span><span class="sxs-lookup"><span data-stu-id="cd7e3-157">The *declaration context* for an enumeration must be a source file, namespace, class, structure, module, or interface, and cannot be a procedure.</span></span> <span data-ttu-id="cd7e3-158">Para obter mais informações, consulte [Contextos de declaração e níveis de acesso padrão](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="cd7e3-158">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>

<span data-ttu-id="cd7e3-159">Você pode aplicar atributos a uma enumeração como um todo, mas não a seus membros individualmente.</span><span class="sxs-lookup"><span data-stu-id="cd7e3-159">You can apply attributes to an enumeration as a whole, but not to its members individually.</span></span> <span data-ttu-id="cd7e3-160">Um atributo contribui com informações para os metadados do assembly.</span><span class="sxs-lookup"><span data-stu-id="cd7e3-160">An attribute contributes information to the assembly's metadata.</span></span>

## <a name="data-type"></a><span data-ttu-id="cd7e3-161">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="cd7e3-161">Data Type</span></span>

<span data-ttu-id="cd7e3-162">A instrução `Enum` pode declarar o tipo de dados de uma enumeração.</span><span class="sxs-lookup"><span data-stu-id="cd7e3-162">The `Enum` statement can declare the data type of an enumeration.</span></span> <span data-ttu-id="cd7e3-163">Cada membro usa o tipo de dados da enumeração.</span><span class="sxs-lookup"><span data-stu-id="cd7e3-163">Each member takes the enumeration's data type.</span></span> <span data-ttu-id="cd7e3-164">Você pode especificar `Byte`, `Integer`, `Long`, `SByte`, `Short`, `UInteger`, `ULong` ou `UShort`.</span><span class="sxs-lookup"><span data-stu-id="cd7e3-164">You can specify `Byte`, `Integer`, `Long`, `SByte`, `Short`, `UInteger`, `ULong`, or `UShort`.</span></span>

<span data-ttu-id="cd7e3-165">Se você não especificar `datatype` para a enumeração, cada membro usará o tipo de dados de seu `initializer`.</span><span class="sxs-lookup"><span data-stu-id="cd7e3-165">If you do not specify `datatype` for the enumeration, each member takes the data type of its `initializer`.</span></span> <span data-ttu-id="cd7e3-166">Se você especificar `datatype` e `initializer`, o tipo de dados de `initializer` deverá ser conversível para `datatype`.</span><span class="sxs-lookup"><span data-stu-id="cd7e3-166">If you specify both `datatype` and `initializer`, the data type of `initializer` must be convertible to `datatype`.</span></span> <span data-ttu-id="cd7e3-167">Se nem `datatype` nem `initializer` estiverem presentes, o tipo de dados padrão será `Integer`.</span><span class="sxs-lookup"><span data-stu-id="cd7e3-167">If neither `datatype` nor `initializer` is present, the data type defaults to `Integer`.</span></span>

## <a name="initializing-members"></a><span data-ttu-id="cd7e3-168">Inicializando Membros</span><span class="sxs-lookup"><span data-stu-id="cd7e3-168">Initializing Members</span></span>

<span data-ttu-id="cd7e3-169">A instrução `Enum` pode inicializar o conteúdo dos membros selecionados em `memberlist`.</span><span class="sxs-lookup"><span data-stu-id="cd7e3-169">The `Enum` statement can initialize the contents of selected members in `memberlist`.</span></span> <span data-ttu-id="cd7e3-170">Você usa `initializer` para fornecer uma expressão a ser atribuída ao membro.</span><span class="sxs-lookup"><span data-stu-id="cd7e3-170">You use `initializer` to supply an expression to be assigned to the member.</span></span>

<span data-ttu-id="cd7e3-171">Se você não especificar `initializer` para um membro, Visual Basic o inicializará como zero (se for o primeiro `member` no `memberlist`) ou com um valor maior que o de `member` imediatamente anterior.</span><span class="sxs-lookup"><span data-stu-id="cd7e3-171">If you do not specify `initializer` for a member, Visual Basic initializes it either to zero (if it is the first `member` in `memberlist`), or to a value greater by one than that of the immediately preceding `member`.</span></span>

<span data-ttu-id="cd7e3-172">A expressão fornecida em cada `initializer` pode ser qualquer combinação de literais, outras constantes que já estão definidas e membros de enumeração que já estão definidos, incluindo um membro anterior dessa enumeração.</span><span class="sxs-lookup"><span data-stu-id="cd7e3-172">The expression supplied in each `initializer` can be any combination of literals, other constants that are already defined, and enumeration members that are already defined, including a previous member of this enumeration.</span></span> <span data-ttu-id="cd7e3-173">Você pode usar operadores aritméticos e lógicos para combinar esses elementos.</span><span class="sxs-lookup"><span data-stu-id="cd7e3-173">You can use arithmetic and logical operators to combine such elements.</span></span>

<span data-ttu-id="cd7e3-174">Você não pode usar variáveis ou funções no `initializer`.</span><span class="sxs-lookup"><span data-stu-id="cd7e3-174">You cannot use variables or functions in `initializer`.</span></span> <span data-ttu-id="cd7e3-175">No entanto, você pode usar palavras-chave de conversão, como `CByte` e `CShort`.</span><span class="sxs-lookup"><span data-stu-id="cd7e3-175">However, you can use conversion keywords such as `CByte` and `CShort`.</span></span> <span data-ttu-id="cd7e3-176">Você também pode usar `AscW` se chamá-lo com uma constante `String` ou `Char` argumento, pois isso pode ser avaliado no momento da compilação.</span><span class="sxs-lookup"><span data-stu-id="cd7e3-176">You can also use `AscW` if you call it with a constant `String` or `Char` argument, since that can be evaluated at compile time.</span></span>

<span data-ttu-id="cd7e3-177">Enumerações não podem ter valores de ponto flutuante.</span><span class="sxs-lookup"><span data-stu-id="cd7e3-177">Enumerations cannot have floating-point values.</span></span> <span data-ttu-id="cd7e3-178">Se um membro recebe um valor de ponto flutuante e `Option Strict` é definido como on, ocorre um erro do compilador.</span><span class="sxs-lookup"><span data-stu-id="cd7e3-178">If a member is assigned a floating-point value and `Option Strict` is set to on, a compiler error occurs.</span></span> <span data-ttu-id="cd7e3-179">Se `Option Strict` for off, o valor será convertido automaticamente para o tipo de `Enum`.</span><span class="sxs-lookup"><span data-stu-id="cd7e3-179">If `Option Strict` is off, the value is automatically converted to the `Enum` type.</span></span>

<span data-ttu-id="cd7e3-180">Se o valor de um membro exceder o intervalo permitido para o tipo de dados subjacente, ou se você inicializar qualquer membro para o valor máximo permitido pelo tipo de dados subjacente, o compilador relatará um erro.</span><span class="sxs-lookup"><span data-stu-id="cd7e3-180">If the value of a member exceeds the allowable range for the underlying data type, or if you initialize any member to the maximum value allowed by the underlying data type, the compiler reports an error.</span></span>

## <a name="modifiers"></a><span data-ttu-id="cd7e3-181">Modificadores</span><span class="sxs-lookup"><span data-stu-id="cd7e3-181">Modifiers</span></span>

<span data-ttu-id="cd7e3-182">Enumerações de classe, estrutura, módulo e membro de interface padrão para acesso público.</span><span class="sxs-lookup"><span data-stu-id="cd7e3-182">Class, structure, module, and interface member enumerations default to public access.</span></span> <span data-ttu-id="cd7e3-183">Você pode ajustar seus níveis de acesso com os modificadores de acesso.</span><span class="sxs-lookup"><span data-stu-id="cd7e3-183">You can adjust their access levels with the access modifiers.</span></span> <span data-ttu-id="cd7e3-184">Enumerações de membro de namespace padrão para Friend Access.</span><span class="sxs-lookup"><span data-stu-id="cd7e3-184">Namespace member enumerations default to friend access.</span></span> <span data-ttu-id="cd7e3-185">Você pode ajustar seus níveis de acesso para público, mas não para privado ou protegido.</span><span class="sxs-lookup"><span data-stu-id="cd7e3-185">You can adjust their access levels to public, but not to private or protected.</span></span> <span data-ttu-id="cd7e3-186">Para obter mais informações, consulte [níveis de acesso em Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="cd7e3-186">For more information, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>

<span data-ttu-id="cd7e3-187">Todos os membros de enumeração têm acesso público e você não pode usar nenhum modificador de acesso neles.</span><span class="sxs-lookup"><span data-stu-id="cd7e3-187">All enumeration members have public access, and you cannot use any access modifiers on them.</span></span> <span data-ttu-id="cd7e3-188">No entanto, se a enumeração tiver um nível de acesso mais restrito, o nível de acesso de enumeração especificado terá precedência.</span><span class="sxs-lookup"><span data-stu-id="cd7e3-188">However, if the enumeration itself has a more restricted access level, the specified enumeration access level takes precedence.</span></span>

<span data-ttu-id="cd7e3-189">Por padrão, todas as enumerações são tipos e seus campos são constantes.</span><span class="sxs-lookup"><span data-stu-id="cd7e3-189">By default, all enumerations are types and their fields are constants.</span></span> <span data-ttu-id="cd7e3-190">Portanto, as palavras-chave `Shared`, `Static` e `ReadOnly` não podem ser usadas ao declarar uma enumeração ou seus membros.</span><span class="sxs-lookup"><span data-stu-id="cd7e3-190">Therefore the `Shared`, `Static`, and `ReadOnly` keywords cannot be used when declaring an enumeration or its members.</span></span>

## <a name="assigning-multiple-values"></a><span data-ttu-id="cd7e3-191">Atribuindo vários valores</span><span class="sxs-lookup"><span data-stu-id="cd7e3-191">Assigning Multiple Values</span></span>

<span data-ttu-id="cd7e3-192">Enumerações normalmente representam valores mutuamente exclusivos.</span><span class="sxs-lookup"><span data-stu-id="cd7e3-192">Enumerations typically represent mutually exclusive values.</span></span> <span data-ttu-id="cd7e3-193">Ao incluir o atributo <xref:System.FlagsAttribute> na declaração `Enum`, você pode atribuir vários valores a uma instância da enumeração.</span><span class="sxs-lookup"><span data-stu-id="cd7e3-193">By including the <xref:System.FlagsAttribute> attribute in the `Enum` declaration, you can instead assign multiple values to an instance of the enumeration.</span></span> <span data-ttu-id="cd7e3-194">O atributo <xref:System.FlagsAttribute> especifica que a enumeração seja tratada como um campo de bits, ou seja, um conjunto de sinalizadores.</span><span class="sxs-lookup"><span data-stu-id="cd7e3-194">The <xref:System.FlagsAttribute> attribute specifies that the enumeration be treated as a bit field, that is, a set of flags.</span></span> <span data-ttu-id="cd7e3-195">Elas são chamadas de enumerações *bit* -ais.</span><span class="sxs-lookup"><span data-stu-id="cd7e3-195">These are called *bitwise* enumerations.</span></span>

<span data-ttu-id="cd7e3-196">Ao declarar uma enumeração usando o atributo <xref:System.FlagsAttribute>, recomendamos que você use potências de 2, ou seja, 1, 2, 4, 8, 16 e assim por diante, para os valores.</span><span class="sxs-lookup"><span data-stu-id="cd7e3-196">When you declare an enumeration by using the <xref:System.FlagsAttribute> attribute, we recommend that you use powers of 2, that is, 1, 2, 4, 8, 16, and so on, for the values.</span></span> <span data-ttu-id="cd7e3-197">Também recomendamos que "None" seja o nome de um membro cujo valor é 0.</span><span class="sxs-lookup"><span data-stu-id="cd7e3-197">We also recommend that "None" be the name of a member whose value is 0.</span></span> <span data-ttu-id="cd7e3-198">Para obter diretrizes adicionais, consulte <xref:System.FlagsAttribute> e <xref:System.Enum>.</span><span class="sxs-lookup"><span data-stu-id="cd7e3-198">For additional guidelines, see <xref:System.FlagsAttribute> and <xref:System.Enum>.</span></span>

## <a name="example"></a><span data-ttu-id="cd7e3-199">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cd7e3-199">Example</span></span>

<span data-ttu-id="cd7e3-200">O exemplo a seguir mostra como usar a instrução `Enum`.</span><span class="sxs-lookup"><span data-stu-id="cd7e3-200">The following example shows how to use the `Enum` statement.</span></span> <span data-ttu-id="cd7e3-201">Observe que o membro é conhecido como `EggSizeEnum.Medium`, e não como `Medium`.</span><span class="sxs-lookup"><span data-stu-id="cd7e3-201">Note that the member is referred to as `EggSizeEnum.Medium`, and not as `Medium`.</span></span>

[!code-vb[VbEnumsTask#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#41)]

## <a name="example"></a><span data-ttu-id="cd7e3-202">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cd7e3-202">Example</span></span>

<span data-ttu-id="cd7e3-203">O método no exemplo a seguir está fora da classe `Egg`.</span><span class="sxs-lookup"><span data-stu-id="cd7e3-203">The method in the following example is outside the `Egg` class.</span></span> <span data-ttu-id="cd7e3-204">Portanto, `EggSizeEnum` é totalmente qualificado como `Egg.EggSizeEnum`.</span><span class="sxs-lookup"><span data-stu-id="cd7e3-204">Therefore, `EggSizeEnum` is fully qualified as `Egg.EggSizeEnum`.</span></span>

[!code-vb[VbEnumsTask#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#42)]

## <a name="example"></a><span data-ttu-id="cd7e3-205">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cd7e3-205">Example</span></span>

<span data-ttu-id="cd7e3-206">O exemplo a seguir usa a instrução `Enum` para definir um conjunto relacionado de valores constantes nomeados.</span><span class="sxs-lookup"><span data-stu-id="cd7e3-206">The following example uses the `Enum` statement to define a related set of named constant values.</span></span> <span data-ttu-id="cd7e3-207">Nesse caso, os valores são cores que você pode optar por criar formulários de entrada de dados para um banco de dado.</span><span class="sxs-lookup"><span data-stu-id="cd7e3-207">In this case, the values are colors you might choose to design data entry forms for a database.</span></span>

[!code-vb[VbEnumsTask#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#30)]

## <a name="example"></a><span data-ttu-id="cd7e3-208">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cd7e3-208">Example</span></span>

<span data-ttu-id="cd7e3-209">O exemplo a seguir mostra valores que incluem números positivos e negativos.</span><span class="sxs-lookup"><span data-stu-id="cd7e3-209">The following example shows values that include both positive and negative numbers.</span></span>

[!code-vb[VbEnumsTask#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#31)]

## <a name="example"></a><span data-ttu-id="cd7e3-210">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cd7e3-210">Example</span></span>

<span data-ttu-id="cd7e3-211">No exemplo a seguir, uma cláusula `As` é usada para especificar o `datatype` de uma enumeração.</span><span class="sxs-lookup"><span data-stu-id="cd7e3-211">In the following example, an `As` clause is used to specify the `datatype` of an enumeration.</span></span>

[!code-vb[VbEnumsTask#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#6)]

## <a name="example"></a><span data-ttu-id="cd7e3-212">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cd7e3-212">Example</span></span>

<span data-ttu-id="cd7e3-213">O exemplo a seguir mostra como usar uma enumeração de bits.</span><span class="sxs-lookup"><span data-stu-id="cd7e3-213">The following example shows how to use a bitwise enumeration.</span></span> <span data-ttu-id="cd7e3-214">Vários valores podem ser atribuídos a uma instância de uma enumeração bit a bit.</span><span class="sxs-lookup"><span data-stu-id="cd7e3-214">Multiple values can be assigned to an instance of a bitwise enumeration.</span></span> <span data-ttu-id="cd7e3-215">A declaração de `Enum` inclui o atributo <xref:System.FlagsAttribute>, que indica que a enumeração pode ser tratada como um conjunto de sinalizadores.</span><span class="sxs-lookup"><span data-stu-id="cd7e3-215">The `Enum` declaration includes the <xref:System.FlagsAttribute> attribute, which indicates that the enumeration can be treated as a set of flags.</span></span>

[!code-vb[VbEnumsTask#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#61)]

## <a name="example"></a><span data-ttu-id="cd7e3-216">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cd7e3-216">Example</span></span>

<span data-ttu-id="cd7e3-217">O exemplo a seguir itera por meio de uma enumeração.</span><span class="sxs-lookup"><span data-stu-id="cd7e3-217">The following example iterates through an enumeration.</span></span> <span data-ttu-id="cd7e3-218">Ele usa o método <xref:System.Enum.GetNames%2A> para recuperar uma matriz de nomes de membro da enumeração e <xref:System.Enum.GetValues%2A> recuperar uma matriz de valores de membro.</span><span class="sxs-lookup"><span data-stu-id="cd7e3-218">It uses the <xref:System.Enum.GetNames%2A> method to retrieve an array of member names from the enumeration, and <xref:System.Enum.GetValues%2A> to retrieve an array of member values.</span></span>

[!code-vb[VbEnumsTask#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#51)]

## <a name="see-also"></a><span data-ttu-id="cd7e3-219">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cd7e3-219">See also</span></span>

- <xref:System.Enum>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- [<span data-ttu-id="cd7e3-220">Instrução Const</span><span class="sxs-lookup"><span data-stu-id="cd7e3-220">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)
- [<span data-ttu-id="cd7e3-221">Instrução Dim</span><span class="sxs-lookup"><span data-stu-id="cd7e3-221">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)
- [<span data-ttu-id="cd7e3-222">Conversões Implícitas e Explícitas</span><span class="sxs-lookup"><span data-stu-id="cd7e3-222">Implicit and Explicit Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="cd7e3-223">Funções de Conversão do Tipo</span><span class="sxs-lookup"><span data-stu-id="cd7e3-223">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="cd7e3-224">Constantes e Enumerações</span><span class="sxs-lookup"><span data-stu-id="cd7e3-224">Constants and Enumerations</span></span>](../../../visual-basic/language-reference/constants-and-enumerations.md)
