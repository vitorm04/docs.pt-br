---
title: Não é possível referenciar &#39; &lt;nome&gt; &#39; porque ele é um membro do campo de tipo de valor &#39; &lt;nome&gt; &#39; da classe &#39; &lt;classname&gt; &#39;que tem &#39;MarshalByRefObject&#39; como uma classe base
ms.date: 07/20/2015
f1_keywords:
- vbc30310
- bc30310
helpviewer_keywords:
- BC30310
ms.assetid: 2aeb8872-7c87-4f01-98ef-9714ba3eebbe
ms.openlocfilehash: f44d33c9d51148e6bbcfbf5db4dbc115101df1f1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33586341"
---
# <a name="cannot-refer-to-39ltnamegt39-because-it-is-a-member-of-the-value-typed-field-39ltnamegt39-of-class-39ltclassnamegt39-which-has-39systemmarshalbyrefobject39-as-a-base-class"></a><span data-ttu-id="0e5fc-102">Não é possível referenciar &#39; &lt;nome&gt; &#39; porque ele é um membro do campo de tipo de valor &#39; &lt;nome&gt; &#39; da classe &#39; &lt;classname&gt; &#39;que tem &#39;MarshalByRefObject&#39; como uma classe base</span><span class="sxs-lookup"><span data-stu-id="0e5fc-102">Cannot refer to &#39;&lt;name&gt;&#39; because it is a member of the value-typed field &#39;&lt;name&gt;&#39; of class &#39;&lt;classname&gt;&#39; which has &#39;System.MarshalByRefObject&#39; as a base class</span></span>
<span data-ttu-id="0e5fc-103">O `System.MarshalByRefObject` classe permite que os aplicativos que oferecem suporte a acesso remoto a objetos nos limites do domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0e5fc-103">The `System.MarshalByRefObject` class enables applications that support remote access to objects across application domain boundaries.</span></span> <span data-ttu-id="0e5fc-104">Tipos devem herdar do `MarshalByRejectObject` classe quando o tipo é usado além dos limites do domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0e5fc-104">Types must inherit from the `MarshalByRejectObject` class when the type is used across application domain boundaries.</span></span> <span data-ttu-id="0e5fc-105">O estado do objeto não deve ser copiado porque os membros do objeto não são utilizáveis fora do domínio de aplicativo no qual eles foram criados.</span><span class="sxs-lookup"><span data-stu-id="0e5fc-105">The state of the object must not be copied because the members of the object are not usable outside the application domain in which they were created.</span></span>  
  
 <span data-ttu-id="0e5fc-106">**ID do erro:** BC30310</span><span class="sxs-lookup"><span data-stu-id="0e5fc-106">**Error ID:** BC30310</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0e5fc-107">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="0e5fc-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="0e5fc-108">Verifique se a referência para certificar-se de que o membro que está sendo referenciado é válido.</span><span class="sxs-lookup"><span data-stu-id="0e5fc-108">Check the reference to make sure the member being referred to is valid.</span></span>  
  
2.  <span data-ttu-id="0e5fc-109">Qualifique explicitamente o membro com o `Me` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="0e5fc-109">Explicitly qualify the member with the `Me` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e5fc-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0e5fc-110">See Also</span></span>  
 <xref:System.MarshalByRefObject>  
 [<span data-ttu-id="0e5fc-111">Instrução Dim</span><span class="sxs-lookup"><span data-stu-id="0e5fc-111">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)
