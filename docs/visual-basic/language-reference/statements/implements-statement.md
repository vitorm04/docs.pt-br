---
title: Instrução Implements (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Implements
- Implements
helpviewer_keywords:
- Implements statement [Visual Basic], syntax
- Implements statement [Visual Basic]
- interface implementation [Visual Basic], Implements statement
ms.assetid: 1fafb83f-f55a-4215-8ea9-681e8622613d
ms.openlocfilehash: 1f0c6b052ead303e0b43465dac2067422abc4ef8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61637733"
---
# <a name="implements-statement"></a><span data-ttu-id="d40f0-102">Instrução Implements</span><span class="sxs-lookup"><span data-stu-id="d40f0-102">Implements Statement</span></span>
<span data-ttu-id="d40f0-103">Especifica um ou mais interfaces, ou membros de interface, que devem ser implementados na classe ou definição de estrutura na qual ele aparece.</span><span class="sxs-lookup"><span data-stu-id="d40f0-103">Specifies one or more interfaces, or interface members, that must be implemented in the class or structure definition in which it appears.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d40f0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d40f0-104">Syntax</span></span>  
  
```  
Implements interfacename [, ...]  
-or-  
Implements interfacename.interfacemember [, ...]  
```  
  
## <a name="parts"></a><span data-ttu-id="d40f0-105">Partes</span><span class="sxs-lookup"><span data-stu-id="d40f0-105">Parts</span></span>  
 `interfacename`  
 <span data-ttu-id="d40f0-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="d40f0-106">Required.</span></span> <span data-ttu-id="d40f0-107">Uma interface cujas propriedades, procedimentos e eventos devem ser implementados por membros correspondentes na classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="d40f0-107">An interface whose properties, procedures, and events are to be implemented by corresponding members in the class or structure.</span></span>  
  
 `interfacemember`  
 <span data-ttu-id="d40f0-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="d40f0-108">Required.</span></span> <span data-ttu-id="d40f0-109">O membro de uma interface que está sendo implementado.</span><span class="sxs-lookup"><span data-stu-id="d40f0-109">The member of an interface that is being implemented.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d40f0-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="d40f0-110">Remarks</span></span>  
 <span data-ttu-id="d40f0-111">Uma interface é uma coleção de protótipos que representam os membros (propriedades, procedimentos e eventos) encapsula a interface.</span><span class="sxs-lookup"><span data-stu-id="d40f0-111">An interface is a collection of prototypes representing the members (properties, procedures, and events) the interface encapsulates.</span></span> <span data-ttu-id="d40f0-112">Interfaces contêm apenas as declarações de membros; classes e estruturas implementam esses membros.</span><span class="sxs-lookup"><span data-stu-id="d40f0-112">Interfaces contain only the declarations for members; classes and structures implement these members.</span></span> <span data-ttu-id="d40f0-113">Para obter mais informações, consulte [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md).</span><span class="sxs-lookup"><span data-stu-id="d40f0-113">For more information, see [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md).</span></span>  
  
 <span data-ttu-id="d40f0-114">O `Implements` instrução deve vir logo após o `Class` ou `Structure` instrução.</span><span class="sxs-lookup"><span data-stu-id="d40f0-114">The `Implements` statement must immediately follow the `Class` or `Structure` statement.</span></span>  
  
 <span data-ttu-id="d40f0-115">Quando você implementa uma interface, você deve implementar todos os membros declarados na interface.</span><span class="sxs-lookup"><span data-stu-id="d40f0-115">When you implement an interface, you must implement all the members declared in the interface.</span></span> <span data-ttu-id="d40f0-116">A omissão de qualquer membro é considerada um erro de sintaxe.</span><span class="sxs-lookup"><span data-stu-id="d40f0-116">Omitting any member is considered to be a syntax error.</span></span> <span data-ttu-id="d40f0-117">Para implementar um membro individual, você deve especificar o [Implements](../../../visual-basic/language-reference/statements/implements-clause.md) palavra-chave (que é separada do `Implements` instrução) quando você declara o membro na classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="d40f0-117">To implement an individual member, you specify the [Implements](../../../visual-basic/language-reference/statements/implements-clause.md) keyword (which is separate from the `Implements` statement) when you declare the member in the class or structure.</span></span> <span data-ttu-id="d40f0-118">Para obter mais informações, consulte [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md).</span><span class="sxs-lookup"><span data-stu-id="d40f0-118">For more information, see [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md).</span></span>  
  
 <span data-ttu-id="d40f0-119">As classes podem usar [privada](../../../visual-basic/language-reference/modifiers/private.md) implementações de propriedades e procedimentos, mas esses membros são acessíveis somente pela conversão de uma instância da classe de implementação em uma variável declarada para ser do tipo da interface.</span><span class="sxs-lookup"><span data-stu-id="d40f0-119">Classes can use [Private](../../../visual-basic/language-reference/modifiers/private.md) implementations of properties and procedures, but these members are accessible only by casting an instance of the implementing class into a variable declared to be of the type of the interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d40f0-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d40f0-120">Example</span></span>  
 <span data-ttu-id="d40f0-121">O exemplo a seguir mostra como usar o `Implements` instrução para implementar membros de uma interface.</span><span class="sxs-lookup"><span data-stu-id="d40f0-121">The following example shows how to use the `Implements` statement to implement members of an interface.</span></span> <span data-ttu-id="d40f0-122">Ele define uma interface denominada `ICustomerInfo` com um evento, uma propriedade e um procedimento.</span><span class="sxs-lookup"><span data-stu-id="d40f0-122">It defines an interface named `ICustomerInfo` with an event, a property, and a procedure.</span></span> <span data-ttu-id="d40f0-123">A classe `customerInfo` implementa todos os membros definidos na interface.</span><span class="sxs-lookup"><span data-stu-id="d40f0-123">The class `customerInfo` implements all the members defined in the interface.</span></span>  
  
 [!code-vb[VbVbalrStatements#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#33)]  
  
 <span data-ttu-id="d40f0-124">Observe que a classe `customerInfo` usa o `Implements` instrução em uma linha de código de origem separado para indicar que a classe implementa todos os membros do `ICustomerInfo` interface.</span><span class="sxs-lookup"><span data-stu-id="d40f0-124">Note that the class `customerInfo` uses the `Implements` statement on a separate source code line to indicate that the class implements all the members of the `ICustomerInfo` interface.</span></span> <span data-ttu-id="d40f0-125">Em seguida, cada membro na classe usa o `Implements` palavra-chave como parte de sua declaração de membro para indicar que ele implementa o membro da interface.</span><span class="sxs-lookup"><span data-stu-id="d40f0-125">Then each member in the class uses the `Implements` keyword as part of its member declaration to indicate that it implements that interface member.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d40f0-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d40f0-126">Example</span></span>  
 <span data-ttu-id="d40f0-127">Os dois procedimentos a seguir mostram como você poderia usar a interface implementada no exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="d40f0-127">The following two procedures show how you could use the interface implemented in the preceding example.</span></span> <span data-ttu-id="d40f0-128">Para testar a implementação, adicione esses procedimentos no seu projeto e chame o `testImplements` procedimento.</span><span class="sxs-lookup"><span data-stu-id="d40f0-128">To test the implementation, add these procedures to your project and call the `testImplements` procedure.</span></span>  
  
 [!code-vb[VbVbalrStatements#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#34)]  
  
## <a name="see-also"></a><span data-ttu-id="d40f0-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d40f0-129">See also</span></span>

- [<span data-ttu-id="d40f0-130">Implements</span><span class="sxs-lookup"><span data-stu-id="d40f0-130">Implements</span></span>](../../../visual-basic/language-reference/statements/implements-clause.md)
- [<span data-ttu-id="d40f0-131">Instrução Interface</span><span class="sxs-lookup"><span data-stu-id="d40f0-131">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)
- [<span data-ttu-id="d40f0-132">Interfaces</span><span class="sxs-lookup"><span data-stu-id="d40f0-132">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
