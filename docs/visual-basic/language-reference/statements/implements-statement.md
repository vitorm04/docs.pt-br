---
title: "Implementa a instrução | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Implements
- Implements
dev_langs:
- VB
helpviewer_keywords:
- Implements statement, syntax
- Implements statement
- interface implementation, Implements statement
ms.assetid: 1fafb83f-f55a-4215-8ea9-681e8622613d
caps.latest.revision: 17
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
ms.openlocfilehash: d005ead4f55123a1cbfc4974930d8036f857d2f4
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="implements-statement"></a><span data-ttu-id="fce28-102">Instrução Implements</span><span class="sxs-lookup"><span data-stu-id="fce28-102">Implements Statement</span></span>
<span data-ttu-id="fce28-103">Especifica uma ou mais interfaces, ou membros de interface, que devem ser implementados na classe ou definição de estrutura na qual ele aparece.</span><span class="sxs-lookup"><span data-stu-id="fce28-103">Specifies one or more interfaces, or interface members, that must be implemented in the class or structure definition in which it appears.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fce28-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fce28-104">Syntax</span></span>  
  
```  
Implements interfacename [, ...]  
-or-  
Implements interfacename.interfacemember [, ...]  
```  
  
## <a name="parts"></a><span data-ttu-id="fce28-105">Partes</span><span class="sxs-lookup"><span data-stu-id="fce28-105">Parts</span></span>  
 `interfacename`  
 <span data-ttu-id="fce28-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="fce28-106">Required.</span></span> <span data-ttu-id="fce28-107">Uma interface cujas propriedades, procedimentos e eventos está para ser implementados por membros correspondentes na classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="fce28-107">An interface whose properties, procedures, and events are to be implemented by corresponding members in the class or structure.</span></span>  
  
 `interfacemember`  
 <span data-ttu-id="fce28-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="fce28-108">Required.</span></span> <span data-ttu-id="fce28-109">O membro de uma interface que está sendo implementado.</span><span class="sxs-lookup"><span data-stu-id="fce28-109">The member of an interface that is being implemented.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fce28-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="fce28-110">Remarks</span></span>  
 <span data-ttu-id="fce28-111">Uma interface é uma coleção de protótipos que representa os membros (propriedades, procedimentos e eventos) encapsula a interface.</span><span class="sxs-lookup"><span data-stu-id="fce28-111">An interface is a collection of prototypes representing the members (properties, procedures, and events) the interface encapsulates.</span></span> <span data-ttu-id="fce28-112">Interfaces contêm somente as declarações de membros; classes e estruturas implementam esses membros.</span><span class="sxs-lookup"><span data-stu-id="fce28-112">Interfaces contain only the declarations for members; classes and structures implement these members.</span></span> <span data-ttu-id="fce28-113">Para obter mais informações, consulte [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md).</span><span class="sxs-lookup"><span data-stu-id="fce28-113">For more information, see [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md).</span></span>  
  
 <span data-ttu-id="fce28-114">O `Implements` instrução deve seguir imediatamente o `Class` ou `Structure` instrução.</span><span class="sxs-lookup"><span data-stu-id="fce28-114">The `Implements` statement must immediately follow the `Class` or `Structure` statement.</span></span>  
  
 <span data-ttu-id="fce28-115">Quando você implementa uma interface, você deve implementar todos os membros declarados na interface.</span><span class="sxs-lookup"><span data-stu-id="fce28-115">When you implement an interface, you must implement all the members declared in the interface.</span></span> <span data-ttu-id="fce28-116">Omitir qualquer membro é considerado um erro de sintaxe.</span><span class="sxs-lookup"><span data-stu-id="fce28-116">Omitting any member is considered to be a syntax error.</span></span> <span data-ttu-id="fce28-117">Para implementar um membro individual, você deve especificar o [implementa](../../../visual-basic/language-reference/statements/implements-clause.md) palavra-chave (que é separada do `Implements` instrução) quando você declara o membro na classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="fce28-117">To implement an individual member, you specify the [Implements](../../../visual-basic/language-reference/statements/implements-clause.md) keyword (which is separate from the `Implements` statement) when you declare the member in the class or structure.</span></span> <span data-ttu-id="fce28-118">Para obter mais informações, consulte [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md).</span><span class="sxs-lookup"><span data-stu-id="fce28-118">For more information, see [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md).</span></span>  
  
 <span data-ttu-id="fce28-119">Classes podem usar [particular](../../../visual-basic/language-reference/modifiers/private.md) implementações de propriedades e procedimentos, mas esses membros são acessíveis somente chamando uma instância da classe implementada dentro de uma variável declarada para ser do tipo da interface.</span><span class="sxs-lookup"><span data-stu-id="fce28-119">Classes can use [Private](../../../visual-basic/language-reference/modifiers/private.md) implementations of properties and procedures, but these members are accessible only by casting an instance of the implementing class into a variable declared to be of the type of the interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fce28-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fce28-120">Example</span></span>  
 <span data-ttu-id="fce28-121">O exemplo a seguir mostra como usar o `Implements` instrução para implementar membros de uma interface.</span><span class="sxs-lookup"><span data-stu-id="fce28-121">The following example shows how to use the `Implements` statement to implement members of an interface.</span></span> <span data-ttu-id="fce28-122">Ele define uma interface nomeada `ICustomerInfo` com um evento, uma propriedade e um procedimento.</span><span class="sxs-lookup"><span data-stu-id="fce28-122">It defines an interface named `ICustomerInfo` with an event, a property, and a procedure.</span></span> <span data-ttu-id="fce28-123">A classe `customerInfo` implementa todos os membros definidos na interface.</span><span class="sxs-lookup"><span data-stu-id="fce28-123">The class `customerInfo` implements all the members defined in the interface.</span></span>  
  
 <span data-ttu-id="fce28-124">[!code-vb[33 VbVbalrStatements](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/implements-statement_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="fce28-124">[!code-vb[VbVbalrStatements#33](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/implements-statement_1.vb)]</span></span>  
  
 <span data-ttu-id="fce28-125">Observe que a classe `customerInfo` usa o `Implements` instrução em uma linha de código fonte separado para indicar que a classe implementa todos os membros do `ICustomerInfo` interface.</span><span class="sxs-lookup"><span data-stu-id="fce28-125">Note that the class `customerInfo` uses the `Implements` statement on a separate source code line to indicate that the class implements all the members of the `ICustomerInfo` interface.</span></span> <span data-ttu-id="fce28-126">Cada membro na classe usa a `Implements` palavra-chave como parte de sua declaração de membros para indicar que ele implementa o membro da interface.</span><span class="sxs-lookup"><span data-stu-id="fce28-126">Then each member in the class uses the `Implements` keyword as part of its member declaration to indicate that it implements that interface member.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fce28-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fce28-127">Example</span></span>  
 <span data-ttu-id="fce28-128">Os dois procedimentos a seguir mostram como usar a interface implementada no exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="fce28-128">The following two procedures show how you could use the interface implemented in the preceding example.</span></span> <span data-ttu-id="fce28-129">Para testar a implementação, adicione esses procedimentos no seu projeto e chame o `testImplements` procedimento.</span><span class="sxs-lookup"><span data-stu-id="fce28-129">To test the implementation, add these procedures to your project and call the `testImplements` procedure.</span></span>  
  
 <span data-ttu-id="fce28-130">[!code-vb[VbVbalrStatements&#34;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/implements-statement_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="fce28-130">[!code-vb[VbVbalrStatements#34](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/implements-statement_2.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fce28-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fce28-131">See Also</span></span>  
 <span data-ttu-id="fce28-132">[Implementa](../../../visual-basic/language-reference/statements/implements-clause.md) </span><span class="sxs-lookup"><span data-stu-id="fce28-132">[Implements](../../../visual-basic/language-reference/statements/implements-clause.md) </span></span>  
<span data-ttu-id="fce28-133"> [Instrução interface](../../../visual-basic/language-reference/statements/interface-statement.md) </span><span class="sxs-lookup"><span data-stu-id="fce28-133"> [Interface Statement](../../../visual-basic/language-reference/statements/interface-statement.md) </span></span>  
<span data-ttu-id="fce28-134"> [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md)</span><span class="sxs-lookup"><span data-stu-id="fce28-134"> [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md)</span></span>
