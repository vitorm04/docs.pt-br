---
title: "Como: controlar a disponibilidade de uma variável (Visual Basic) | Documentos do Microsoft"
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
- access levels, declared elements
- Private keyword, accessing variables
- access levels, variables
- Public keyword, accessing variables
- Friend keyword, accessing variables
- variables [Visual Basic], access level
- declared elements, access level
- Protected keyword, accessing variables
ms.assetid: eaf4f073-7922-43ce-ae1e-90ff376ae947
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
ms.openlocfilehash: 87e88f3fc3b32a945ab048f5625983b7c2cefb86
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-control-the-availability-of-a-variable-visual-basic"></a><span data-ttu-id="439d9-102">Como controlar a disponibilidade de uma variável (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="439d9-102">How to: Control the Availability of a Variable (Visual Basic)</span></span>
<span data-ttu-id="439d9-103">Controlar a disponibilidade de uma variável especificando seu *nível de acesso*.</span><span class="sxs-lookup"><span data-stu-id="439d9-103">You control the availability of a variable by specifying its *access level*.</span></span> <span data-ttu-id="439d9-104">O nível de acesso determina qual código tem permissão para ler ou gravar na variável.</span><span class="sxs-lookup"><span data-stu-id="439d9-104">The access level determines what code has permission to read or write to the variable.</span></span>  
  
-   <span data-ttu-id="439d9-105">*Variáveis de membro* (definida no nível de módulo e fora de qualquer procedimento) padrão para acesso público, o que significa que qualquer código que pode vê-los pode acessá-los.</span><span class="sxs-lookup"><span data-stu-id="439d9-105">*Member variables* (defined at module level and outside any procedure) default to public access, which means any code that can see them can access them.</span></span> <span data-ttu-id="439d9-106">Você pode alterar isso, especificando um modificador de acesso.</span><span class="sxs-lookup"><span data-stu-id="439d9-106">You can change this by specifying an access modifier.</span></span>  
  
-   <span data-ttu-id="439d9-107">*Variáveis locais* (definido dentro de um procedimento) nominais têm acesso público, embora somente o código dentro de seu procedimento possa acessá-los.</span><span class="sxs-lookup"><span data-stu-id="439d9-107">*Local variables* (defined inside a procedure) nominally have public access, although only code within their procedure can access them.</span></span> <span data-ttu-id="439d9-108">Você não pode alterar o nível de acesso de uma variável local, mas você pode alterar o nível de acesso do procedimento que o contém.</span><span class="sxs-lookup"><span data-stu-id="439d9-108">You cannot change the access level of a local variable, but you can change the access level of the procedure that contains it.</span></span>  
  
 <span data-ttu-id="439d9-109">Para obter mais informações, consulte [níveis de acesso no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="439d9-109">For more information, see [Access Levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
## <a name="private-and-public-access"></a><span data-ttu-id="439d9-110">Acesso privado e público</span><span class="sxs-lookup"><span data-stu-id="439d9-110">Private and Public Access</span></span>  
  
#### <a name="to-make-a-variable-accessible-only-from-within-its-module-class-or-structure"></a><span data-ttu-id="439d9-111">Para fazer uma variável acessível somente dentro do seu módulo, classe ou estrutura</span><span class="sxs-lookup"><span data-stu-id="439d9-111">To make a variable accessible only from within its module, class, or structure</span></span>  
  
1.  <span data-ttu-id="439d9-112">Local de [instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) para a variável dentro do módulo, classe ou estrutura, mas fora de qualquer procedimento.</span><span class="sxs-lookup"><span data-stu-id="439d9-112">Place the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) for the variable inside the module, class, or structure, but outside any procedure.</span></span>  
  
2.  <span data-ttu-id="439d9-113">Incluir o [particular](../../../../visual-basic/language-reference/modifiers/private.md) palavra-chave no `Dim` instrução.</span><span class="sxs-lookup"><span data-stu-id="439d9-113">Include the [Private](../../../../visual-basic/language-reference/modifiers/private.md) keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="439d9-114">Você pode ler ou gravar a variável em qualquer lugar dentro do módulo, classe ou estrutura, mas não de fora dele.</span><span class="sxs-lookup"><span data-stu-id="439d9-114">You can read or write to the variable from anywhere within the module, class, or structure, but not from outside it.</span></span>  
  
#### <a name="to-make-a-variable-accessible-from-any-code-that-can-see-it"></a><span data-ttu-id="439d9-115">Para tornar acessível de qualquer código que possa vê-la uma variável</span><span class="sxs-lookup"><span data-stu-id="439d9-115">To make a variable accessible from any code that can see it</span></span>  
  
1.  <span data-ttu-id="439d9-116">Para uma variável de membro, coloque o `Dim` instrução para a variável dentro de um módulo, classe ou estrutura, mas fora de qualquer procedimento.</span><span class="sxs-lookup"><span data-stu-id="439d9-116">For a member variable, place the `Dim` statement for the variable inside a module, class, or structure, but outside any procedure.</span></span>  
  
2.  <span data-ttu-id="439d9-117">Incluir o [pública](../../../../visual-basic/language-reference/modifiers/public.md) palavra-chave no `Dim` instrução.</span><span class="sxs-lookup"><span data-stu-id="439d9-117">Include the [Public](../../../../visual-basic/language-reference/modifiers/public.md) keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="439d9-118">Você pode ler ou gravar a variável de qualquer código que interopera com o assembly.</span><span class="sxs-lookup"><span data-stu-id="439d9-118">You can read or write to the variable from any code that interoperates with your assembly.</span></span>  
  
 <span data-ttu-id="439d9-119">-ou-</span><span class="sxs-lookup"><span data-stu-id="439d9-119">-or-</span></span>  
  
1.  <span data-ttu-id="439d9-120">Para uma variável local, coloque o `Dim` instrução para a variável dentro de um procedimento.</span><span class="sxs-lookup"><span data-stu-id="439d9-120">For a local variable, place the `Dim` statement for the variable inside a procedure.</span></span>  
  
2.  <span data-ttu-id="439d9-121">Não inclua o `Public` palavra-chave no `Dim` instrução.</span><span class="sxs-lookup"><span data-stu-id="439d9-121">Do not include the `Public` keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="439d9-122">Você pode ler ou gravar a variável em qualquer lugar dentro do procedimento, mas não de fora dele.</span><span class="sxs-lookup"><span data-stu-id="439d9-122">You can read or write to the variable from anywhere within the procedure, but not from outside it.</span></span>  
  
## <a name="protected-and-friend-access"></a><span data-ttu-id="439d9-123">Protegidos e o acesso de amigo</span><span class="sxs-lookup"><span data-stu-id="439d9-123">Protected and Friend Access</span></span>  
 <span data-ttu-id="439d9-124">Você pode limitar o nível de acesso de uma variável para sua classe e quaisquer classes derivadas, ou seu assembly.</span><span class="sxs-lookup"><span data-stu-id="439d9-124">You can limit the access level of a variable to its class and any derived classes, or to its assembly.</span></span> <span data-ttu-id="439d9-125">Você também pode especificar a união dessas limitações, que permite o acesso do código em qualquer classe derivada ou em qualquer outro lugar no mesmo assembly.</span><span class="sxs-lookup"><span data-stu-id="439d9-125">You can also specify the union of these limitations, which allows access from code in any derived class or in any other place in the same assembly.</span></span> <span data-ttu-id="439d9-126">Especificar essa união combinando o `Protected` e `Friend` palavras-chave na mesma declaração.</span><span class="sxs-lookup"><span data-stu-id="439d9-126">You specify this union by combining the `Protected` and `Friend` keywords in the same declaration.</span></span>  
  
#### <a name="to-make-a-variable-accessible-only-from-within-its-class-and-any-derived-classes"></a><span data-ttu-id="439d9-127">Para fazer uma variável acessível somente dentro de sua classe e quaisquer classes derivadas</span><span class="sxs-lookup"><span data-stu-id="439d9-127">To make a variable accessible only from within its class and any derived classes</span></span>  
  
1.  <span data-ttu-id="439d9-128">Local de `Dim` instrução para a variável dentro de uma classe, mas fora de qualquer procedimento.</span><span class="sxs-lookup"><span data-stu-id="439d9-128">Place the `Dim` statement for the variable inside a class, but outside any procedure.</span></span>  
  
2.  <span data-ttu-id="439d9-129">Incluir o [protegido](../../../../visual-basic/language-reference/modifiers/protected.md) palavra-chave no `Dim` instrução.</span><span class="sxs-lookup"><span data-stu-id="439d9-129">Include the [Protected](../../../../visual-basic/language-reference/modifiers/protected.md) keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="439d9-130">Você pode ler ou gravar a variável em qualquer lugar dentro da classe, bem como do qualquer classe derivada dela, mas não de fora de qualquer classe na cadeia de derivação.</span><span class="sxs-lookup"><span data-stu-id="439d9-130">You can read or write to the variable from anywhere within the class, as well as from within any class derived from it, but not from outside any class in the derivation chain.</span></span>  
  
#### <a name="to-make-a-variable-accessible-only-from-within-the-same-assembly"></a><span data-ttu-id="439d9-131">Para fazer uma variável acessível somente dentro do mesmo assembly</span><span class="sxs-lookup"><span data-stu-id="439d9-131">To make a variable accessible only from within the same assembly</span></span>  
  
1.  <span data-ttu-id="439d9-132">Local de `Dim` instrução para a variável dentro de um módulo, classe ou estrutura, mas fora de qualquer procedimento.</span><span class="sxs-lookup"><span data-stu-id="439d9-132">Place the `Dim` statement for the variable inside a module, class, or structure, but outside any procedure.</span></span>  
  
2.  <span data-ttu-id="439d9-133">Incluir o [amigo](../../../../visual-basic/language-reference/modifiers/friend.md) palavra-chave no `Dim` instrução.</span><span class="sxs-lookup"><span data-stu-id="439d9-133">Include the [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="439d9-134">Você pode ler ou gravar a variável em qualquer lugar dentro do módulo, classe ou estrutura, bem como qualquer código no mesmo assembly, mas não de fora do assembly.</span><span class="sxs-lookup"><span data-stu-id="439d9-134">You can read or write to the variable from anywhere within the module, class, or structure, as well as from any code in the same assembly, but not from outside the assembly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="439d9-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="439d9-135">Example</span></span>  
 <span data-ttu-id="439d9-136">O exemplo a seguir mostra as declarações de variáveis com `Public`, `Protected`, `Friend`, `Protected Friend`, e `Private` níveis de acesso.</span><span class="sxs-lookup"><span data-stu-id="439d9-136">The following example shows declarations of variables with `Public`, `Protected`, `Friend`, `Protected Friend`, and `Private` access levels.</span></span> <span data-ttu-id="439d9-137">Observe que, quando o `Dim` instrução Especifica um nível de acesso, você não precisa incluir o `Dim` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="439d9-137">Note that when the `Dim` statement specifies an access level, you do not need to include the `Dim` keyword.</span></span>  
  
```  
Public Class classForEverybody  
Protected Class classForMyHeirs  
Friend stringForThisProject As String  
Protected Friend stringForProjectAndHeirs As String  
Private numberForMeOnly As Integer  
```  
  
## <a name="net-framework-security"></a><span data-ttu-id="439d9-138">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="439d9-138">.NET Framework Security</span></span>  
 <span data-ttu-id="439d9-139">A configuração mais restritiva do nível de acesso de uma variável, menores as chances de código mal-intencionado pode fazer inadequado usá-lo.</span><span class="sxs-lookup"><span data-stu-id="439d9-139">The more restrictive the access level of a variable, the smaller the chances that malicious code can make improper use of it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="439d9-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="439d9-140">See Also</span></span>  
 <span data-ttu-id="439d9-141">[Níveis de acesso no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md) </span><span class="sxs-lookup"><span data-stu-id="439d9-141">[Access Levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md) </span></span>  
<span data-ttu-id="439d9-142"> [Instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) </span><span class="sxs-lookup"><span data-stu-id="439d9-142"> [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) </span></span>  
<span data-ttu-id="439d9-143"> [Público](../../../../visual-basic/language-reference/modifiers/public.md) </span><span class="sxs-lookup"><span data-stu-id="439d9-143"> [Public](../../../../visual-basic/language-reference/modifiers/public.md) </span></span>  
<span data-ttu-id="439d9-144"> [Protegido](../../../../visual-basic/language-reference/modifiers/protected.md) </span><span class="sxs-lookup"><span data-stu-id="439d9-144"> [Protected](../../../../visual-basic/language-reference/modifiers/protected.md) </span></span>  
<span data-ttu-id="439d9-145"> [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) </span><span class="sxs-lookup"><span data-stu-id="439d9-145"> [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) </span></span>  
<span data-ttu-id="439d9-146"> [Privado](../../../../visual-basic/language-reference/modifiers/private.md)</span><span class="sxs-lookup"><span data-stu-id="439d9-146"> [Private](../../../../visual-basic/language-reference/modifiers/private.md)</span></span>
