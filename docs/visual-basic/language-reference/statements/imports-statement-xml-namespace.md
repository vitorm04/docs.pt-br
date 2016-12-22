---
title: "Instru&#231;&#227;o Imports (namespace XML) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.ImportsXmlns"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "imports [Visual Basic]"
  - "instrução Imports [Visual Basic]"
  - "namespaces [Visual Basic], importando"
  - "namespace XML [Visual Basic], importando"
ms.assetid: 1f4d50a6-08c7-4c2e-8206-ccae35fcd1b4
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Instru&#231;&#227;o Imports (namespace XML)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Importa prefixos do namespace XML ara usar em literais XML e propriedades de eixo XML.  
  
## Sintaxe  
  
```  
Imports <xmlns:xmlNamespacePrefix = "xmlNamespaceName">  
```  
  
## Partes  
 `xmlNamespacePrefix`  
 Opcional.  A sequência de caracteres pela qual elementos e atributos XML podem se referir a `xmlNamespaceName`.  Se nenhum `xmlNamespacePrefix` for fornecido, o namespace XML importado é o namespace XML padrão.  Deve ser um identificador XML válido.  Para obter mais informações, consulte [Nomes de elementos e atributos XML declarados](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).  
  
 `xmlNamespaceName`  
 Obrigatório.  A sequência de caracteres que identifica o namespace XML que está sendo importado.  
  
## Comentários  
 Você pode usar a instrução `Imports` para definir namespaces XML globais que você pode usar com literais XML e propriedades de eixo XML, ou como parâmetros passados para o operador `GetXmlNamespace`.  \(Para obter informações sobre como usar a instrução `Imports` para importar um alias que pode ser usado onde nomes de tipo são usados em seu código, consulte [Instrução Imports \(tipo e namespace .NET\)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).\) A sintaxe para declarar um namespace XML usando a instrução `Imports` é idêntica a sintaxe usada em XML.  Portanto, você pode copiar uma declaração de namespace de um arquivo XML e usá\-la em uma instrução `Imports`.  
  
 Prefixos de namespace XML são úteis quando você deseja criar repetidamente elementos XML que são do mesmo namespace.  O prefixo de namespace XML declarado com a instrução `Imports` é global no sentido de que está disponível a todos os códigos no arquivo.  Você pode usá\-lo quando você cria literais de elemento XML e quando você acessa propriedades de eixo XML.  Para obter mais informações, consulte [Literal do elemento XML](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) e [Propriedades do eixo XML](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md).  
  
 Se você definir um namespace XML global sem um prefixo de namespace \(por exemplo, `Imports <xmlns="http://SomeNameSpace>"`\), esse namespace é considerado o namespace XML padrão.  O namespace XML padrão é usado para quaisquer literais de elemento XML ou propriedades de eixo de atributo XML que não especificam explicitamente um namespace.  O namespace padrão também é usado se namespace especificado for o namespace vazio \(ou seja, `xmlns=""`\).  O namespace XML padrão não se aplica aos atributos XML em literais XML ou às propriedades de eixo do atributo XML que não têm um namespace.  
  
 Namespaces XML são definidos em um literal XML, que são chamados *namesapces XML locais*, têm precedência sobre namespaces XML que são definidos pela instrução `Imports` como globais.  Namespaces XML que são definidos pela instrução `Imports` têm precedência sobre namespaces XML importados para um projeto Visual Basic.  Se um literal XML define um namespace XML, esse namespaces local não se aplica a expressões incorporados.  
  
 Namespaces XML globais seguem as mesmas regras de escopo e definição que namespaces do .NET Framework.  Como resultado, você pode incluir uma instrução `Imports` para definir um namespace XML global em qualquer lugar que você pode importar um namespace do .NET Framework.  Isso inclui namespaces importados de arquivos de código e no nível do projeto.  Para obter informações sobre namespaces importados no nível do projeto, consulte [Página Referências, Designer de Projeto \(Visual Basic\)](/visual-studio/ide/reference/references-page-project-designer-visual-basic).  
  
 Cada arquivo\-fonte pode conter qualquer número de declarações `Imports`.  Elas devem seguir declarações de opções, como a instrução `Option Strict`, e devem preceder declarações de elemento de programação, como instruções  `Module` ou `Class`.  
  
## Exemplo  
 O exemplo a seguir importa um namespace XML padrão e um namespace XML identificado com o prefixo `ns`.  Em seguida, cria literais XML que usam os dois namespaces.  
  
 [!CODE [VbXMLSamples#45](../CodeSnippet/VS_Snippets_VBCSharp/VbXMLSamples#45)]  
  
 Esse código exibe o texto a seguir:  
  
```  
<ns:outer xmlns="http://DefaultNamespace"   
          xmlns:ns="http://NewNamespace">  
  <ns:innerElement></ns:innerElement>  
  <siblingElement></siblingElement>  
  <innerElement />  
</ns:outer>  
```  
  
## Exemplo  
 O exemplo a seguir importa o prefixo `ns` do namespace XML.  Em seguida, cria um literal XML que usa o prefixo do namespace e exibe a forma final do elemento.  
  
 [!CODE [VbXMLSamples#22](../CodeSnippet/VS_Snippets_VBCSharp/VbXMLSamples#22)]  
  
 Esse código exibe o texto a seguir:  
  
```  
<ns:outer xmlns:ns="http://SomeNamespace">  
  <ns:middle xmlns:ns="http://NewNamespace">  
    <ns:inner1 />  
    <inner2 xmlns="http://SomeNamespace" />  
  </ns:middle>  
</ns:outer>  
```  
  
 Observe que o compilador converteu o prefixo do namespace XML de um prefixo global para uma definição de prefixo local.  
  
## Exemplo  
 O exemplo a seguir importa o prefixo `ns` do namespace XML.  Ele então usa o prefixo de namespace para criar um literal XML e acessar o primeiro nó filho com o nome qualificado `ns:name`.  
  
 [!CODE [VbXMLSamples#19](../CodeSnippet/VS_Snippets_VBCSharp/VbXMLSamples#19)]  
  
 Esse código exibe o texto a seguir:  
  
 `Patrick Hines`  
  
## Consulte também  
 [Literal do elemento XML](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)   
 [Propriedades do eixo XML](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)   
 [Nomes de elementos e atributos XML declarados](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)   
 [Operador GetXmlNamespace](../../../visual-basic/language-reference/operators/getxmlnamespace-operator.md)