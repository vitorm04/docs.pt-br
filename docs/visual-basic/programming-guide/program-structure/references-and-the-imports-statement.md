---
title: Referências e a instrução Imports (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- assemblies [Visual Basic], namespaces
- references [Visual Basic], assembly
- namespaces [Visual Basic], assemblies
- referencing assemblies
- Imports statement [Visual Basic], referencing assemblies
- assemblies [Visual Basic], references
ms.assetid: 38149bd4-0a6f-4b31-b5f8-94a8c33f1600
ms.openlocfilehash: d767f42f8c836995064623b4aca15c86c98ec643
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="references-and-the-imports-statement-visual-basic"></a>Referências e a instrução Imports (Visual Basic)
Você pode disponibilizar objetos externos ao seu projeto, escolhendo o **adicionar referência** comando o **projeto** menu. Referências no Visual Basic poderá apontar para assemblies, que são como bibliotecas mas contêm mais informações.  
  
## <a name="the-imports-statement"></a>A instrução Imports  
 Assemblies de incluem um ou mais namespaces. Quando você adiciona uma referência a um assembly, você também pode adicionar um `Imports` instrução em um módulo que controla a visibilidade dos namespaces daquele assembly dentro do módulo. O `Imports` instrução fornece um contexto de escopo que permite que você use apenas a parte do namespace necessária para fornecer uma referência única.  
  
 O `Imports` instrução tem a seguinte sintaxe:  
  
 `Imports` [`|``Aliasname` =] `Namespace`  
  
 `Aliasname` se refere a um nome curto, que você pode usar para se referir a um namespace importado no código. `Namespace` é uma referência de projeto, por meio de uma definição de dentro do projeto ou anterior de um namespace disponível através de `Imports` instrução.  
  
 Um módulo pode conter qualquer número de `Imports` instruções. Elas devem aparecer após qualquer `Option` instruções, se presente, mas antes de qualquer outro código.  
  
> [!NOTE]
>  Não confunda referências de projeto com o `Imports` instrução ou o `Declare` instrução. Referências de projeto tornam objetos externos, como objetos em assemblies, disponíveis para projetos do Visual Basic. O `Imports` instrução é usada para simplificar o acesso às referências do projeto, mas não fornece acesso a esses objetos. O `Declare` instrução é usada para declarar uma referência a um procedimento externo em uma biblioteca de vínculo dinâmico (DLL).  
  
## <a name="using-aliases-with-the-imports-statement"></a>Usando Aliases com a instrução Imports  
 O `Imports` instrução torna mais fácil para os métodos de acesso de classes, eliminando a necessidade de digitar explicitamente os nomes totalmente qualificados de referências. Os aliases permitem que você atribua um nome amigável para apenas uma parte de um namespace. Por exemplo, o retorno de carro/linha de feed de sequência que faz com que uma única parte do texto a ser exibido em várias linhas é parte do <xref:Microsoft.VisualBasic.ControlChars> módulo o <xref:Microsoft.VisualBasic?displayProperty=nameWithType> namespace. Para usar esta constante em um programa sem um alias, você precisa digitar o código a seguir:  
  
 [!code-vb[VbVbalrApplication#3](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_1.vb)]  
  
 `Imports` instruções devem sempre ser as primeiras linhas imediatamente após qualquer `Option` instruções em um módulo. O fragmento de código a seguir mostra como importar e atribuir um alias para o <xref:Microsoft.VisualBasic.ControlChars?displayProperty=nameWithType> módulo:  
  
 [!code-vb[VbVbalrApplication#4](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_2.vb)]  
  
 Referências futuras a esse namespace podem ser consideravelmente menores:  
  
 [!code-vb[VbVbalrApplication#5](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_3.vb)]  
  
 Se um `Imports` instrução não incluir um nome de alias, elementos definidos no namespace importado podem ser usados no módulo sem qualificação. Se o nome do alias for especificado, ele deve ser usado como um qualificador para nomes contidos naquele namespace.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.ControlChars>  
 <xref:Microsoft.VisualBasic>  
   
 [Namespaces no Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 [Assemblies e o Cache de Assembly Global](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [Como criar e usar assemblies usando a linha de comando](http://msdn.microsoft.com/library/70f65026-3687-4e9c-ab79-c18b97dd8be4)  
 [Instrução Imports (Tipo e Namespace .NET)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
