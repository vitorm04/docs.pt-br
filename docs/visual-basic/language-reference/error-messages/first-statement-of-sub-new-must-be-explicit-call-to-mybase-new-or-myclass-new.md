---
title: "A primeira instrução deste 'Sub New' deve ser uma chamada explícita para MyBase.New' ou 'MyClass.New' porque '<constructorname>' na classe base '<baseclassname>' de '<derivedclassname>' está marcado como obsoleto: '<errormessage>'"
ms.date: 07/20/2015
f1_keywords:
- vbc30920
- bc30920
helpviewer_keywords:
- BC30920
ms.assetid: e47dc755-4294-4368-b813-2177b7677957
ms.openlocfilehash: 31f92d1e52e50b2a87fd6a6af6e3c87292f4437f
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55268785"
---
# <a name="first-statement-of-this-sub-new-must-be-an-explicit-call-to-mybasenew-or-myclassnew-because-the-constructorname-in-the-base-class-baseclassname-of-derivedclassname-is-marked-obsolete-errormessage"></a>A primeira instrução deste 'Sub New' deve ser uma chamada explícita para 'MyBase. New' ou 'MyClass. New' porque o '\<constructorname >' na classe base\<baseclassname >' de '\<derivedclassname >' está marcado como obsoleto: '\< ErrorMessage >'
Um construtor de classe não chama explicitamente um construtor de classe base, e o construtor de classe base implícita é marcado com o <xref:System.ObsoleteAttribute> atributo e a diretiva para tratá-lo como um erro.  
  
 Quando um construtor de classe derivada não chama um construtor de classe base, o Visual Basic tenta gerar uma chamada implícita para um construtor sem parâmetros de classe base. Se não houver nenhum construtor acessível na classe base que pode ser chamado sem argumentos, o Visual Basic não é possível gerar uma chamada implícita. Nesse caso, o construtor necessário é marcado com o <xref:System.ObsoleteAttribute> de atributo, portanto, o Visual Basic não pode chamá-lo.  
  
 Você pode marcar qualquer elemento de programação como sendo não mais em uso por meio da aplicação <xref:System.ObsoleteAttribute> a ele. Se você fizer isso, você pode definir o atributo <xref:System.ObsoleteAttribute.IsError%2A> propriedade para um `True` ou `False`. Se você defini-lo como `True`, o compilador trata uma tentativa de usar o elemento como um erro. Se você defini-lo `False`, ou deixá-lo como padrão `False`, o compilador emitirá um aviso se não houver uma tentativa de usar o elemento.  
  
 **ID do erro:** BC30920  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Examine a mensagem de erro entre aspas e tomar as devidas providências.  
  
2.  Incluir uma chamada para `MyBase.New()` ou `MyClass.New()` como a primeira instrução da `Sub New` na classe derivada.  
  
## <a name="see-also"></a>Consulte também
- [Visão geral de atributos](../../../visual-basic/programming-guide/concepts/attributes/index.md)

