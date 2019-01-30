---
title: Fragmento da árvore de resultado nas transformações
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: df363480-ba02-4233-9ddf-8434e421c4f1
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4835536dd3ae815fbe7e50582b94caefb1fc9082
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54683814"
---
# <a name="result-tree-fragment-in-transformations"></a><span data-ttu-id="dafcb-102">Fragmento da árvore de resultado nas transformações</span><span class="sxs-lookup"><span data-stu-id="dafcb-102">Result Tree Fragment in Transformations</span></span>

> [!NOTE]
> <span data-ttu-id="dafcb-103">A classe <xref:System.Xml.Xsl.XslTransform> está obsoleta no [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="dafcb-103">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span> <span data-ttu-id="dafcb-104">Você pode executar a linguagem XSL Transformations (XSLT) usando a classe <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="dafcb-104">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="dafcb-105">Confira [Usar a classe XslCompiledTransform](using-the-xslcompiledtransform-class.md) e [Migrar da classe XslTransform](migrating-from-the-xsltransform-class.md) para saber mais.</span><span class="sxs-lookup"><span data-stu-id="dafcb-105">See [Using the XslCompiledTransform Class](using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](migrating-from-the-xsltransform-class.md) for more information.</span></span>

 <span data-ttu-id="dafcb-106">Os fragmentos da árvore de resultado, também conhecido como partes da árvore de resultado, não há nada mais que um tipo especial de conjunto do nó.</span><span class="sxs-lookup"><span data-stu-id="dafcb-106">Result tree fragments, also known as result tree fragments, are nothing more than a special type of node set.</span></span> <span data-ttu-id="dafcb-107">Você pode executar qualquer função em que eles podem ser executados em um conjunto de nó.</span><span class="sxs-lookup"><span data-stu-id="dafcb-107">You can perform any function on them that can be performed on a node set.</span></span> <span data-ttu-id="dafcb-108">Ou, você também pode converter um fragmento da árvore de resultado a um conjunto de nó usando a função de `node-set()` e depois usá-lo qualquer lugar que um conjunto de nó pode ser usado.</span><span class="sxs-lookup"><span data-stu-id="dafcb-108">Or, you can also convert a result tree fragment to a node set using the `node-set()` function and subsequently use it any place that a node set can be used.</span></span>

 <span data-ttu-id="dafcb-109">Um fragmento da árvore do resultado é criado como resultado de usar um elemento de `<xsl:variable>` ou de `<xsl:param>` de uma maneira específica em uma folha de estilos.</span><span class="sxs-lookup"><span data-stu-id="dafcb-109">A result tree fragment is created as a result of using an `<xsl:variable>` or `<xsl:param>` element in a specific manner in a style sheet.</span></span> <span data-ttu-id="dafcb-110">A sintaxe para elementos de `variable` e de `parameter` é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="dafcb-110">The syntax for the `variable` and `parameter` elements is as follows:</span></span>

```xml
<xsl:param name=Qname select= XPath Expression >
    template body
</xsl:param>

<xsl:variable name=Qname select=XPath Expression >
    template body
</xsl:variable>
```

<span data-ttu-id="dafcb-111">Para o elemento de `parameter` , o valor é atribuído ao nome qualificado (`Qname`) em várias maneiras.</span><span class="sxs-lookup"><span data-stu-id="dafcb-111">For the `parameter` element, the value is assigned to the qualified name (`Qname`) in several ways.</span></span> <span data-ttu-id="dafcb-112">Você pode atribuir um valor padrão para o parâmetro retornando o conteúdo de uma expressão de idioma do caminho de XML (XPath) no atributo de `select` , ou atribuindo o conteúdo do corpo do modelo.</span><span class="sxs-lookup"><span data-stu-id="dafcb-112">You can assign a default value to the parameter by returning content from the XML Path Language (XPath) expression in the `select` attribute, or by assigning it the contents of the template body.</span></span>

<span data-ttu-id="dafcb-113">Para o elemento de `variable` , o valor é atribuído também em várias maneiras.</span><span class="sxs-lookup"><span data-stu-id="dafcb-113">For the `variable` element, the value is also assigned in several ways.</span></span> <span data-ttu-id="dafcb-114">Você pode atribuí-lo retornando o conteúdo de expressão XPath no atributo de `select` , ou atribuindo o conteúdo do corpo do modelo.</span><span class="sxs-lookup"><span data-stu-id="dafcb-114">You can assign it by returning content from the XPath expression in the `select` attribute, or by assigning it the contents of the template body.</span></span>

<span data-ttu-id="dafcb-115">Para os elementos `parameter` e `variable`, se um valor for atribuído pela expressão XPath, um dos quatro tipos XPath básicos será retornado: Booliano, cadeia de caracteres, número ou conjunto de nós.</span><span class="sxs-lookup"><span data-stu-id="dafcb-115">For both the `parameter` and `variable` elements, if a value is assigned by the XPath expression, then one of the four basic XPath types will be returned: Boolean, string, number, or node set.</span></span> <span data-ttu-id="dafcb-116">Quando o valor é fornecido usando um corpo não vazio de modelo, então um tipo de dados não XPath será retornado, e que será um fragmento da árvore de resultado.</span><span class="sxs-lookup"><span data-stu-id="dafcb-116">When the value is given by using a non-empty template body, then a non-XPath data type is returned, and that will be a result tree fragment.</span></span>

<span data-ttu-id="dafcb-117">Quando uma variável é associado a um fragmento da árvore de resultado em vez de um dos quatro tipos de dados básicos XPath, este é a única vez que uma consulta XPath retorna um tipo que não é um dos quatro tipos de objeto XPath.</span><span class="sxs-lookup"><span data-stu-id="dafcb-117">When a variable is bound to a result tree fragment instead of one of the four basic XPath data types, this is the only time that an XPath query returns a type that is not one of the four XPath object types.</span></span> <span data-ttu-id="dafcb-118">Os fragmentos da árvore de resultado e seu comportamento são discutidos na [especificação World Wide Web Consortium (W3C)](https://www.w3.org/TR/xslt-10/), da [seção 11.1 Fragmentos da Árvore do Resultado](https://www.w3.org/TR/xslt-10/#section-Result-Tree-Fragments) até [seção 11.6 Passando Parâmetros para os Modelos](https://www.w3.org/TR/xslt-10/#section-Passing-Parameters-to-Templates).</span><span class="sxs-lookup"><span data-stu-id="dafcb-118">Result tree fragments and their behavior are discussed in the [World Wide Web Consortium (W3C) specification](https://www.w3.org/TR/xslt-10/), [section 11.1 Result Tree Fragments](https://www.w3.org/TR/xslt-10/#section-Result-Tree-Fragments) through [section 11.6 Passing Parameters to Templates](https://www.w3.org/TR/xslt-10/#section-Passing-Parameters-to-Templates).</span></span> <span data-ttu-id="dafcb-119">Além disso, a [seção 1 Introdução](https://www.w3.org/TR/xslt-10/#section-Introduction) discute como os modelos podem conter elementos do namespace XSLT que retornam ou como podem criar fragmentos da árvore de resultado.</span><span class="sxs-lookup"><span data-stu-id="dafcb-119">Also, [section 1 Introduction](https://www.w3.org/TR/xslt-10/#section-Introduction) discusses how templates can contain elements from the XSLT namespace that return or create result tree fragments.</span></span>

<span data-ttu-id="dafcb-120">Um fragmento da árvore de resultado, o conceito, se comporta como um nó definido com nada mais de um único nó raiz.</span><span class="sxs-lookup"><span data-stu-id="dafcb-120">A result tree fragment, in concept, behaves like a node set with nothing more than a single root node.</span></span> <span data-ttu-id="dafcb-121">No entanto, o resto de nós retornados é nós filho.</span><span class="sxs-lookup"><span data-stu-id="dafcb-121">However, the rest of the nodes returned are child nodes.</span></span> <span data-ttu-id="dafcb-122">Para ver programaticamente nós filho, copie o fragmento da árvore de resultado à árvore de resultado usando o elemento de `<xsl:copy-of>` .</span><span class="sxs-lookup"><span data-stu-id="dafcb-122">To programmatically see the child nodes, copy the result tree fragment to the result tree using the `<xsl:copy-of>` element.</span></span> <span data-ttu-id="dafcb-123">Quando cópia- de for executado, todos os nós filhos são copiados também à árvore de resultado em ordem.</span><span class="sxs-lookup"><span data-stu-id="dafcb-123">When the copy-of is performed, all the child nodes are also copied to the result tree in sequence.</span></span> <span data-ttu-id="dafcb-124">Até `copy` ou `copy-of` é usado, um fragmento da árvore do resultado não é parte da árvore de resultado ou da saída de transformação.</span><span class="sxs-lookup"><span data-stu-id="dafcb-124">Until a `copy` or `copy-of` is used, a result tree fragment is not part of the result tree or the output from the transformation.</span></span>

<span data-ttu-id="dafcb-125">Para iterar sobre os nós retornados de um fragmento da árvore de resultado, <xref:System.Xml.XPath.XPathNavigator> é usado.</span><span class="sxs-lookup"><span data-stu-id="dafcb-125">To iterate over the returned nodes of a result tree fragment, an <xref:System.Xml.XPath.XPathNavigator> is used.</span></span> <span data-ttu-id="dafcb-126">O exemplo de código a seguir mostra como criar um fragmento da árvore de resultado em uma folha de estilos chamar a função com um parâmetro `fragment`, que contém XML.</span><span class="sxs-lookup"><span data-stu-id="dafcb-126">The following code sample shows how to create a result tree fragment within a style sheet by calling the function with a parameter `fragment`, which contains XML.</span></span>

```xml
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform"
                xmlns:msxsl="urn:schemas-microsoft-com:xslt"
                xmlns:user="http://www.adventure-works.com"
                version="1.0">
    <xsl:var name="fragment">
        <node1>
            <node2/>
        </node1>
    <xsl:var>

  <msxsl:script language="C#" implements-prefix="user">
    function NodeFragment(XPathNavigator nav)
    {
      if (nav.HasSelection == false)
        XPathNavigator.MoveToNext();
      return;
    }
  </msxsl:script>

    <xsl:template match="/">
            <xsl:value-of select="user:NodeFragment(msxml:node-set($fragment))"/>
    </xsl:template>
</xsl:stylesheet>
```

<span data-ttu-id="dafcb-127">Aqui está um exemplo que mostra uma variável, que está em formato rich text (RTF), portanto, um tipo de fragmento da árvore de resultado, que não é convertido em um conjunto de nó.</span><span class="sxs-lookup"><span data-stu-id="dafcb-127">Here is another sample showing a variable, which is in Rich Text Format (RTF), and hence, a type of result tree fragment, that is not converted to a node set.</span></span> <span data-ttu-id="dafcb-128">Em vez disso, é passado para uma função de script, e <xref:System.Xml.XPath.XPathNavigator> é usado para navegar sobre os nós.</span><span class="sxs-lookup"><span data-stu-id="dafcb-128">Instead, it is passed to a script function, and the <xref:System.Xml.XPath.XPathNavigator> is used to navigate over the nodes.</span></span>

```xml
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform"
        xmlns:msxsl="urn:schemas-microsoft-com:xslt"
        xmlns:user="urn:books"
        exclude-result-prefixes="msxsl">

<xsl:output method="xml" indent="yes" omit-xml-declaration="yes"/>

<xsl:variable name="node-fragment">
    <book>Book1</book>
    <book>Book2</book>
    <book>Book3</book>
    <book>Book4</book>
</xsl:variable>

<msxsl:script implements-prefix="user" language="c#">

<![CDATA[
    string func(XPathNavigator nav)
    {
        bool b = nav.MoveToFirstChild();
        if (b)
            return nav.Value;
        else
            return "Does not exist";
    }

]]>

</msxsl:script>

<xsl:template match="/">
    <first_book>
        <xsl:value-of select="user:func($node-fragment)"/>
    </first_book>
</xsl:template>

</xsl:stylesheet>
```

<span data-ttu-id="dafcb-129">O resultado de qualquer transformar XML com essa folha de estilos é mostrado na seguinte saída.</span><span class="sxs-lookup"><span data-stu-id="dafcb-129">The result of transforming any XML with this style sheet is shown in the following output.</span></span>

## <a name="output"></a><span data-ttu-id="dafcb-130">Saída</span><span class="sxs-lookup"><span data-stu-id="dafcb-130">Output</span></span>

```xml
<first_book xmlns:user="urn:books">Book1</first_book>
```

<span data-ttu-id="dafcb-131">Como dito acima, a função de `node-set` permite que você converter um fragmento da árvore de resultado em um conjunto de nó.</span><span class="sxs-lookup"><span data-stu-id="dafcb-131">As stated above, the `node-set` function enables you to convert a result tree fragment into a node set.</span></span> <span data-ttu-id="dafcb-132">O nó resultante sempre contém um único nó que é o nó raiz da árvore.</span><span class="sxs-lookup"><span data-stu-id="dafcb-132">The resulting node always contains a single node that is the root node of the tree.</span></span> <span data-ttu-id="dafcb-133">Se você converter um fragmento da árvore de resultado a um conjunto de nó, então você pode usá-lo em qualquer lugar que um conjunto normal do nó é usado, como em para- cada instrução ou o valor de um atributo de `select` .</span><span class="sxs-lookup"><span data-stu-id="dafcb-133">If you convert a result tree fragment to a node set, then you can use it anywhere a regular node set is used, such as in a for-each statement or in the value of a `select` attribute.</span></span> <span data-ttu-id="dafcb-134">As seguintes linhas de código mostram o fragmento que está sendo convertido em um nó definido e usaram-se como um nó definida:</span><span class="sxs-lookup"><span data-stu-id="dafcb-134">The following lines of code show the fragment being converted to a node set and used as a node set:</span></span>

`<xsl:for-each select="msxsl:node-set($node-fragment)">`

`<xsl:value-of select="user:func(msxsl:node-set($node-fragment))"/>`

<span data-ttu-id="dafcb-135">Quando um fragmento é convertido em um conjunto de nó, você não usa <xref:System.Xml.XPath.XPathNavigator> para navegar sobre ele.</span><span class="sxs-lookup"><span data-stu-id="dafcb-135">When a fragment is converted to a node set, you no longer use the <xref:System.Xml.XPath.XPathNavigator> to navigate over it.</span></span> <span data-ttu-id="dafcb-136">Para um conjunto de nó, você usa <xref:System.Xml.XPath.XPathNodeIterator> em vez disso.</span><span class="sxs-lookup"><span data-stu-id="dafcb-136">For a node set, you use the <xref:System.Xml.XPath.XPathNodeIterator> instead.</span></span>

<span data-ttu-id="dafcb-137">No exemplo a seguir, `$var` é uma variável que é uma árvore de nós na folha de estilos.</span><span class="sxs-lookup"><span data-stu-id="dafcb-137">In the following example, `$var` is a variable that is a node tree in the style sheet.</span></span> <span data-ttu-id="dafcb-138">Para- cada declaração, combinada com a função de `node-set` , permite que o usuário itere sobre esta árvore como um conjunto de nó.</span><span class="sxs-lookup"><span data-stu-id="dafcb-138">The for-each statement, combined with the `node-set` function, allows the user to iterate over this tree as a node set.</span></span>

```xml
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform"
                xmlns:msxsl="urn:schemas-microsoft-com:xslt"
                xmlns:user="http://www.adventure-works.com"
                version="1.0">
    <xsl:variable name="states">
        <node1>AL</node1>
        <node1>CA</node1>
        <node1>CO</node1>
        <node1>WA</node1>
    </xsl:variable>

    <xsl:template match="/">
            <xsl:for-each select="msxsl:node-set($states)"/> 
    </xsl:template>
</xsl:stylesheet>
```

<span data-ttu-id="dafcb-139">Aqui está um exemplo de uma variável que está em RTF, e portanto de fragmento da árvore do resultado de tipo, que é convertido em um nó definida antes de ser passado para uma função script como XPathNodeIterator.</span><span class="sxs-lookup"><span data-stu-id="dafcb-139">Here is another example of a variable that is in RTF, and hence of type result tree fragment, that is converted to a node set before being passed to a script function as XPathNodeIterator.</span></span>

```xml
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform"
        xmlns:msxsl="urn:schemas-microsoft-com:xslt"
        xmlns:user="urn:books"
        exclude-result-prefixes="msxsl">

<xsl:output method="xml" indent="yes" omit-xml-declaration="yes"/>

<xsl:variable name="node-fragment">
    <book>Book1</book>
    <book>Book2</book>
    <book>Book3</book>
    <book>Book4</book>
</xsl:variable>

<msxsl:script implements-prefix="user" language="c#">

<![CDATA[
    string func(XPathNodeIterator it)
    {
        it.MoveNext(); 
        return it.Current.Value; 
        //it.Current returns XPathNavigator positioned on the current node
    }

]]>

</msxsl:script>
<xsl:template match="/">
    <books>
        <xsl:value-of select="user:func(msxsl:node-set($node-fragment))"/>
    </books>
</xsl:template>

</xsl:stylesheet>
```

<span data-ttu-id="dafcb-140">O seguinte é o resultado de transformar XML com essa folha de estilos:</span><span class="sxs-lookup"><span data-stu-id="dafcb-140">The following is the result of transforming XML with this style sheet:</span></span>

```xml
<books xmlns:user="urn:books">Book1Book2Book3Book4</books>
```

## <a name="see-also"></a><span data-ttu-id="dafcb-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dafcb-141">See also</span></span>

- <xref:System.Xml.XPath.XPathNodeIterator>
- <xref:System.Xml.XPath.XPathNodeIterator>
- [<span data-ttu-id="dafcb-142">Transformações XSLT com a classe XslTransform</span><span class="sxs-lookup"><span data-stu-id="dafcb-142">XSLT Transformations with the XslTransform Class</span></span>](xslt-transformations-with-the-xsltransform-class.md)
- [<span data-ttu-id="dafcb-143">A classe XslTransform implementa o processador XSLT</span><span class="sxs-lookup"><span data-stu-id="dafcb-143">XslTransform Class Implements the XSLT Processor</span></span>](xsltransform-class-implements-the-xslt-processor.md)
