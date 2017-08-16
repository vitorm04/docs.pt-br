---
title: "Delimitadores para marcações de documentação (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- XML [C#], delimiters
- /** */ delimiters for C# documentation tags
- /// delimiter for C# documentation
ms.assetid: 9b2bdd18-4f5c-4c0b-988e-fb992e0d233e
caps.latest.revision: 21
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 3e31f0c3d815c0454a9be6813ff9a04e5fa4c7de
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="delimiters-for-documentation-tags-c-programming-guide"></a>Delimitadores para marcações de documentação (Guia de Programação em C#)
O uso de comentários do documento XML requer delimitadores, que indicam ao compilador em que um comentário de documentação começa e termina. Você pode usar os seguintes tipos de delimitadores com as marcas de documentação XML:  
  
 `///`  
 O delimitador de linha única. Este é o formulário mostrado nos exemplos de documentação e usado pelos modelos de projeto do Visual C#. Se houver um caractere de espaço em branco depois do delimitador, esse caractere não estará incluído na saída XML.  
  
> [!NOTE]
>  A IDE do Visual Studio tem um recurso chamado Edição de Comentário Inteligente que insere automaticamente as marcas \<summary> e \</summary> e move o cursor dentro dessas marcas depois que você digita o delimitador `///` no Editor de Código. Acesse esse recurso de [Opções, Editor de Texto, C#, Formatação](/visualstudio/ide/reference/options-text-editor-csharp-formatting) em suas páginas de propriedade do projeto.  
  
 `/** */`  
 Delimitadores multilinha.  
  
 Há algumas regras de formatação a serem seguidas ao usar os delimitadores `/** */`.  
  
-   Na linha que contém o delimitador `/**`, se o restante da linha for um espaço em branco, a linha não será processada para comentários. Se o primeiro caractere após o delimitador `/**` for um espaço em branco, esse caractere de espaço em branco será ignorado e o restante da linha será processado. Caso contrário, todo o texto da linha após o delimitador `/**` é processado como parte do comentário.  
  
-   Na linha que contém o delimitador `*/`, se houver apenas espaços em branco até o delimitador `*/`, essa linha será ignorada. Caso contrário, o texto da linha até o delimitador `*/` é processado como parte do comentário, sujeito às regras de correspondência de padrão descritas no marcador seguinte.  
  
-   Para as linhas após a que começa com o delimitador `/**`, o compilador procura um padrão comum no início de cada linha. O padrão pode consistir de espaço em branco opcional e um asterisco (`*`), seguido de mais espaço em branco opcional. Se o compilador encontrar um padrão comum no início de cada linha que não começa com o delimitador `/**` ou com o delimitador `*/`, ele ignorará esse padrão para cada linha.  
  
 Os exemplos a seguir ilustram essas regras.  
  
-   A única parte do comentário a seguir que será processada é a linha que começa com `<summary>`. Os três formatos de marca produzem os mesmos comentários.  
  
    ```  
    /** <summary>text</summary> */   
  
    /**   
    <summary>text</summary>   
    */   
  
    /**   
     * <summary>text</summary>   
    */  
    ```  
  
-   O compilador identifica um padrão comum de " * " no início da segunda e terceira linhas. O padrão não é incluído na saída.  
  
    ```  
    /**   
     * <summary>   
     * text </summary>*/   
    ```  
  
-   O compilador não encontra nenhum padrão comum no seguinte comentário porque o segundo caractere na terceira linha não é um asterisco. Portanto, todo o texto na segunda e terceira linhas é processado como parte do comentário.  
  
    ```  
    /**   
     * <summary>   
       text </summary>  
    */   
    ```  
  
-   O compilador não encontra nenhum padrão no seguinte comentário por dois motivos. Primeiro, o número de espaços antes do asterisco não é consistente. Segundo, a quinta linha começa com uma guia, que não coincide com espaços. Portanto, todo o texto das linhas de dois a cinco é processado como parte do comentário.  
  
    ```  
    /**   
      * <summary>   
      * text   
     *  text2   
        *  </summary>   
    */   
    ```  
  
## <a name="see-also"></a>Consulte também  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Comentários da documentação XML](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)   
 [/doc (Opções do compilador C#)](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)   
 [Comentários da documentação XML](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)

