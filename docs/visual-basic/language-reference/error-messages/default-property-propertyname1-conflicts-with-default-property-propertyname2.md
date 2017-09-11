---
title: "Propriedade padrão &quot;&lt;propertyname1&gt;&quot;está em conflito com a propriedade padrão&quot;&lt;propertyname2&gt;&quot;in&quot;&lt;classname&gt;&quot; e, portanto, deve ser declarado como &quot;Shadows&quot; | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40007
- bc40007
dev_langs:
- VB
helpviewer_keywords:
- BC40007
ms.assetid: 692ccf76-5715-4f11-a972-84cf9de30bc1
caps.latest.revision: 9
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
ms.openlocfilehash: 6eac9e0fdc468e27afac82a8a7c9b2251a8f7317
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="default-property-39ltpropertyname1gt39-conflicts-with-default-property-39ltpropertyname2gt39-in-39ltclassnamegt39-and-so-should-be-declared-39shadows39"></a><span data-ttu-id="1c0fd-102">Propriedade padrão '&lt;propertyname1&gt;'está em conflito com a propriedade padrão'&lt;propertyname2&gt;'in'&lt;classname&gt;' e, portanto, deve ser declarado como 'Shadows'</span><span class="sxs-lookup"><span data-stu-id="1c0fd-102">Default property &#39;&lt;propertyname1&gt;&#39; conflicts with default property &#39;&lt;propertyname2&gt;&#39; in &#39;&lt;classname&gt;&#39; and so should be declared &#39;Shadows&#39;</span></span>
<span data-ttu-id="1c0fd-103">Uma propriedade é declarada com o mesmo nome de uma propriedade definida na classe base.</span><span class="sxs-lookup"><span data-stu-id="1c0fd-103">A property is declared with the same name as a property defined in the base class.</span></span> <span data-ttu-id="1c0fd-104">Nessa situação, a propriedade nessa classe deve sombrear a propriedade de classe base.</span><span class="sxs-lookup"><span data-stu-id="1c0fd-104">In this situation, the property in this class should shadow the base class property.</span></span>  
  
 <span data-ttu-id="1c0fd-105">Essa mensagem é um aviso.</span><span class="sxs-lookup"><span data-stu-id="1c0fd-105">This message is a warning.</span></span> <span data-ttu-id="1c0fd-106">`Shadows`será considerado por padrão.</span><span class="sxs-lookup"><span data-stu-id="1c0fd-106">`Shadows` is assumed by default.</span></span> <span data-ttu-id="1c0fd-107">Para obter mais informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="1c0fd-107">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="1c0fd-108">**ID do erro:** BC40007</span><span class="sxs-lookup"><span data-stu-id="1c0fd-108">**Error ID:** BC40007</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1c0fd-109">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="1c0fd-109">To correct this error</span></span>  
  
-   <span data-ttu-id="1c0fd-110">Adicionar o `Shadows` palavra-chave para a declaração, ou alterar o nome da propriedade que está sendo declarado.</span><span class="sxs-lookup"><span data-stu-id="1c0fd-110">Add the `Shadows` keyword to the declaration, or change the name of the property being declared.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c0fd-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1c0fd-111">See Also</span></span>  
 <span data-ttu-id="1c0fd-112">[Sombras](../../../visual-basic/language-reference/modifiers/shadows.md) </span><span class="sxs-lookup"><span data-stu-id="1c0fd-112">[Shadows](../../../visual-basic/language-reference/modifiers/shadows.md) </span></span>  
<span data-ttu-id="1c0fd-113"> [Sombreamento no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)</span><span class="sxs-lookup"><span data-stu-id="1c0fd-113"> [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)</span></span>
