---
title: Blocos de script usando msxsl:script
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: fde6f43f-c594-486f-abcb-2211197fae20
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: badf5511c5638d98d25997f31a3aff8dc11144d6
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="script-blocks-using-msxslscript"></a><span data-ttu-id="b8887-102">Blocos de script usando msxsl:script</span><span class="sxs-lookup"><span data-stu-id="b8887-102">Script Blocks Using msxsl:script</span></span>
<span data-ttu-id="b8887-103">A classe <xref:System.Xml.Xsl.XslCompiledTransform> oferece suporte a scripts inserido usando o elemento `msxsl:script`.</span><span class="sxs-lookup"><span data-stu-id="b8887-103">The <xref:System.Xml.Xsl.XslCompiledTransform> class supports embedded scripts using the `msxsl:script` element.</span></span> <span data-ttu-id="b8887-104">Quando a folha de estilos é carregada, todas as funções definidas são compiladas para Microsoft Intermediate Language (MSIL) pelo Code Document Object Model (CodeDOM) e executadas durante o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="b8887-104">When the style sheet is loaded, any defined functions are compiled to Microsoft intermediate language (MSIL) by the Code Document Object Model (CodeDOM) and are executed during run time.</span></span> <span data-ttu-id="b8887-105">O assembly gerado no bloco de script inserido é separado do assembly gerado para a folha de estilos.</span><span class="sxs-lookup"><span data-stu-id="b8887-105">The assembly generated from the embedded script block is separate than the assembly generated for the style sheet.</span></span>  
  
## <a name="enable-xslt-script"></a><span data-ttu-id="b8887-106">Habilitar scripts XSLT</span><span class="sxs-lookup"><span data-stu-id="b8887-106">Enable XSLT Script</span></span>  
 <span data-ttu-id="b8887-107">O suporte a scripts inseridos é uma configuração XSLT opcional na classe <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="b8887-107">Support for embedded scripts is an optional XSLT setting on the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="b8887-108">O suporte a script é desabilitado por padrão.</span><span class="sxs-lookup"><span data-stu-id="b8887-108">Script support is disabled by default.</span></span> <span data-ttu-id="b8887-109">Para habilitar o suporte a script, crie um objeto <xref:System.Xml.Xsl.XsltSettings> com a propriedade <xref:System.Xml.Xsl.XsltSettings.EnableScript%2A> definida para `true` e passe o objeto para o método <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A>.</span><span class="sxs-lookup"><span data-stu-id="b8887-109">To enable script support, create an <xref:System.Xml.Xsl.XsltSettings> object with the <xref:System.Xml.Xsl.XsltSettings.EnableScript%2A> property set to `true` and pass the object to the <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b8887-110">O script XSLT deverá ser habilitado somente se você precisar de suporte a script e estiver trabalhando em um ambiente totalmente confiável.</span><span class="sxs-lookup"><span data-stu-id="b8887-110">XSLT scripting should be enabled only if you require script support and you are working in a fully trusted environment.</span></span>  
  
## <a name="msxslscript-element-definition"></a><span data-ttu-id="b8887-111">Definição do elemento msxsl:script</span><span class="sxs-lookup"><span data-stu-id="b8887-111">msxsl:script Element Definition</span></span>  
 <span data-ttu-id="b8887-112">O elemento `msxsl:script` é uma extensão da Microsoft para a recomendação XSLT 1.0 e tem a seguinte definição:</span><span class="sxs-lookup"><span data-stu-id="b8887-112">The `msxsl:script` element is a Microsoft extension to the XSLT 1.0 recommendation and has the following definition:</span></span>  
  
```xml  
<msxsl:script language = "language-name" implements-prefix = "prefix of user namespace"> </msxsl:script>  
```  
  
 <span data-ttu-id="b8887-113">O prefixo `msxsl` é associado ao URI do namespace `urn:schemas-microsoft-com:xslt`.</span><span class="sxs-lookup"><span data-stu-id="b8887-113">The `msxsl` prefix is bound to the `urn:schemas-microsoft-com:xslt` namespace URI.</span></span> <span data-ttu-id="b8887-114">A folha de estilos deve incluir a declaração de namespace `xmlns:msxsl=urn:schemas-microsoft-com:xslt`.</span><span class="sxs-lookup"><span data-stu-id="b8887-114">The style sheet must include the `xmlns:msxsl=urn:schemas-microsoft-com:xslt` namespace declaration.</span></span>  
  
 <span data-ttu-id="b8887-115">O atributo `language` é opcional.</span><span class="sxs-lookup"><span data-stu-id="b8887-115">The `language` attribute is optional.</span></span> <span data-ttu-id="b8887-116">Seu valor é a linguagem de código do bloco de código inserido.</span><span class="sxs-lookup"><span data-stu-id="b8887-116">Its value is the code language of the embedded code block.</span></span> <span data-ttu-id="b8887-117">O idioma é mapeado para o compilador CodeDOM apropriado que usa o método <xref:System.CodeDom.Compiler.CodeDomProvider.CreateProvider%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b8887-117">The language is mapped to the appropriate CodeDOM compiler using the <xref:System.CodeDom.Compiler.CodeDomProvider.CreateProvider%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="b8887-118">A classe <xref:System.Xml.Xsl.XslCompiledTransform> pode oferecer suporte a qualquer linguagem do Microsoft .NET, supondo que o provedor apropriado esteja instalado no computador e registrado na seção de system.codedom do arquivo machine.config.</span><span class="sxs-lookup"><span data-stu-id="b8887-118">The <xref:System.Xml.Xsl.XslCompiledTransform> class can support any Microsoft .NET language, assuming the appropriate provider is installed on the machine and is registered in the system.codedom section of the machine.config file.</span></span> <span data-ttu-id="b8887-119">Se o atributo `language` não for especificado, a linguagem assume JScript como padrão.</span><span class="sxs-lookup"><span data-stu-id="b8887-119">If a `language` attribute is not specified, the language defaults to JScript.</span></span> <span data-ttu-id="b8887-120">O nome da linguagem não diferencia maiúsculas de minúsculas; portanto, 'JavaScript' e 'javascript' são equivalentes.</span><span class="sxs-lookup"><span data-stu-id="b8887-120">The language name is not case-sensitive so 'JavaScript' and 'javascript' are equivalent.</span></span>  
  
 <span data-ttu-id="b8887-121">O atributo `implements-prefix` é obrigatório.</span><span class="sxs-lookup"><span data-stu-id="b8887-121">The `implements-prefix` attribute is mandatory.</span></span> <span data-ttu-id="b8887-122">Esse atributo é usado para declarar um namespace e associá-lo ao bloco de script.</span><span class="sxs-lookup"><span data-stu-id="b8887-122">This attribute is used to declare a namespace and associate it with the script block.</span></span> <span data-ttu-id="b8887-123">O valor desse atributo é o prefixo que representa o namespace.</span><span class="sxs-lookup"><span data-stu-id="b8887-123">The value of this attribute is the prefix that represents the namespace.</span></span> <span data-ttu-id="b8887-124">Este prefixo pode ser definido em qualquer lugar de uma folha de estilos.</span><span class="sxs-lookup"><span data-stu-id="b8887-124">This prefix can be defined somewhere in a style sheet.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b8887-125">Ao usar o elemento `msxsl:script`, é altamente recomendável que o script, independentemente da linguagem, seja colocado em uma seção CDATA.</span><span class="sxs-lookup"><span data-stu-id="b8887-125">When using the `msxsl:script` element, we strongly recommend that the script, regardless of language, be placed inside a CDATA section.</span></span> <span data-ttu-id="b8887-126">Como o script pode conter operadores, identificadores ou delimitadores para uma linguagem específica, caso ele não esteja em uma seção CDATA, ele podes ser interpretado incorretamente como XML.</span><span class="sxs-lookup"><span data-stu-id="b8887-126">Because the script can contain operators, identifiers, or delimiters for a given language, if it is not contained within a CDATA section, it has the potential of being misinterpreted as XML.</span></span> <span data-ttu-id="b8887-127">O XML a seguir mostra um modelo da seção CDATA em que o código pode ser inserido.</span><span class="sxs-lookup"><span data-stu-id="b8887-127">The following XML shows a template of the CDATA section where code can be placed.</span></span>  
  
```xml  
<msxsl:script implements-prefix='your-prefix' language='CSharp'>  
<![CDATA[  
// Code block.  
]]>  
</msxsl:script>  
```  
  
## <a name="script-functions"></a><span data-ttu-id="b8887-128">Funções de script</span><span class="sxs-lookup"><span data-stu-id="b8887-128">Script Functions</span></span>  
 <span data-ttu-id="b8887-129">As funções podem ser declaradas no elemento `msxsl:script`.</span><span class="sxs-lookup"><span data-stu-id="b8887-129">Functions can be declared within the `msxsl:script` element.</span></span> <span data-ttu-id="b8887-130">Quando uma função é declarada, ela está contida em um bloco de script.</span><span class="sxs-lookup"><span data-stu-id="b8887-130">When a function is declared, it is contained in a script block.</span></span> <span data-ttu-id="b8887-131">As folhas de estilos podem conter vários blocos de script, cada uma funcionando de maneira independente da outra.</span><span class="sxs-lookup"><span data-stu-id="b8887-131">Style sheets can contain multiple script blocks, each operating independent of the other.</span></span> <span data-ttu-id="b8887-132">Isso significa que, se você estiver realizando a execução em um bloco de script, não poderá chamar uma função definida em outro bloco de script, a menos que tenha sido declarado que ela tem o mesmo namespace e a mesma linguagem de script.</span><span class="sxs-lookup"><span data-stu-id="b8887-132">That means that if you are executing inside a script block, you cannot call a function that you defined in another script block unless it is declared to have the same namespace and the same scripting language.</span></span> <span data-ttu-id="b8887-133">Como cada bloco de script pode ter sua própria linguagem, e o bloco é analisado de acordo com as regras de gramática do analisador de linguagem, é recomendável utilizar a sintaxe correta para a linguagem em uso.</span><span class="sxs-lookup"><span data-stu-id="b8887-133">Because each script block can be in its own language, and the block is parsed according to the grammar rules of that language parser we recommend that you use the correct syntax for the language in use.</span></span> <span data-ttu-id="b8887-134">Por exemplo, se você estiver em um bloco de script do Microsoft C#, use a sintaxe de comentário C#.</span><span class="sxs-lookup"><span data-stu-id="b8887-134">For example, if you are in a Microsoft C# script block, use the C# comment syntax.</span></span>  
  
 <span data-ttu-id="b8887-135">Os argumentos e valores de retorno fornecidos para a função podem ser de qualquer tipo.</span><span class="sxs-lookup"><span data-stu-id="b8887-135">The supplied arguments and return values to the function can be of any type.</span></span> <span data-ttu-id="b8887-136">Como os tipos W3C XPath são um subconjunto dos tipos de Common Language Runtime (CLR), a conversão de tipo ocorre nos tipos que não são considerados um tipo XPath.</span><span class="sxs-lookup"><span data-stu-id="b8887-136">Because the W3C XPath types are a subset of the common language runtime (CLR) types, type conversion takes place on types that are not considered to be an XPath type.</span></span> <span data-ttu-id="b8887-137">A tabela a seguir mostra os tipos W3C correspondentes e o tipo CLR equivalente.</span><span class="sxs-lookup"><span data-stu-id="b8887-137">The following table shows the corresponding W3C types and the equivalent CLR type.</span></span>  
  
|<span data-ttu-id="b8887-138">Tipo W3C</span><span class="sxs-lookup"><span data-stu-id="b8887-138">W3C type</span></span>|<span data-ttu-id="b8887-139">Tipo CLR</span><span class="sxs-lookup"><span data-stu-id="b8887-139">CLR type</span></span>|  
|--------------|--------------|  
|`String`|<xref:System.String>|  
|`Boolean`|<xref:System.Boolean>|  
|`Number`|<xref:System.Double>|  
|`Result Tree Fragment`|<xref:System.Xml.XPath.XPathNavigator>|  
|`Node Set`|<xref:System.Xml.XPath.XPathNodeIterator>|  
  
 <span data-ttu-id="b8887-140">Os tipos numéricos de CLR são convertidos em <xref:System.Double>.</span><span class="sxs-lookup"><span data-stu-id="b8887-140">CLR numeric types are converted to <xref:System.Double>.</span></span> <span data-ttu-id="b8887-141">O tipo <xref:System.DateTime> é convertido em <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="b8887-141">The <xref:System.DateTime> type is converted to <xref:System.String>.</span></span> <span data-ttu-id="b8887-142">Os tipos <xref:System.Xml.XPath.IXPathNavigable> são convertidos em <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="b8887-142"><xref:System.Xml.XPath.IXPathNavigable> types are converted to <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="b8887-143">**XPathNavigator[]** é convertido em <xref:System.Xml.XPath.XPathNodeIterator>.</span><span class="sxs-lookup"><span data-stu-id="b8887-143">**XPathNavigator[]** is converted to <xref:System.Xml.XPath.XPathNodeIterator>.</span></span>  
  
 <span data-ttu-id="b8887-144">Todos os outros tipos lançam um erro.</span><span class="sxs-lookup"><span data-stu-id="b8887-144">All other types throw an error.</span></span>  
  
### <a name="importing-namespaces-and-assemblies"></a><span data-ttu-id="b8887-145">Importando namespaces e assemblies</span><span class="sxs-lookup"><span data-stu-id="b8887-145">Importing Namespaces and Assemblies</span></span>  
 <span data-ttu-id="b8887-146">A classe <xref:System.Xml.Xsl.XslCompiledTransform> predefine um conjunto de assemblies e namespaces com suporte, por padrão, no elemento `msxsl:script`.</span><span class="sxs-lookup"><span data-stu-id="b8887-146">The <xref:System.Xml.Xsl.XslCompiledTransform> class predefines a set of assemblies and namespaces that are supported by default by the `msxsl:script` element.</span></span> <span data-ttu-id="b8887-147">No entanto, você pode usar as classes e os membros pertencentes a um namespace que não está na lista predefinida importando o assembly e o namespace no bloco `msxsl:script`.</span><span class="sxs-lookup"><span data-stu-id="b8887-147">However, you can use classes and members belonging to a namespace that is not on the predefined list by importing the assembly and namespace in `msxsl:script` block.</span></span>  
  
#### <a name="assemblies"></a><span data-ttu-id="b8887-148">Assemblies</span><span class="sxs-lookup"><span data-stu-id="b8887-148">Assemblies</span></span>  
 <span data-ttu-id="b8887-149">Os dois assemblies seguintes são referenciados por padrão:</span><span class="sxs-lookup"><span data-stu-id="b8887-149">The following two assemblies are referenced by default:</span></span>  
  
-   <span data-ttu-id="b8887-150">System.dll</span><span class="sxs-lookup"><span data-stu-id="b8887-150">System.dll</span></span>  
  
-   <span data-ttu-id="b8887-151">System.Xml.dll</span><span class="sxs-lookup"><span data-stu-id="b8887-151">System.Xml.dll</span></span>  
  
-   <span data-ttu-id="b8887-152">Microsoft.VisualBasic.dll (quando a linguagem de script for VB)</span><span class="sxs-lookup"><span data-stu-id="b8887-152">Microsoft.VisualBasic.dll (when the script language is VB)</span></span>  
  
 <span data-ttu-id="b8887-153">Você pode importar os assemblies adicionais usando o elemento `msxsl:assembly`.</span><span class="sxs-lookup"><span data-stu-id="b8887-153">You can import the additional assemblies using the `msxsl:assembly` element.</span></span> <span data-ttu-id="b8887-154">Isso inclui o assembly quando a folha de estilos é compilada.</span><span class="sxs-lookup"><span data-stu-id="b8887-154">This includes the assembly when the style sheet is compiled.</span></span> <span data-ttu-id="b8887-155">O elemento `msxsl:assembly` tem a seguinte definição:</span><span class="sxs-lookup"><span data-stu-id="b8887-155">The `msxsl:assembly` element has the following definition:</span></span>  
  
```xml  
<msxsl:script>  
  <msxsl:assembly name="system.assemblyName" />  
  <msxsl:assembly href="path-name" />  
    <![CDATA[  
    // User code  
    ]]>  
</msxsl:script>  
```  
  
 <span data-ttu-id="b8887-156">O atributo `name` contém o nome do assembly e o atributo `href` contém o caminho para o assembly.</span><span class="sxs-lookup"><span data-stu-id="b8887-156">The `name` attribute contains the name of the assembly and the `href` attribute contains the path to the assembly.</span></span> <span data-ttu-id="b8887-157">O nome do assembly pode ser um nome completo, como "System.Data, Version=2.0.3600.0, Culture=neutral, PublicKeyToken=b77a5c561934e089", ou um nome curto, como "System.Web".</span><span class="sxs-lookup"><span data-stu-id="b8887-157">The assembly name can be a full name, such as "System.Data, Version=2.0.3600.0, Culture=neutral, PublicKeyToken=b77a5c561934e089", or a short name, such as "System.Web".</span></span>  
  
#### <a name="namespaces"></a><span data-ttu-id="b8887-158">Namespaces</span><span class="sxs-lookup"><span data-stu-id="b8887-158">Namespaces</span></span>  
 <span data-ttu-id="b8887-159">Os seguintes namespaces são incluídos por padrão:</span><span class="sxs-lookup"><span data-stu-id="b8887-159">The following namespaces are included by default:</span></span>  
  
-   <span data-ttu-id="b8887-160">Sistema</span><span class="sxs-lookup"><span data-stu-id="b8887-160">System</span></span>  
  
-   <span data-ttu-id="b8887-161">System.Collection</span><span class="sxs-lookup"><span data-stu-id="b8887-161">System.Collection</span></span>  
  
-   <span data-ttu-id="b8887-162">System.Text</span><span class="sxs-lookup"><span data-stu-id="b8887-162">System.Text</span></span>  
  
-   <span data-ttu-id="b8887-163">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="b8887-163">System.Text.RegularExpressions</span></span>  
  
-   <span data-ttu-id="b8887-164">System.Xml</span><span class="sxs-lookup"><span data-stu-id="b8887-164">System.Xml</span></span>  
  
-   <span data-ttu-id="b8887-165">System.Xml.Xsl</span><span class="sxs-lookup"><span data-stu-id="b8887-165">System.Xml.Xsl</span></span>  
  
-   <span data-ttu-id="b8887-166">System.Xml.XPath</span><span class="sxs-lookup"><span data-stu-id="b8887-166">System.Xml.XPath</span></span>  
  
-   <span data-ttu-id="b8887-167">Microsoft.VisualBasic (quando a linguagem de script for VB)</span><span class="sxs-lookup"><span data-stu-id="b8887-167">Microsoft.VisualBasic (when the script language is VB)</span></span>  
  
 <span data-ttu-id="b8887-168">Você pode adicionar suporte a namespaces adicionais usando o atributo `namespace`.</span><span class="sxs-lookup"><span data-stu-id="b8887-168">You can add support for additional namespaces using the `namespace` attribute.</span></span> <span data-ttu-id="b8887-169">O valor do atributo é o nome do namespace.</span><span class="sxs-lookup"><span data-stu-id="b8887-169">The attribute value is the name of the namespace.</span></span>  
  
```xml  
<msxsl:script>  
  <msxsl:using namespace="system.namespaceName" />  
    <![CDATA[  
    // User code  
    ]]>  
</msxsl:script>  
```  
  
## <a name="example"></a><span data-ttu-id="b8887-170">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b8887-170">Example</span></span>  
 <span data-ttu-id="b8887-171">O exemplo a seguir usa um script inserido para calcular a circunferência de um círculo considerando o seu raio.</span><span class="sxs-lookup"><span data-stu-id="b8887-171">The following example uses an embedded script to calculate the circumference of a circle given its radius.</span></span>  
  
 [!code-csharp[XSLT_Script#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XSLT_Script/CS/xslt_script.cs#1)]
 [!code-vb[XSLT_Script#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XSLT_Script/VB/xslt_script.vb#1)]  
  
#### <a name="numberxml"></a><span data-ttu-id="b8887-172">number.xml</span><span class="sxs-lookup"><span data-stu-id="b8887-172">number.xml</span></span>  
 [!code-xml[XSLT_Script#2](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Script/XML/number.xml#2)]  
  
#### <a name="calcxsl"></a><span data-ttu-id="b8887-173">calc.xsl</span><span class="sxs-lookup"><span data-stu-id="b8887-173">calc.xsl</span></span>  
 [!code-xml[XSLT_Script#3](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Script/XML/calc.xsl#3)]  
  
### <a name="output"></a><span data-ttu-id="b8887-174">Saída</span><span class="sxs-lookup"><span data-stu-id="b8887-174">Output</span></span>  
  
```xml  
<circles xmlns:msxsl="urn:schemas-microsoft-com:xslt" xmlns:user="urn:my-scripts">  
  <circle>  
    <radius>12</radius>  
    <circumference>75.36</circumference>  
  </circle>  
  <circle>  
    <radius>37.5</radius>  
    <circumference>235.5</circumference>  
  </circle>  
</circles>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b8887-175">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b8887-175">See Also</span></span>  
 [<span data-ttu-id="b8887-176">Transformações XSLT</span><span class="sxs-lookup"><span data-stu-id="b8887-176">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)  
 <span data-ttu-id="b8887-177">[Dynamic Source Code Generation and Compilation](../../../../docs/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation.md) (Compilação e geração de código-fonte dinâmico)</span><span class="sxs-lookup"><span data-stu-id="b8887-177">[Dynamic Source Code Generation and Compilation](../../../../docs/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation.md)</span></span>
