---
title: Instrução Enum (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
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
caps.latest.revision: 44
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7a8244318e0be8e50f3384b56cf63e59182b6cda
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="enum-statement-visual-basic"></a><span data-ttu-id="bc779-102">Instrução Enum (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bc779-102">Enum Statement (Visual Basic)</span></span>
<span data-ttu-id="bc779-103">Declara uma enumeração e define os valores de seus membros.</span><span class="sxs-lookup"><span data-stu-id="bc779-103">Declares an enumeration and defines the values of its members.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc779-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bc779-104">Syntax</span></span>  
  
```  
[ <attributelist> ] [ accessmodifier ]  [ Shadows ]   
Enum enumerationname [ As datatype ]   
   memberlist  
End Enum  
```  
  
## <a name="parts"></a><span data-ttu-id="bc779-105">Partes</span><span class="sxs-lookup"><span data-stu-id="bc779-105">Parts</span></span>  
  
-   `attributelist`  
  
     <span data-ttu-id="bc779-106">Opcional.</span><span class="sxs-lookup"><span data-stu-id="bc779-106">Optional.</span></span> <span data-ttu-id="bc779-107">Lista de atributos que se aplicam a essa enumeração.</span><span class="sxs-lookup"><span data-stu-id="bc779-107">List of attributes that apply to this enumeration.</span></span> <span data-ttu-id="bc779-108">Você deve colocar o [a lista de atributos](../../../visual-basic/language-reference/statements/attribute-list.md) entre colchetes angulares ("`<`"e"`>`").</span><span class="sxs-lookup"><span data-stu-id="bc779-108">You must enclose the [attribute list](../../../visual-basic/language-reference/statements/attribute-list.md) in angle brackets ("`<`" and "`>`").</span></span>  
  
     <span data-ttu-id="bc779-109">O <xref:System.FlagsAttribute> atributo indica que o valor de uma instância de enumeração pode incluir vários membros de enumeração, e cada membro representa um campo de bit no valor de enumeração.</span><span class="sxs-lookup"><span data-stu-id="bc779-109">The <xref:System.FlagsAttribute> attribute indicates that the value of an instance of the enumeration can include multiple enumeration members, and that each member represents a bit field in the enumeration value.</span></span>  
  
-   `accessmodifier`  
  
     <span data-ttu-id="bc779-110">Opcional.</span><span class="sxs-lookup"><span data-stu-id="bc779-110">Optional.</span></span> <span data-ttu-id="bc779-111">Especifica o código pode acessar essa enumeração.</span><span class="sxs-lookup"><span data-stu-id="bc779-111">Specifies what code can access this enumeration.</span></span> <span data-ttu-id="bc779-112">Pode ser um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="bc779-112">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="bc779-113">Público</span><span class="sxs-lookup"><span data-stu-id="bc779-113">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [<span data-ttu-id="bc779-114">Protegido</span><span class="sxs-lookup"><span data-stu-id="bc779-114">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [<span data-ttu-id="bc779-115">Friend</span><span class="sxs-lookup"><span data-stu-id="bc779-115">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [<span data-ttu-id="bc779-116">Privado</span><span class="sxs-lookup"><span data-stu-id="bc779-116">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
  
     <span data-ttu-id="bc779-117">Você pode especificar `Protected``Friend` para permitir o acesso de código dentro classe de enumeração da, uma classe derivada ou do mesmo assembly.</span><span class="sxs-lookup"><span data-stu-id="bc779-117">You can specify `Protected``Friend` to allow access from code within the enumeration's class, a derived class, or the same assembly.</span></span>  
  
-   `Shadows`  
  
     <span data-ttu-id="bc779-118">Opcional.</span><span class="sxs-lookup"><span data-stu-id="bc779-118">Optional.</span></span> <span data-ttu-id="bc779-119">Especifica que esta enumeração redeclara e oculta um elemento de programação com o mesmo nome, ou um conjunto de elementos sobrecarregados, em uma classe base.</span><span class="sxs-lookup"><span data-stu-id="bc779-119">Specifies that this enumeration redeclares and hides an identically named programming element, or set of overloaded elements, in a base class.</span></span> <span data-ttu-id="bc779-120">Você pode especificar [sombras](../../../visual-basic/language-reference/modifiers/shadows.md) somente na enumeração em si, não em qualquer um de seus membros.</span><span class="sxs-lookup"><span data-stu-id="bc779-120">You can specify [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md) only on the enumeration itself, not on any of its members.</span></span>  
  
-   `enumerationname`  
  
     <span data-ttu-id="bc779-121">Necessário.</span><span class="sxs-lookup"><span data-stu-id="bc779-121">Required.</span></span> <span data-ttu-id="bc779-122">Nome da enumeração.</span><span class="sxs-lookup"><span data-stu-id="bc779-122">Name of the enumeration.</span></span> <span data-ttu-id="bc779-123">Para obter informações sobre nomes válidos, consulte [nomes de elemento declarado](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="bc779-123">For information on valid names, see [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
-   `datatype`  
  
     <span data-ttu-id="bc779-124">Opcional.</span><span class="sxs-lookup"><span data-stu-id="bc779-124">Optional.</span></span> <span data-ttu-id="bc779-125">Tipo de dados de enumeração e todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="bc779-125">Data type of the enumeration and all its members.</span></span>  
  
-   `memberlist`  
  
     <span data-ttu-id="bc779-126">Necessário.</span><span class="sxs-lookup"><span data-stu-id="bc779-126">Required.</span></span> <span data-ttu-id="bc779-127">Lista de constantes de membro que está sendo declarada nessa instrução.</span><span class="sxs-lookup"><span data-stu-id="bc779-127">List of member constants being declared in this statement.</span></span> <span data-ttu-id="bc779-128">Vários membros aparecem em linhas de código de origem individuais.</span><span class="sxs-lookup"><span data-stu-id="bc779-128">Multiple members appear on individual source code lines.</span></span>  
  
     <span data-ttu-id="bc779-129">Cada `member` tem a seguinte sintaxe e partes:`[<attribute list>] member name [ = initializer ]`</span><span class="sxs-lookup"><span data-stu-id="bc779-129">Each `member` has the following syntax and parts: `[<attribute list>] member name [ = initializer ]`</span></span>  
  
    |<span data-ttu-id="bc779-130">Parte</span><span class="sxs-lookup"><span data-stu-id="bc779-130">Part</span></span>|<span data-ttu-id="bc779-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="bc779-131">Description</span></span>|  
    |---|---|  
    |`membername`|<span data-ttu-id="bc779-132">Necessário.</span><span class="sxs-lookup"><span data-stu-id="bc779-132">Required.</span></span> <span data-ttu-id="bc779-133">Nome desse membro.</span><span class="sxs-lookup"><span data-stu-id="bc779-133">Name of this member.</span></span>|  
    |`initializer`|<span data-ttu-id="bc779-134">Opcional.</span><span class="sxs-lookup"><span data-stu-id="bc779-134">Optional.</span></span> <span data-ttu-id="bc779-135">Expressão que é avaliada em tempo de compilação e atribuída a este membro.</span><span class="sxs-lookup"><span data-stu-id="bc779-135">Expression that is evaluated at compile time and assigned to this member.</span></span>|  
  
-   <span data-ttu-id="bc779-136">`End` `Enum`</span><span class="sxs-lookup"><span data-stu-id="bc779-136">`End` `Enum`</span></span>  
  
     <span data-ttu-id="bc779-137">Encerra o `Enum` bloco.</span><span class="sxs-lookup"><span data-stu-id="bc779-137">Terminates the `Enum` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bc779-138">Comentários</span><span class="sxs-lookup"><span data-stu-id="bc779-138">Remarks</span></span>  
 <span data-ttu-id="bc779-139">Se você tiver um conjunto de valores sem variação que são logicamente relacionados uns aos outros, você pode defini-los juntos em uma enumeração.</span><span class="sxs-lookup"><span data-stu-id="bc779-139">If you have a set of unchanging values that are logically related to each other, you can define them together in an enumeration.</span></span> <span data-ttu-id="bc779-140">Isso fornece nomes significativos para a enumeração e seus membros, que são mais fáceis de lembrar que seus valores.</span><span class="sxs-lookup"><span data-stu-id="bc779-140">This provides meaningful names for the enumeration and its members, which are easier to remember than their values.</span></span> <span data-ttu-id="bc779-141">Em seguida, você pode usar os membros de enumeração em vários locais no seu código.</span><span class="sxs-lookup"><span data-stu-id="bc779-141">You can then use the enumeration members in many places in your code.</span></span>  
  
 <span data-ttu-id="bc779-142">Os benefícios de usar enumerações incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="bc779-142">The benefits of using enumerations include the following:</span></span>  
  
-   <span data-ttu-id="bc779-143">Reduz os erros causados por Transpor ou números de erros de digitação.</span><span class="sxs-lookup"><span data-stu-id="bc779-143">Reduces errors caused by transposing or mistyping numbers.</span></span>  
  
-   <span data-ttu-id="bc779-144">É fácil alterar os valores no futuro.</span><span class="sxs-lookup"><span data-stu-id="bc779-144">Makes it easy to change values in the future.</span></span>  
  
-   <span data-ttu-id="bc779-145">Torna o código mais fácil de ler, o que significa que é menos provável que serão introduzidos erros.</span><span class="sxs-lookup"><span data-stu-id="bc779-145">Makes code easier to read, which means it is less likely that errors will be introduced.</span></span>  
  
-   <span data-ttu-id="bc779-146">Garante a compatibilidade com versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="bc779-146">Ensures forward compatibility.</span></span> <span data-ttu-id="bc779-147">Se você usar enumerações, seu código é menos provável falhe se futuramente alguém altera os valores correspondentes aos nomes de membros.</span><span class="sxs-lookup"><span data-stu-id="bc779-147">If you use enumerations, your code is less likely to fail if in the future someone changes the values corresponding to the member names.</span></span>  
  
 <span data-ttu-id="bc779-148">Uma enumeração tem um nome, um tipo de dados subjacente e um conjunto de membros.</span><span class="sxs-lookup"><span data-stu-id="bc779-148">An enumeration has a name, an underlying data type, and a set of members.</span></span> <span data-ttu-id="bc779-149">Cada membro representa uma constante.</span><span class="sxs-lookup"><span data-stu-id="bc779-149">Each member represents a constant.</span></span>  
  
 <span data-ttu-id="bc779-150">Uma enumeração declarada na classe, estrutura, módulo ou nível de interface, fora de qualquer procedimento, é um *membro de enumeração*.</span><span class="sxs-lookup"><span data-stu-id="bc779-150">An enumeration declared at class, structure, module, or interface level, outside any procedure, is a *member enumeration*.</span></span> <span data-ttu-id="bc779-151">É um membro de classe, estrutura, módulo ou interface que declara.</span><span class="sxs-lookup"><span data-stu-id="bc779-151">It is a member of the class, structure, module, or interface that declares it.</span></span>  
  
 <span data-ttu-id="bc779-152">Enumerações de membro podem ser acessadas de qualquer lugar dentro de sua classe, estrutura, módulo ou interface.</span><span class="sxs-lookup"><span data-stu-id="bc779-152">Member enumerations can be accessed from anywhere within their class, structure, module, or interface.</span></span> <span data-ttu-id="bc779-153">Código fora de uma classe, estrutura, ou módulo deve qualificar nome do membro de uma enumeração com o nome da classe, estrutura ou módulo.</span><span class="sxs-lookup"><span data-stu-id="bc779-153">Code outside a class, structure, or module must qualify a member enumeration's name with the name of that class, structure, or module.</span></span> <span data-ttu-id="bc779-154">Você pode evitar a necessidade de usar nomes totalmente qualificados, adicionando uma [Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) instrução para o arquivo de origem.</span><span class="sxs-lookup"><span data-stu-id="bc779-154">You can avoid the need to use fully qualified names by adding an [Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) statement to the source file.</span></span>  
  
 <span data-ttu-id="bc779-155">Uma enumeração declarada no nível de namespace, fora de qualquer classe, estrutura, módulo ou interface, é um membro do namespace no qual ele aparece.</span><span class="sxs-lookup"><span data-stu-id="bc779-155">An enumeration declared at namespace level, outside any class, structure, module, or interface, is a member of the namespace in which it appears.</span></span>  
  
 <span data-ttu-id="bc779-156">O *contexto declaração* para uma enumeração deve ser um arquivo de origem, namespace, classe, estrutura, módulo ou interface e não pode ser um procedimento.</span><span class="sxs-lookup"><span data-stu-id="bc779-156">The *declaration context* for an enumeration must be a source file, namespace, class, structure, module, or interface, and cannot be a procedure.</span></span> <span data-ttu-id="bc779-157">Para obter mais informações, consulte [Contextos de declaração e níveis de acesso padrão](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="bc779-157">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="bc779-158">Você pode aplicar atributos a uma enumeração como um todo, mas não a seus membros individualmente.</span><span class="sxs-lookup"><span data-stu-id="bc779-158">You can apply attributes to an enumeration as a whole, but not to its members individually.</span></span> <span data-ttu-id="bc779-159">Um atributo contribui com informações para metadados do assembly.</span><span class="sxs-lookup"><span data-stu-id="bc779-159">An attribute contributes information to the assembly's metadata.</span></span>  
  
## <a name="data-type"></a><span data-ttu-id="bc779-160">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="bc779-160">Data Type</span></span>  
 <span data-ttu-id="bc779-161">O `Enum` instrução pode declarar o tipo de dados de uma enumeração.</span><span class="sxs-lookup"><span data-stu-id="bc779-161">The `Enum` statement can declare the data type of an enumeration.</span></span> <span data-ttu-id="bc779-162">Cada membro tem o tipo de dados da enumeração.</span><span class="sxs-lookup"><span data-stu-id="bc779-162">Each member takes the enumeration's data type.</span></span> <span data-ttu-id="bc779-163">Você pode especificar `Byte`, `Integer`, `Long`, `SByte`, `Short`, `UInteger`, `ULong`, ou `UShort`.</span><span class="sxs-lookup"><span data-stu-id="bc779-163">You can specify `Byte`, `Integer`, `Long`, `SByte`, `Short`, `UInteger`, `ULong`, or `UShort`.</span></span>  
  
 <span data-ttu-id="bc779-164">Se você não especificar `datatype` para a enumeração, cada membro tem o tipo de dados do seu `initializer`.</span><span class="sxs-lookup"><span data-stu-id="bc779-164">If you do not specify `datatype` for the enumeration, each member takes the data type of its `initializer`.</span></span> <span data-ttu-id="bc779-165">Se você especificar ambos `datatype` e `initializer`, o tipo de dados `initializer` deve ser conversível em `datatype`.</span><span class="sxs-lookup"><span data-stu-id="bc779-165">If you specify both `datatype` and `initializer`, the data type of `initializer` must be convertible to `datatype`.</span></span> <span data-ttu-id="bc779-166">Se nem `datatype` nem `initializer` estiver presente, o tipo de dados padrão é `Integer`.</span><span class="sxs-lookup"><span data-stu-id="bc779-166">If neither `datatype` nor `initializer` is present, the data type defaults to `Integer`.</span></span>  
  
## <a name="initializing-members"></a><span data-ttu-id="bc779-167">Membros de inicialização</span><span class="sxs-lookup"><span data-stu-id="bc779-167">Initializing Members</span></span>  
 <span data-ttu-id="bc779-168">O `Enum` instrução pode inicializar o conteúdo de membros selecionados na `memberlist`.</span><span class="sxs-lookup"><span data-stu-id="bc779-168">The `Enum` statement can initialize the contents of selected members in `memberlist`.</span></span> <span data-ttu-id="bc779-169">Você usa `initializer` para fornecer uma expressão a ser atribuída ao membro.</span><span class="sxs-lookup"><span data-stu-id="bc779-169">You use `initializer` to supply an expression to be assigned to the member.</span></span>  
  
 <span data-ttu-id="bc779-170">Se você não especificar `initializer` para um membro, Visual Basic o inicializa com zero (se ele for o primeiro `member` na `memberlist`), ou para um valor maior do que o precede imediatamente `member`.</span><span class="sxs-lookup"><span data-stu-id="bc779-170">If you do not specify `initializer` for a member, Visual Basic initializes it either to zero (if it is the first `member` in `memberlist`), or to a value greater by one than that of the immediately preceding `member`.</span></span>  
  
 <span data-ttu-id="bc779-171">A expressão fornecida em cada `initializer` pode ser qualquer combinação de literais, outras constantes que já estão definidas e membros de enumeração que já estão definidos, incluindo um membro anterior dessa enumeração.</span><span class="sxs-lookup"><span data-stu-id="bc779-171">The expression supplied in each `initializer` can be any combination of literals, other constants that are already defined, and enumeration members that are already defined, including a previous member of this enumeration.</span></span> <span data-ttu-id="bc779-172">Você pode usar operadores aritméticos e lógicos para combinar esses elementos.</span><span class="sxs-lookup"><span data-stu-id="bc779-172">You can use arithmetic and logical operators to combine such elements.</span></span>  
  
 <span data-ttu-id="bc779-173">Você não pode usar variáveis ou funções no `initializer`.</span><span class="sxs-lookup"><span data-stu-id="bc779-173">You cannot use variables or functions in `initializer`.</span></span> <span data-ttu-id="bc779-174">No entanto, você pode usar palavras-chave de conversão, como `CByte` e `CShort`.</span><span class="sxs-lookup"><span data-stu-id="bc779-174">However, you can use conversion keywords such as `CByte` and `CShort`.</span></span> <span data-ttu-id="bc779-175">Você também pode usar `AscW` se chamá-lo com uma constante `String` ou `Char` argumento, desde que possa ser avaliado em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="bc779-175">You can also use `AscW` if you call it with a constant `String` or `Char` argument, since that can be evaluated at compile time.</span></span>  
  
 <span data-ttu-id="bc779-176">Enumerações não podem ter valores de ponto flutuante.</span><span class="sxs-lookup"><span data-stu-id="bc779-176">Enumerations cannot have floating-point values.</span></span> <span data-ttu-id="bc779-177">Se um membro é atribuído um valor de ponto flutuante e `Option Strict` é definida como on, ocorre um erro do compilador.</span><span class="sxs-lookup"><span data-stu-id="bc779-177">If a member is assigned a floating-point value and `Option Strict` is set to on, a compiler error occurs.</span></span> <span data-ttu-id="bc779-178">Se `Option Strict` estiver desativado, o valor é convertido automaticamente para o `Enum` tipo.</span><span class="sxs-lookup"><span data-stu-id="bc779-178">If `Option Strict` is off, the value is automatically converted to the `Enum` type.</span></span>  
  
 <span data-ttu-id="bc779-179">Se o valor de um membro exceder o intervalo permitido para o tipo de dados, ou se você inicializar qualquer membro para o valor máximo permitido pelo tipo de dados subjacente, o compilador relata um erro.</span><span class="sxs-lookup"><span data-stu-id="bc779-179">If the value of a member exceeds the allowable range for the underlying data type, or if you initialize any member to the maximum value allowed by the underlying data type, the compiler reports an error.</span></span>  
  
## <a name="modifiers"></a><span data-ttu-id="bc779-180">Modificadores</span><span class="sxs-lookup"><span data-stu-id="bc779-180">Modifiers</span></span>  
 <span data-ttu-id="bc779-181">Classe, estrutura, módulo e padrão de enumerações de membro de interface de acesso público.</span><span class="sxs-lookup"><span data-stu-id="bc779-181">Class, structure, module, and interface member enumerations default to public access.</span></span> <span data-ttu-id="bc779-182">Você pode ajustar os níveis de acesso com os modificadores de acesso.</span><span class="sxs-lookup"><span data-stu-id="bc779-182">You can adjust their access levels with the access modifiers.</span></span> <span data-ttu-id="bc779-183">Padrão de enumerações de membro de Namespace para acesso friend.</span><span class="sxs-lookup"><span data-stu-id="bc779-183">Namespace member enumerations default to friend access.</span></span> <span data-ttu-id="bc779-184">Você pode ajustar os níveis de acesso para público, mas não a particular ou protegido.</span><span class="sxs-lookup"><span data-stu-id="bc779-184">You can adjust their access levels to public, but not to private or protected.</span></span> <span data-ttu-id="bc779-185">Para obter mais informações, consulte [acessar níveis no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="bc779-185">For more information, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="bc779-186">Todos os membros de enumeração têm acesso público e você não pode usar quaisquer modificadores de acesso neles.</span><span class="sxs-lookup"><span data-stu-id="bc779-186">All enumeration members have public access, and you cannot use any access modifiers on them.</span></span> <span data-ttu-id="bc779-187">No entanto, se a enumeração tiver um nível de acesso mais restrito, o nível de acesso especificado enumeração tem precedência.</span><span class="sxs-lookup"><span data-stu-id="bc779-187">However, if the enumeration itself has a more restricted access level, the specified enumeration access level takes precedence.</span></span>  
  
 <span data-ttu-id="bc779-188">Por padrão, todas as enumerações são tipos e seus campos são constantes.</span><span class="sxs-lookup"><span data-stu-id="bc779-188">By default, all enumerations are types and their fields are constants.</span></span> <span data-ttu-id="bc779-189">Portanto, o `Shared`, `Static`, e `ReadOnly` palavras-chave não podem ser usadas ao declarar uma enumeração ou seus membros.</span><span class="sxs-lookup"><span data-stu-id="bc779-189">Therefore the `Shared`, `Static`, and `ReadOnly` keywords cannot be used when declaring an enumeration or its members.</span></span>  
  
## <a name="assigning-multiple-values"></a><span data-ttu-id="bc779-190">Atribuindo valores múltiplos</span><span class="sxs-lookup"><span data-stu-id="bc779-190">Assigning Multiple Values</span></span>  
 <span data-ttu-id="bc779-191">Enumerações geralmente representam valores mutuamente exclusivos.</span><span class="sxs-lookup"><span data-stu-id="bc779-191">Enumerations typically represent mutually exclusive values.</span></span> <span data-ttu-id="bc779-192">Incluindo o <xref:System.FlagsAttribute> atributo o `Enum` declaração, você pode em vez disso, atribuir vários valores para uma instância da enumeração.</span><span class="sxs-lookup"><span data-stu-id="bc779-192">By including the <xref:System.FlagsAttribute> attribute in the `Enum` declaration, you can instead assign multiple values to an instance of the enumeration.</span></span> <span data-ttu-id="bc779-193">O <xref:System.FlagsAttribute> atributo especifica que a enumeração ser tratado como um campo de bits, ou seja, um conjunto de sinalizadores.</span><span class="sxs-lookup"><span data-stu-id="bc779-193">The <xref:System.FlagsAttribute> attribute specifies that the enumeration be treated as a bit field, that is, a set of flags.</span></span> <span data-ttu-id="bc779-194">Esses são chamados de *bit a bit* enumerações.</span><span class="sxs-lookup"><span data-stu-id="bc779-194">These are called *bitwise* enumerations.</span></span>  
  
 <span data-ttu-id="bc779-195">Quando você declara uma enumeração usando o <xref:System.FlagsAttribute> atributo, é recomendável que você use potências de 2, que é 1, 2, 4, 8, 16 e assim por diante, para os valores.</span><span class="sxs-lookup"><span data-stu-id="bc779-195">When you declare an enumeration by using the <xref:System.FlagsAttribute> attribute, we recommend that you use powers of 2, that is, 1, 2, 4, 8, 16, and so on, for the values.</span></span> <span data-ttu-id="bc779-196">Também recomendamos que "None" seja o nome de um membro cujo valor é 0.</span><span class="sxs-lookup"><span data-stu-id="bc779-196">We also recommend that "None" be the name of a member whose value is 0.</span></span> <span data-ttu-id="bc779-197">Para obter diretrizes adicionais, consulte <xref:System.FlagsAttribute> e <xref:System.Enum>.</span><span class="sxs-lookup"><span data-stu-id="bc779-197">For additional guidelines, see <xref:System.FlagsAttribute> and <xref:System.Enum>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bc779-198">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bc779-198">Example</span></span>  
 <span data-ttu-id="bc779-199">O exemplo a seguir mostra como usar o `Enum` instrução.</span><span class="sxs-lookup"><span data-stu-id="bc779-199">The following example shows how to use the `Enum` statement.</span></span> <span data-ttu-id="bc779-200">Observe que o membro é conhecido como `EggSizeEnum.Medium`e não como `Medium`.</span><span class="sxs-lookup"><span data-stu-id="bc779-200">Note that the member is referred to as `EggSizeEnum.Medium`, and not as `Medium`.</span></span>  
  
 [!code-vb[VbEnumsTask#41](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="bc779-201">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bc779-201">Example</span></span>  
 <span data-ttu-id="bc779-202">O método no exemplo a seguir está fora do `Egg` classe.</span><span class="sxs-lookup"><span data-stu-id="bc779-202">The method in the following example is outside the `Egg` class.</span></span> <span data-ttu-id="bc779-203">Portanto, `EggSizeEnum` é totalmente qualificado como `Egg.EggSizeEnum`.</span><span class="sxs-lookup"><span data-stu-id="bc779-203">Therefore, `EggSizeEnum` is fully qualified as `Egg.EggSizeEnum`.</span></span>  
  
 [!code-vb[VbEnumsTask#42](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="bc779-204">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bc779-204">Example</span></span>  
 <span data-ttu-id="bc779-205">O exemplo a seguir usa o `Enum` chamada de instrução para definir um conjunto relacionado de valores constantes.</span><span class="sxs-lookup"><span data-stu-id="bc779-205">The following example uses the `Enum` statement to define a related set of named constant values.</span></span> <span data-ttu-id="bc779-206">Nesse caso, os valores são cores, que você pode escolher para criar formulários de entrada de dados para um banco de dados.</span><span class="sxs-lookup"><span data-stu-id="bc779-206">In this case, the values are colors you might choose to design data entry forms for a database.</span></span>  
  
 [!code-vb[VbEnumsTask#30](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_3.vb)]  
  
## <a name="example"></a><span data-ttu-id="bc779-207">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bc779-207">Example</span></span>  
 <span data-ttu-id="bc779-208">O exemplo a seguir mostra os valores que incluem números positivos e negativos.</span><span class="sxs-lookup"><span data-stu-id="bc779-208">The following example shows values that include both positive and negative numbers.</span></span>  
  
 [!code-vb[VbEnumsTask#31](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_4.vb)]  
  
## <a name="example"></a><span data-ttu-id="bc779-209">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bc779-209">Example</span></span>  
 <span data-ttu-id="bc779-210">No exemplo a seguir, uma `As` cláusula é usada para especificar o `datatype` de uma enumeração.</span><span class="sxs-lookup"><span data-stu-id="bc779-210">In the following example, an `As` clause is used to specify the `datatype` of an enumeration.</span></span>  
  
 [!code-vb[VbEnumsTask#6](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_5.vb)]  
  
## <a name="example"></a><span data-ttu-id="bc779-211">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bc779-211">Example</span></span>  
 <span data-ttu-id="bc779-212">O exemplo a seguir mostra como usar uma enumeração de bit a bit.</span><span class="sxs-lookup"><span data-stu-id="bc779-212">The following example shows how to use a bitwise enumeration.</span></span> <span data-ttu-id="bc779-213">Vários valores podem ser atribuídos a uma instância de uma enumeração de bit a bit.</span><span class="sxs-lookup"><span data-stu-id="bc779-213">Multiple values can be assigned to an instance of a bitwise enumeration.</span></span> <span data-ttu-id="bc779-214">O `Enum` declaração inclui o <xref:System.FlagsAttribute> atributo, que indica que a enumeração pode ser tratada como um conjunto de sinalizadores.</span><span class="sxs-lookup"><span data-stu-id="bc779-214">The `Enum` declaration includes the <xref:System.FlagsAttribute> attribute, which indicates that the enumeration can be treated as a set of flags.</span></span>  
  
 [!code-vb[VbEnumsTask#61](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_6.vb)]  
  
## <a name="example"></a><span data-ttu-id="bc779-215">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bc779-215">Example</span></span>  
 <span data-ttu-id="bc779-216">O exemplo a seguir itera por meio de uma enumeração.</span><span class="sxs-lookup"><span data-stu-id="bc779-216">The following example iterates through an enumeration.</span></span> <span data-ttu-id="bc779-217">Ele usa o <xref:System.Enum.GetNames%2A> método para recuperar uma matriz de nomes de membro de enumeração, e <xref:System.Enum.GetValues%2A> para recuperar uma matriz de valores de membro.</span><span class="sxs-lookup"><span data-stu-id="bc779-217">It uses the <xref:System.Enum.GetNames%2A> method to retrieve an array of member names from the enumeration, and <xref:System.Enum.GetValues%2A> to retrieve an array of member values.</span></span>  
  
 [!code-vb[VbEnumsTask#51](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_7.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="bc779-218">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bc779-218">See Also</span></span>  
 <xref:System.Enum>  
 <xref:Microsoft.VisualBasic.Strings.AscW%2A>  
 [<span data-ttu-id="bc779-219">Instrução Const</span><span class="sxs-lookup"><span data-stu-id="bc779-219">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
 [<span data-ttu-id="bc779-220">Instrução Dim</span><span class="sxs-lookup"><span data-stu-id="bc779-220">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
 [<span data-ttu-id="bc779-221">Conversões Implícitas e Explícitas</span><span class="sxs-lookup"><span data-stu-id="bc779-221">Implicit and Explicit Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [<span data-ttu-id="bc779-222">Funções de Conversão do Tipo</span><span class="sxs-lookup"><span data-stu-id="bc779-222">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="bc779-223">Constantes e Enumerações</span><span class="sxs-lookup"><span data-stu-id="bc779-223">Constants and Enumerations</span></span>](../../../visual-basic/language-reference/constants-and-enumerations.md)
