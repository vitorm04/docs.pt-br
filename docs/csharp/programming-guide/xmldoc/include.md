---
title: "&lt;include&gt; (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "include"
  - "<include>"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "Marca &lt;include&gt; (XML) C#"
  - "marca XML C# include"
ms.assetid: a8a70302-6196-4643-bd09-ef33f411f18f
caps.latest.revision: 19
caps.handback.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# &lt;include&gt; (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

## Sintaxe  
  
```  
<include file='filename' path='tagpath[@name="id"]' />  
```  
  
#### Parâmetros  
 `filename`  
 O nome do arquivo XML que contém a documentação.  O nome do arquivo pode ser qualificado com um caminho.  Coloque `filename` entre aspas simples \(' '\).  
  
 `tagpath`  
 O caminho nas marcas `filename` que leva a marca de `name`.  Coloque o caminho entre aspas simples \(' '\).  
  
 `name`  
 O especificador de nome na marca que precede os comentários.  `name`terá um `id`.  
  
 `id`  
 A identificação de marca que precede os comentários.  Coloque a identificação entre aspas duplas \(""\).  
  
## Comentários  
 O \<include\> marca permite que você consulte os comentários em outro arquivo que descrevem os tipos e membros em seu código\-fonte.  Essa é uma alternativa à colocação de comentários da documentação diretamente no seu arquivo de código\-fonte.  Colocando a documentação em um arquivo separado, você pode aplicar o controle de origem a documentação separadamente do código fonte.  Uma pessoa pode ter o arquivo de código\-fonte com check\-out e outra pessoa pode ter o check\-out do arquivo de documentação.  
  
 O \<include\> marca usa a sintaxe do XPath XML.  Consulte a documentação do XPath para formas de personalizar seu \<include\> Use.  
  
## Exemplo  
 Este é um exemplo de vários arquivos.  O primeiro arquivo, que usa \<include\>, está listada abaixo:  
  
 [!code-cs[csProgGuideDocComments#5](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/include_1.cs)]  
  
 O segundo arquivo, xml\_include\_tag.doc, contém os comentários de documentação a seguir:  
  
```  
<MyDocs>  
  
<MyMembers name="test">  
<summary>  
The summary for this type.  
</summary>  
</MyMembers>  
  
<MyMembers name="test2">  
<summary>  
The summary for this other type.  
</summary>  
</MyMembers>  
  
</MyDocs>  
```  
  
## Saída do programa  
 A seguinte saída é gerada quando você compila as classes de teste e Test2 com a seguinte linha de comando: `/doc:DocFileName.xml.` em Visual Studio, que você especifica a opção de comentários XML doc no painel Build do Project Designer.  Quando o compilador C\# vê \<inclue\> marca, ele irá procurar os comentários de documentação no xml\_include\_tag.doc em vez do arquivo de origem atual.  O compilador gera, em seguida, DocFileName.xml, e esse é o arquivo que é consumido pelas ferramentas de documentação, como [Sandcastle](http://go.microsoft.com/fwlink/?LinkId=124061) para produzir a documentação final.  
  
```  
<?xml version="1.0"?>   
<doc>   
    <assembly>   
        <name>xml_include_tag</name>   
    </assembly>   
    <members>   
        <member name="T:Test">   
            <summary>   
The summary for this type.   
</summary>   
        </member>   
        <member name="T:Test2">   
            <summary>   
The summary for this other type.   
</summary>   
        </member>   
    </members>   
</doc>   
```  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Marcas recomendadas para comentários de documentação](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)