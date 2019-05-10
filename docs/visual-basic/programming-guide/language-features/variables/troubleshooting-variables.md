---
title: Solucionando problemas de variáveis no Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting [Visual Basic], variables
- variables [Visual Basic], troubleshooting
ms.assetid: 928a2dc8-e565-4ae4-8ba3-80cc0cb50090
ms.openlocfilehash: 31aca95bb292ecd0bb04fda6ded83d4af8be0e2f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64598610"
---
# <a name="troubleshooting-variables-in-visual-basic"></a>Solucionando problemas de variáveis no Visual Basic
Esta página lista alguns problemas comuns que podem ocorrer ao trabalhar com variáveis no Visual Basic.  
  
## <a name="unable-to-access-members-of-an-object"></a>Não é possível acessar membros de um objeto  
 Se seu código tenta acessar uma propriedade ou método em um objeto, há dois resultados de erro possíveis:  
  
- O compilador pode gerar uma mensagem de erro se você declarar a variável de objeto para ser de um tipo específico e, em seguida, fazer referência a um membro não definido por esse tipo.  
  
- Um tempo de execução <xref:System.MemberAccessException> ocorre quando o objeto atribuído a uma variável de objeto não expõe o membro que seu código está tentando acessar. No caso de uma variável de [tipo de dados do objeto](../../../../visual-basic/language-reference/data-types/object-data-type.md), você também pode obter essa exceção se o membro não for `Public`. Isso ocorre porque a associação tardia permite acesso somente a `Public` membros.  
  
 Quando o [instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) conjuntos de verificação de tipo `On`, uma variável de objeto pode acessar somente os métodos e propriedades da classe com a qual você declará-la. O exemplo a seguir ilustra essa situação.  

 [!code-vb[VbVbalrVariables#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrVariables/VB/Class1.vb#2)]  
  
 Neste exemplo, `p` pode usar somente os membros do <xref:System.Object> classe em si, que não incluem o `Left` propriedade. Por outro lado, `q` tiver sido declarado para ser do tipo <xref:System.Windows.Forms.Label>, portanto, ele pode usar todos os métodos e propriedades da <xref:System.Windows.Forms.Label> classe o <xref:System.Windows.Forms> namespace.  
  
### <a name="correct-approach"></a>Abordagem correta  
 Para poder acessar todos os membros de um objeto de uma determinada classe, declare a variável de objeto para ser do tipo de classe quando possível. Se você não pode fazer isso, por exemplo, se você não souber o objeto de tipo em tempo de compilação, você deve definir `Option Strict` para `Off` e declarar a variável como o [tipo de dados do objeto](../../../../visual-basic/language-reference/data-types/object-data-type.md). Isso permite que os objetos de qualquer tipo a ser atribuído à variável, e você deve tomar medidas para garantir que o objeto atribuído no momento é de um tipo aceitável. Você pode usar o [operador TypeOf](../../../../visual-basic/language-reference/operators/typeof-operator.md) para tomar essa decisão.  
  
## <a name="other-components-cannot-access-your-variable"></a>Outros componentes não é possível acessar sua variável  
 Nomes de Visual Basic são *diferencia maiusculas de minúsculas*. Se dois nomes diferem somente no caso alfabético, o compilador interpreta como o mesmo nome. Por exemplo, ele considera `ABC` e `abc` para se referir ao mesmo elemento declarado.  
  
 No entanto, o common language runtime (CLR) usa *diferencia maiusculas de minúsculas* associação. Portanto, quando você produzir um assembly ou uma DLL e disponibilizá-lo para outros assemblies, seus nomes não diferenciam maiusculas de minúsculas. Por exemplo, se você definir uma classe com um elemento chamado `ABC`, e outros assemblies fazer uso de sua classe por meio do common language runtime, eles devem se referir ao elemento como `ABC`. Se você posteriormente recompilar sua classe e alterar o nome do elemento para `abc`, os outros assemblies usando sua classe não podem acessar esse elemento. Portanto, quando você liberar uma versão atualizada de um assembly, você não deve alterar maiusculas e minúsculas em qualquer elemento público.  
  
 Para obter mais informações, consulte [Common Language Runtime](../../../../standard/clr.md).  
  
### <a name="correct-approach"></a>Abordagem correta  
 Para permitir que outros componentes acessar suas variáveis, trate seus nomes como se diferenciassem maiusculas de minúsculas. Quando você estiver testando sua classe ou módulo, certifique-se de que outros assemblies são de associação para as variáveis que você espera que eles. Depois que você publicou um componente, não faça quaisquer modificações em nomes de variáveis existentes, incluindo seus casos de alteração.  
  
## <a name="wrong-variable-being-used"></a>Variável incorreta que está sendo usado  
 Quando você tiver mais de uma variável com o mesmo nome, o compilador do Visual Basic tenta resolver cada referência a esse nome. Se as variáveis têm escopo diferente, o compilador resolve uma referência para a declaração com o escopo mais restrito. Se eles tiverem o mesmo escopo, a resolução falhará e o compilador sinaliza um erro. Para obter mais informações, consulte [referências a elementos declarados](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
### <a name="correct-approach"></a>Abordagem correta  
 Evite usar variáveis com o mesmo nome mas com escopo diferente. Se você estiver usando outros assemblies ou projetos, evite usar qualquer nomes definidos nesses componentes externos tanto quanto possível. Se você tiver mais de uma variável com o mesmo nome, certifique-se de que você qualifica cada referência a ele. Para obter mais informações, consulte [referências a elementos declarados](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
## <a name="see-also"></a>Consulte também

- [Variáveis](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [Declaração de Variável](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Variáveis de Objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Declaração de Variável do Objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [Como: Acessar membros de um objeto](../../../../visual-basic/programming-guide/language-features/variables/how-to-access-members-of-an-object.md)
- [Valores de Variável de Objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [Como: Determinar que tipo uma variável de objeto se refere a](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-what-type-an-object-variable-refers-to.md)
- [Referências a Elementos Declarados](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Nomes de Elementos Declarados](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
