---
title: "A primeira instrução isso &#39; Sub novo &#39; deve ser uma chamada explícita para &#39; MyBase. New &#39; ou &#39; MyClass. New &#39; porque o &#39; &lt;constructorname&gt;&#39; na classe base &#39;&lt; baseclassname&gt;&#39; do &#39;&lt; derivedclassname&gt;&#39; está marcado como obsoleto: &#39;&lt; ErrorMessage&gt;&#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30920
- bc30920
helpviewer_keywords: BC30920
ms.assetid: e47dc755-4294-4368-b813-2177b7677957
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8882acd947251d85804fbefd54267ce078e31b95
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="first-statement-of-this-39sub-new39-must-be-an-explicit-call-to-39mybasenew39-or-39myclassnew39-because-the-39ltconstructornamegt39-in-the-base-class-39ltbaseclassnamegt39-of-39ltderivedclassnamegt39-is-marked-obsolete-39lterrormessagegt39"></a><span data-ttu-id="bb50b-102">A primeira instrução isso &#39; Sub novo &#39; deve ser uma chamada explícita para &#39; MyBase. New &#39; ou &#39; MyClass. New &#39; porque o &#39; &lt;constructorname&gt;&#39; na classe base &#39;&lt; baseclassname&gt;&#39; do &#39;&lt; derivedclassname&gt;&#39; está marcado como obsoleto: &#39;&lt; ErrorMessage&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="bb50b-102">First statement of this &#39;Sub New&#39; must be an explicit call to &#39;MyBase.New&#39; or &#39;MyClass.New&#39; because the &#39;&lt;constructorname&gt;&#39; in the base class &#39;&lt;baseclassname&gt;&#39; of &#39;&lt;derivedclassname&gt;&#39; is marked obsolete: &#39;&lt;errormessage&gt;&#39;</span></span>
<span data-ttu-id="bb50b-103">Um construtor de classe não chama explicitamente um construtor de classe base, e o construtor de classe de base implícito está marcado com o <xref:System.ObsoleteAttribute> atributo e a diretiva para tratá-lo como um erro.</span><span class="sxs-lookup"><span data-stu-id="bb50b-103">A class constructor does not explicitly call a base class constructor, and the implicit base class constructor is marked with the <xref:System.ObsoleteAttribute> attribute and the directive to treat it as an error.</span></span>  
  
 <span data-ttu-id="bb50b-104">Quando um construtor de classe derivada não chama um construtor de classe base [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] tenta gerar uma chamada implícita para um construtor sem parâmetros de classe base.</span><span class="sxs-lookup"><span data-stu-id="bb50b-104">When a derived class constructor does not call a base class constructor, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] attempts to generate an implicit call to a parameterless base class constructor.</span></span> <span data-ttu-id="bb50b-105">Se não houver nenhum construtor acessível na classe base que pode ser chamado sem argumentos, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] não é possível gerar uma chamada implícita.</span><span class="sxs-lookup"><span data-stu-id="bb50b-105">If there is no accessible constructor in the base class that can be called without arguments, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] cannot generate an implicit call.</span></span> <span data-ttu-id="bb50b-106">Nesse caso, o construtor necessário está marcado com o <xref:System.ObsoleteAttribute> de atributo, isso [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] não é possível chamá-lo.</span><span class="sxs-lookup"><span data-stu-id="bb50b-106">In this case, the required constructor is marked with the <xref:System.ObsoleteAttribute> attribute, so [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] cannot call it.</span></span>  
  
 <span data-ttu-id="bb50b-107">Você pode marcar qualquer elemento de programação como sendo não mais em uso aplicando <xref:System.ObsoleteAttribute> a ele.</span><span class="sxs-lookup"><span data-stu-id="bb50b-107">You can mark any programming element as being no longer in use by applying <xref:System.ObsoleteAttribute> to it.</span></span> <span data-ttu-id="bb50b-108">Se você fizer isso, você pode definir o atributo <xref:System.ObsoleteAttribute.IsError%2A> propriedade como `True` ou `False`.</span><span class="sxs-lookup"><span data-stu-id="bb50b-108">If you do this, you can set the attribute's <xref:System.ObsoleteAttribute.IsError%2A> property to either `True` or `False`.</span></span> <span data-ttu-id="bb50b-109">Se você defini-lo `True`, o compilador trata uma tentativa de usar o elemento como um erro.</span><span class="sxs-lookup"><span data-stu-id="bb50b-109">If you set it to `True`, the compiler treats an attempt to use the element as an error.</span></span> <span data-ttu-id="bb50b-110">Se você defini-lo `False`, ou deixá-lo como padrão `False`, o compilador emite um aviso se houver uma tentativa de usar o elemento.</span><span class="sxs-lookup"><span data-stu-id="bb50b-110">If you set it to `False`, or let it default to `False`, the compiler issues a warning if there is an attempt to use the element.</span></span>  
  
 <span data-ttu-id="bb50b-111">**ID do erro:** BC30920</span><span class="sxs-lookup"><span data-stu-id="bb50b-111">**Error ID:** BC30920</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="bb50b-112">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="bb50b-112">To correct this error</span></span>  
  
1.  <span data-ttu-id="bb50b-113">Examine a mensagem de erro entre aspas e tomar as devidas providências.</span><span class="sxs-lookup"><span data-stu-id="bb50b-113">Examine the quoted error message and take appropriate action.</span></span>  
  
2.  <span data-ttu-id="bb50b-114">Incluir uma chamada para `MyBase.New()` ou `MyClass.New()` como a primeira instrução de `Sub New` na classe derivada.</span><span class="sxs-lookup"><span data-stu-id="bb50b-114">Include a call to `MyBase.New()` or `MyClass.New()` as the first statement of the `Sub New` in the derived class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb50b-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bb50b-115">See Also</span></span>  
 [<span data-ttu-id="bb50b-116">Visão geral de atributos</span><span class="sxs-lookup"><span data-stu-id="bb50b-116">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)
 
