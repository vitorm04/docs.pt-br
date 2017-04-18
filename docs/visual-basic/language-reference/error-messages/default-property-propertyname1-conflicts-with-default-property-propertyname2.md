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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 803b42b7659c16fd97251635e4b6ba49362e0a02
ms.lasthandoff: 03/13/2017

---
# <a name="default-property-39ltpropertyname1gt39-conflicts-with-default-property-39ltpropertyname2gt39-in-39ltclassnamegt39-and-so-should-be-declared-39shadows39"></a>Propriedade padrão '&lt;propertyname1&gt;'está em conflito com a propriedade padrão'&lt;propertyname2&gt;'in'&lt;classname&gt;' e, portanto, deve ser declarado como 'Shadows'
Uma propriedade é declarada com o mesmo nome de uma propriedade definida na classe base. Nessa situação, a propriedade nessa classe deve sombrear a propriedade de classe base.  
  
 Essa mensagem é um aviso. `Shadows`será considerado por padrão. Para obter mais informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID do erro:** BC40007  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Adicionar o `Shadows` palavra-chave para a declaração, ou alterar o nome da propriedade que está sendo declarado.  
  
## <a name="see-also"></a>Consulte também  
 [Sombras](../../../visual-basic/language-reference/modifiers/shadows.md)   
 [Sombreamento no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
