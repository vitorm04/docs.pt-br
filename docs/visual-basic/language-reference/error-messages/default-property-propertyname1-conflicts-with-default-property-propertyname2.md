---
title: Propriedade padrão &#39; &lt;propertyname1&gt;&#39; está em conflito com a propriedade padrão &#39;&lt; propertyName2&gt;&#39; no &#39;&lt; nome da classe&gt;&#39; e, portanto, deve ser declarado como &#39; Sombras &#39;
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40007
- bc40007
helpviewer_keywords:
- BC40007
ms.assetid: 692ccf76-5715-4f11-a972-84cf9de30bc1
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: af92c06f6d07b6ea64a05b9043547a46e3679111
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="default-property-39ltpropertyname1gt39-conflicts-with-default-property-39ltpropertyname2gt39-in-39ltclassnamegt39-and-so-should-be-declared-39shadows39"></a>Propriedade padrão &#39; &lt;propertyname1&gt;&#39; está em conflito com a propriedade padrão &#39;&lt; propertyName2&gt;&#39; no &#39;&lt; nome da classe&gt;&#39; e, portanto, deve ser declarado como &#39; Sombras &#39;
Uma propriedade é declarada com o mesmo nome de uma propriedade definida na classe base. Nessa situação, a propriedade nessa classe deve sombrear a propriedade de classe base.  
  
 Essa mensagem é um aviso. `Shadows`será considerado por padrão. Para obter mais informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID do erro:** BC40007  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Adicionar o `Shadows` palavra-chave para a declaração, ou alterar o nome da propriedade que está sendo declarado.  
  
## <a name="see-also"></a>Consulte também  
 [Sombras](../../../visual-basic/language-reference/modifiers/shadows.md)  
 [Sombreamento no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
