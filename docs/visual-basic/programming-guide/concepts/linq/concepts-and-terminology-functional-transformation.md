---
title: Conceitos e terminologia (transformação funcional) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 24fd244d-ebae-4721-8858-89bb544aea0b
ms.openlocfilehash: e98e24bb60dd2a5b6e84195120429fac0b8832e9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54651858"
---
# <a name="concepts-and-terminology-functional-transformation-visual-basic"></a>Conceitos e terminologia (transformação funcional) (Visual Basic)
Este tópico apresenta os conceitos e a terminologia de transformações e puras. A abordagem funcional de transformação a transformação passa de dados codificação que geralmente é mais rápido, mais programar completo expressive, e mais fácil depurar e manter que a programação mais tradicional, mais imperativa.  
  
 Observe que os tópicos nesta seção não são destinados explicar totalmente funcional programação. Em vez disso, esses tópicos identificam alguns dos recursos funcionais de programação que facilitam transformar XML de uma forma para outra.  
  
## <a name="what-is-pure-functional-transformation"></a>Transformação que é funcional pura?  
 Na *transformação funcional pura*, um conjunto de funções, chamadas *funções puras*, define como transformar um conjunto de dados estruturados de sua forma original em outra forma. A palavra "pura" indica que as funções são *combináveis*, que exigem que elas sejam:  
  
-   *Autocontidas*, de modo que elas possam ser ordenadas e reorganizadas livremente sem complicação ou interdependências com o restante do programa. As transformações puras não têm nenhum conhecimento de efetuam-no ou em cima do seu ambiente. Isto é, as funções usadas na transformação não têm *efeito colateral*.  
  
-   *Sem monitoração de estado*, de modo que a execução da mesma função ou conjunto específico de funções, na mesma entrada, sempre resultará na mesma saída. As transformações puras não têm memória do seu uso prévio.  
  
> [!IMPORTANT]
>  No restante deste tutorial, o termo “function” pura é usado em um sentido geral indicar uma abordagem de programação, e não em um recurso de linguagem específica.  
>   
>  Observe que as funções puras devem ser implementadas como funções no Visual Basic.  
>   
>  Além disso, você não deve confundir funções puras com os métodos puros virtuais em C++. O último indica que a classe recipiente é abstrato e que nenhum corpo do método é fornecido.  
  
### <a name="functional-programming"></a>Programação funcional  
 A *programação funcional* é uma abordagem de programação que dá suporte diretamente à transformação funcional pura.  
  
 Historicamente, as linguagens de programação funcionais de uso geral, como o ML, Scheme, Haskell e F#, têm sido, principalmente, de interesse da comunidade acadêmica. Embora sempre foi possível escrever transformações funcionais puras no Visual Basic, a dificuldade de fazer então não tornou essa opção atrativa à maioria dos programadores. Com versões posteriores do Visual Basic, no entanto, nova construções de linguagem como expressões lambda e Inferência de tipos tornaram a programação funcional muito mais fácil e mais produtivo.  
  
 Para obter mais informações sobre programação funcional, consulte [Programação funcional versus Programação imperativa (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-programming-vs-imperative-programming.md).  
  
#### <a name="domain-specific-fp-languages"></a>Linguagens específicas do domínio FP  
 Embora as linguagens de programação e gerais não sejam amplamente adotadas, as linguagens de programação e específicas do domínio específicas tinham melhor êxito. Por exemplo, folhas de estilos em cascata (CSS) são usadas para determinar a aparência de muitas páginas da Web, e as folhas de estilos extensíveis de transformações de language (XSLT) são usadas amplamente na manipulação de dados XML. Para obter mais informações sobre XSLT, consulte [Transformações XSLT](../../../../standard/data/xml/xslt-transformations.md).  
  
## <a name="terminology"></a>Terminologia  
 A tabela a seguir define os termos relacionados às transformações funcionais.  
  
 função (de primeira classe) de pedido superior  
 Uma função que pode ser tratado como um objeto através de programação. Por exemplo, uma função de pedido superior pode ser passada para ou retornado de outras funções. No Visual Basic, representantes e expressões lambda são recursos de linguagem que dão suporte a funções de ordem superior. Para gravar uma função de pedido superior, você declara um ou mais argumentos para tomar representantes, e você frequentemente usa expressões lambda para chamá-lo. Muitos dos operadores de consulta padrão são funções de pedido superior.  
  
 Para obter mais informações, consulte [visão geral de operadores padrão consulta (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).  
  
 expressão lambda  
 Essencialmente, uma função anônimo embutido que pode ser usada em que um tipo delegate é esperada. Esta é uma definição simplificada de expressões lambda, mas é suficiente para fins deste tutorial.  
  
 Para obter mais informações, consulte [Expressões lambda](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
 Coleção  
 Um conjunto estruturada de dados, geralmente um tipo de uniforme. Para ser compatível com LINQ, uma coleção deve implementar a interface de <xref:System.Collections.IEnumerable> ou a interface de <xref:System.Linq.IQueryable> (ou uma de suas contrapartes genéricos, de <xref:System.Collections.Generic.IEnumerator%601> ou de <xref:System.Linq.IQueryable%601>).  
  
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
- [Introdução às transformações funcionais puras (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)
- [Programação funcional versus Programação imperativa (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-programming-vs-imperative-programming.md)
