---
title: "'<elementname>' está obsoleto (aviso do Visual Basic)"
ms.date: 07/20/2015
f1_keywords:
- vbc40008
- bc40008
helpviewer_keywords:
- BC40008
ms.assetid: 729e3eb5-76ac-4c55-9fdd-78350e0de55e
ms.openlocfilehash: 7914bc859966e17f3da41c9a13a01573b31baf91
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409667"
---
# <a name="elementname-is-obsolete-visual-basic-warning"></a><span data-ttu-id="c4a9a-102">'\<elementname>' está obsoleto (aviso do Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c4a9a-102">'\<elementname>' is obsolete (Visual Basic Warning)</span></span>
<span data-ttu-id="c4a9a-103">Uma instrução tenta acessar um elemento de programação que foi marcado com o <xref:System.ObsoleteAttribute> atributo e a diretiva para tratá-lo como um aviso.</span><span class="sxs-lookup"><span data-stu-id="c4a9a-103">A statement attempts to access a programming element which has been marked with the <xref:System.ObsoleteAttribute> attribute and the directive to treat it as a warning.</span></span>  
  
 <span data-ttu-id="c4a9a-104">Você pode marcar qualquer elemento de programação como não sendo mais usado aplicando <xref:System.ObsoleteAttribute> -se a ele.</span><span class="sxs-lookup"><span data-stu-id="c4a9a-104">You can mark any programming element as being no longer in use by applying <xref:System.ObsoleteAttribute> to it.</span></span> <span data-ttu-id="c4a9a-105">Se você fizer isso, poderá definir a propriedade do atributo <xref:System.ObsoleteAttribute.IsError%2A> como `True` ou `False` .</span><span class="sxs-lookup"><span data-stu-id="c4a9a-105">If you do this, you can set the attribute's <xref:System.ObsoleteAttribute.IsError%2A> property to either `True` or `False`.</span></span> <span data-ttu-id="c4a9a-106">Se você defini-lo como `True` , o compilador tratará uma tentativa de usar o elemento como um erro.</span><span class="sxs-lookup"><span data-stu-id="c4a9a-106">If you set it to `True`, the compiler treats an attempt to use the element as an error.</span></span> <span data-ttu-id="c4a9a-107">Se você defini-lo como `False` , ou deixá-lo como padrão `False` , o compilador emitirá um aviso se houver uma tentativa de usar o elemento.</span><span class="sxs-lookup"><span data-stu-id="c4a9a-107">If you set it to `False`, or let it default to `False`, the compiler issues a warning if there is an attempt to use the element.</span></span>  
  
 <span data-ttu-id="c4a9a-108">Por padrão, essa mensagem é um aviso, pois a <xref:System.ObsoleteAttribute.IsError%2A> propriedade de <xref:System.ObsoleteAttribute> é `False` .</span><span class="sxs-lookup"><span data-stu-id="c4a9a-108">By default, this message is a warning, because the <xref:System.ObsoleteAttribute.IsError%2A> property of <xref:System.ObsoleteAttribute> is `False`.</span></span> <span data-ttu-id="c4a9a-109">Para obter mais informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="c4a9a-109">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="c4a9a-110">**ID do erro:** BC40008</span><span class="sxs-lookup"><span data-stu-id="c4a9a-110">**Error ID:** BC40008</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c4a9a-111">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="c4a9a-111">To correct this error</span></span>  
  
- <span data-ttu-id="c4a9a-112">Certifique-se de que a referência de código-fonte esteja soletrando o nome do elemento corretamente.</span><span class="sxs-lookup"><span data-stu-id="c4a9a-112">Ensure that the source-code reference is spelling the element name correctly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4a9a-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="c4a9a-113">See also</span></span>

- [<span data-ttu-id="c4a9a-114">Visão geral de atributos</span><span class="sxs-lookup"><span data-stu-id="c4a9a-114">Attributes overview</span></span>](../../programming-guide/concepts/attributes/index.md)
