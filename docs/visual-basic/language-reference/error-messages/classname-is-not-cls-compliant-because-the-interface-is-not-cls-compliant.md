---
title: "'<classname>' não é compatível com CLS porque a interface '<interfacename>' implementada não é compatível com CLS"
ms.date: 07/20/2015
f1_keywords:
- bc40029
- vbc40029
helpviewer_keywords:
- BC40029
ms.assetid: 178452f3-5575-4da0-9d6c-53bcddb6a338
ms.openlocfilehash: a482d14094a3fa86b56ca84af46c45e6093416c5
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874622"
---
# <a name="classname-is-not-cls-compliant-because-the-interface-interfacename-it-implements-is-not-cls-compliant"></a><span data-ttu-id="eb9bf-102">'\<classname>' não é compatível com CLS porque a interface '\<interfacename>' implementada não é compatível com CLS</span><span class="sxs-lookup"><span data-stu-id="eb9bf-102">'\<classname>' is not CLS-compliant because the interface '\<interfacename>' it implements is not CLS-compliant</span></span>

<span data-ttu-id="eb9bf-103">Uma classe ou interface é marcada como `<CLSCompliant(True)>` quando deriva de ou implementa um tipo que está marcado como `<CLSCompliant(False)>` ou não está marcado.</span><span class="sxs-lookup"><span data-stu-id="eb9bf-103">A class or interface is marked as `<CLSCompliant(True)>` when it derives from or implements a type that is marked as `<CLSCompliant(False)>` or is not marked.</span></span>  
  
 <span data-ttu-id="eb9bf-104">Para que uma classe ou interface seja compatível com a [independência de linguagem e com os componentes independentes de linguagem](../../../standard/language-independence-and-language-independent-components.md) (CLS), sua hierarquia de herança inteira deve ser compatível.</span><span class="sxs-lookup"><span data-stu-id="eb9bf-104">For a class or interface to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), its entire inheritance hierarchy must be compliant.</span></span> <span data-ttu-id="eb9bf-105">Isso significa que todos os tipos dos quais ele herda, direta ou indiretamente, devem ser compatíveis.</span><span class="sxs-lookup"><span data-stu-id="eb9bf-105">That means every type from which it inherits, directly or indirectly, must be compliant.</span></span> <span data-ttu-id="eb9bf-106">Da mesma forma, se uma classe implementa uma ou mais interfaces, todas elas devem estar em conformidade em suas hierarquias de herança.</span><span class="sxs-lookup"><span data-stu-id="eb9bf-106">Similarly, if a class implements one or more interfaces, they must all be compliant throughout their inheritance hierarchies.</span></span>  
  
 <span data-ttu-id="eb9bf-107">Quando você aplica o a <xref:System.CLSCompliantAttribute> um elemento de programação, você define o parâmetro do atributo `isCompliant` como `True` ou `False` para indicar conformidade ou não conformidade.</span><span class="sxs-lookup"><span data-stu-id="eb9bf-107">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="eb9bf-108">Não há nenhum padrão para esse parâmetro, e você deve fornecer um valor.</span><span class="sxs-lookup"><span data-stu-id="eb9bf-108">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="eb9bf-109">Se você não aplicar o <xref:System.CLSCompliantAttribute> a um elemento, será considerado como não compatível.</span><span class="sxs-lookup"><span data-stu-id="eb9bf-109">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="eb9bf-110">Por padrão, esta mensagem é um aviso.</span><span class="sxs-lookup"><span data-stu-id="eb9bf-110">By default, this message is a warning.</span></span> <span data-ttu-id="eb9bf-111">Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="eb9bf-111">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="eb9bf-112">**ID do erro:** BC40029</span><span class="sxs-lookup"><span data-stu-id="eb9bf-112">**Error ID:** BC40029</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="eb9bf-113">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="eb9bf-113">To correct this error</span></span>  
  
- <span data-ttu-id="eb9bf-114">Se você precisar de conformidade com CLS, defina esse tipo em uma hierarquia de herança ou esquema de implementação diferente.</span><span class="sxs-lookup"><span data-stu-id="eb9bf-114">If you require CLS compliance, define this type within a different inheritance hierarchy or implementation scheme.</span></span>  
  
- <span data-ttu-id="eb9bf-115">Se você precisar que esse tipo permaneça em sua hierarquia de herança ou esquema de implementação atual, remova o <xref:System.CLSCompliantAttribute> de sua definição ou marque-o como `<CLSCompliant(False)>` .</span><span class="sxs-lookup"><span data-stu-id="eb9bf-115">If you require that this type remain within its current inheritance hierarchy or implementation scheme, remove the <xref:System.CLSCompliantAttribute> from its definition or mark it as `<CLSCompliant(False)>`.</span></span>  
