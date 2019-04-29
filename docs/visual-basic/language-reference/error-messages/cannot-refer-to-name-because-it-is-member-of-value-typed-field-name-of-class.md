---
title: Não é possível fazer referência a '<name>' porque ele é um membro do campo de tipo de valor '<name>' da classe '<classname>' que tem 'System.MarshalByRefObject' como uma classe base
ms.date: 07/20/2015
f1_keywords:
- vbc30310
- bc30310
helpviewer_keywords:
- BC30310
ms.assetid: 2aeb8872-7c87-4f01-98ef-9714ba3eebbe
ms.openlocfilehash: 78b0a3131b6e77ed257f200523ecebd4dfce3691
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61649927"
---
# <a name="cannot-refer-to-name-because-it-is-a-member-of-the-value-typed-field-name-of-class-classname-which-has-systemmarshalbyrefobject-as-a-base-class"></a><span data-ttu-id="b7186-102">Não é possível referenciar '\<nome >' porque ele é um membro do campo de tipo de valor '\<nome >' da classe\<classname >' que tem 'System. MarshalByRefObject' como uma classe base</span><span class="sxs-lookup"><span data-stu-id="b7186-102">Cannot refer to '\<name>' because it is a member of the value-typed field '\<name>' of class '\<classname>' which has 'System.MarshalByRefObject' as a base class</span></span>
<span data-ttu-id="b7186-103">O `System.MarshalByRefObject` classe permite que os aplicativos que dão suporte ao acesso remoto a objetos entre limites de domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b7186-103">The `System.MarshalByRefObject` class enables applications that support remote access to objects across application domain boundaries.</span></span> <span data-ttu-id="b7186-104">Tipos devem herdar a `MarshalByRejectObject` classe quando o tipo é usado entre os limites de domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b7186-104">Types must inherit from the `MarshalByRejectObject` class when the type is used across application domain boundaries.</span></span> <span data-ttu-id="b7186-105">O estado do objeto não deve ser copiado porque os membros do objeto não são utilizáveis fora do domínio de aplicativo no qual eles foram criados.</span><span class="sxs-lookup"><span data-stu-id="b7186-105">The state of the object must not be copied because the members of the object are not usable outside the application domain in which they were created.</span></span>  
  
 <span data-ttu-id="b7186-106">**ID do erro:** BC30310</span><span class="sxs-lookup"><span data-stu-id="b7186-106">**Error ID:** BC30310</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b7186-107">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="b7186-107">To correct this error</span></span>  
  
1. <span data-ttu-id="b7186-108">Verifique se a referência para garantir que o membro que está sendo referenciado é válido.</span><span class="sxs-lookup"><span data-stu-id="b7186-108">Check the reference to make sure the member being referred to is valid.</span></span>  
  
2. <span data-ttu-id="b7186-109">Qualifique explicitamente o membro com o `Me` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="b7186-109">Explicitly qualify the member with the `Me` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7186-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b7186-110">See also</span></span>

- <xref:System.MarshalByRefObject>
- [<span data-ttu-id="b7186-111">Instrução Dim</span><span class="sxs-lookup"><span data-stu-id="b7186-111">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)
