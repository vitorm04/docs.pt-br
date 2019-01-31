---
title: "'<elementname>' está obsoleto (aviso do Visual Basic)"
ms.date: 07/20/2015
f1_keywords:
- vbc40008
- bc40008
helpviewer_keywords:
- BC40008
ms.assetid: 729e3eb5-76ac-4c55-9fdd-78350e0de55e
ms.openlocfilehash: c6d927ef6681838d8a77a0c6018eb6bbe30913e8
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55255855"
---
# <a name="elementname-is-obsolete-visual-basic-warning"></a><span data-ttu-id="4984d-102">'\<elementname >' é obsoleto (aviso do Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4984d-102">'\<elementname>' is obsolete (Visual Basic Warning)</span></span>
<span data-ttu-id="4984d-103">Uma instrução tenta acessar um elemento de programação que foi marcado com o <xref:System.ObsoleteAttribute> atributo e a diretiva para tratá-lo como um aviso.</span><span class="sxs-lookup"><span data-stu-id="4984d-103">A statement attempts to access a programming element which has been marked with the <xref:System.ObsoleteAttribute> attribute and the directive to treat it as a warning.</span></span>  
  
 <span data-ttu-id="4984d-104">Você pode marcar qualquer elemento de programação como sendo não mais em uso por meio da aplicação <xref:System.ObsoleteAttribute> a ele.</span><span class="sxs-lookup"><span data-stu-id="4984d-104">You can mark any programming element as being no longer in use by applying <xref:System.ObsoleteAttribute> to it.</span></span> <span data-ttu-id="4984d-105">Se você fizer isso, você pode definir o atributo <xref:System.ObsoleteAttribute.IsError%2A> propriedade para um `True` ou `False`.</span><span class="sxs-lookup"><span data-stu-id="4984d-105">If you do this, you can set the attribute's <xref:System.ObsoleteAttribute.IsError%2A> property to either `True` or `False`.</span></span> <span data-ttu-id="4984d-106">Se você defini-lo como `True`, o compilador trata uma tentativa de usar o elemento como um erro.</span><span class="sxs-lookup"><span data-stu-id="4984d-106">If you set it to `True`, the compiler treats an attempt to use the element as an error.</span></span> <span data-ttu-id="4984d-107">Se você defini-lo `False`, ou deixá-lo como padrão `False`, o compilador emitirá um aviso se não houver uma tentativa de usar o elemento.</span><span class="sxs-lookup"><span data-stu-id="4984d-107">If you set it to `False`, or let it default to `False`, the compiler issues a warning if there is an attempt to use the element.</span></span>  
  
 <span data-ttu-id="4984d-108">Por padrão, essa mensagem é um aviso, porque o <xref:System.ObsoleteAttribute.IsError%2A> propriedade de <xref:System.ObsoleteAttribute> é `False`.</span><span class="sxs-lookup"><span data-stu-id="4984d-108">By default, this message is a warning, because the <xref:System.ObsoleteAttribute.IsError%2A> property of <xref:System.ObsoleteAttribute> is `False`.</span></span> <span data-ttu-id="4984d-109">Para obter mais informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="4984d-109">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="4984d-110">**ID do erro:** BC40008</span><span class="sxs-lookup"><span data-stu-id="4984d-110">**Error ID:** BC40008</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4984d-111">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="4984d-111">To correct this error</span></span>  
  
-   <span data-ttu-id="4984d-112">Certifique-se de que a referência do código-fonte é o nome do elemento digitado corretamente.</span><span class="sxs-lookup"><span data-stu-id="4984d-112">Ensure that the source-code reference is spelling the element name correctly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4984d-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4984d-113">See also</span></span>
- [<span data-ttu-id="4984d-114">Visão geral de atributos</span><span class="sxs-lookup"><span data-stu-id="4984d-114">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)
