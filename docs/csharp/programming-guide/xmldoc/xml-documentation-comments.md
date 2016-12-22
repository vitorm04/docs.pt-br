---
title: "Coment&#225;rios de documenta&#231;&#227;o XML (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
  - "cs.xml"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "Linguagem C#, comentários de código XML"
  - "arquivos de código-fonte C#"
  - "comentários [C#], XML"
  - "comentários de documentação [C#]"
  - "XML [C#], comentários de código"
  - "comentários de documentação XML [C#]"
ms.assetid: 803b7f7b-7428-4725-b5db-9a6cff273199
caps.latest.revision: 26
caps.handback.revision: 26
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Coment&#225;rios de documenta&#231;&#227;o XML (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

No Visual C\#, você pode criar documentação para seu código ao incluir elementos XML nos campos de comentários especiais \(indicados por barras triplas\) no código\-fonte logo antes do bloco de código ao qual os comentários se referem, por exemplo:  
  
```  
/// <summary>  
///  This class performs an important function.  
/// </summary>  
public class MyClass{}  
```  
  
 Ao compilar com a opção [\/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md), o compilador procurará todas as marcas XML no código\-fonte e criará um arquivo de documentação XML.  Para criar a documentação final com base no arquivo gerado pelo compilador, você pode criar uma ferramenta personalizada ou usar uma ferramenta como [Sandcastle](http://go.microsoft.com/fwlink/?LinkId=124061).  
  
 Para consultar elementos XML \(por exemplo, sua função processa elementos XML específicos que você deseja descrever em um comentário da documentação XML\), você pode usar o mecanismo de citação padrão \(`<` e `>`\).  Para consultar identificadores genéricos em elementos de referência de código \(`cref`\), você pode usar os caracteres de escape \(por exemplo, `cref="List<T>"`\) ou chaves \(`cref="List{T}"`\).  Como um caso especial, o compilador analisa as chaves como colchetes angulares para tornar o comentário da documentação menos incômodo para o autor ao fazer referência a identificadores genéricos.  
  
> [!NOTE]
>  Os comentários da documentação XML não são metadados; eles não estão incluídos no assembly compilado e, portanto, não são acessíveis através de reflexão.  
  
## Nesta seção  
  
-   [Marcas recomendadas para comentários de documentação](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)  
  
-   [Processando o arquivo XML](../../../csharp/programming-guide/xmldoc/processing-the-xml-file.md)  
  
-   [Delimitadores para marcas de documentação](../../../csharp/programming-guide/xmldoc/delimiters-for-documentation-tags.md)  
  
-   [Como: Usar os recursos da documentação XML](../../../csharp/programming-guide/xmldoc/how-to-use-the-xml-documentation-features.md)  
  
## Seções relacionadas  
 Para obter mais informações, consulte:  
  
-   [\/doc \(comentários da documentação de processos\)](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)  
  
## Especificação da Linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)