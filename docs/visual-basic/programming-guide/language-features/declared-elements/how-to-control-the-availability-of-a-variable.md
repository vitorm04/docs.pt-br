---
title: Como controlar a disponibilidade de uma variável (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- access levels, declared elements
- Private keyword [Visual Basic], accessing variables
- access levels, variables
- Public keyword [Visual Basic], accessing variables
- Friend keyword [Visual Basic], accessing variables
- variables [Visual Basic], access level
- declared elements [Visual Basic], access level
- Protected keyword [Visual Basic], accessing variables
ms.assetid: eaf4f073-7922-43ce-ae1e-90ff376ae947
ms.openlocfilehash: 27ee5d3405ea24c0754cffa85e9b89b2ac561e42
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33652162"
---
# <a name="how-to-control-the-availability-of-a-variable-visual-basic"></a><span data-ttu-id="5a657-102">Como controlar a disponibilidade de uma variável (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5a657-102">How to: Control the Availability of a Variable (Visual Basic)</span></span>
<span data-ttu-id="5a657-103">Controlar a disponibilidade de uma variável especificando seu *nível de acesso*.</span><span class="sxs-lookup"><span data-stu-id="5a657-103">You control the availability of a variable by specifying its *access level*.</span></span> <span data-ttu-id="5a657-104">O nível de acesso determina qual código tem permissão para ler ou gravar para a variável.</span><span class="sxs-lookup"><span data-stu-id="5a657-104">The access level determines what code has permission to read or write to the variable.</span></span>  
  
-   <span data-ttu-id="5a657-105">*Variáveis de membro* (definido no nível de módulo e fora de qualquer procedimento) padrão para acesso público, o que significa que qualquer código que pode vê-los pode acessá-los.</span><span class="sxs-lookup"><span data-stu-id="5a657-105">*Member variables* (defined at module level and outside any procedure) default to public access, which means any code that can see them can access them.</span></span> <span data-ttu-id="5a657-106">Você pode alterar isso, especificando um modificador de acesso.</span><span class="sxs-lookup"><span data-stu-id="5a657-106">You can change this by specifying an access modifier.</span></span>  
  
-   <span data-ttu-id="5a657-107">*Variáveis locais* (definido dentro de um procedimento) tem uma acesso público, embora somente o código dentro do seu procedimento pode acessá-los.</span><span class="sxs-lookup"><span data-stu-id="5a657-107">*Local variables* (defined inside a procedure) nominally have public access, although only code within their procedure can access them.</span></span> <span data-ttu-id="5a657-108">Você não pode alterar o nível de acesso de uma variável local, mas você pode alterar o nível de acesso do procedimento que o contém.</span><span class="sxs-lookup"><span data-stu-id="5a657-108">You cannot change the access level of a local variable, but you can change the access level of the procedure that contains it.</span></span>  
  
 <span data-ttu-id="5a657-109">Para obter mais informações, consulte [acessar níveis no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="5a657-109">For more information, see [Access levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
## <a name="private-and-public-access"></a><span data-ttu-id="5a657-110">Acesso privado e público</span><span class="sxs-lookup"><span data-stu-id="5a657-110">Private and Public Access</span></span>  
  
#### <a name="to-make-a-variable-accessible-only-from-within-its-module-class-or-structure"></a><span data-ttu-id="5a657-111">Para disponibilizar uma variável somente de dentro de seu módulo, classe ou estrutura</span><span class="sxs-lookup"><span data-stu-id="5a657-111">To make a variable accessible only from within its module, class, or structure</span></span>  
  
1.  <span data-ttu-id="5a657-112">Coloque o [instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) para a variável dentro do módulo, classe ou estrutura, mas fora de qualquer procedimento.</span><span class="sxs-lookup"><span data-stu-id="5a657-112">Place the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) for the variable inside the module, class, or structure, but outside any procedure.</span></span>  
  
2.  <span data-ttu-id="5a657-113">Incluir o [privada](../../../../visual-basic/language-reference/modifiers/private.md) palavra-chave no `Dim` instrução.</span><span class="sxs-lookup"><span data-stu-id="5a657-113">Include the [Private](../../../../visual-basic/language-reference/modifiers/private.md) keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="5a657-114">Você pode ler ou gravar a variável em qualquer lugar dentro do módulo, classe ou estrutura, mas não de fora.</span><span class="sxs-lookup"><span data-stu-id="5a657-114">You can read or write to the variable from anywhere within the module, class, or structure, but not from outside it.</span></span>  
  
#### <a name="to-make-a-variable-accessible-from-any-code-that-can-see-it"></a><span data-ttu-id="5a657-115">Para disponibilizar uma variável de qualquer código que pode vê-lo</span><span class="sxs-lookup"><span data-stu-id="5a657-115">To make a variable accessible from any code that can see it</span></span>  
  
1.  <span data-ttu-id="5a657-116">Para uma variável de membro, coloque o `Dim` instrução para a variável dentro de um módulo, classe ou estrutura, mas fora de qualquer procedimento.</span><span class="sxs-lookup"><span data-stu-id="5a657-116">For a member variable, place the `Dim` statement for the variable inside a module, class, or structure, but outside any procedure.</span></span>  
  
2.  <span data-ttu-id="5a657-117">Incluir o [pública](../../../../visual-basic/language-reference/modifiers/public.md) palavra-chave no `Dim` instrução.</span><span class="sxs-lookup"><span data-stu-id="5a657-117">Include the [Public](../../../../visual-basic/language-reference/modifiers/public.md) keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="5a657-118">Você pode ler ou gravar a variável de qualquer código que interage com seu assembly.</span><span class="sxs-lookup"><span data-stu-id="5a657-118">You can read or write to the variable from any code that interoperates with your assembly.</span></span>  
  
 <span data-ttu-id="5a657-119">-ou-</span><span class="sxs-lookup"><span data-stu-id="5a657-119">-or-</span></span>  
  
1.  <span data-ttu-id="5a657-120">Para uma variável local, coloque o `Dim` instrução para a variável dentro de um procedimento.</span><span class="sxs-lookup"><span data-stu-id="5a657-120">For a local variable, place the `Dim` statement for the variable inside a procedure.</span></span>  
  
2.  <span data-ttu-id="5a657-121">Não inclua o `Public` palavra-chave no `Dim` instrução.</span><span class="sxs-lookup"><span data-stu-id="5a657-121">Do not include the `Public` keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="5a657-122">Você pode ler ou gravar a variável em qualquer lugar dentro do procedimento, mas não de fora.</span><span class="sxs-lookup"><span data-stu-id="5a657-122">You can read or write to the variable from anywhere within the procedure, but not from outside it.</span></span>  
  
## <a name="protected-and-friend-access"></a><span data-ttu-id="5a657-123">Protegido e o acesso Friend</span><span class="sxs-lookup"><span data-stu-id="5a657-123">Protected and Friend Access</span></span>  
 <span data-ttu-id="5a657-124">Você pode limitar o nível de acesso de uma variável para sua classe e qualquer classe derivada ou seu assembly.</span><span class="sxs-lookup"><span data-stu-id="5a657-124">You can limit the access level of a variable to its class and any derived classes, or to its assembly.</span></span> <span data-ttu-id="5a657-125">Você também pode especificar a união dessas limitações, que permite o acesso do código em qualquer classe derivada ou em qualquer outro lugar no mesmo assembly.</span><span class="sxs-lookup"><span data-stu-id="5a657-125">You can also specify the union of these limitations, which allows access from code in any derived class or in any other place in the same assembly.</span></span> <span data-ttu-id="5a657-126">Especifique esta união combinando o `Protected` e `Friend` palavras-chave na mesma declaração.</span><span class="sxs-lookup"><span data-stu-id="5a657-126">You specify this union by combining the `Protected` and `Friend` keywords in the same declaration.</span></span>  
  
#### <a name="to-make-a-variable-accessible-only-from-within-its-class-and-any-derived-classes"></a><span data-ttu-id="5a657-127">Para disponibilizar uma variável somente de dentro de sua classe e todas as classes derivadas</span><span class="sxs-lookup"><span data-stu-id="5a657-127">To make a variable accessible only from within its class and any derived classes</span></span>  
  
1.  <span data-ttu-id="5a657-128">Coloque o `Dim` instrução para a variável dentro de uma classe, mas fora de qualquer procedimento.</span><span class="sxs-lookup"><span data-stu-id="5a657-128">Place the `Dim` statement for the variable inside a class, but outside any procedure.</span></span>  
  
2.  <span data-ttu-id="5a657-129">Incluir o [protegidos](../../../../visual-basic/language-reference/modifiers/protected.md) palavra-chave no `Dim` instrução.</span><span class="sxs-lookup"><span data-stu-id="5a657-129">Include the [Protected](../../../../visual-basic/language-reference/modifiers/protected.md) keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="5a657-130">Você pode ler ou gravar para a variável em qualquer lugar dentro da classe, bem como no qualquer classe derivada dela, mas não de fora de qualquer classe na cadeia de derivação.</span><span class="sxs-lookup"><span data-stu-id="5a657-130">You can read or write to the variable from anywhere within the class, as well as from within any class derived from it, but not from outside any class in the derivation chain.</span></span>  
  
#### <a name="to-make-a-variable-accessible-only-from-within-the-same-assembly"></a><span data-ttu-id="5a657-131">Para disponibilizar uma variável somente de dentro do mesmo assembly</span><span class="sxs-lookup"><span data-stu-id="5a657-131">To make a variable accessible only from within the same assembly</span></span>  
  
1.  <span data-ttu-id="5a657-132">Coloque o `Dim` instrução para a variável dentro de um módulo, classe ou estrutura, mas fora de qualquer procedimento.</span><span class="sxs-lookup"><span data-stu-id="5a657-132">Place the `Dim` statement for the variable inside a module, class, or structure, but outside any procedure.</span></span>  
  
2.  <span data-ttu-id="5a657-133">Incluir o [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) palavra-chave no `Dim` instrução.</span><span class="sxs-lookup"><span data-stu-id="5a657-133">Include the [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="5a657-134">Você pode ler ou gravar a variável em qualquer lugar dentro do módulo, classe ou estrutura, bem como qualquer código no mesmo assembly, mas não de fora do assembly.</span><span class="sxs-lookup"><span data-stu-id="5a657-134">You can read or write to the variable from anywhere within the module, class, or structure, as well as from any code in the same assembly, but not from outside the assembly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5a657-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5a657-135">Example</span></span>  
 <span data-ttu-id="5a657-136">O exemplo a seguir mostra as declarações de variáveis com `Public`, `Protected`, `Friend`, `Protected Friend`, e `Private` níveis de acesso.</span><span class="sxs-lookup"><span data-stu-id="5a657-136">The following example shows declarations of variables with `Public`, `Protected`, `Friend`, `Protected Friend`, and `Private` access levels.</span></span> <span data-ttu-id="5a657-137">Observe que, quando o `Dim` instrução Especifica um nível de acesso, você não precisa incluir o `Dim` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="5a657-137">Note that when the `Dim` statement specifies an access level, you do not need to include the `Dim` keyword.</span></span>  
  
```  
Public Class classForEverybody  
Protected Class classForMyHeirs  
Friend stringForThisProject As String  
Protected Friend stringForProjectAndHeirs As String  
Private numberForMeOnly As Integer  
```  
  
## <a name="net-framework-security"></a><span data-ttu-id="5a657-138">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="5a657-138">.NET Framework Security</span></span>  
 <span data-ttu-id="5a657-139">A configuração mais restritiva o nível de acesso de uma variável, menores as chances de código mal-intencionado pode fazer inadequado usá-lo.</span><span class="sxs-lookup"><span data-stu-id="5a657-139">The more restrictive the access level of a variable, the smaller the chances that malicious code can make improper use of it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a657-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5a657-140">See Also</span></span>  
 [<span data-ttu-id="5a657-141">Níveis de acesso no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5a657-141">Access levels in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [<span data-ttu-id="5a657-142">Instrução Dim</span><span class="sxs-lookup"><span data-stu-id="5a657-142">Dim Statement</span></span>](../../../../visual-basic/language-reference/statements/dim-statement.md)  
 [<span data-ttu-id="5a657-143">Público</span><span class="sxs-lookup"><span data-stu-id="5a657-143">Public</span></span>](../../../../visual-basic/language-reference/modifiers/public.md)  
 [<span data-ttu-id="5a657-144">Protegido</span><span class="sxs-lookup"><span data-stu-id="5a657-144">Protected</span></span>](../../../../visual-basic/language-reference/modifiers/protected.md)  
 [<span data-ttu-id="5a657-145">Friend</span><span class="sxs-lookup"><span data-stu-id="5a657-145">Friend</span></span>](../../../../visual-basic/language-reference/modifiers/friend.md)  
 [<span data-ttu-id="5a657-146">Privado</span><span class="sxs-lookup"><span data-stu-id="5a657-146">Private</span></span>](../../../../visual-basic/language-reference/modifiers/private.md)
