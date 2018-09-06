---
title: '&#39;&lt;ElementName&gt; &#39; é obsoleto (aviso do Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vbc40008
- bc40008
helpviewer_keywords:
- BC40008
ms.assetid: 729e3eb5-76ac-4c55-9fdd-78350e0de55e
ms.openlocfilehash: 4dc2d0b8eace9bc411a344b4f2c4c79f7e09ac22
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33586764"
---
# <a name="39ltelementnamegt39-is-obsolete-visual-basic-warning"></a><span data-ttu-id="5c426-102">&#39;&lt;ElementName&gt; &#39; é obsoleto (aviso do Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5c426-102">&#39;&lt;elementname&gt;&#39; is obsolete (Visual Basic Warning)</span></span>
<span data-ttu-id="5c426-103">Uma instrução tenta acessar um elemento de programação que foi marcado com o <xref:System.ObsoleteAttribute> atributo e a diretiva para tratá-lo como um aviso.</span><span class="sxs-lookup"><span data-stu-id="5c426-103">A statement attempts to access a programming element which has been marked with the <xref:System.ObsoleteAttribute> attribute and the directive to treat it as a warning.</span></span>  
  
 <span data-ttu-id="5c426-104">Você pode marcar qualquer elemento de programação como sendo não mais em uso aplicando <xref:System.ObsoleteAttribute> a ele.</span><span class="sxs-lookup"><span data-stu-id="5c426-104">You can mark any programming element as being no longer in use by applying <xref:System.ObsoleteAttribute> to it.</span></span> <span data-ttu-id="5c426-105">Se você fizer isso, você pode definir o atributo <xref:System.ObsoleteAttribute.IsError%2A> propriedade como `True` ou `False`.</span><span class="sxs-lookup"><span data-stu-id="5c426-105">If you do this, you can set the attribute's <xref:System.ObsoleteAttribute.IsError%2A> property to either `True` or `False`.</span></span> <span data-ttu-id="5c426-106">Se você defini-lo `True`, o compilador trata uma tentativa de usar o elemento como um erro.</span><span class="sxs-lookup"><span data-stu-id="5c426-106">If you set it to `True`, the compiler treats an attempt to use the element as an error.</span></span> <span data-ttu-id="5c426-107">Se você defini-lo `False`, ou deixá-lo como padrão `False`, o compilador emite um aviso se houver uma tentativa de usar o elemento.</span><span class="sxs-lookup"><span data-stu-id="5c426-107">If you set it to `False`, or let it default to `False`, the compiler issues a warning if there is an attempt to use the element.</span></span>  
  
 <span data-ttu-id="5c426-108">Por padrão, essa mensagem é um aviso, porque o <xref:System.ObsoleteAttribute.IsError%2A> propriedade <xref:System.ObsoleteAttribute> é `False`.</span><span class="sxs-lookup"><span data-stu-id="5c426-108">By default, this message is a warning, because the <xref:System.ObsoleteAttribute.IsError%2A> property of <xref:System.ObsoleteAttribute> is `False`.</span></span> <span data-ttu-id="5c426-109">Para obter mais informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="5c426-109">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="5c426-110">**ID do erro:** BC40008</span><span class="sxs-lookup"><span data-stu-id="5c426-110">**Error ID:** BC40008</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5c426-111">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="5c426-111">To correct this error</span></span>  
  
-   <span data-ttu-id="5c426-112">Certifique-se de que a referência do código-fonte está digitado corretamente o nome do elemento.</span><span class="sxs-lookup"><span data-stu-id="5c426-112">Ensure that the source-code reference is spelling the element name correctly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c426-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5c426-113">See Also</span></span>  
 [<span data-ttu-id="5c426-114">Visão geral de atributos</span><span class="sxs-lookup"><span data-stu-id="5c426-114">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)
