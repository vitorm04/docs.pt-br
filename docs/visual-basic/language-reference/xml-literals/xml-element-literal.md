---
title: "Literal do elemento XML (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.XmlLiteralElement"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "elemento literal XML [Visual Basic]"
  - "elemento literal [Visual Basic]"
  - "Elemento, de literais XML [Visual Basic]"
ms.assetid: 95039642-7893-48b7-b23f-45a6c55d8f67
caps.latest.revision: 32
caps.handback.revision: 32
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Literal do elemento XML (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Um literal que representa um <xref:System.Xml.Linq.XElement> objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<name [ attributeList ] />  
-or-  
<name [ attributeList ] > [ elementContents ] </[ name ]>  
```  
  
## <a name="parts"></a>Partes  
  
-   `<`  
  
     Obrigatório. Abre a marca do elemento inicial.  
  
-   `name`  
  
     Obrigatório. Nome do elemento. O formato é um dos seguintes:  
  
    -   Texto literal para o nome do elemento do formulário [`ePrefix``:`]`eName`, onde:  
  
        |||  
        |-|-|  
        |Parte|Descrição|  
        |`ePrefix`|Opcional. Prefixo de namespace XML para o elemento. Deve ser um namespace XML global que é definido com um `Imports` instrução no arquivo ou no nível do projeto, ou um namespace XML local que está definido nesse elemento ou um elemento pai.|  
        |`eName`|Obrigatório. Nome do elemento. O formato é um dos seguintes:<br /><br /> -Texto literal. Consulte [nomes de elementos e atributos XML declarados](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).<br />-Expressão incorporada do formulário `<%=` e`NameExp` `%>`. O tipo de `eNameExp` deve ser `String` ou um tipo que é implicitamente conversível para <xref:System.Xml.Linq.XName>.|  
  
    -   Expressão incorporada do formulário `<%=` `nameExp` `%>`. O tipo de `nameExp` deve ser `String` ou um tipo implicitamente conversível para <xref:System.Xml.Linq.XName>. Uma expressão inserida não é permitida em uma marca de fechamento de um elemento.  
  
-   `attributeList`  
  
     Opcional. Lista de atributos declarados no literal.  
  
     `attribute [ attribute ... ]`  
  
     Cada `attribute` tem uma das seguintes sintaxes:  
  
    -   Atribuição de atributos, do formulário [`aPrefix``:`]`aName``=``aValue`, onde:  
  
        |||  
        |-|-|  
        |Parte|Descrição|  
        |`aPrefix`|Opcional. Prefixo de namespace XML para o atributo. Deve ser um namespace XML global que é definido com um `Imports` instrução ou um namespace XML local que está definido nesse elemento ou um elemento pai.|  
        |`aName`|Obrigatório. Nome do atributo. O formato é um dos seguintes:<br /><br /> -Texto literal. Consulte [nomes de elementos e atributos XML declarados](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).<br />-Expressão incorporada do formulário `<%=` `aNameExp` `%>`. O tipo de `aNameExp` deve ser `String` ou um tipo que é implicitamente conversível para <xref:System.Xml.Linq.XName>.|  
        |`aValue`|Opcional. Valor do atributo. O formato é um dos seguintes:<br /><br /> -Texto literal, entre aspas.<br />-Expressão incorporada do formulário `<%=` `aValueExp` `%>`. Qualquer tipo é permitido.|  
  
    -   Expressão incorporada do formulário `<%=` `aExp` `%>`.  
  
-   `/>`  
  
     Opcional. Indica que o elemento é um elemento vazio, sem conteúdo.  
  
-   `>`  
  
     Obrigatório. Finaliza a marca do elemento iniciante ou vazio.  
  
-   `elementContents`  
  
     Opcional. Conteúdo do elemento.  
  
     `content [ content ... ]`  
  
     Cada `content` pode ser uma das seguintes opções:  
  
    -   Texto literal. Todo o espaço em branco em `elementContents` torna-se significativos se houver qualquer texto literal.  
  
    -   Expressão incorporada do formulário `<%=` `contentExp` `%>`.  
  
    -   Elemento XML literal.  
  
    -   Literal de comentário XML. Consulte [Literal de comentário XML](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).  
  
    -   Instrução de processamento XML literal. Consulte [Literal de instrução de processamento XML](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).  
  
    -   Literal XML CDATA. Consulte [Literal CDATA XML](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md).  
  
-   `</`[`name`]`>`  
  
     Opcional. Representa a marca de fechamento do elemento. Opcional `name` parâmetro não é permitido quando ele é o resultado de uma expressão inserida.  
  
## <a name="return-value"></a>Valor de retorno  
 Um <xref:System.Xml.Linq.XElement> objeto.  
  
## <a name="remarks"></a>Comentários  
 Você pode usar a sintaxe de literal de elemento XML para criar <xref:System.Xml.Linq.XElement> objetos no seu código.  
  
> [!NOTE]
>  Um literal XML pode abranger várias linhas sem usar caracteres de continuação de linha. Esse recurso permite que você copiar o conteúdo de um documento XML e colá-lo diretamente em um [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] programa.  
  
 Expressões inseridas do formulário `<%=` `exp` `%>` permitem que você adicione informações dinâmicas a um literal de elemento XML. Para obter mais informações, consulte [expressões inseridas no XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).  
  
 O [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilador converte o literal de elemento XML em chamadas para o <xref:System.Xml.Linq.XElement.%23ctor%2A> construtor e, se necessário, o <xref:System.Xml.Linq.XAttribute.%23ctor%2A> construtor.  
  
## <a name="xml-namespaces"></a>Namespaces XML  
 Prefixos de namespace XML são úteis quando você tem que criar literais XML com elementos do mesmo namespace muitas vezes no código. Você pode usar prefixos de namespace XML global, que você define usando o `Imports` instrução ou prefixos locais, que você define usando o `xmlns:``xmlPrefix`= "`xmlNamespace`" sintaxe de atributo. Para obter mais informações, consulte [instrução Imports (Namespace XML)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).  
  
 De acordo com as regras de escopo para namespaces XML, prefixos locais têm precedência sobre prefixos globais. No entanto, se um literal XML define um namespace XML, esse namespace não está disponível para expressões que aparecem em uma expressão inserida. A expressão inserida pode acessar somente o namespace XML global.  
  
 O [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilador converte cada namespace XML global que é usado por um XML literal em uma definição de namespace local no código gerado. Namespaces XML globais que não são usados não aparecem no código gerado.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como criar um elemento XML simples que tem dois elementos aninhados vazios.  
  
 [!CODE [VbXMLSamples#20](../CodeSnippet/VS_Snippets_VBCSharp/VbXMLSamples#20)]  
  
 O exemplo exibe o texto a seguir. Observe que o literal preserva a estrutura dos elementos vazios.  
  
```  
<outer>  
  <inner1></inner1>  
  <inner2 />  
</outer>  
```  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar expressões inseridas para nomear um elemento e criar atributos.  
  
 [!CODE [VbXMLSamples#21](../CodeSnippet/VS_Snippets_VBCSharp/VbXMLSamples#21)]  
  
 Esse código exibe o seguinte texto:  
  
```  
<book isbn="1234" author="My Author" year="1999" title="My Book" />  
```  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir declara `ns` como um prefixo de namespace XML. Em seguida, ele usa o prefixo de namespace para criar um literal XML e exibe o formulário final do elemento.  
  
 [!CODE [VbXMLSamples#22](../CodeSnippet/VS_Snippets_VBCSharp/VbXMLSamples#22)]  
  
 Esse código exibe o seguinte texto:  
  
```  
<ns:outer xmlns:ns="http://SomeNamespace">  
  <ns:middle xmlns:ns="http://NewNamespace">  
    <ns:inner1 />  
    <inner2 xmlns="http://SomeNamespace" />  
  </ns:middle>  
</ns:outer>  
```  
  
 Observe que o compilador converteu o prefixo de namespace XML global em uma definição de prefixo para o namespace XML. O elemento \< ns:middle > redefine o prefixo de namespace XML para o elemento \< ns:inner1 >. No entanto, o elemento \< ns:inner2 > usa o namespace definido pelo `Imports` instrução.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Xml.Linq.XElement>   
 [Nomes de elementos e atributos XML declarados](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)   
 [Literal de comentário XML](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md)   
 [Literal CDATA XML](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md)   
 [Literais XML](../../../visual-basic/language-reference/xml-literals/index.md)   
 [Criando XML no Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)   
 [Expressões inseridas no XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)   
 [Instrução Imports (Namespace XML)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)