---
title: "Delimitadores para marcas de documenta&#231;&#227;o (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "delimitadores /** */ para marcas de documentação C#"
  - "delimitador /// para documentação C#"
  - "XML [C#], delimitadores"
ms.assetid: 9b2bdd18-4f5c-4c0b-988e-fb992e0d233e
caps.latest.revision: 21
caps.handback.revision: 21
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Delimitadores para marcas de documenta&#231;&#227;o (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O uso de comentários doc do XML requer delimitadores, que indicam ao compilador onde um comentário de documentação começa e termina.  Você pode usar os seguintes tipos de delimitadores com as marcas de documentação XML:  
  
 `///`  
 Delimitador de linha única.  Este é o formulário que é mostrado nos exemplos de documentação e usado pelos modelos de projeto do Visual C\#.  Se houver um caractere de espaço em branco após o delimitador, esse caractere não está incluído na saída XML.  
  
> [!NOTE]
>  O IDE Visual Studio tem um recurso chamado Smart edição de comentário que insere automaticamente o \<summary\> e \<\/summary\> as marcações e move o cursor dentro dessas marcas após digitar a `///` no Editor de código do delimitador.  Para acessar este recurso a partir do [Opções, editor de texto, C\#, formatação](/visual-studio/ide/reference/options-text-editor-csharp-formatting) em suas páginas de propriedades do projeto.  
  
 `/** */`  
 Delimitadores de várias linhas.  
  
 Existem algumas regras de formatação a seguir ao usar o `/** */` delimitadores.  
  
-   Na linha que contém o `/**` delimitador, se o restante da linha é o espaço em branco, a linha não é processado para comentários.  Se o primeiro caractere após o `/**` delimitador é o espaço em branco, que o caractere de espaço em branco será ignorado e o restante da linha é processado.  Caso contrário, todo o texto da linha após a `/**` delimitador é processado como parte do comentário.  
  
-   Na linha que contém o `*/` delimitador, se houver somente espaços em branco até o `*/` delimitador, essa linha é ignorado.  Caso contrário, o texto da linha até o `*/` delimitador é processado como parte do comentário, sujeitas às regras de correspondência de padrões descrito no seguinte marcador.  
  
-   Para as linhas após a que começa com o `/**` delimitador, o compilador procura um padrão comum no início de cada linha.  O padrão pode consistir em espaços em branco opcional e um asterisco \(`*`\), seguido de mais espaço em branco opcional.  Se o compilador localiza um padrão comum no início de cada linha que não começa com o `/**` delimitador ou a `*/` delimitador, ele ignora esse padrão para cada linha.  
  
 Os exemplos a seguir ilustram essas regras.  
  
-   A única parte do seguinte comentário será processada é a linha que começa com `<summary>`.  Formatos de três marca produzem os mesmos comentários.  
  
    ```  
    /** <summary>text</summary> */   
  
    /**   
    <summary>text</summary>   
    */   
  
    /**   
     * <summary>text</summary>   
    */  
  
    ```  
  
-   O compilador identifica um padrão comum de "\*" no início da segunda e terceira linhas.  O padrão não está incluído na saída.  
  
    ```  
    /**   
     * <summary>   
     * text </summary>*/   
    ```  
  
-   O compilador não encontra nenhum padrão comum no seguinte comentário porque o segundo caractere na terceira linha não é um asterisco.  Portanto, todo o texto a segunda e terceira linhas é processado como parte do comentário.  
  
    ```  
    /**   
     * <summary>   
       text </summary>  
    */   
    ```  
  
-   O compilador não encontra nenhum padrão no seguinte comentário por dois motivos.  Primeiro, o número de espaços antes do asterisco não é consistente.  Em segundo lugar, a quinta linha começa com uma guia, o que não coincide com espaços.  Portanto, todo o texto das linhas de dois a cinco é processado como parte do comentário.  
  
    ```  
    /**   
      * <summary>   
      * text   
     *  text2   
        *  </summary>   
    */   
    ```  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Comentários de documentação XML](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)   
 [\/doc \(Process Documentation Comments\)](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)   
 [Comentários de documentação XML](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)