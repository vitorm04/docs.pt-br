---
title: Propriedade padrão &#39; &lt;propertyname1&gt; &#39; está em conflito com a propriedade padrão &#39; &lt;propertyname2&gt; &#39; na &#39; &lt;classname&gt; &#39;e, portanto, deve ser declarado como &#39;sombras&#39;
ms.date: 07/20/2015
f1_keywords:
- vbc40007
- bc40007
helpviewer_keywords:
- BC40007
ms.assetid: 692ccf76-5715-4f11-a972-84cf9de30bc1
ms.openlocfilehash: b305f7a59a9865ebeb6b6f53607757b719fb4d41
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="default-property-39ltpropertyname1gt39-conflicts-with-default-property-39ltpropertyname2gt39-in-39ltclassnamegt39-and-so-should-be-declared-39shadows39"></a><span data-ttu-id="e337e-102">Propriedade padrão &#39; &lt;propertyname1&gt; &#39; está em conflito com a propriedade padrão &#39; &lt;propertyname2&gt; &#39; na &#39; &lt;classname&gt; &#39;e, portanto, deve ser declarado como &#39;sombras&#39;</span><span class="sxs-lookup"><span data-stu-id="e337e-102">Default property &#39;&lt;propertyname1&gt;&#39; conflicts with default property &#39;&lt;propertyname2&gt;&#39; in &#39;&lt;classname&gt;&#39; and so should be declared &#39;Shadows&#39;</span></span>
<span data-ttu-id="e337e-103">Uma propriedade é declarada com o mesmo nome de uma propriedade definida na classe base.</span><span class="sxs-lookup"><span data-stu-id="e337e-103">A property is declared with the same name as a property defined in the base class.</span></span> <span data-ttu-id="e337e-104">Nessa situação, a propriedade nessa classe deve sombrear a propriedade de classe base.</span><span class="sxs-lookup"><span data-stu-id="e337e-104">In this situation, the property in this class should shadow the base class property.</span></span>  
  
 <span data-ttu-id="e337e-105">Essa mensagem é um aviso.</span><span class="sxs-lookup"><span data-stu-id="e337e-105">This message is a warning.</span></span> <span data-ttu-id="e337e-106">`Shadows` será considerado por padrão.</span><span class="sxs-lookup"><span data-stu-id="e337e-106">`Shadows` is assumed by default.</span></span> <span data-ttu-id="e337e-107">Para obter mais informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="e337e-107">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="e337e-108">**ID do erro:** BC40007</span><span class="sxs-lookup"><span data-stu-id="e337e-108">**Error ID:** BC40007</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e337e-109">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="e337e-109">To correct this error</span></span>  
  
-   <span data-ttu-id="e337e-110">Adicionar o `Shadows` palavra-chave para a declaração, ou alterar o nome da propriedade que está sendo declarado.</span><span class="sxs-lookup"><span data-stu-id="e337e-110">Add the `Shadows` keyword to the declaration, or change the name of the property being declared.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e337e-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e337e-111">See Also</span></span>  
 [<span data-ttu-id="e337e-112">Sombras</span><span class="sxs-lookup"><span data-stu-id="e337e-112">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)  
 [<span data-ttu-id="e337e-113">Sombreamento no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e337e-113">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
