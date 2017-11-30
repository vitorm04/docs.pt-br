---
title: "Solucionando problemas de variáveis no Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- troubleshooting [Visual Basic], variables
- variables [Visual Basic], troubleshooting
ms.assetid: 928a2dc8-e565-4ae4-8ba3-80cc0cb50090
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bf6d2a0c7318c12b3001a92a8aa06625b4edabb6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="troubleshooting-variables-in-visual-basic"></a>Solucionando problemas de variáveis no Visual Basic
Esta página lista alguns problemas comuns que podem ocorrer ao trabalhar com variáveis em [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].  
  
## <a name="unable-to-access-members-of-an-object"></a>Não é possível acessar membros de um objeto  
 Se seu código tentar acessar uma propriedade ou método em um objeto, há dois resultados possíveis de erro:  
  
-   O compilador pode gerar uma mensagem de erro se você declarar a variável de objeto para ser de um tipo específico e, em seguida, se referir a um membro não definido por este tipo.  
  
-   Um tempo de execução <xref:System.MemberAccessException> ocorre quando o objeto atribuído a uma variável de objeto não expõe o membro que seu código está tentando acessar. No caso de uma variável de [tipo de dados de objeto](../../../../visual-basic/language-reference/data-types/object-data-type.md), você também pode obter essa exceção se o membro não é `Public`. Isso ocorre porque a associação tardia permite acesso somente à `Public` membros.  
  
 Quando o [instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) conjuntos de verificação de tipo `On`, uma variável de objeto pode acessar somente os métodos e propriedades da classe com a qual foi declarada. O exemplo a seguir ilustra essa situação.  

 [!code-vb[VbVbalrVariables#2](../../../../visual-basic/programming-guide/language-features/variables/codesnippet/VisualBasic/troubleshooting-variables_1.vb)]  
  
 Neste exemplo, `p` pode usar somente os membros do <xref:System.Object> classe em si, que não inclui o `Left` propriedade. Por outro lado, `q` foi declarado para ser do tipo <xref:System.Windows.Forms.Label>, portanto, ele pode usar todos os métodos e propriedades do <xref:System.Windows.Forms.Label> classe no <xref:System.Windows.Forms> namespace.  
  
### <a name="correct-approach"></a>Abordagem correta  
 Para poder acessar todos os membros de um objeto de uma determinada classe, declare a variável de objeto para ser do tipo de classe quando possível. Se você não pode fazer isso, por exemplo, se você não souber o objeto de tipo em tempo de compilação, você deve definir `Option Strict` para `Off` e declarar a variável para ser o [tipo de dados do objeto](../../../../visual-basic/language-reference/data-types/object-data-type.md). Isso permite que os objetos de qualquer tipo a ser atribuído à variável, e você deve tomar medidas para garantir que o objeto atualmente atribuído seja de um tipo aceitável. Você pode usar o [operador TypeOf](../../../../visual-basic/language-reference/operators/typeof-operator.md) para tomar essa decisão.  
  
## <a name="other-components-cannot-access-your-variable"></a>Outros componentes não é possível acessar a variável  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]os nomes são *maiusculas de minúsculas*. Se dois nomes diferem somente no caso alfabético, o compilador interpreta como o mesmo nome. Por exemplo, ele considera `ABC` e `abc` para se referir ao mesmo elemento declarado.  
  
 No entanto, o common language runtime (CLR) usa *diferencia maiusculas de minúsculas* associação. Portanto, quando você produzir um assembly ou uma DLL e disponibilizá-lo para outros assemblies, seus nomes não diferenciam maiusculas de minúsculas. Por exemplo, se você definir uma classe com um elemento chamado `ABC`, e outros assemblies fazer uso de sua classe por meio do common language runtime, eles devem se referir ao elemento como `ABC`. Se você posteriormente recompilar sua classe e alterar o nome do elemento para `abc`, os outros assemblies usando a classe não podem mais acessar esse elemento. Portanto, quando você solta uma versão atualizada de um assembly, você não deve alterar maiusculas e minúsculas em quaisquer elementos públicos.  
  
 Para obter mais informações, consulte [Common Language Runtime](../../../../standard/clr.md).  
  
### <a name="correct-approach"></a>Abordagem correta  
 Para permitir que outros componentes acessem as variáveis, trate seus nomes como se fossem diferencia maiusculas de minúsculas. Quando você estiver testando sua classe ou um módulo, certifique-se de que outros assemblies são associados às variáveis esperadas. Depois de publicar um componente, não faz nenhuma modificação para nomes de variáveis existentes, incluindo alterar seus casos.  
  
## <a name="wrong-variable-being-used"></a>Variável errada sendo usado  
 Quando você tiver mais de uma variável com o mesmo nome, o [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compilador tenta resolver cada referência a esse nome. Se as variáveis têm escopo diferente, o compilador resolve uma referência para a declaração com o escopo mais restrito. Se eles tiverem o mesmo escopo, a resolução falhará e o compilador sinaliza um erro. Para obter mais informações, consulte [referências a elementos declarados](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
### <a name="correct-approach"></a>Abordagem correta  
 Evite usar variáveis com o mesmo nome mas escopo diferente. Se você estiver usando outros assemblies ou projetos, evite usar qualquer nomes definidos nesses componentes externos tanto quanto possível. Se você tiver mais de uma variável com o mesmo nome, certifique-se de que qualificar cada referência a ela. Para obter mais informações, consulte [referências a elementos declarados](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
## <a name="see-also"></a>Consulte também  
 [Variáveis](../../../../visual-basic/programming-guide/language-features/variables/index.md)  
 [Declaração de Variável](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [Variáveis de Objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [Declaração de Variável do Objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)  
 [Como acessar membros de um objeto](../../../../visual-basic/programming-guide/language-features/variables/how-to-access-members-of-an-object.md)  
 [Valores de Variável de Objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)  
 [Como determinar a que tipo uma variável de objeto se refere](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-what-type-an-object-variable-refers-to.md)  
 [Referências a Elementos Declarados](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [Nomes de Elementos Declarados](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
