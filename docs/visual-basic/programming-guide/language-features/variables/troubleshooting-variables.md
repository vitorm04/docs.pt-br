---
title: "Solucionando problemas de vari&#225;veis no Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "variáveis, de solução de problemas [Visual Basic]"
  - "variáveis [Visual Basic], solução de problemas"
ms.assetid: 928a2dc8-e565-4ae4-8ba3-80cc0cb50090
caps.latest.revision: 20
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Solucionando problemas de vari&#225;veis no Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Esta página lista alguns problemas comuns que podem ocorrer ao trabalhar com variáveis em [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
## Não é possível acessar membros de um objeto  
 Se seu código tenta acessar uma propriedade ou método em um objeto, há dois resultados possíveis de erro:  
  
-   O compilador pode gerar uma mensagem de erro se você declarar a variável de objeto para ser de um tipo específico e, em seguida, se referir a um membro não definido por aquele tipo.  
  
-   Um tempo de execução <xref:System.MemberAccessException> ocorre quando o objeto atribuído a uma variável de objeto não expõe o membro que seu código está tentando acessar. No caso de uma variável de [Tipo de dados Object](../../../../visual-basic/language-reference/data-types/object-data-type.md), você também pode obter essa exceção se o membro não é `Public`. Isso ocorre porque a associação tardia permite acesso somente a `Public` membros.  
  
 Quando o [Instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) conjuntos de verificação de tipo `On`, uma variável de objeto pode acessar somente os métodos e propriedades da classe com a qual foi declarada. O exemplo a seguir ilustra isso.  
  
 [!CODE [VbVbalrStatements#49](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrStatements#49)]  
  
 [!code-vb[VbVbalrVariables#2](../../../../visual-basic/programming-guide/language-features/variables/codesnippet/VisualBasic/troubleshooting-variables_2.vb)]  
  
 Neste exemplo, `p` pode usar somente os membros do <xref:System.Object> classe em si, que não inclui o `Left` propriedade. Por outro lado, `q` foi declarado para ser do tipo <xref:System.Windows.Forms.Label>, portanto, ele pode usar todos os métodos e propriedades da <xref:System.Windows.Forms.Label> classe o <xref:System.Windows.Forms> namespace.  
  
### Abordagem correta  
 Para ser capaz de acessar todos os membros de um objeto de uma determinada classe, declare a variável de objeto para ser do tipo de classe quando possível. Se você não puder fazer isso, por exemplo, se você não souber o objeto de tipo em tempo de compilação, você deve definir `Option Strict` para `Off` e declarar a variável para ser o [Tipo de dados Object](../../../../visual-basic/language-reference/data-types/object-data-type.md). Isso permite que os objetos de qualquer tipo a ser atribuído à variável, e você deve tomar medidas para garantir que o objeto atualmente atribuído seja de um tipo aceitável. Você pode usar o [Operador TypeOf](../../../../visual-basic/language-reference/operators/typeof-operator.md) para tomar essa decisão.  
  
## Outros componentes não podem acessar sua variável  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] os nomes são *diferenciam maiúsculas de minúsculas*. Se dois nomes diferem somente no caso alfabético, o compilador interpreta como o mesmo nome. Por exemplo, ele considera `ABC` e `abc` para referir\-se ao mesmo elemento declarado.  
  
 No entanto, o common language runtime \(CLR\) usa *diferencia maiúsculas de minúsculas* associação. Portanto, quando você gerar um assembly ou uma DLL e disponibilizá\-lo para outros assemblies, seus nomes não diferenciam maiúsculas de minúsculas. Por exemplo, se você definir uma classe com um elemento chamado `ABC`, e outros assemblies fazer uso de sua classe por meio do common language runtime, eles devem se referir ao elemento como `ABC`. Se você posteriormente recompilar sua classe e alterar o nome do elemento para `abc`, os outros assemblies usando sua classe não poderão mais acessar esse elemento. Portanto, quando você lançar uma versão atualizada de um assembly, você não deve alterar maiúsculas e minúsculas em quaisquer elementos públicos.  
  
 Para obter mais informações, consulte [Common Language Runtime](../Topic/Common%20Language%20Runtime%20\(CLR\).md).  
  
### Abordagem correta  
 Para permitir que outros componentes acessem as variáveis, trate seus nomes como se fossem diferencia maiúsculas de minúsculas. Quando você estiver testando sua classe ou módulo, certifique\-se de que outros conjuntos estão vinculados às variáveis esperadas. Depois de publicar um componente, não faça modificações para nomes de variável existentes, incluindo seus casos de alteração.  
  
## Variável errada sendo usada  
 Quando você tiver mais de uma variável com o mesmo nome, o [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilador tenta resolver cada referência a esse nome. Se as variáveis têm escopo diferente, o compilador resolve uma referência para a declaração com o escopo mais restrito. Se eles tiverem o mesmo escopo, a resolução falhará e o compilador sinaliza um erro. Para obter mais informações, consulte [Referências a elementos declarados](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
### Abordagem correta  
 Evite usar variáveis com o mesmo nome mas escopo diferente. Se você estiver usando outros assemblies ou projetos, evite usar qualquer nomes definidos nesses componentes externos tanto quanto possível. Se você tiver mais de uma variável com o mesmo nome, não deixe de que qualificar cada referência a ela. Para obter mais informações, consulte [Referências a elementos declarados](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
## Consulte também  
 [Variáveis](../../../../visual-basic/reference/command-line-compiler/index.md)   
 [Declaração de variável](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)   
 [Variáveis de objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)   
 [Declaração de variável do objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)   
 [Como acessar membros de um objeto](../../../../visual-basic/programming-guide/language-features/variables/how-to-access-members-of-an-object.md)   
 [Valores de variável de objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)   
 [Como determinar a que tipo uma variável de objeto se refere](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-what-type-an-object-variable-refers-to.md)   
 [Referências a elementos declarados](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)   
 [Nomes de elemento declarados](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)