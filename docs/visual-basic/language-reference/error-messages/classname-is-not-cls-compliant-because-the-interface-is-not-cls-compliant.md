---
title: "&quot;&lt;classname&gt;&quot; não é compatível com CLS porque a interface &quot;&lt;interfacename&gt;&quot; ele implementa não é compatível com CLS | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc40029
- vbc40029
dev_langs:
- VB
helpviewer_keywords:
- BC40029
ms.assetid: 178452f3-5575-4da0-9d6c-53bcddb6a338
caps.latest.revision: 13
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: 1e5c948ed5ddeaa2f8a8efd4aa83a2539cc862f3
ms.lasthandoff: 03/13/2017

---
# <a name="39ltclassnamegt39-is-not-cls-compliant-because-the-interface-39ltinterfacenamegt39-it-implements-is-not-cls-compliant"></a>'&lt;classname&gt;' não é compatível com CLS porque a interface '&lt;interfacename&gt;' ele implementa não é compatível com CLS
Uma classe ou interface está marcado como `<CLSCompliant(True)>` quando ela deriva de ou implementa um tipo que está marcado como `<CLSCompliant(False)>` ou não está marcado.  
  
 Para uma classe ou interface seja compatível com o [independência da linguagem e componentes independentes de linguagem](https://msdn.microsoft.com/library/12a7a7h3) (CLS), sua hierarquia de herança inteira deve ser compatível. Isso significa que cada tipo do qual ele herda, direta ou indiretamente, deve ser compatível. Da mesma forma, se uma classe implementa uma ou mais interfaces, eles devem todos ser compatíveis em suas hierarquias de herança.  
  
 Quando você aplica o <xref:System.CLSCompliantAttribute>para um elemento de programação, você definir o atributo `isCompliant` parâmetro como `True` ou `False` para indicar compatibilidade ou incompatibilidade.</xref:System.CLSCompliantAttribute> Não há nenhum padrão para esse parâmetro, e você deve fornecer um valor.  
  
 Se você não aplicar o <xref:System.CLSCompliantAttribute>a um elemento, ele é considerado incompatível.</xref:System.CLSCompliantAttribute>  
  
 Por padrão, esta mensagem é um aviso. Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID do erro:** BC40029  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Se você precisar de compatibilidade com CLS, defina este tipo em um esquema de implementação ou hierarquia de herança diferente.  
  
-   Se você precisar que esse tipo permaneça em seu esquema atual de implementação ou hierarquia de herança, remova o <xref:System.CLSCompliantAttribute>da sua definição ou marque-a como `<CLSCompliant(False)>`.</xref:System.CLSCompliantAttribute>  
  
## <a name="see-also"></a>Consulte também  
 [\<PAVE em > escrevendo código compatível com CLS](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)
