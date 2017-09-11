---
title: "Não é possível referenciar &quot;&lt;nome&gt;&quot;porque ele é membro do campo de tipo de valor&quot;&lt;nome&gt;&quot;da classe&quot;&lt;classname&gt;&quot; que tem &quot;System. MarshalByRefObject&quot; como uma classe base | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30310
- bc30310
dev_langs:
- VB
helpviewer_keywords:
- BC30310
ms.assetid: 2aeb8872-7c87-4f01-98ef-9714ba3eebbe
caps.latest.revision: 9
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
ms.openlocfilehash: 87eaea985ab86b7d0994a1106f1d452068e9cc88
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="cannot-refer-to-39ltnamegt39-because-it-is-a-member-of-the-value-typed-field-39ltnamegt39-of-class-39ltclassnamegt39-which-has-39systemmarshalbyrefobject39-as-a-base-class"></a><span data-ttu-id="b2e39-102">Não é possível referenciar '&lt;nome&gt;'porque ele é membro do campo de tipo de valor'&lt;nome&gt;'da classe'&lt;classname&gt;' que tem 'System. MarshalByRefObject' como uma classe base</span><span class="sxs-lookup"><span data-stu-id="b2e39-102">Cannot refer to &#39;&lt;name&gt;&#39; because it is a member of the value-typed field &#39;&lt;name&gt;&#39; of class &#39;&lt;classname&gt;&#39; which has &#39;System.MarshalByRefObject&#39; as a base class</span></span>
<span data-ttu-id="b2e39-103">O `System.MarshalByRefObject` classe permite que os aplicativos que oferecem suporte a acesso remoto a objetos nos limites do domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b2e39-103">The `System.MarshalByRefObject` class enables applications that support remote access to objects across application domain boundaries.</span></span> <span data-ttu-id="b2e39-104">Tipos devem herdar do `MarshalByRejectObject` classe quando o tipo é usado nos limites do domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b2e39-104">Types must inherit from the `MarshalByRejectObject` class when the type is used across application domain boundaries.</span></span> <span data-ttu-id="b2e39-105">O estado do objeto não deve ser copiado porque os membros do objeto não são utilizáveis fora do domínio de aplicativo no qual eles foram criados.</span><span class="sxs-lookup"><span data-stu-id="b2e39-105">The state of the object must not be copied because the members of the object are not usable outside the application domain in which they were created.</span></span>  
  
 <span data-ttu-id="b2e39-106">**ID do erro:** BC30310</span><span class="sxs-lookup"><span data-stu-id="b2e39-106">**Error ID:** BC30310</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b2e39-107">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="b2e39-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="b2e39-108">Verifique a referência para certificar-se de que o membro sendo referenciado é válido.</span><span class="sxs-lookup"><span data-stu-id="b2e39-108">Check the reference to make sure the member being referred to is valid.</span></span>  
  
2.  <span data-ttu-id="b2e39-109">Qualifique explicitamente o membro com o `Me` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="b2e39-109">Explicitly qualify the member with the `Me` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2e39-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b2e39-110">See Also</span></span>  
 <span data-ttu-id="b2e39-111"><xref:System.MarshalByRefObject></xref:System.MarshalByRefObject></span><span class="sxs-lookup"><span data-stu-id="b2e39-111"><xref:System.MarshalByRefObject></span></span>   
<span data-ttu-id="b2e39-112"> [Instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md)</span><span class="sxs-lookup"><span data-stu-id="b2e39-112"> [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md)</span></span>
