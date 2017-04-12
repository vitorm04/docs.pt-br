---
title: "Solucionando problemas de variáveis no Visual Basic | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- troubleshooting [Visual Basic], variables
- variables [Visual Basic], troubleshooting
ms.assetid: 928a2dc8-e565-4ae4-8ba3-80cc0cb50090
caps.latest.revision: 20
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 9cddf7ced50c42514ebc9a613f49adee31edde0b
ms.lasthandoff: 03/13/2017

---
# <a name="troubleshooting-variables-in-visual-basic"></a>Solucionando problemas de variáveis no Visual Basic
Esta página lista alguns problemas comuns que podem ocorrer ao trabalhar com variáveis em [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
## <a name="unable-to-access-members-of-an-object"></a>Não é possível acessar membros de um objeto  
 Se seu código tenta acessar uma propriedade ou método em um objeto, há dois resultados possíveis de erro:  
  
-   O compilador pode gerar uma mensagem de erro se você declarar a variável de objeto para ser de um tipo específico e, em seguida, se referir a um membro não definido por aquele tipo.  
  
-   Um tempo de execução <xref:System.MemberAccessException>ocorre quando o objeto atribuído a uma variável de objeto não expõe o membro que seu código está tentando acessar.</xref:System.MemberAccessException> No caso de uma variável de [tipo de dados Object](../../../../visual-basic/language-reference/data-types/object-data-type.md), você também pode obter essa exceção se o membro não é `Public`. Isso ocorre porque a associação tardia permite acesso somente a `Public` membros.  
  
 Quando o [instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) conjuntos de verificação de tipo `On`, uma variável de objeto pode acessar somente os métodos e propriedades da classe com a qual foi declarada. O exemplo a seguir ilustra essa situação.  

 [!code-vb[VbVbalrVariables n º&2;](../../../../visual-basic/programming-guide/language-features/variables/codesnippet/VisualBasic/troubleshooting-variables_1.vb)]  
  
 Neste exemplo, `p` pode usar somente os membros do <xref:System.Object>classe em si, que não inclui o `Left` propriedade.</xref:System.Object> Por outro lado, `q` foi declarado para ser do tipo <xref:System.Windows.Forms.Label>, portanto, ele pode usar todos os métodos e propriedades da <xref:System.Windows.Forms.Label>classe o <xref:System.Windows.Forms>namespace.</xref:System.Windows.Forms> </xref:System.Windows.Forms.Label> </xref:System.Windows.Forms.Label>  
  
### <a name="correct-approach"></a>Abordagem correta  
 Para ser capaz de acessar todos os membros de um objeto de uma determinada classe, declare a variável de objeto para ser do tipo de classe quando possível. Se você não puder fazer isso, por exemplo, se você não souber o objeto de tipo em tempo de compilação, você deve definir `Option Strict` para `Off` e declarar a variável para ser o [tipo de dados do objeto](../../../../visual-basic/language-reference/data-types/object-data-type.md). Isso permite que os objetos de qualquer tipo a ser atribuído à variável, e você deve tomar medidas para garantir que o objeto atualmente atribuído seja de um tipo aceitável. Você pode usar o [operador TypeOf](../../../../visual-basic/language-reference/operators/typeof-operator.md) para tomar essa decisão.  
  
## <a name="other-components-cannot-access-your-variable"></a>Outros componentes não podem acessar sua variável  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]os nomes são *diferenciam maiusculas de minúsculas*. Se dois nomes diferem somente no caso alfabético, o compilador interpreta como o mesmo nome. Por exemplo, ele considera `ABC` e `abc` para referir-se ao mesmo elemento declarado.  
  
 No entanto, o common language runtime (CLR) usa *diferencia maiusculas de minúsculas* associação. Portanto, quando você gerar um assembly ou uma DLL e disponibilizá-lo para outros assemblies, seus nomes não diferenciam maiusculas de minúsculas. Por exemplo, se você definir uma classe com um elemento chamado `ABC`, e outros assemblies fazer uso de sua classe por meio do common language runtime, eles devem se referir ao elemento como `ABC`. Se você posteriormente recompilar sua classe e alterar o nome do elemento para `abc`, os outros assemblies usando sua classe não poderão mais acessar esse elemento. Portanto, quando você lançar uma versão atualizada de um assembly, você não deve alterar maiusculas e minúsculas em quaisquer elementos públicos.  
  
 Para obter mais informações, consulte [Common Language Runtime](http://msdn.microsoft.com/library/059a624e-f7db-4134-ba9f-08b676050482).  
  
### <a name="correct-approach"></a>Abordagem correta  
 Para permitir que outros componentes acessem as variáveis, trate seus nomes como se fossem diferencia maiusculas de minúsculas. Quando você estiver testando sua classe ou módulo, certifique-se de que outros conjuntos estão vinculados às variáveis esperadas. Depois de publicar um componente, não faça modificações para nomes de variável existentes, incluindo seus casos de alteração.  
  
## <a name="wrong-variable-being-used"></a>Variável errada sendo usada  
 Quando você tiver mais de uma variável com o mesmo nome, o [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilador tenta resolver cada referência a esse nome. Se as variáveis têm escopo diferente, o compilador resolve uma referência para a declaração com o escopo mais restrito. Se eles tiverem o mesmo escopo, a resolução falhará e o compilador sinaliza um erro. Para obter mais informações, consulte [referências a elementos declarados](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
### <a name="correct-approach"></a>Abordagem correta  
 Evite usar variáveis com o mesmo nome mas escopo diferente. Se você estiver usando outros assemblies ou projetos, evite usar qualquer nomes definidos nesses componentes externos tanto quanto possível. Se você tiver mais de uma variável com o mesmo nome, não deixe de que qualificar cada referência a ela. Para obter mais informações, consulte [referências a elementos declarados](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
## <a name="see-also"></a>Consulte também  
 [Variáveis](../../../../visual-basic/programming-guide/language-features/variables/index.md)   
 [Declaração de variável](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)   
 [Variáveis de objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)   
 [Declaração de variável de objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)   
 [Como: acessar membros de um objeto](../../../../visual-basic/programming-guide/language-features/variables/how-to-access-members-of-an-object.md)   
 [Valores de variáveis de objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)   
 [Como: determinar que tipo uma variável de objeto se refere](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-what-type-an-object-variable-refers-to.md)   
 [Referências a elementos declarados](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)   
 [Nomes de Elementos Declarados](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
