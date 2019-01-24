---
title: Não pode se referir a &#39; &lt;nome&gt; &#39; porque ele é um membro do campo tipo de valor de &#39; &lt;nome&gt; &#39; da classe &#39; &lt;classname&gt; &#39;que tem &#39;System. MarshalByRefObject&#39; como uma classe base
ms.date: 07/20/2015
f1_keywords:
- vbc30310
- bc30310
helpviewer_keywords:
- BC30310
ms.assetid: 2aeb8872-7c87-4f01-98ef-9714ba3eebbe
ms.openlocfilehash: a6298c3e0f5102397d5cc3f237a186598c6b5ecc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54739291"
---
# <a name="cannot-refer-to-39ltnamegt39-because-it-is-a-member-of-the-value-typed-field-39ltnamegt39-of-class-39ltclassnamegt39-which-has-39systemmarshalbyrefobject39-as-a-base-class"></a><span data-ttu-id="c37b8-102">Não pode se referir a &#39; &lt;nome&gt; &#39; porque ele é um membro do campo tipo de valor de &#39; &lt;nome&gt; &#39; da classe &#39; &lt;classname&gt; &#39;que tem &#39;System. MarshalByRefObject&#39; como uma classe base</span><span class="sxs-lookup"><span data-stu-id="c37b8-102">Cannot refer to &#39;&lt;name&gt;&#39; because it is a member of the value-typed field &#39;&lt;name&gt;&#39; of class &#39;&lt;classname&gt;&#39; which has &#39;System.MarshalByRefObject&#39; as a base class</span></span>
<span data-ttu-id="c37b8-103">O `System.MarshalByRefObject` classe permite que os aplicativos que dão suporte ao acesso remoto a objetos entre limites de domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c37b8-103">The `System.MarshalByRefObject` class enables applications that support remote access to objects across application domain boundaries.</span></span> <span data-ttu-id="c37b8-104">Tipos devem herdar a `MarshalByRejectObject` classe quando o tipo é usado entre os limites de domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c37b8-104">Types must inherit from the `MarshalByRejectObject` class when the type is used across application domain boundaries.</span></span> <span data-ttu-id="c37b8-105">O estado do objeto não deve ser copiado porque os membros do objeto não são utilizáveis fora do domínio de aplicativo no qual eles foram criados.</span><span class="sxs-lookup"><span data-stu-id="c37b8-105">The state of the object must not be copied because the members of the object are not usable outside the application domain in which they were created.</span></span>  
  
 <span data-ttu-id="c37b8-106">**ID do erro:** BC30310</span><span class="sxs-lookup"><span data-stu-id="c37b8-106">**Error ID:** BC30310</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c37b8-107">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="c37b8-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="c37b8-108">Verifique se a referência para garantir que o membro que está sendo referenciado é válido.</span><span class="sxs-lookup"><span data-stu-id="c37b8-108">Check the reference to make sure the member being referred to is valid.</span></span>  
  
2.  <span data-ttu-id="c37b8-109">Qualifique explicitamente o membro com o `Me` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="c37b8-109">Explicitly qualify the member with the `Me` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c37b8-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c37b8-110">See also</span></span>
- <xref:System.MarshalByRefObject>
- [<span data-ttu-id="c37b8-111">Instrução Dim</span><span class="sxs-lookup"><span data-stu-id="c37b8-111">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)
