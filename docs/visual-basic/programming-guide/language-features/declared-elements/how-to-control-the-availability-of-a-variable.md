---
title: Como controlar a disponibilidade de uma variável
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
ms.openlocfilehash: e6173a0eaa0bf84abb1979711c6df932533c5ce9
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91086108"
---
# <a name="how-to-control-the-availability-of-a-variable-visual-basic"></a><span data-ttu-id="08312-102">Como controlar a disponibilidade de uma variável (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="08312-102">How to: Control the Availability of a Variable (Visual Basic)</span></span>

<span data-ttu-id="08312-103">Você controla a disponibilidade de uma variável especificando seu *nível de acesso*.</span><span class="sxs-lookup"><span data-stu-id="08312-103">You control the availability of a variable by specifying its *access level*.</span></span> <span data-ttu-id="08312-104">O nível de acesso determina qual código tem permissão para ler ou gravar na variável.</span><span class="sxs-lookup"><span data-stu-id="08312-104">The access level determines what code has permission to read or write to the variable.</span></span>  
  
- <span data-ttu-id="08312-105">As *variáveis de membro* (definidas em nível de módulo e fora de qualquer procedimento) assumem o padrão de acesso público, o que significa que qualquer código que possa vê-las pode acessá-las.</span><span class="sxs-lookup"><span data-stu-id="08312-105">*Member variables* (defined at module level and outside any procedure) default to public access, which means any code that can see them can access them.</span></span> <span data-ttu-id="08312-106">Você pode alterar isso especificando um modificador de acesso.</span><span class="sxs-lookup"><span data-stu-id="08312-106">You can change this by specifying an access modifier.</span></span>  
  
- <span data-ttu-id="08312-107">As *variáveis locais* (definidas dentro de um procedimento) nominalmente têm acesso público, embora apenas o código dentro de seu procedimento possa acessá-las.</span><span class="sxs-lookup"><span data-stu-id="08312-107">*Local variables* (defined inside a procedure) nominally have public access, although only code within their procedure can access them.</span></span> <span data-ttu-id="08312-108">Você não pode alterar o nível de acesso de uma variável local, mas pode alterar o nível de acesso do procedimento que a contém.</span><span class="sxs-lookup"><span data-stu-id="08312-108">You cannot change the access level of a local variable, but you can change the access level of the procedure that contains it.</span></span>  
  
 <span data-ttu-id="08312-109">Para obter mais informações, consulte [níveis de acesso em Visual Basic](access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="08312-109">For more information, see [Access levels in Visual Basic](access-levels.md).</span></span>  
  
## <a name="private-and-public-access"></a><span data-ttu-id="08312-110">Acesso público e privado</span><span class="sxs-lookup"><span data-stu-id="08312-110">Private and Public Access</span></span>  
  
#### <a name="to-make-a-variable-accessible-only-from-within-its-module-class-or-structure"></a><span data-ttu-id="08312-111">Para tornar uma variável acessível somente de dentro de seu módulo, classe ou estrutura</span><span class="sxs-lookup"><span data-stu-id="08312-111">To make a variable accessible only from within its module, class, or structure</span></span>  
  
1. <span data-ttu-id="08312-112">Coloque a [instrução Dim](../../../language-reference/statements/dim-statement.md) para a variável dentro do módulo, da classe ou da estrutura, mas fora de qualquer procedimento.</span><span class="sxs-lookup"><span data-stu-id="08312-112">Place the [Dim Statement](../../../language-reference/statements/dim-statement.md) for the variable inside the module, class, or structure, but outside any procedure.</span></span>  
  
2. <span data-ttu-id="08312-113">Inclua a palavra-chave [Private](../../../language-reference/modifiers/private.md) na `Dim` instrução.</span><span class="sxs-lookup"><span data-stu-id="08312-113">Include the [Private](../../../language-reference/modifiers/private.md) keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="08312-114">Você pode ler ou gravar na variável de qualquer lugar dentro do módulo, da classe ou da estrutura, mas não de fora dela.</span><span class="sxs-lookup"><span data-stu-id="08312-114">You can read or write to the variable from anywhere within the module, class, or structure, but not from outside it.</span></span>  
  
#### <a name="to-make-a-variable-accessible-from-any-code-that-can-see-it"></a><span data-ttu-id="08312-115">Para tornar uma variável acessível de qualquer código que possa vê-la</span><span class="sxs-lookup"><span data-stu-id="08312-115">To make a variable accessible from any code that can see it</span></span>  
  
1. <span data-ttu-id="08312-116">Para uma variável de membro, coloque a `Dim` instrução para a variável dentro de um módulo, classe ou estrutura, mas fora de qualquer procedimento.</span><span class="sxs-lookup"><span data-stu-id="08312-116">For a member variable, place the `Dim` statement for the variable inside a module, class, or structure, but outside any procedure.</span></span>  
  
2. <span data-ttu-id="08312-117">Inclua a palavra-chave [Public](../../../language-reference/modifiers/public.md) na `Dim` instrução.</span><span class="sxs-lookup"><span data-stu-id="08312-117">Include the [Public](../../../language-reference/modifiers/public.md) keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="08312-118">Você pode ler ou gravar na variável de qualquer código que interopere com seu assembly.</span><span class="sxs-lookup"><span data-stu-id="08312-118">You can read or write to the variable from any code that interoperates with your assembly.</span></span>  
  
 <span data-ttu-id="08312-119">- ou -</span><span class="sxs-lookup"><span data-stu-id="08312-119">-or-</span></span>  
  
1. <span data-ttu-id="08312-120">Para uma variável local, coloque a `Dim` instrução para a variável dentro de um procedimento.</span><span class="sxs-lookup"><span data-stu-id="08312-120">For a local variable, place the `Dim` statement for the variable inside a procedure.</span></span>  
  
2. <span data-ttu-id="08312-121">Não inclua a `Public` palavra-chave na `Dim` instrução.</span><span class="sxs-lookup"><span data-stu-id="08312-121">Do not include the `Public` keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="08312-122">Você pode ler ou gravar na variável de qualquer lugar dentro do procedimento, mas não de fora dela.</span><span class="sxs-lookup"><span data-stu-id="08312-122">You can read or write to the variable from anywhere within the procedure, but not from outside it.</span></span>  
  
## <a name="protected-and-friend-access"></a><span data-ttu-id="08312-123">Acesso protegido e amigo</span><span class="sxs-lookup"><span data-stu-id="08312-123">Protected and Friend Access</span></span>  

 <span data-ttu-id="08312-124">Você pode limitar o nível de acesso de uma variável à sua classe e a todas as classes derivadas ou a seu assembly.</span><span class="sxs-lookup"><span data-stu-id="08312-124">You can limit the access level of a variable to its class and any derived classes, or to its assembly.</span></span> <span data-ttu-id="08312-125">Você também pode especificar a União dessas limitações, que permite o acesso a partir do código em qualquer classe derivada ou em qualquer outro lugar no mesmo assembly.</span><span class="sxs-lookup"><span data-stu-id="08312-125">You can also specify the union of these limitations, which allows access from code in any derived class or in any other place in the same assembly.</span></span> <span data-ttu-id="08312-126">Você especifica essa União combinando as `Protected` `Friend` palavras-chave e na mesma declaração.</span><span class="sxs-lookup"><span data-stu-id="08312-126">You specify this union by combining the `Protected` and `Friend` keywords in the same declaration.</span></span>  
  
#### <a name="to-make-a-variable-accessible-only-from-within-its-class-and-any-derived-classes"></a><span data-ttu-id="08312-127">Para tornar uma variável acessível somente de dentro de sua classe e de quaisquer classes derivadas</span><span class="sxs-lookup"><span data-stu-id="08312-127">To make a variable accessible only from within its class and any derived classes</span></span>  
  
1. <span data-ttu-id="08312-128">Coloque a `Dim` instrução para a variável dentro de uma classe, mas fora de qualquer procedimento.</span><span class="sxs-lookup"><span data-stu-id="08312-128">Place the `Dim` statement for the variable inside a class, but outside any procedure.</span></span>  
  
2. <span data-ttu-id="08312-129">Inclua a palavra-chave [Protected](../../../language-reference/modifiers/protected.md) na `Dim` instrução.</span><span class="sxs-lookup"><span data-stu-id="08312-129">Include the [Protected](../../../language-reference/modifiers/protected.md) keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="08312-130">Você pode ler ou gravar na variável de qualquer lugar dentro da classe, bem como de dentro de qualquer classe derivada dela, mas não de fora de nenhuma classe na cadeia de derivação.</span><span class="sxs-lookup"><span data-stu-id="08312-130">You can read or write to the variable from anywhere within the class, as well as from within any class derived from it, but not from outside any class in the derivation chain.</span></span>  
  
#### <a name="to-make-a-variable-accessible-only-from-within-the-same-assembly"></a><span data-ttu-id="08312-131">Para tornar uma variável acessível somente de dentro do mesmo assembly</span><span class="sxs-lookup"><span data-stu-id="08312-131">To make a variable accessible only from within the same assembly</span></span>  
  
1. <span data-ttu-id="08312-132">Coloque a `Dim` instrução para a variável dentro de um módulo, classe ou estrutura, mas fora de qualquer procedimento.</span><span class="sxs-lookup"><span data-stu-id="08312-132">Place the `Dim` statement for the variable inside a module, class, or structure, but outside any procedure.</span></span>  
  
2. <span data-ttu-id="08312-133">Inclua a palavra-chave [Friend](../../../language-reference/modifiers/friend.md) na `Dim` instrução.</span><span class="sxs-lookup"><span data-stu-id="08312-133">Include the [Friend](../../../language-reference/modifiers/friend.md) keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="08312-134">Você pode ler ou gravar na variável de qualquer lugar dentro do módulo, da classe ou da estrutura, bem como de qualquer código no mesmo assembly, mas não de fora do assembly.</span><span class="sxs-lookup"><span data-stu-id="08312-134">You can read or write to the variable from anywhere within the module, class, or structure, as well as from any code in the same assembly, but not from outside the assembly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="08312-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="08312-135">Example</span></span>  

 <span data-ttu-id="08312-136">O exemplo a seguir mostra declarações de variáveis `Public` com `Protected` `Friend` os níveis de acesso,,, `Protected Friend` e `Private` .</span><span class="sxs-lookup"><span data-stu-id="08312-136">The following example shows declarations of variables with `Public`, `Protected`, `Friend`, `Protected Friend`, and `Private` access levels.</span></span> <span data-ttu-id="08312-137">Observe que, quando a `Dim` instrução especifica um nível de acesso, você não precisa incluir a `Dim` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="08312-137">Note that when the `Dim` statement specifies an access level, you do not need to include the `Dim` keyword.</span></span>  
  
```vb  
Public Class classForEverybody  
Protected Class classForMyHeirs  
Friend stringForThisProject As String  
Protected Friend stringForProjectAndHeirs As String  
Private numberForMeOnly As Integer  
```  
  
## <a name="net-framework-security"></a><span data-ttu-id="08312-138">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="08312-138">.NET Framework Security</span></span>  

 <span data-ttu-id="08312-139">Quanto mais restritiva for o nível de acesso de uma variável, menor será a probabilidade de que o código mal-intencionado possa usar o uso impróprio.</span><span class="sxs-lookup"><span data-stu-id="08312-139">The more restrictive the access level of a variable, the smaller the chances that malicious code can make improper use of it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08312-140">Confira também</span><span class="sxs-lookup"><span data-stu-id="08312-140">See also</span></span>

- [<span data-ttu-id="08312-141">Níveis de acesso no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="08312-141">Access levels in Visual Basic</span></span>](access-levels.md)
- [<span data-ttu-id="08312-142">Instrução Dim</span><span class="sxs-lookup"><span data-stu-id="08312-142">Dim Statement</span></span>](../../../language-reference/statements/dim-statement.md)
- [<span data-ttu-id="08312-143">Pública</span><span class="sxs-lookup"><span data-stu-id="08312-143">Public</span></span>](../../../language-reference/modifiers/public.md)
- [<span data-ttu-id="08312-144">Protected</span><span class="sxs-lookup"><span data-stu-id="08312-144">Protected</span></span>](../../../language-reference/modifiers/protected.md)
- [<span data-ttu-id="08312-145">Friend</span><span class="sxs-lookup"><span data-stu-id="08312-145">Friend</span></span>](../../../language-reference/modifiers/friend.md)
- [<span data-ttu-id="08312-146">Privado</span><span class="sxs-lookup"><span data-stu-id="08312-146">Private</span></span>](../../../language-reference/modifiers/private.md)
