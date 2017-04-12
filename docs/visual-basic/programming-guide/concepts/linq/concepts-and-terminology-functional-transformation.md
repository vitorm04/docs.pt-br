---
title: "Conceitos e terminologia (transformação funcional) (Visual Basic) | Documentos do Microsoft"
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
ms.assetid: 24fd244d-ebae-4721-8858-89bb544aea0b
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 9c4716765199798e50c4318b290f8a2d76ef5841
ms.lasthandoff: 03/13/2017


---
# <a name="concepts-and-terminology-functional-transformation-visual-basic"></a>Conceitos e terminologia (transformação funcional) (Visual Basic)
Este tópico apresenta os conceitos e a terminologia de transformações e puras. A abordagem funcional de transformação a transformação passa de dados codificação que geralmente é mais rápido, mais programar completo expressive, e mais fácil depurar e manter que a programação mais tradicional, mais imperativa.  
  
 Observe que os tópicos nesta seção não são destinados explicar totalmente funcional programação. Em vez disso, esses tópicos identificam alguns dos recursos funcionais de programação que facilitam transformar XML de uma forma para outra.  
  
## <a name="what-is-pure-functional-transformation"></a>Transformação que é funcional pura?  
 Em *transformação funcional pura*, um conjunto de funções, chamadas *funções puras*, defina como transformar um conjunto de dados estruturados em sua forma original em outro formulário. A palavra "pura" indica que as funções são *Combinável*, que exige que eles são:  
  
-   *Independente*, de modo que eles podem ser livremente solicitados e reorganizados sem complicação ou interdependências com o restante do programa. As transformações puras não têm nenhum conhecimento de efetuam-no ou em cima do seu ambiente. Ou seja, as funções usadas na transformação têm não *efeitos colaterais*.  
  
-   *Sem monitoração de estado*, de modo que a mesma função ou um conjunto específico de funções em execução na mesma entrada sempre resultará na mesma saída. As transformações puras não têm memória do seu uso prévio.  
  
> [!IMPORTANT]
>  No restante deste tutorial, o termo “function” pura é usado em um sentido geral indicar uma abordagem de programação, e não em um recurso de linguagem específica.  
>   
>  Observe que as funções puras devem ser implementadas como funções no Visual Basic.  
>   
>  Além disso, você não deve confundir funções puras com os métodos puros virtuais em C++. O último indica que a classe recipiente é abstrato e que nenhum corpo do método é fornecido.  
  
### <a name="functional-programming"></a>Programação funcional  
 *Programação funcional* é uma abordagem de programação que oferece suporte diretamente a transformação funcional pura.  
  
 Historicamente, linguagens de programação funcionais para fins gerais, como AM, esquema, Haskell e F #, principalmente foram de interesse para a comunidade acadêmica. Embora sempre foi possível escrever transformações e puras no Visual Basic, a dificuldade de fazer então não tornou uma opção atraente para a maioria dos programadores. Com versões posteriores do Visual Basic, no entanto, novas construções de linguagem como expressões lambda e Inferência de tipo tornam programação funcional muito mais fácil e mais produtivo.  
  
 Para obter mais informações sobre programação funcional, consulte [vs programação funcional. Programação imperativa (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-programming-vs-imperative-programming.md).  
  
#### <a name="domain-specific-fp-languages"></a>Linguagens específicas do domínio FP  
 Embora as linguagens de programação e gerais não sejam amplamente adotadas, as linguagens de programação e específicas do domínio específicas tinham melhor êxito. Por exemplo, folhas de estilos em cascata (CSS) são usadas para determinar a aparência de muitas páginas da Web, e as folhas de estilos extensíveis de transformações de language (XSLT) são usadas amplamente na manipulação de dados XML. Para obter mais informações sobre XSLT, consulte [transformações XSLT](http://msdn.microsoft.com/library/202f8820-224c-494f-b61e-cd127eac6e03).  
  
## <a name="terminology"></a>Terminologia  
 A tabela a seguir define os termos relacionados às transformações funcionais.  
  
 função (de primeira classe) de pedido superior  
 Uma função que pode ser tratado como um objeto através de programação. Por exemplo, uma função de pedido superior pode ser passada para ou retornado de outras funções. No Visual Basic, representantes e expressões lambda são recursos de linguagem que oferecem suporte a funções de ordem superior. Para gravar uma função de pedido superior, você declara um ou mais argumentos para tomar representantes, e você frequentemente usa expressões lambda para chamá-lo. Muitos dos operadores de consulta padrão são funções de pedido superior.  
  
 Para obter mais informações, consulte [Standard Query Operators Overview (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).  
  
 expressão lambda  
 Essencialmente, uma função anônimo embutido que pode ser usada em que um tipo delegate é esperada. Esta é uma definição simplificada de expressões lambda, mas é suficiente para fins deste tutorial.  
  
 Para obter mais informações sobre, consulte [expressões Lambda](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
 Coleção  
 Um conjunto estruturada de dados, geralmente um tipo de uniforme. Para ser compatível com o LINQ, uma coleção deve implementar a <xref:System.Collections.IEnumerable>interface ou <xref:System.Linq.IQueryable>interface (ou uma de suas contrapartes genéricos, <xref:System.Collections.Generic.IEnumerator%601>ou <xref:System.Linq.IQueryable%601>).</xref:System.Linq.IQueryable%601> </xref:System.Collections.Generic.IEnumerator%601> </xref:System.Linq.IQueryable> </xref:System.Collections.IEnumerable>  
  
 tuple (tipos anônimos)  
 Um conceito matemático, um tuple é uma sequência finito rotuladas de objetos, cada um de um tipo específico. Um tuple também é conhecido como uma lista ordenada. Tipos anônimos são uma implementação de linguagem desse conceito, que permitem que um tipo sem nome da classe ser declarados e um objeto do tipo a ser instanciada ao mesmo tempo.  
  
 Para obter mais informações, consulte [tipos anônimos](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
 inferência de tipos (digite implícito)  
 A capacidade de um compilador de determinar o tipo de uma variável na ausência de uma declaração de tipo explícita.  
  
 Para obter mais informações, consulte [inferência de tipo Local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).  
  
 execução adiada e avaliação lazy  
 O atraso de avaliação de uma expressão até que o valor resolvido é realmente necessário. A execução adiada é suportado em coleções.  
  
 Para obter mais informações, consulte [operações básicas de consulta (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md) e [execução adiada e avaliação lenta em LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).  
  
 Esses recursos de idioma serão usados em exemplos de código em todo esta seção.  
  
## <a name="see-also"></a>Consulte também  
 [Introdução às transformações e puras (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)   
 [Programação funcional versus Programação imperativa (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-programming-vs-imperative-programming.md)
