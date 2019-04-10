---
title: "A primeira instrução deste 'Sub New' deve ser uma chamada explícita para MyBase.New' ou 'MyClass.New' porque '<constructorname>' na classe base '<baseclassname>' de '<derivedclassname>' está marcado como obsoleto: '<errormessage>'"
ms.date: 07/20/2015
f1_keywords:
- vbc30920
- bc30920
helpviewer_keywords:
- BC30920
ms.assetid: e47dc755-4294-4368-b813-2177b7677957
ms.openlocfilehash: 89b6c241bb637f2efc6014c4640b3b463c4facfa
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59313471"
---
# <a name="first-statement-of-this-sub-new-must-be-an-explicit-call-to-mybasenew-or-myclassnew-because-the-constructorname-in-the-base-class-baseclassname-of-derivedclassname-is-marked-obsolete-errormessage"></a><span data-ttu-id="be34d-102">A primeira instrução deste 'Sub New' deve ser uma chamada explícita para 'MyBase. New' ou 'MyClass. New' porque o '\<constructorname >' na classe base\<baseclassname >' de '\<derivedclassname >' está marcado como obsoleto: '\< ErrorMessage >'</span><span class="sxs-lookup"><span data-stu-id="be34d-102">First statement of this 'Sub New' must be an explicit call to 'MyBase.New' or 'MyClass.New' because the '\<constructorname>' in the base class '\<baseclassname>' of '\<derivedclassname>' is marked obsolete: '\<errormessage>'</span></span>
<span data-ttu-id="be34d-103">Um construtor de classe não chama explicitamente um construtor de classe base, e o construtor de classe base implícita é marcado com o <xref:System.ObsoleteAttribute> atributo e a diretiva para tratá-lo como um erro.</span><span class="sxs-lookup"><span data-stu-id="be34d-103">A class constructor does not explicitly call a base class constructor, and the implicit base class constructor is marked with the <xref:System.ObsoleteAttribute> attribute and the directive to treat it as an error.</span></span>  
  
 <span data-ttu-id="be34d-104">Quando um construtor de classe derivada não chama um construtor de classe base, o Visual Basic tenta gerar uma chamada implícita para um construtor sem parâmetros de classe base.</span><span class="sxs-lookup"><span data-stu-id="be34d-104">When a derived class constructor does not call a base class constructor, Visual Basic attempts to generate an implicit call to a parameterless base class constructor.</span></span> <span data-ttu-id="be34d-105">Se não houver nenhum construtor acessível na classe base que pode ser chamado sem argumentos, o Visual Basic não é possível gerar uma chamada implícita.</span><span class="sxs-lookup"><span data-stu-id="be34d-105">If there is no accessible constructor in the base class that can be called without arguments, Visual Basic cannot generate an implicit call.</span></span> <span data-ttu-id="be34d-106">Nesse caso, o construtor necessário é marcado com o <xref:System.ObsoleteAttribute> de atributo, portanto, o Visual Basic não pode chamá-lo.</span><span class="sxs-lookup"><span data-stu-id="be34d-106">In this case, the required constructor is marked with the <xref:System.ObsoleteAttribute> attribute, so Visual Basic cannot call it.</span></span>  
  
 <span data-ttu-id="be34d-107">Você pode marcar qualquer elemento de programação como sendo não mais em uso por meio da aplicação <xref:System.ObsoleteAttribute> a ele.</span><span class="sxs-lookup"><span data-stu-id="be34d-107">You can mark any programming element as being no longer in use by applying <xref:System.ObsoleteAttribute> to it.</span></span> <span data-ttu-id="be34d-108">Se você fizer isso, você pode definir o atributo <xref:System.ObsoleteAttribute.IsError%2A> propriedade para um `True` ou `False`.</span><span class="sxs-lookup"><span data-stu-id="be34d-108">If you do this, you can set the attribute's <xref:System.ObsoleteAttribute.IsError%2A> property to either `True` or `False`.</span></span> <span data-ttu-id="be34d-109">Se você defini-lo como `True`, o compilador trata uma tentativa de usar o elemento como um erro.</span><span class="sxs-lookup"><span data-stu-id="be34d-109">If you set it to `True`, the compiler treats an attempt to use the element as an error.</span></span> <span data-ttu-id="be34d-110">Se você defini-lo `False`, ou deixá-lo como padrão `False`, o compilador emitirá um aviso se não houver uma tentativa de usar o elemento.</span><span class="sxs-lookup"><span data-stu-id="be34d-110">If you set it to `False`, or let it default to `False`, the compiler issues a warning if there is an attempt to use the element.</span></span>  
  
 <span data-ttu-id="be34d-111">**ID do erro:** BC30920</span><span class="sxs-lookup"><span data-stu-id="be34d-111">**Error ID:** BC30920</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="be34d-112">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="be34d-112">To correct this error</span></span>  
  
1. <span data-ttu-id="be34d-113">Examine a mensagem de erro entre aspas e tomar as devidas providências.</span><span class="sxs-lookup"><span data-stu-id="be34d-113">Examine the quoted error message and take appropriate action.</span></span>  
  
2. <span data-ttu-id="be34d-114">Incluir uma chamada para `MyBase.New()` ou `MyClass.New()` como a primeira instrução da `Sub New` na classe derivada.</span><span class="sxs-lookup"><span data-stu-id="be34d-114">Include a call to `MyBase.New()` or `MyClass.New()` as the first statement of the `Sub New` in the derived class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be34d-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="be34d-115">See also</span></span>

- [<span data-ttu-id="be34d-116">Visão geral de atributos</span><span class="sxs-lookup"><span data-stu-id="be34d-116">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)
