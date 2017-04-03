---
title: "Como usar as funcionalidades da Documentação XML (Guia de Programação em C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- XML documentation [C#]
- C# language, XML documentation features
ms.assetid: 8f33917b-9577-4c9a-818a-640dbbb0b399
caps.latest.revision: 19
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
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: f4e74e2da4a5f8ba0a9964a5eff4f2a492b8981f
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-use-the-xml-documentation-features-c-programming-guide"></a>Como usar as Funcionalidades da Documentação XML (Guia de Programação em C#)
O exemplo a seguir fornece uma visão geral básica de um tipo que foi documentado.  
  
## <a name="example"></a>Exemplo  
 [!code-cs[csProgGuideDocComments#15](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/how-to-use-the-xml-documentation-features_1.cs)]  
  
 **// Este arquivo .xml foi gerado com o exemplo de código anterior.**  
**\<?xml version="1.0"?>**  
**\<doc>**  
 **\<assembly>**  
 **\<name>xmlsample\</name>**  
 **\</assembly>**  
 **\<members>**  
 **\<nome do membro="T:SomeClass">**  
 **\<summary>**  
 **A documentação de resumo de nível fica aqui. \</summary>**  
 **\<remarks>**  
 **Comentários mais longos podem ser associados a um tipo ou membro**   
 **por meio da marca de comentário\</remarks>**  
 **\</member>**  
 **\<nome do membro="F:SomeClass.m_Name">**  
 **\<summary>**  
 **Repositório para a propriedade de nome\</summary>**  
 **\</member>**  
 **\<nome do membro="M:SomeClass.#ctor">**  
 **\<summary>O construtor de classe.\</summary>**   
 **\</member>**  
 **\<nome do membro="M:SomeClass.SomeMethod(System.String)">**  
 **\<summary>**  
 **Descrição de SomeMethod.\</summary>**  
 **\<nome do parâmetro="s"> A descrição do parâmetro para s fica aqui\</param>**  
 **\<seealso cref="T:System.String">**  
 **Você pode usar o atributo cref em qualquer marca para fazer referência a um tipo ou membro**   
 **e o compilador verificará se a referência existe. \</seealso>**  
 **\</member>**  
 **\<nome do membro="M:SomeClass.SomeOtherMethod">**  
 **\<summary>**  
 **Algum outro método. \</summary>**  
 **\<returns>**  
 **Resultados retornados são descritos por meio da marca returns. \</returns>**  
 **\<seealso cref="M:SomeClass.SomeMethod(System.String)">**  
 **Observe o uso do atributo cref para fazer referência a um método específico \</seealso>**  
 **\</member>**  
 **\<nome do membro="M:SomeClass.Main(System.String[])">**  
 **\<summary>**  
 **O ponto de entrada do aplicativo.**  
 **\</summary>**  
 **\<nome do parâmetro ="args"> Uma lista de argumentos de linha de comando\</param>**  
 **\</member>**  
 **\<nome do membro="P:SomeClass.Name">**  
 **\<summary>**  
 **Propriedade de nome \</summary>**  
 **\<value>**  
 **Uma marca value é usada para descrever o valor da propriedade \</value>**  
 **\</member>**  
 **\</members>**  
**\</doc>**   
## <a name="compiling-the-code"></a>Compilando o código  
 Para compilar o exemplo, digite a seguinte linha de comando:  
  
 `csc XMLsample.cs /doc:XMLsample.xml`  
  
 Isso criará o arquivo XML XMLsample.xml, que você pode exibir em seu navegador ou usando o comando TYPE.  
  
## <a name="robust-programming"></a>Programação robusta  
 A documentação XML começa com ///. Quando você cria um novo projeto, os assistentes colocam algumas linhas iniciais /// para você. O processamento desses comentários tem algumas restrições:  
  
-   A documentação deve ser em XML bem formado. Se o XML não estiver bem formado, um aviso será gerado e o arquivo de documentação conterá um comentário que diz que foi encontrado um erro.  
  
-   Os desenvolvedores são livres para criar seu próprio conjunto de marcas. Há um conjunto de marcas recomendado (consulte a seção de Leituras complementares). Algumas das marcas recomendadas têm significado especial:  
  
    -   A marca \<param> é usada para descrever parâmetros. Se ela for usada, o compilador verificará se o parâmetro existe e se todos os parâmetros são descritos na documentação. Se a verificação falhar, o compilador emitirá um aviso.  
  
    -   O atributo `cref` pode ser anexado a qualquer marca para fornecer uma referência a um elemento de código. O compilador verificará se este elemento de código existe. Se a verificação falhar, o compilador emitirá um aviso. O compilador respeita qualquer instrução `using` quando procura por um tipo descrito no atributo `cref`.  
  
    -   A marca \<summary> é usada pelo IntelliSense no Visual Studio para exibir informações adicionais sobre um tipo ou membro.  
  
        > [!NOTE]
        >  O arquivo XML não fornece informações completas sobre o tipo e os membros (por exemplo, ele não contém nenhuma informação de tipo). Para obter informações completas sobre um tipo ou membro, o arquivo de documentação deve ser usado com a reflexão no membro ou tipo real.  
  
## <a name="see-also"></a>Consulte também  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [/doc (Opções do compilador C#)](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)   
 [Comentários da documentação XML](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)
