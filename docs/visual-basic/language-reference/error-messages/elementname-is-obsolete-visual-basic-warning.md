---
title: "&quot;&lt;elementname&gt;&quot; é obsoleto (aviso do Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40008
- bc40008
dev_langs:
- VB
helpviewer_keywords:
- BC40008
ms.assetid: 729e3eb5-76ac-4c55-9fdd-78350e0de55e
caps.latest.revision: 12
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
ms.openlocfilehash: 77708f052f7aec7a5da2b24605ba3bd794f83979
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="39ltelementnamegt39-is-obsolete-visual-basic-warning"></a><span data-ttu-id="4e30b-102">'&lt;elementname&gt;' é obsoleto (aviso do Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4e30b-102">&#39;&lt;elementname&gt;&#39; is obsolete (Visual Basic Warning)</span></span>
<span data-ttu-id="4e30b-103">Uma instrução tenta acessar um elemento de programação que foi marcado com o <xref:System.ObsoleteAttribute>atributo e com a diretriz para tratá-lo como um aviso.</xref:System.ObsoleteAttribute></span><span class="sxs-lookup"><span data-stu-id="4e30b-103">A statement attempts to access a programming element which has been marked with the <xref:System.ObsoleteAttribute> attribute and the directive to treat it as a warning.</span></span>  
  
 <span data-ttu-id="4e30b-104">Você pode marcar qualquer elemento de programação como sendo não mais em uso aplicando-se <xref:System.ObsoleteAttribute>ao proprietário.</xref:System.ObsoleteAttribute></span><span class="sxs-lookup"><span data-stu-id="4e30b-104">You can mark any programming element as being no longer in use by applying <xref:System.ObsoleteAttribute> to it.</span></span> <span data-ttu-id="4e30b-105">Se você fizer isso, você pode definir o atributo <xref:System.ObsoleteAttribute.IsError%2A>propriedade como `True` ou `False`.</xref:System.ObsoleteAttribute.IsError%2A></span><span class="sxs-lookup"><span data-stu-id="4e30b-105">If you do this, you can set the attribute's <xref:System.ObsoleteAttribute.IsError%2A> property to either `True` or `False`.</span></span> <span data-ttu-id="4e30b-106">Se você defini-lo como `True`, o compilador trata uma tentativa de usar o elemento como um erro.</span><span class="sxs-lookup"><span data-stu-id="4e30b-106">If you set it to `True`, the compiler treats an attempt to use the element as an error.</span></span> <span data-ttu-id="4e30b-107">Se você defini-lo como `False`, ou deixá-lo como padrão `False`, o compilador emite um aviso se houver uma tentativa de usar o elemento.</span><span class="sxs-lookup"><span data-stu-id="4e30b-107">If you set it to `False`, or let it default to `False`, the compiler issues a warning if there is an attempt to use the element.</span></span>  
  
 <span data-ttu-id="4e30b-108">Por padrão, essa mensagem é um aviso, porque o <xref:System.ObsoleteAttribute.IsError%2A>propriedade <xref:System.ObsoleteAttribute>é `False`.</xref:System.ObsoleteAttribute> </xref:System.ObsoleteAttribute.IsError%2A></span><span class="sxs-lookup"><span data-stu-id="4e30b-108">By default, this message is a warning, because the <xref:System.ObsoleteAttribute.IsError%2A> property of <xref:System.ObsoleteAttribute> is `False`.</span></span> <span data-ttu-id="4e30b-109">Para obter mais informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="4e30b-109">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="4e30b-110">**ID do erro:** BC40008</span><span class="sxs-lookup"><span data-stu-id="4e30b-110">**Error ID:** BC40008</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4e30b-111">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="4e30b-111">To correct this error</span></span>  
  
-   <span data-ttu-id="4e30b-112">Certifique-se de que a referência do código-fonte é o nome do elemento digitado corretamente.</span><span class="sxs-lookup"><span data-stu-id="4e30b-112">Ensure that the source-code reference is spelling the element name correctly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e30b-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4e30b-113">See Also</span></span>  
 [<span data-ttu-id="4e30b-114">Visão geral de atributos</span><span class="sxs-lookup"><span data-stu-id="4e30b-114">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)

