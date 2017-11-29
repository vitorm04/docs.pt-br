---
title: "&#39; &lt;classname&gt;&#39; não é compatível com CLS porque a interface &#39;&lt; InterfaceName&gt;&#39; ele implementa não é compatível com CLS"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc40029
- vbc40029
helpviewer_keywords: BC40029
ms.assetid: 178452f3-5575-4da0-9d6c-53bcddb6a338
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7bad6aa4c8fa9979824766e83aba75697d6e98d8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="39ltclassnamegt39-is-not-cls-compliant-because-the-interface-39ltinterfacenamegt39-it-implements-is-not-cls-compliant"></a><span data-ttu-id="d718f-102">&#39; &lt;classname&gt;&#39; não é compatível com CLS porque a interface &#39;&lt; InterfaceName&gt;&#39; ele implementa não é compatível com CLS</span><span class="sxs-lookup"><span data-stu-id="d718f-102">&#39;&lt;classname&gt;&#39; is not CLS-compliant because the interface &#39;&lt;interfacename&gt;&#39; it implements is not CLS-compliant</span></span>
<span data-ttu-id="d718f-103">Uma classe ou interface está marcado como `<CLSCompliant(True)>` quando ela deriva de ou implementa um tipo que está marcado como `<CLSCompliant(False)>` ou não está marcado.</span><span class="sxs-lookup"><span data-stu-id="d718f-103">A class or interface is marked as `<CLSCompliant(True)>` when it derives from or implements a type that is marked as `<CLSCompliant(False)>` or is not marked.</span></span>  
  
 <span data-ttu-id="d718f-104">Para uma classe ou interface seja compatível com o [independência da linguagem e componentes independentes da linguagem](https://msdn.microsoft.com/library/12a7a7h3) (CLS), sua hierarquia de herança inteira deve ser compatível.</span><span class="sxs-lookup"><span data-stu-id="d718f-104">For a class or interface to be compliant with the [Language Independence and Language-Independent Components](https://msdn.microsoft.com/library/12a7a7h3) (CLS), its entire inheritance hierarchy must be compliant.</span></span> <span data-ttu-id="d718f-105">Isso significa que todos os tipos da qual ela herda, direta ou indiretamente, devem ser compatíveis.</span><span class="sxs-lookup"><span data-stu-id="d718f-105">That means every type from which it inherits, directly or indirectly, must be compliant.</span></span> <span data-ttu-id="d718f-106">Da mesma forma, se uma classe implementa uma ou mais interfaces, eles devem todos ser compatíveis em suas hierarquias de herança.</span><span class="sxs-lookup"><span data-stu-id="d718f-106">Similarly, if a class implements one or more interfaces, they must all be compliant throughout their inheritance hierarchies.</span></span>  
  
 <span data-ttu-id="d718f-107">Quando você aplica o <xref:System.CLSCompliantAttribute> para um elemento de programação, você definir o atributo `isCompliant` parâmetro a `True` ou `False` para indicar compatibilidade ou incompatibilidade.</span><span class="sxs-lookup"><span data-stu-id="d718f-107">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="d718f-108">Não há nenhum padrão para esse parâmetro, e você deve fornecer um valor.</span><span class="sxs-lookup"><span data-stu-id="d718f-108">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="d718f-109">Se você não se aplicam a <xref:System.CLSCompliantAttribute> a um elemento, ele é considerado incompatível.</span><span class="sxs-lookup"><span data-stu-id="d718f-109">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="d718f-110">Por padrão, esta mensagem é um aviso.</span><span class="sxs-lookup"><span data-stu-id="d718f-110">By default, this message is a warning.</span></span> <span data-ttu-id="d718f-111">Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="d718f-111">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="d718f-112">**ID do erro:** BC40029</span><span class="sxs-lookup"><span data-stu-id="d718f-112">**Error ID:** BC40029</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d718f-113">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="d718f-113">To correct this error</span></span>  
  
-   <span data-ttu-id="d718f-114">Se você precisar de compatibilidade com CLS, defina este tipo em um esquema de implementação ou hierarquia de herança diferente.</span><span class="sxs-lookup"><span data-stu-id="d718f-114">If you require CLS compliance, define this type within a different inheritance hierarchy or implementation scheme.</span></span>  
  
-   <span data-ttu-id="d718f-115">Se você precisar que esse tipo permaneça em seu esquema de implementação ou hierarquia de herança atual, remova o <xref:System.CLSCompliantAttribute> da sua definição ou marque-a como `<CLSCompliant(False)>`.</span><span class="sxs-lookup"><span data-stu-id="d718f-115">If you require that this type remain within its current inheritance hierarchy or implementation scheme, remove the <xref:System.CLSCompliantAttribute> from its definition or mark it as `<CLSCompliant(False)>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d718f-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d718f-116">See Also</span></span>  
 [<span data-ttu-id="d718f-117">\<PAVE sobre > escrevendo código compatível com CLS</span><span class="sxs-lookup"><span data-stu-id="d718f-117">\<PAVE OVER> Writing CLS-Compliant Code</span></span>](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)
