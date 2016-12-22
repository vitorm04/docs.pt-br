---
title: "Como usar as Funcionalidades da Documenta&#231;&#227;o XML (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
  - "documentação XML [C#]"
  - "Linguagem c#, recursos de documentação XML"
ms.assetid: 8f33917b-9577-4c9a-818a-640dbbb0b399
caps.latest.revision: 19
caps.handback.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Como usar as Funcionalidades da Documenta&#231;&#227;o XML (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O exemplo a seguir fornece uma visão geral básica de um tipo que foi documentado.  
  
## <a name="example"></a>Exemplo  
 [!code-cs[csProgGuideDocComments#15](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/how-to-use-the-xml-documentation-features_1.cs)]  
  
 **Esse arquivo. XML foi gerado com o exemplo de código anterior.**  
**\<? xml versão = "1.0"?>**  
**\< doc>**  
 **\< assembly>**  
 **\< nome>xmlsample \< / nome>**  
 **\< / assembly>**  
 **\< membros>**  
 **\< nome do membro = "T:SomeClass">**  
 **\< resumo>**  
 **Documentação de resumo de nível de classe vai aqui. \< / summary>**  
 **\< comentários>**  
 **Mais comentários podem ser associados um tipo ou membro**   
 **por meio da marca de comentários \< / comentários>**  
 **\< / membro>**  
 **\< membro name="F:SomeClass.m_Name">**  
 **\< resumo>**  
 **Armazenamento para a propriedade nome \< / summary>**  
 **\< / membro>**  
 **\< nome do membro = "M:SomeClass. #ctor">**  
 **\< resumo>o construtor de classe. \< / summary>**   
 **\< / membro>**  
 **\< membro name="M:SomeClass.SomeMethod(System.String)">**  
 **\< resumo>**  
 **Descrição para SomeMethod. \< / summary>**  
 **\< nome do parâmetro = "s"> Descrição do parâmetro para s aqui \< / param>**  
 **\< seealso cref="T:System.String">**  
 **Você pode usar o atributo cref em qualquer marca para fazer referência a um tipo ou membro**   
 **e o compilador verificará se existe a referência. \< / seealso>**  
 **\< / membro>**  
 **\< membro name="M:SomeClass.SomeOtherMethod">**  
 **\< resumo>**  
 **Algum outro método. \< / summary>**  
 **\< retorna>**  
 **Retornar resultados descritos pela marca retorna. \< / retorna>**  
 **\< seealso cref="M:SomeClass.SomeMethod(System.String)">**  
 **Observe o uso do atributo cref para fazer referência a um método específico de \< / seealso>**  
 **\< / membro>**  
 **\< membro name="M:SomeClass.Main(System.String[])">**  
 **\< resumo>**  
 **O ponto de entrada para o aplicativo.**  
 **\< / summary>**  
 **\< nome do parâmetro = "args"> uma lista de argumentos de linha de comando \< / param>**  
 **\< / membro>**  
 **\< membro name="P:SomeClass.Name">**  
 **\< resumo>**  
 **Propriedade Name \< / summary>**  
 **\< valor>**  
 **Uma marca de valor é usada para descrever o valor da propriedade \< / valor>**  
 **\< / membro>**  
 **\< / membros>**  
**\< / doc>**   
## <a name="compiling-the-code"></a>Compilando o código  
 Para compilar o exemplo, digite a seguinte linha de comando:  
  
 `csc XMLsample.cs /doc:XMLsample.xml`  
  
 Isso criará o arquivo XML XMLsample.xml, que você pode exibir no navegador ou usando o comando TYPE.  
  
## <a name="robust-programming"></a>Programação robusta  
 Documentação XML começa com / / /. Quando você cria um novo projeto, os assistentes colocar alguns starter / / / linhas para você. O processamento desses comentários tem algumas restrições:  
  
-   A documentação deve ser bem formada XML. Se o XML não está bem formado, um aviso será gerado e o arquivo de documentação conterá um comentário que diz que foi encontrado um erro.  
  
-   Os desenvolvedores são livres para criar seu próprio conjunto de marcas. Há um conjunto recomendado de marcas (consulte a seção de leitura adicional). Algumas das marcas recomendadas têm significado especial:  
  
    -   O \< param> marca é usada para descrever os parâmetros. Se usado, o compilador verificará se o parâmetro existe e que todos os parâmetros estão descritos na documentação. Se a verificação falhar, o compilador emite um aviso.  
  
    -   O `cref` atributo pode ser anexado a qualquer marca para fornecer uma referência a um elemento de código. O compilador verificará se este elemento de código existe. Se a verificação falhar, o compilador emite um aviso. O compilador respeita qualquer `using` instruções quando ele procura por um tipo descrito o `cref` atributo.  
  
    -   O \< resumo> marca é usada pelo IntelliSense no Visual Studio para exibir informações adicionais sobre um tipo ou membro.  
  
        > [!NOTE]
        >  O arquivo XML não fornece informações completas sobre o tipo e membros (por exemplo, ele não contém qualquer informação de tipo). Para obter informações completas sobre um tipo ou membro, o arquivo de documentação deve ser usado junto com reflexão no tipo real ou membro.  
  
## <a name="see-also"></a>Consulte também  
 [Guia de programação em c#](../../../csharp/programming-guide/index.md)   
 [/doc (opções do compilador c#)](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)   
 [Comentários de documentação XML](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)