---
title: "Palavras-chave como nomes de elementos em código (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- Visual Basic code, naming conventions
- keywords [Visual Basic], in code
- name conflicts
- element names, in code
ms.assetid: 2e4e8e02-23f7-49b9-a1c8-2b0402b6b525
caps.latest.revision: 11
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
ms.openlocfilehash: 3994f5baa644e86d03ef549cb29b8b264bd63d48
ms.lasthandoff: 03/13/2017

---
# <a name="keywords-as-element-names-in-code-visual-basic"></a>Palavras-chave como nomes de elemento em código (Visual Basic)
Qualquer elemento de programa — como uma variável, classe ou membro — pode ter o mesmo nome que uma palavra-chave restrita. Por exemplo, você pode criar uma variável chamada `Loop`. No entanto, para se referir a sua versão disso — que tem o mesmo nome restritas `Loop` palavra-chave — você deve precedê-lo com uma cadeia de caracteres de qualificação completa ou colocá-lo entre colchetes (`[ ]`), como mostra o exemplo a seguir.  
  
 [!code-vb[VbVbcnConventions n º&8;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/keywords-as-element-names-in-code_1.vb)]  
  
 Se você não fizer um deles, Visual Basic assume o uso da intrínseca `Loop` palavra-chave e produz um erro, como no exemplo a seguir:  
  
 `' The following statement causes a compiler error.`  
  
 `Loop.Visible = True`  
  
 Você pode usar colchetes quando referir a formulários e controles e quando declarando uma variável ou definindo um procedimento com o mesmo nome que uma palavra chave restrita. É fácil esquecer de qualificar nomes ou incluir colchetes e, portanto, introduzir erros em seu código e torná-lo mais difícil de ler. Por esse motivo, recomendamos que você não use palavras-chave restritas como nomes de elementos de programa. No entanto, se uma versão futura do Visual Basic define uma nova palavra-chave que conflite com um formulário existente ou o nome do controle, em seguida, você pode usar essa técnica quando atualizar seu código para trabalhar com a nova versão.  
  
> [!NOTE]
>  O programa também pode incluir nomes de elemento fornecidos por outros assemblies referenciados. Se esses nomes entrarem em conflito com palavras-chave restritas, então colocar colchetes em volta deles faz com que o Visual Basic para interpretá-los como seus elementos definidos.  
  
## <a name="see-also"></a>Consulte também  
 [Convenções de nomenclatura do Visual Basic](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)   
 [Estrutura do programa e convenções de código](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)   
 [Palavras-chave](../../../visual-basic/language-reference/keywords/index.md)
