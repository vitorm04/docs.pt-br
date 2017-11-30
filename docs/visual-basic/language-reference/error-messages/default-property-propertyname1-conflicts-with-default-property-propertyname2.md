---
title: "Propriedade padrão &#39; &lt;propertyname1&gt;&#39; está em conflito com a propriedade padrão &#39;&lt; propertyName2&gt;&#39; no &#39;&lt; nome da classe&gt;&#39; e, portanto, deve ser declarado como &#39; Sombras &#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40007
- bc40007
helpviewer_keywords: BC40007
ms.assetid: 692ccf76-5715-4f11-a972-84cf9de30bc1
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: af92c06f6d07b6ea64a05b9043547a46e3679111
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="default-property-39ltpropertyname1gt39-conflicts-with-default-property-39ltpropertyname2gt39-in-39ltclassnamegt39-and-so-should-be-declared-39shadows39"></a><span data-ttu-id="13cc2-102">Propriedade padrão &#39; &lt;propertyname1&gt;&#39; está em conflito com a propriedade padrão &#39;&lt; propertyName2&gt;&#39; no &#39;&lt; nome da classe&gt;&#39; e, portanto, deve ser declarado como &#39; Sombras &#39;</span><span class="sxs-lookup"><span data-stu-id="13cc2-102">Default property &#39;&lt;propertyname1&gt;&#39; conflicts with default property &#39;&lt;propertyname2&gt;&#39; in &#39;&lt;classname&gt;&#39; and so should be declared &#39;Shadows&#39;</span></span>
<span data-ttu-id="13cc2-103">Uma propriedade é declarada com o mesmo nome de uma propriedade definida na classe base.</span><span class="sxs-lookup"><span data-stu-id="13cc2-103">A property is declared with the same name as a property defined in the base class.</span></span> <span data-ttu-id="13cc2-104">Nessa situação, a propriedade nessa classe deve sombrear a propriedade de classe base.</span><span class="sxs-lookup"><span data-stu-id="13cc2-104">In this situation, the property in this class should shadow the base class property.</span></span>  
  
 <span data-ttu-id="13cc2-105">Essa mensagem é um aviso.</span><span class="sxs-lookup"><span data-stu-id="13cc2-105">This message is a warning.</span></span> <span data-ttu-id="13cc2-106">`Shadows`será considerado por padrão.</span><span class="sxs-lookup"><span data-stu-id="13cc2-106">`Shadows` is assumed by default.</span></span> <span data-ttu-id="13cc2-107">Para obter mais informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="13cc2-107">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="13cc2-108">**ID do erro:** BC40007</span><span class="sxs-lookup"><span data-stu-id="13cc2-108">**Error ID:** BC40007</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="13cc2-109">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="13cc2-109">To correct this error</span></span>  
  
-   <span data-ttu-id="13cc2-110">Adicionar o `Shadows` palavra-chave para a declaração, ou alterar o nome da propriedade que está sendo declarado.</span><span class="sxs-lookup"><span data-stu-id="13cc2-110">Add the `Shadows` keyword to the declaration, or change the name of the property being declared.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13cc2-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="13cc2-111">See Also</span></span>  
 [<span data-ttu-id="13cc2-112">Sombras</span><span class="sxs-lookup"><span data-stu-id="13cc2-112">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)  
 [<span data-ttu-id="13cc2-113">Sombreamento no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="13cc2-113">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
