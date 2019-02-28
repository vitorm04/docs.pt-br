---
title: Palavras-chave como nomes de elemento em código (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, naming conventions
- keywords [Visual Basic], in code
- name conflicts [Visual Basic]
- element names [Visual Basic], in code
ms.assetid: 2e4e8e02-23f7-49b9-a1c8-2b0402b6b525
ms.openlocfilehash: 053149334118d69e5e85bdbd0f9a45e855e3d4dd
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56980094"
---
# <a name="keywords-as-element-names-in-code-visual-basic"></a>Palavras-chave como nomes de elemento em código (Visual Basic)
Qualquer elemento de programa — como uma variável, classe ou membro — pode ter o mesmo nome que uma palavra-chave restrita. Por exemplo, você pode criar uma variável chamada `Loop`. No entanto, para referir-se à sua versão dele — que tem o mesmo nome que restritas `Loop` palavra-chave — você deve precedê-lo com uma cadeia de caracteres de qualificação completa ou coloque-o entre colchetes (`[ ]`), como mostra o exemplo a seguir.  
  
 [!code-vb[VbVbcnConventions#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#8)]  
  
 Se você não fizer uma destas, Visual Basic assume o uso da intrínseca `Loop` palavra-chave e produz um erro, como no exemplo a seguir:  
  
 `' The following statement causes a compiler error.`  
  
 `Loop.Visible = True`  
  
 Você pode usar colchetes para se referir a formulários e controles e ao declarar uma variável ou definindo um procedimento com o mesmo nome como uma palavra-chave restrita. É fácil esquecer de qualificar nomes ou incluir colchetes e, portanto, introduzir erros no seu código e torná-lo mais difícil de ler. Por esse motivo, recomendamos que você não use palavras-chave restritas como os nomes dos elementos do programa. No entanto, se uma versão futura do Visual Basic define uma nova palavra-chave que está em conflito com um formulário existente ou o nome do controle, em seguida, você pode usar essa técnica quando atualizar seu código para trabalhar com a nova versão.  
  
> [!NOTE]
>  O programa também pode incluir nomes de elemento fornecidos por outros assemblies referenciados. Se esses nomes em conflito com palavras-chave restritas, então colocar colchetes ao redor deles faz com que o Visual Basic para interpretá-los como seus elementos definidos.  
  
## <a name="see-also"></a>Consulte também
- [Convenções de nomenclatura do Visual Basic](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
- [Estrutura do Programa e Convenções de Código](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [Palavras-chave](../../../visual-basic/language-reference/keywords/index.md)
