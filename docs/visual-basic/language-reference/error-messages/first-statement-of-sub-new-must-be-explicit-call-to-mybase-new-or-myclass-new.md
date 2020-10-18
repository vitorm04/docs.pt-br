---
title: "A primeira instrução deste 'Sub New' deve ser uma chamada explícita para MyBase.New' ou 'MyClass.New' porque '<constructorname>' na classe base '<baseclassname>' de '<derivedclassname>' está marcado como obsoleto: '<errormessage>'"
ms.date: 07/20/2015
f1_keywords:
- vbc30920
- bc30920
helpviewer_keywords:
- BC30920
ms.assetid: e47dc755-4294-4368-b813-2177b7677957
ms.openlocfilehash: 4b927e3eed8f9d7f46255b907342465f48263724
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163032"
---
# <a name="bc30920-first-statement-of-this-sub-new-must-be-an-explicit-call-to-mybasenew-or-myclassnew-because-the-constructorname-in-the-base-class-baseclassname-of-derivedclassname-is-marked-obsolete-errormessage"></a><span data-ttu-id="65323-102">BC30920: a primeira instrução deste ' Sub New ' deve ser uma chamada explícita para ' MyBase. New ' ou ' MyClass. New ' porque o ' \<constructorname> ' na classe base ' \<baseclassname> ' de ' \<derivedclassname> ' está marcado como obsoleto: ' \<errormessage> '</span><span class="sxs-lookup"><span data-stu-id="65323-102">BC30920: First statement of this 'Sub New' must be an explicit call to 'MyBase.New' or 'MyClass.New' because the '\<constructorname>' in the base class '\<baseclassname>' of '\<derivedclassname>' is marked obsolete: '\<errormessage>'</span></span>

<span data-ttu-id="65323-103">Um construtor de classe não chama explicitamente um construtor de classe base e o construtor da classe base implícita é marcado com o <xref:System.ObsoleteAttribute> atributo e a diretiva para tratá-lo como um erro.</span><span class="sxs-lookup"><span data-stu-id="65323-103">A class constructor does not explicitly call a base class constructor, and the implicit base class constructor is marked with the <xref:System.ObsoleteAttribute> attribute and the directive to treat it as an error.</span></span>

 <span data-ttu-id="65323-104">Quando um construtor de classe derivada não chama um construtor de classe base, Visual Basic tenta gerar uma chamada implícita para um construtor de classe base sem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="65323-104">When a derived class constructor does not call a base class constructor, Visual Basic attempts to generate an implicit call to a parameterless base class constructor.</span></span> <span data-ttu-id="65323-105">Se não houver nenhum construtor acessível na classe base que possa ser chamado sem argumentos, Visual Basic não poderá gerar uma chamada implícita.</span><span class="sxs-lookup"><span data-stu-id="65323-105">If there is no accessible constructor in the base class that can be called without arguments, Visual Basic cannot generate an implicit call.</span></span> <span data-ttu-id="65323-106">Nesse caso, o Construtor necessário é marcado com o <xref:System.ObsoleteAttribute> atributo, portanto Visual Basic não pode chamá-lo.</span><span class="sxs-lookup"><span data-stu-id="65323-106">In this case, the required constructor is marked with the <xref:System.ObsoleteAttribute> attribute, so Visual Basic cannot call it.</span></span>

 <span data-ttu-id="65323-107">Você pode marcar qualquer elemento de programação como não sendo mais usado aplicando <xref:System.ObsoleteAttribute> -se a ele.</span><span class="sxs-lookup"><span data-stu-id="65323-107">You can mark any programming element as being no longer in use by applying <xref:System.ObsoleteAttribute> to it.</span></span> <span data-ttu-id="65323-108">Se você fizer isso, poderá definir a propriedade do atributo <xref:System.ObsoleteAttribute.IsError%2A> como `True` ou `False` .</span><span class="sxs-lookup"><span data-stu-id="65323-108">If you do this, you can set the attribute's <xref:System.ObsoleteAttribute.IsError%2A> property to either `True` or `False`.</span></span> <span data-ttu-id="65323-109">Se você defini-lo como `True` , o compilador tratará uma tentativa de usar o elemento como um erro.</span><span class="sxs-lookup"><span data-stu-id="65323-109">If you set it to `True`, the compiler treats an attempt to use the element as an error.</span></span> <span data-ttu-id="65323-110">Se você defini-lo como `False` , ou deixá-lo como padrão `False` , o compilador emitirá um aviso se houver uma tentativa de usar o elemento.</span><span class="sxs-lookup"><span data-stu-id="65323-110">If you set it to `False`, or let it default to `False`, the compiler issues a warning if there is an attempt to use the element.</span></span>

 <span data-ttu-id="65323-111">**ID do erro:** BC30920</span><span class="sxs-lookup"><span data-stu-id="65323-111">**Error ID:** BC30920</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="65323-112">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="65323-112">To correct this error</span></span>

1. <span data-ttu-id="65323-113">Examine a mensagem de erro entre aspas e execute a ação apropriada.</span><span class="sxs-lookup"><span data-stu-id="65323-113">Examine the quoted error message and take appropriate action.</span></span>

2. <span data-ttu-id="65323-114">Inclua uma chamada para `MyBase.New()` ou `MyClass.New()` como a primeira instrução do `Sub New` na classe derivada.</span><span class="sxs-lookup"><span data-stu-id="65323-114">Include a call to `MyBase.New()` or `MyClass.New()` as the first statement of the `Sub New` in the derived class.</span></span>

## <a name="see-also"></a><span data-ttu-id="65323-115">Veja também</span><span class="sxs-lookup"><span data-stu-id="65323-115">See also</span></span>

- [<span data-ttu-id="65323-116">Visão geral de atributos</span><span class="sxs-lookup"><span data-stu-id="65323-116">Attributes overview</span></span>](../../programming-guide/concepts/attributes/index.md)
