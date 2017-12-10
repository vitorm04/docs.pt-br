---
title: "&#39; &lt;classname&gt;&#39; não é compatível com CLS porque a interface &#39;&lt; InterfaceName&gt;&#39; ele implementa não é compatível com CLS"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc40029
- vbc40029
helpviewer_keywords: BC40029
ms.assetid: 178452f3-5575-4da0-9d6c-53bcddb6a338
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 60c41332d3a5d93b05df906eefdeeb0d1b67e638
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/09/2017
---
# <a name="39ltclassnamegt39-is-not-cls-compliant-because-the-interface-39ltinterfacenamegt39-it-implements-is-not-cls-compliant"></a>&#39; &lt;classname&gt;&#39; não é compatível com CLS porque a interface &#39;&lt; InterfaceName&gt;&#39; ele implementa não é compatível com CLS
Uma classe ou interface está marcado como `<CLSCompliant(True)>` quando ela deriva de ou implementa um tipo que está marcado como `<CLSCompliant(False)>` ou não está marcado.  
  
 Para uma classe ou interface seja compatível com o [independência da linguagem e componentes independentes da linguagem](../../../../docs/standard/language-independence-and-language-independent-components.md) (CLS), sua hierarquia de herança inteira deve ser compatível. Isso significa que todos os tipos da qual ela herda, direta ou indiretamente, devem ser compatíveis. Da mesma forma, se uma classe implementa uma ou mais interfaces, eles devem todos ser compatíveis em suas hierarquias de herança.  
  
 Quando você aplica o <xref:System.CLSCompliantAttribute> para um elemento de programação, você definir o atributo `isCompliant` parâmetro a `True` ou `False` para indicar compatibilidade ou incompatibilidade. Não há nenhum padrão para esse parâmetro, e você deve fornecer um valor.  
  
 Se você não se aplicam a <xref:System.CLSCompliantAttribute> a um elemento, ele é considerado incompatível.  
  
 Por padrão, esta mensagem é um aviso. Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID do erro:** BC40029  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Se você precisar de compatibilidade com CLS, defina este tipo em um esquema de implementação ou hierarquia de herança diferente.  
  
-   Se você precisar que esse tipo permaneça em seu esquema de implementação ou hierarquia de herança atual, remova o <xref:System.CLSCompliantAttribute> da sua definição ou marque-a como `<CLSCompliant(False)>`.  
  
## <a name="see-also"></a>Consulte também  
 [\<PAVE sobre > escrevendo código compatível com CLS](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)
