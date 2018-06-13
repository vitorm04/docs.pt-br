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
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33586618"
---
# <a name="default-property-39ltpropertyname1gt39-conflicts-with-default-property-39ltpropertyname2gt39-in-39ltclassnamegt39-and-so-should-be-declared-39shadows39"></a>Propriedade padrão &#39; &lt;propertyname1&gt; &#39; está em conflito com a propriedade padrão &#39; &lt;propertyname2&gt; &#39; na &#39; &lt;classname&gt; &#39;e, portanto, deve ser declarado como &#39;sombras&#39;
Uma propriedade é declarada com o mesmo nome de uma propriedade definida na classe base. Nessa situação, a propriedade nessa classe deve sombrear a propriedade de classe base.  
  
 Essa mensagem é um aviso. `Shadows` será considerado por padrão. Para obter mais informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID do erro:** BC40007  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Adicionar o `Shadows` palavra-chave para a declaração, ou alterar o nome da propriedade que está sendo declarado.  
  
## <a name="see-also"></a>Consulte também  
 [Sombras](../../../visual-basic/language-reference/modifiers/shadows.md)  
 [Sombreamento no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
