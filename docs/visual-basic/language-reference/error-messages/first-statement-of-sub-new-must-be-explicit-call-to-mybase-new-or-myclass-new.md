---
title: "A primeira instrução deste &quot;Sub New&quot; deve ser uma chamada explícita para &quot;MyBase. New&quot; ou &quot;MyClass. New&quot; porque o &quot;&lt;constructorname&gt;&quot;na classe base&quot;&lt;baseclassname&gt;&quot;de&quot;&lt;derivedclassname&gt;&quot; está marcado como obsoleto: &quot;&lt;errormessage&gt;&quot; | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30920
- bc30920
dev_langs:
- VB
helpviewer_keywords:
- BC30920
ms.assetid: e47dc755-4294-4368-b813-2177b7677957
caps.latest.revision: 10
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
ms.openlocfilehash: d46192bc9a9f2807f56cbdd7bdd4fd21f6c9a7b0
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="first-statement-of-this-39sub-new39-must-be-an-explicit-call-to-39mybasenew39-or-39myclassnew39-because-the-39ltconstructornamegt39-in-the-base-class-39ltbaseclassnamegt39-of-39ltderivedclassnamegt39-is-marked-obsolete-39lterrormessagegt39"></a><span data-ttu-id="acfa6-102">A primeira instrução deste 'Sub New' deve ser uma chamada explícita para 'MyBase. New' ou 'MyClass. New' porque o '&lt;constructorname&gt;'na classe base'&lt;baseclassname&gt;'de'&lt;derivedclassname&gt;' está marcado como obsoleto: '&lt;errormessage&gt;'</span><span class="sxs-lookup"><span data-stu-id="acfa6-102">First statement of this &#39;Sub New&#39; must be an explicit call to &#39;MyBase.New&#39; or &#39;MyClass.New&#39; because the &#39;&lt;constructorname&gt;&#39; in the base class &#39;&lt;baseclassname&gt;&#39; of &#39;&lt;derivedclassname&gt;&#39; is marked obsolete: &#39;&lt;errormessage&gt;&#39;</span></span>
<span data-ttu-id="acfa6-103">Um construtor de classe não chama explicitamente um construtor de classe base, e o construtor de classe de base implícito está marcado com o <xref:System.ObsoleteAttribute>atributo e com a diretriz para tratá-lo como um erro.</xref:System.ObsoleteAttribute></span><span class="sxs-lookup"><span data-stu-id="acfa6-103">A class constructor does not explicitly call a base class constructor, and the implicit base class constructor is marked with the <xref:System.ObsoleteAttribute> attribute and the directive to treat it as an error.</span></span>  
  
 <span data-ttu-id="acfa6-104">Quando um construtor de classe derivada não chama um construtor de classe base, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] tenta gerar uma chamada implícita para um construtor de classe base sem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="acfa6-104">When a derived class constructor does not call a base class constructor, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] attempts to generate an implicit call to a parameterless base class constructor.</span></span> <span data-ttu-id="acfa6-105">Se não houver nenhum construtor acessível na classe base que pode ser chamado sem argumentos, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] não é possível gerar uma chamada implícita.</span><span class="sxs-lookup"><span data-stu-id="acfa6-105">If there is no accessible constructor in the base class that can be called without arguments, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] cannot generate an implicit call.</span></span> <span data-ttu-id="acfa6-106">Nesse caso, o construtor exigido é marcado com o <xref:System.ObsoleteAttribute>atributo, isso [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] não é possível chamar proprietário.</xref:System.ObsoleteAttribute></span><span class="sxs-lookup"><span data-stu-id="acfa6-106">In this case, the required constructor is marked with the <xref:System.ObsoleteAttribute> attribute, so [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] cannot call it.</span></span>  
  
 <span data-ttu-id="acfa6-107">Você pode marcar qualquer elemento de programação como sendo não mais em uso aplicando-se <xref:System.ObsoleteAttribute>ao proprietário.</xref:System.ObsoleteAttribute></span><span class="sxs-lookup"><span data-stu-id="acfa6-107">You can mark any programming element as being no longer in use by applying <xref:System.ObsoleteAttribute> to it.</span></span> <span data-ttu-id="acfa6-108">Se você fizer isso, você pode definir o atributo <xref:System.ObsoleteAttribute.IsError%2A>propriedade como `True` ou `False`.</xref:System.ObsoleteAttribute.IsError%2A></span><span class="sxs-lookup"><span data-stu-id="acfa6-108">If you do this, you can set the attribute's <xref:System.ObsoleteAttribute.IsError%2A> property to either `True` or `False`.</span></span> <span data-ttu-id="acfa6-109">Se você defini-lo como `True`, o compilador trata uma tentativa de usar o elemento como um erro.</span><span class="sxs-lookup"><span data-stu-id="acfa6-109">If you set it to `True`, the compiler treats an attempt to use the element as an error.</span></span> <span data-ttu-id="acfa6-110">Se você defini-lo como `False`, ou deixá-lo como padrão `False`, o compilador emite um aviso se houver uma tentativa de usar o elemento.</span><span class="sxs-lookup"><span data-stu-id="acfa6-110">If you set it to `False`, or let it default to `False`, the compiler issues a warning if there is an attempt to use the element.</span></span>  
  
 <span data-ttu-id="acfa6-111">**ID do erro:** BC30920</span><span class="sxs-lookup"><span data-stu-id="acfa6-111">**Error ID:** BC30920</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="acfa6-112">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="acfa6-112">To correct this error</span></span>  
  
1.  <span data-ttu-id="acfa6-113">Examine a mensagem de erro entre aspas e tomar as devidas providências.</span><span class="sxs-lookup"><span data-stu-id="acfa6-113">Examine the quoted error message and take appropriate action.</span></span>  
  
2.  <span data-ttu-id="acfa6-114">Incluir uma chamada para `MyBase.New()` ou `MyClass.New()` como a primeira instrução do `Sub New` na classe derivada.</span><span class="sxs-lookup"><span data-stu-id="acfa6-114">Include a call to `MyBase.New()` or `MyClass.New()` as the first statement of the `Sub New` in the derived class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acfa6-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="acfa6-115">See Also</span></span>  
 [<span data-ttu-id="acfa6-116">Visão geral de atributos</span><span class="sxs-lookup"><span data-stu-id="acfa6-116">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)
 
