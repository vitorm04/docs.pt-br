---
title: Palavras-chave como nomes de elemento em código (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, naming conventions
- keywords [Visual Basic], in code
- name conflicts [Visual Basic]
- element names [Visual Basic], in code
ms.assetid: 2e4e8e02-23f7-49b9-a1c8-2b0402b6b525
ms.openlocfilehash: 53c3172e8518115d001c23be2430fbc87ae1b60f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33652572"
---
# <a name="keywords-as-element-names-in-code-visual-basic"></a>Palavras-chave como nomes de elemento em código (Visual Basic)
Qualquer elemento do programa, como uma variável, classe ou membro — pode ter o mesmo nome de uma palavra-chave restrita. Por exemplo, você pode criar uma variável chamada `Loop`. No entanto, para referir-se à sua versão do mesmo — que tem o mesmo nome que o restrito `Loop` palavra-chave — você deve precedê-lo de uma cadeia de caracteres de qualificação completa ou coloque-o entre colchetes (`[ ]`), como mostra o exemplo a seguir.  
  
 [!code-vb[VbVbcnConventions#8](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/keywords-as-element-names-in-code_1.vb)]  
  
 Se você não fizer qualquer uma delas, Visual Basic assume o uso de intrínseca `Loop` palavra-chave e produz um erro, como no exemplo a seguir:  
  
 `' The following statement causes a compiler error.`  
  
 `Loop.Visible = True`  
  
 Você pode usar colchetes quando referir a formulários e controles e quando declarando uma variável ou definindo um procedimento com o mesmo nome como uma palavra-chave restrita. É fácil esquecer de qualificar nomes ou incluir colchetes e, portanto, introduzir erros em seu código e torná-lo mais difícil de ler. Por esse motivo, é recomendável que você não use palavras-chave restritas como os nomes dos elementos do programa. No entanto, se uma versão futura do Visual Basic define uma nova palavra-chave que está em conflito com um formulário existente ou o nome do controle, em seguida, você pode usar essa técnica quando atualizar seu código para trabalhar com a nova versão.  
  
> [!NOTE]
>  O programa também pode incluir nomes de elemento fornecidos por outros assemblies referenciados. Se esses nomes em conflito com palavras-chave restritas, então colocar colchetes ao redor deles faz com que o Visual Basic para interpretá-los como seus elementos definidos.  
  
## <a name="see-also"></a>Consulte também  
 [Convenções de nomenclatura do Visual Basic](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)  
 [Estrutura do Programa e Convenções de Código](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)  
 [Palavras-chave](../../../visual-basic/language-reference/keywords/index.md)
