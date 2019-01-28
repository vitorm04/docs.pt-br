---
title: '&lt;include&gt; – Guia de Programação em C#'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- include
- <include>
helpviewer_keywords:
- <include> C# XML tag
- include C# XML tag
ms.assetid: a8a70302-6196-4643-bd09-ef33f411f18f
ms.openlocfilehash: a9e87e803bef38ceb91849b976e2019deed54471
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54541164"
---
# <a name="ltincludegt-c-programming-guide"></a>&lt;include&gt; (Guia de Programação em C#)
## <a name="syntax"></a>Sintaxe  
  
```xml  
<include file='filename' path='tagpath[@name="id"]' />  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `filename`  
 O nome do arquivo XML que contém a documentação. O nome do arquivo pode ser qualificado com um caminho relativo ao arquivo de código-fonte. Coloque `filename` entre aspas simples (' ').  
  
 `tagpath`  
 O caminho das marcas em `filename` que leva à marca `name`. Coloque o caminho entre aspas simples (' ').  
  
 `name`  
 O especificador de nome na marca que precede os comentários; `name` terá um `id`.  
  
 `id`  
 A ID da marca que precede os comentários. Coloque a ID entre aspas duplas (" ").  
  
## <a name="remarks"></a>Comentários  
 A marca \<include> permite consultar comentários em outro arquivo que descrevem os tipos e membros em seu código-fonte. Essa é uma alternativa para inserir comentários de documentação diretamente em seu arquivo de código-fonte. Colocando a documentação em um arquivo separado, é possível aplicar o controle do código-fonte à documentação separadamente do código-fonte. Uma pessoa pode fazer o check-out do arquivo de código-fonte e outra pessoa pode fazer o check-out do arquivo de documentação.  
  
 A marca \<include> usa a sintaxe XML XPath. Consulte a documentação do XPath para obter maneiras de personalizar o uso de \<include>.  
  
## <a name="example"></a>Exemplo  
 Este é um exemplo de vários arquivos. O primeiro arquivo, que usa \<include>, é listado abaixo:  
  
 [!code-csharp[csProgGuideDocComments#5](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/include_1.cs)]  
  
 O segundo arquivo, xml_include_tag.doc, contém os comentários de documentação a seguir:  
  
```xml  
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
  
## <a name="program-output"></a>Saída do Programa  
 A seguinte saída é gerada quando você compila as classes Test e Test2 com a seguinte linha de comando: `/doc:DocFileName.xml.` No Visual Studio, você especifica a opção de comentários do documento XML no painel Compilar do Designer de Projeto. Quando o compilador C# encontrar a marca \<include>, ele pesquisará os comentários da documentação em xml_include_tag.doc, em vez de no arquivo de origem atual. O compilador, então, gera DocFileName.xml e esse é o arquivo consumido pelas ferramentas de documentação como [Sandcastle](https://github.com/EWSoftware/SHFB) para gerar a documentação final.  
  
```xml  
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
  
## <a name="see-also"></a>Consulte também

- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)
- [Marcas recomendadas para comentários de documentação](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
