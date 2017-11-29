---
title: Literal do elemento XML (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.XmlLiteralElement
helpviewer_keywords:
- XML element literal [Visual Basic]
- element literal [Visual Basic]
- XML literals [Visual Basic], element
ms.assetid: 95039642-7893-48b7-b23f-45a6c55d8f67
caps.latest.revision: "32"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: de5825a6af1dd1b93c3c85651125cf817dc564f2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="xml-element-literal-visual-basic"></a>Literal do elemento XML (Visual Basic)

Um literal que representa um <xref:System.Xml.Linq.XElement> objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<name [ attributeList ] />  
-or-  
<name [ attributeList ] > [ elementContents ] </[ name ]>  
```  
  
## <a name="parts"></a>Partes  
  
-   `<`  
  
     Necessário. Abre a marca do elemento inicial.  
  
-   `name`  
  
     Necessário. Nome do elemento. O formato é um dos seguintes:  
  
    -   Texto literal para o nome do elemento do formulário `[ePrefix:]eName`, onde:  
  
        |Parte|Descrição|  
        |---|---|  
        |`ePrefix`|Opcional. Prefixo de namespace XML para o elemento. Deve ser um namespace XML global que é definido com um `Imports` instrução no arquivo ou no nível de projeto, ou um namespace XML local que está definido nesse elemento ou um elemento pai.|  
        |`eName`|Necessário. Nome do elemento. O formato é um dos seguintes:<br /><br /> -Texto literal. Consulte [nomes de elementos e atributos XML declarados](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).<br />-Expressão inserida do formulário `<%= eNameExp %>`. O tipo de `eNameExp` devem ser `String` ou um tipo que é implicitamente conversível em <xref:System.Xml.Linq.XName>.|  
  
    -   Expressão inserida do formulário `<%= nameExp %>`. O tipo de `nameExp` devem ser `String` ou um tipo implicitamente conversível para <xref:System.Xml.Linq.XName>. Uma expressão inserida não é permitida em uma marca de fechamento de um elemento.  
  
-   `attributeList`  
  
     Opcional. Lista de atributos declarados no literal.  
  
     `attribute [ attribute ... ]`  
  
     Cada `attribute` tem uma das seguintes sintaxes:  
  
    -   Atribuição de atributos, do formulário `[aPrefix:]aName=aValue`, onde:  
  
        |Parte|Descrição|  
        |---|---|  
        |`aPrefix`|Opcional. Prefixo de namespace XML para o atributo. Deve ser um namespace XML global que é definido com um `Imports` instrução ou um namespace XML local que está definido nesse elemento ou um elemento pai.|  
        |`aName`|Necessário. Nome do atributo. O formato é um dos seguintes:<br /><br /> -Texto literal. Consulte [nomes de elementos e atributos XML declarados](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).<br />-Expressão inserida do formulário `<%= aNameExp %>`. O tipo de `aNameExp` devem ser `String` ou um tipo que é implicitamente conversível em <xref:System.Xml.Linq.XName>.|  
        |`aValue`|Opcional. Valor do atributo. O formato é um dos seguintes:<br /><br /> -Texto literal, entre aspas.<br />-Expressão inserida do formulário `<%= aValueExp %>`. Qualquer tipo é permitido.|  
  
    -   Expressão inserida do formulário `<%= aExp %>`.  
  
-   `/>`  
  
     Opcional. Indica que o elemento é um elemento vazio, sem conteúdo.  
  
-   `>`  
  
     Necessário. Termina a marca do elemento iniciante ou vazio.  
  
-   `elementContents`  
  
     Opcional. Conteúdo do elemento.  
  
     `content [ content ... ]`  
  
     Cada `content` pode ser um dos seguintes:  
  
    -   Texto literal. Todo o espaço em branco em `elementContents` se tornar significativo se houver qualquer texto literal.  
  
    -   Expressão inserida do formulário `<%= contentExp %>`.  
  
    -   Elemento XML literal.  
  
    -   Literal de comentário XML. Consulte [Literal de comentário XML](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).  
  
    -   Instrução de processamento XML literal. Consulte [Literal de instrução de processamento XML](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).  
  
    -   Literal XML CDATA. Consulte [Literal CDATA XML](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md).  
  
-   `</[name]>`  
  
     Opcional. Representa a marca de fechamento para o elemento. Opcional `name` parâmetro não é permitido quando ele é o resultado de uma expressão inserida.  
  
## <a name="return-value"></a>Valor de retorno  
 Um objeto <xref:System.Xml.Linq.XElement>.  
  
## <a name="remarks"></a>Comentários  
 Você pode usar a sintaxe de literais de elemento XML para criar <xref:System.Xml.Linq.XElement> objetos no seu código.  
  
> [!NOTE]
>  Um literal XML pode abranger várias linhas sem usar caracteres de continuação de linha. Esse recurso permite que você copiar o conteúdo de um documento XML e cole-o diretamente em um [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] programa.  
  
 Expressões inseridas do formulário `<%= exp %>` permitem que você adicione informações dinâmicas a um literal de elemento XML. Para obter mais informações, consulte [expressões inseridas no XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).  
  
 O [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compilador converte o literal de elemento XML em chamadas para o <xref:System.Xml.Linq.XElement.%23ctor%2A> construtor e, se necessário, o <xref:System.Xml.Linq.XAttribute.%23ctor%2A> construtor.  
  
## <a name="xml-namespaces"></a>Namespaces XML  
 Prefixos de namespace XML são úteis quando você tem que criar literais XML com elementos do mesmo namespace muitas vezes no código. Você pode usar prefixos de namespace XML global, que você define usando a `Imports` instrução ou prefixos locais, que você define usando a `xmlns:xmlPrefix="xmlNamespace"` sintaxe de atributo. Para obter mais informações, consulte [instrução Imports (Namespace XML)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).  
  
 Conformidade com as regras de escopo para namespaces XML, prefixos locais têm precedência sobre prefixos globais. No entanto, se um literal XML define um namespace XML, esse namespace não está disponível para expressões que aparecem em uma expressão inserida. A expressão inserida pode acessar somente o namespace XML global.  
  
 O [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compilador converte cada namespace XML global que é usado por um XML literal em uma definição de namespace local no código gerado. Namespaces XML globais que não são usados não aparecem no código gerado.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como criar um elemento XML simples que tem dois elementos aninhados vazios.  
  
 [!code-vb[VbXMLSamples#20](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-element-literal_1.vb)]  
  
 O exemplo exibe o texto a seguir. Observe que o literal preserva a estrutura dos elementos vazios.  
  
```xml  
<outer>  
  <inner1></inner1>  
  <inner2 />  
</outer>  
```  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar expressões inseridas para nomear um elemento e criar atributos.  
  
 [!code-vb[VbXMLSamples#21](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-element-literal_2.vb)]  
  
 Este código exibe o seguinte texto:  
  
```xml  
<book isbn="1234" author="My Author" year="1999" title="My Book" />  
```  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir declara `ns` como um prefixo de namespace XML. Em seguida, ele usa o prefixo de namespace para criar um literal XML e exibe a forma final do elemento.  
  
 [!code-vb[VbXMLSamples#22](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-element-literal_3.vb)]  
  
 Este código exibe o seguinte texto:  
  
```xml  
<ns:outer xmlns:ns="http://SomeNamespace">  
  <ns:middle xmlns:ns="http://NewNamespace">  
    <ns:inner1 />  
    <inner2 xmlns="http://SomeNamespace" />  
  </ns:middle>  
</ns:outer>  
```  
  
 Observe que o compilador converteu o prefixo do namespace XML global em uma definição de prefixo para o namespace XML. O \<ns:middle > elemento redefine o prefixo de namespace XML para o \<ns:inner1 > elemento. No entanto, o \<ns:inner2 > elemento usa o namespace definido pelo `Imports` instrução.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Xml.Linq.XElement>  
 [Nomes de Elementos e Atributos XML Declarados](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)  
 [Literal de Comentário XML](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md)  
 [Literal CDATA XML](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md)  
 [Literais XML](../../../visual-basic/language-reference/xml-literals/index.md)  
 [Criando XML no Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [Expressões Inseridas no XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)  
 [Instrução Imports (Namespace de XML)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)
