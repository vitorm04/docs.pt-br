---
title: "Instrução Namespace | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Namespace
dev_langs:
- VB
helpviewer_keywords:
- namespaces, root
- Namespace statement
- namespaces, nested
- declaring namespaces, syntax
- namespaces, declaring
- root namespaces
- declarations, namespaces
ms.assetid: a31fbd95-9ace-4c3d-bbb1-51222a2272b2
caps.latest.revision: 39
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
ms.openlocfilehash: dde67fae0b750e7d43fea0e5090596410d8c272c
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="namespace-statement"></a><span data-ttu-id="191c1-102">Instrução Namespace</span><span class="sxs-lookup"><span data-stu-id="191c1-102">Namespace Statement</span></span>
<span data-ttu-id="191c1-103">Declara o nome de um namespace e faz com que o código-fonte que segue a declaração seja compilado dentro desse namespace.</span><span class="sxs-lookup"><span data-stu-id="191c1-103">Declares the name of a namespace and causes the source code that follows the declaration to be compiled within that namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="191c1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="191c1-104">Syntax</span></span>  
  
```  
Namespace [Global.] { name | name.name }  
    [ componenttypes ]  
End Namespace  
```  
  
## <a name="parts"></a><span data-ttu-id="191c1-105">Partes</span><span class="sxs-lookup"><span data-stu-id="191c1-105">Parts</span></span>  
 <span data-ttu-id="191c1-106">Global</span><span class="sxs-lookup"><span data-stu-id="191c1-106">Global</span></span>  
 <span data-ttu-id="191c1-107">Opcional.</span><span class="sxs-lookup"><span data-stu-id="191c1-107">Optional.</span></span> <span data-ttu-id="191c1-108">Permite definir um namespace fora do namespace raiz do projeto.</span><span class="sxs-lookup"><span data-stu-id="191c1-108">Allows you to define a namespace out of the root namespace of your project.</span></span> <span data-ttu-id="191c1-109">Consulte [Namespaces no Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="191c1-109">See [Namespaces in Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md).</span></span>  
  
 `name`  
 <span data-ttu-id="191c1-110">Necessário.</span><span class="sxs-lookup"><span data-stu-id="191c1-110">Required.</span></span> <span data-ttu-id="191c1-111">Um nome exclusivo que identifica o namespace.</span><span class="sxs-lookup"><span data-stu-id="191c1-111">A unique name that identifies the namespace.</span></span> <span data-ttu-id="191c1-112">Deve ser um identificador válido Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="191c1-112">Must be a valid Visual Basic identifier.</span></span> <span data-ttu-id="191c1-113">Para obter mais informações, consulte [nomes de elemento declarado](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="191c1-113">For more information, see [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
 `componenttypes`  
 <span data-ttu-id="191c1-114">Opcional.</span><span class="sxs-lookup"><span data-stu-id="191c1-114">Optional.</span></span> <span data-ttu-id="191c1-115">Elementos que compõem o namespace.</span><span class="sxs-lookup"><span data-stu-id="191c1-115">Elements that make up the namespace.</span></span> <span data-ttu-id="191c1-116">Esses incluem, mas não estão limitadas a, enumerações, estruturas, interfaces, classes, módulos, representantes e outros namespaces.</span><span class="sxs-lookup"><span data-stu-id="191c1-116">These include, but are not limited to, enumerations, structures, interfaces, classes, modules, delegates, and other namespaces.</span></span>  
  
 `End Namespace`  
 <span data-ttu-id="191c1-117">Finaliza uma `Namespace` bloco.</span><span class="sxs-lookup"><span data-stu-id="191c1-117">Terminates a `Namespace` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="191c1-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="191c1-118">Remarks</span></span>  
 <span data-ttu-id="191c1-119">Namespaces são usados como um sistema organizacional.</span><span class="sxs-lookup"><span data-stu-id="191c1-119">Namespaces are used as an organizational system.</span></span> <span data-ttu-id="191c1-120">Eles fornecem uma maneira de classificar e apresentar os elementos de programação que são expostos a outros programas e aplicativos.</span><span class="sxs-lookup"><span data-stu-id="191c1-120">They provide a way to classify and present programming elements that are exposed to other programs and applications.</span></span> <span data-ttu-id="191c1-121">Observe que um namespace não é um *tipo* no sentido de que uma classe ou estrutura é — você não pode declarar um elemento de programação para ter o tipo de dados de um namespace.</span><span class="sxs-lookup"><span data-stu-id="191c1-121">Note that a namespace is not a *type* in the sense that a class or structure is—you cannot declare a programming element to have the data type of a namespace.</span></span>  
  
 <span data-ttu-id="191c1-122">Todos os elementos de programação declarados após uma `Namespace` instrução pertencem a esse namespace.</span><span class="sxs-lookup"><span data-stu-id="191c1-122">All programming elements declared after a `Namespace` statement belong to that namespace.</span></span> <span data-ttu-id="191c1-123">Visual Basic continua a compilar elementos no último namespace declarado até encontrar uma `End Namespace` instrução ou outro `Namespace` instrução.</span><span class="sxs-lookup"><span data-stu-id="191c1-123">Visual Basic continues to compile elements into the last declared namespace until it encounters either an `End Namespace` statement or another `Namespace` statement.</span></span>  
  
 <span data-ttu-id="191c1-124">Se um namespace já estiver definido, até mesmo fora do seu projeto, você pode adicionar elementos de programação a ele.</span><span class="sxs-lookup"><span data-stu-id="191c1-124">If a namespace is already defined, even outside your project, you can add programming elements to it.</span></span> <span data-ttu-id="191c1-125">Para fazer isso, você deve usar um `Namespace` instrução para direcionar o Visual Basic para compilar os elementos para esse namespace.</span><span class="sxs-lookup"><span data-stu-id="191c1-125">To do this, you use a `Namespace` statement to direct Visual Basic to compile elements into that namespace.</span></span>  
  
 <span data-ttu-id="191c1-126">Você pode usar um `Namespace` instrução somente no nível de namespace ou arquivo.</span><span class="sxs-lookup"><span data-stu-id="191c1-126">You can use a `Namespace` statement only at the file or namespace level.</span></span> <span data-ttu-id="191c1-127">Isso significa que o *contexto declaração* para um namespace deve ser um arquivo fonte ou namespace e não pode ser uma classe, estrutura, módulo, interface ou procedimento.</span><span class="sxs-lookup"><span data-stu-id="191c1-127">This means the *declaration context* for a namespace must be a source file or another namespace, and cannot be a class, structure, module, interface, or procedure.</span></span> <span data-ttu-id="191c1-128">Para obter mais informações, consulte [contextos de declaração e níveis de acesso padrão](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="191c1-128">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="191c1-129">Você pode declarar um namespace dentro de outro.</span><span class="sxs-lookup"><span data-stu-id="191c1-129">You can declare one namespace within another.</span></span> <span data-ttu-id="191c1-130">Não há nenhum limite estrito aos níveis de aninhamento você pode declarar, mas lembre-se de que, quando outro código acessa os elementos declarados no namespace mais interno, ele deve usar uma cadeia de caracteres de qualificação que contém todos os nomes de namespaces na hierarquia de aninhamento.</span><span class="sxs-lookup"><span data-stu-id="191c1-130">There is no strict limit to the levels of nesting you can declare, but remember that when other code accesses the elements declared in the innermost namespace, it must use a qualification string that contains all the namespace names in the nesting hierarchy.</span></span>  
  
## <a name="access-level"></a><span data-ttu-id="191c1-131">Nível de acesso</span><span class="sxs-lookup"><span data-stu-id="191c1-131">Access Level</span></span>  
 <span data-ttu-id="191c1-132">Namespaces são tratados como se tivessem um `Public` nível de acesso.</span><span class="sxs-lookup"><span data-stu-id="191c1-132">Namespaces are treated as if they have a `Public` access level.</span></span> <span data-ttu-id="191c1-133">Um namespace pode ser acessado de código em qualquer lugar no mesmo projeto, de outros projetos que referenciem o projeto e de qualquer assembly compilado do projeto.</span><span class="sxs-lookup"><span data-stu-id="191c1-133">A namespace can be accessed from code anywhere in the same project, from other projects that reference the project, and from any assembly built from the project.</span></span>  
  
 <span data-ttu-id="191c1-134">Elementos de programação declarados no nível de namespace, que significa que em um namespace mas não dentro de qualquer outro elemento, podem ter `Public` ou `Friend` acesso.</span><span class="sxs-lookup"><span data-stu-id="191c1-134">Programming elements declared at namespace level, meaning in a namespace but not inside any other element, can have `Public` or `Friend` access.</span></span> <span data-ttu-id="191c1-135">Se não for especificado, o nível de acesso de tal elemento usa `Friend` por padrão.</span><span class="sxs-lookup"><span data-stu-id="191c1-135">If unspecified, the access level of such an element uses `Friend` by default.</span></span> <span data-ttu-id="191c1-136">Você pode declarar no nível de namespace de elementos incluem classes, estruturas, módulos, interfaces, enumerações e delegados.</span><span class="sxs-lookup"><span data-stu-id="191c1-136">Elements you can declare at namespace level include classes, structures, modules, interfaces, enumerations, and delegates.</span></span> <span data-ttu-id="191c1-137">Para obter mais informações, consulte [contextos de declaração e níveis de acesso padrão](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="191c1-137">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>  
  
## <a name="root-namespace"></a><span data-ttu-id="191c1-138">Namespace Raiz</span><span class="sxs-lookup"><span data-stu-id="191c1-138">Root Namespace</span></span>  
 <span data-ttu-id="191c1-139">Todos os nomes de namespace em seu projeto são baseados em um *namespace raiz*.</span><span class="sxs-lookup"><span data-stu-id="191c1-139">All namespace names in your project are based on a *root namespace*.</span></span> <span data-ttu-id="191c1-140">Visual Studio atribui o nome do projeto como o namespace de raiz padrão para todo o código em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="191c1-140">Visual Studio assigns your project name as the default root namespace for all code in your project.</span></span> <span data-ttu-id="191c1-141">Por exemplo, se seu projeto for chamado `Payroll`, seus elementos de programação pertencem ao namespace `Payroll`.</span><span class="sxs-lookup"><span data-stu-id="191c1-141">For example, if your project is named `Payroll`, its programming elements belong to namespace `Payroll`.</span></span> <span data-ttu-id="191c1-142">Se você declarar `Namespace funding`, é o nome completo do namespace `Payroll.funding`.</span><span class="sxs-lookup"><span data-stu-id="191c1-142">If you declare `Namespace funding`, the full name of that namespace is `Payroll.funding`.</span></span>  
  
 <span data-ttu-id="191c1-143">Se você quiser especificar um namespace existente em um `Namespace` instrução, como no exemplo de classe de lista genérica, você pode definir seu namespace raiz com um valor nulo.</span><span class="sxs-lookup"><span data-stu-id="191c1-143">If you want to specify an existing namespace in a `Namespace` statement, such as in the generic list class example, you can set your root namespace to a null value.</span></span> <span data-ttu-id="191c1-144">Para fazer isso, clique em **propriedades do projeto** do **projeto** menu e desmarque o **namespace raiz** entrada para que a caixa estiver vazia.</span><span class="sxs-lookup"><span data-stu-id="191c1-144">To do this, click **Project Properties** from the **Project** menu and then clear the **Root namespace** entry so that the box is empty.</span></span> <span data-ttu-id="191c1-145">Se você não fizer isso no exemplo de classe de lista genérica, o compilador Visual Basic tomaria `System.Collections.Generic` como um novo namespace no projeto `Payroll`, com o nome completo do `Payroll.System.Collections.Generic`.</span><span class="sxs-lookup"><span data-stu-id="191c1-145">If you did not do this in the generic list class example, the Visual Basic compiler would take `System.Collections.Generic` as a new namespace within project `Payroll`, with the full name of `Payroll.System.Collections.Generic`.</span></span>  
  
 <span data-ttu-id="191c1-146">Como alternativa, você pode usar o `Global` palavra-chave para se referir a elementos de namespaces definidos fora do projeto.</span><span class="sxs-lookup"><span data-stu-id="191c1-146">Alternatively, you can use the `Global` keyword to refer to elements of namespaces defined outside your project.</span></span> <span data-ttu-id="191c1-147">Isso permite que você mantenha o nome do projeto como o namespace raiz.</span><span class="sxs-lookup"><span data-stu-id="191c1-147">Doing so lets you retain your project name as the root namespace.</span></span> <span data-ttu-id="191c1-148">Isso reduz a chance de mesclagem, inadvertidamente, elementos de programação com os dos namespaces existentes.</span><span class="sxs-lookup"><span data-stu-id="191c1-148">This reduces the chance of unintentionally merging your programming elements together with those of existing namespaces.</span></span> <span data-ttu-id="191c1-149">Para obter mais informações, consulte a seção "Global palavra-chave em nomes totalmente qualificados" [Namespaces no Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="191c1-149">For more information, see the "Global Keyword in Fully Qualified Names" section in [Namespaces in Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md).</span></span>  
  
 <span data-ttu-id="191c1-150">O `Global` palavra-chave também pode ser usado em uma declaração de Namespace.</span><span class="sxs-lookup"><span data-stu-id="191c1-150">The `Global` keyword can also be used in a Namespace statement.</span></span> <span data-ttu-id="191c1-151">Isso permite definir um namespace fora do namespace raiz do projeto.</span><span class="sxs-lookup"><span data-stu-id="191c1-151">This lets you define a namespace out of the root namespace of your project.</span></span> <span data-ttu-id="191c1-152">Para obter mais informações, consulte a seção "Palavra-chave no Namespace instruções globais" [Namespaces no Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="191c1-152">For more information, see the "Global Keyword in Namespace Statements" section in [Namespaces in Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md).</span></span>  
  
 <span data-ttu-id="191c1-153">**Solução de problemas.**</span><span class="sxs-lookup"><span data-stu-id="191c1-153">**Troubleshooting.**</span></span> <span data-ttu-id="191c1-154">O namespace raiz pode levar à concatenações inesperadas de nomes de namespace.</span><span class="sxs-lookup"><span data-stu-id="191c1-154">The root namespace can lead to unexpected concatenations of namespace names.</span></span> <span data-ttu-id="191c1-155">Se você fizer referência a namespaces definidos fora do projeto, o compilador do Visual Basic pode construe-los como namespaces aninhados no namespace raiz.</span><span class="sxs-lookup"><span data-stu-id="191c1-155">If you make reference to namespaces defined outside your project, the Visual Basic compiler can construe them as nested namespaces in the root namespace.</span></span> <span data-ttu-id="191c1-156">Nesse caso, o compilador não reconhece quaisquer tipos que tiverem sido já definidos em namespaces externos.</span><span class="sxs-lookup"><span data-stu-id="191c1-156">In such a case, the compiler does not recognize any types that have been already defined in the external namespaces.</span></span> <span data-ttu-id="191c1-157">Para evitar isso, defina seu namespace raiz com um valor nulo, conforme descrito em "Namespace raiz", ou use o `Global` palavra-chave para acessar elementos de namespaces externos.</span><span class="sxs-lookup"><span data-stu-id="191c1-157">To avoid this, either set your root namespace to a null value as described in "Root Namespace," or use the `Global` keyword to access elements of external namespaces.</span></span>  
  
## <a name="attributes-and-modifiers"></a><span data-ttu-id="191c1-158">Atributos e modificadores</span><span class="sxs-lookup"><span data-stu-id="191c1-158">Attributes and Modifiers</span></span>  
 <span data-ttu-id="191c1-159">Você não pode aplicar atributos a um namespace.</span><span class="sxs-lookup"><span data-stu-id="191c1-159">You cannot apply attributes to a namespace.</span></span> <span data-ttu-id="191c1-160">Um atributo contribui com informações para metadados do assembly, que não é significativo para fontes classificadores como namespaces.</span><span class="sxs-lookup"><span data-stu-id="191c1-160">An attribute contributes information to the assembly's metadata, which is not meaningful for source classifiers such as namespaces.</span></span>  
  
 <span data-ttu-id="191c1-161">É possível aplicar qualquer acesso ou modificadores de procedimento ou qualquer outros modificadores, a um namespace.</span><span class="sxs-lookup"><span data-stu-id="191c1-161">You cannot apply any access or procedure modifiers, or any other modifiers, to a namespace.</span></span> <span data-ttu-id="191c1-162">Porque ele não é um tipo, esses modificadores não são significativos.</span><span class="sxs-lookup"><span data-stu-id="191c1-162">Because it is not a type, these modifiers are not meaningful.</span></span>  
  
## <a name="example"></a><span data-ttu-id="191c1-163">Exemplo</span><span class="sxs-lookup"><span data-stu-id="191c1-163">Example</span></span>  
 <span data-ttu-id="191c1-164">O exemplo a seguir declara dois namespaces, um aninhado no outro.</span><span class="sxs-lookup"><span data-stu-id="191c1-164">The following example declares two namespaces, one nested in the other.</span></span>  
  
 <span data-ttu-id="191c1-165">[!code-vb[VbVbalrStatements&#43;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/namespace-statement_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="191c1-165">[!code-vb[VbVbalrStatements#43](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/namespace-statement_1.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="191c1-166">Exemplo</span><span class="sxs-lookup"><span data-stu-id="191c1-166">Example</span></span>  
 <span data-ttu-id="191c1-167">O exemplo a seguir declara vários namespaces aninhados em uma única linha, e é equivalente ao exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="191c1-167">The following example declares multiple nested namespaces on a single line, and it is equivalent to the previous example.</span></span>  
  
 <span data-ttu-id="191c1-168">[!code-vb[41 VbVbalrStatements](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/namespace-statement_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="191c1-168">[!code-vb[VbVbalrStatements#41](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/namespace-statement_2.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="191c1-169">Exemplo</span><span class="sxs-lookup"><span data-stu-id="191c1-169">Example</span></span>  
 <span data-ttu-id="191c1-170">O exemplo a seguir acessa a classe definida nos exemplos anteriores.</span><span class="sxs-lookup"><span data-stu-id="191c1-170">The following example accesses the class defined in the previous examples.</span></span>  
  
 <span data-ttu-id="191c1-171">[!code-vb[VbVbalrStatements&42;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/namespace-statement_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="191c1-171">[!code-vb[VbVbalrStatements#42](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/namespace-statement_3.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="191c1-172">Exemplo</span><span class="sxs-lookup"><span data-stu-id="191c1-172">Example</span></span>  
 <span data-ttu-id="191c1-173">O exemplo a seguir define o esqueleto de uma nova classe de lista genérica e adiciona-o para o <xref:System.Collections.Generic?displayProperty=fullName>namespace.</xref:System.Collections.Generic?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="191c1-173">The following example defines the skeleton of a new generic list class and adds it to the <xref:System.Collections.Generic?displayProperty=fullName> namespace.</span></span>  
  
```vb  
Namespace System.Collections.Generic  
    Class specialSortedList(Of T)  
        Inherits List(Of T)  
        ' Insert code to define the special generic list class.  
    End Class  
End Namespace  
```  
  
## <a name="see-also"></a><span data-ttu-id="191c1-174">Consulte também</span><span class="sxs-lookup"><span data-stu-id="191c1-174">See Also</span></span>  
 <span data-ttu-id="191c1-175">[Instrução Imports (tipo e Namespace .NET)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) </span><span class="sxs-lookup"><span data-stu-id="191c1-175">[Imports Statement (.NET Namespace and Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) </span></span>  
<span data-ttu-id="191c1-176"> [Nomes de elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md) </span><span class="sxs-lookup"><span data-stu-id="191c1-176"> [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md) </span></span>  
<span data-ttu-id="191c1-177"> [Namespaces no Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md)</span><span class="sxs-lookup"><span data-stu-id="191c1-177"> [Namespaces in Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md)</span></span>
