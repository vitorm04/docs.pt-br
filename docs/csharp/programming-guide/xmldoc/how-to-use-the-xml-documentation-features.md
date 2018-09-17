---
title: Como usar as funcionalidades da documentação XML (Guia de Programação do C#)
ms.date: 06/01/2018
helpviewer_keywords:
- XML documentation [C#]
- C# language, XML documentation features
ms.assetid: 8f33917b-9577-4c9a-818a-640dbbb0b399
ms.openlocfilehash: 48654968e5099164874bae8a00767d12c8fe4582
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45514437"
---
# <a name="how-to-use-the-xml-documentation-features"></a>Como usar as funcionalidades da documentação XML

O exemplo a seguir fornece uma visão geral básica de um tipo que foi documentado.

## <a name="example"></a>Exemplo

[!code-csharp[csProgGuideDocComments#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#15)]

O exemplo gera um arquivo .xml com o seguinte conteúdo:

```xml
<?xml version="1.0"?>
<doc>
    <assembly>
        <name>xmlsample</name>
    </assembly>
    <members>
        <member name="T:TestClass">
            <summary>
            Class level summary documentation goes here.
            </summary>
            <remarks>
            Longer comments can be associated with a type or member through
            the remarks tag.
            </remarks>
        </member>
        <member name="F:TestClass._name">
            <summary>
            Store for the Name property.
            </summary>
        </member>
        <member name="M:TestClass.#ctor">
            <summary>
            The class constructor.
            </summary>
        </member>
        <member name="P:TestClass.Name">
            <summary>
            Name property.
            </summary>
            <value>
            A value tag is used to describe the property value.
            </value>
        </member>
        <member name="M:TestClass.SomeMethod(System.String)">
            <summary>
            Description for SomeMethod.
            </summary>
            <param name="s"> Parameter description for s goes here.</param>
            <seealso cref="T:System.String">
            You can use the cref attribute on any tag to reference a type or member 
            and the compiler will check that the reference exists.
            </seealso>
        </member>
        <member name="M:TestClass.SomeOtherMethod">
            <summary>
            Some other method.
            </summary>
            <returns>
            Return values are described through the returns tag.
            </returns>
            <seealso cref="M:TestClass.SomeMethod(System.String)">
            Notice the use of the cref attribute to reference a specific method.
            </seealso>
        </member>
        <member name="M:TestClass.Main(System.String[])">
            <summary>
            The entry point for the application.
            </summary>
            <param name="args"> A list of command line arguments.</param>
        </member>
        <member name="T:TestInterface">
            <summary>
            Documentation that describes the interface goes here.
            </summary>
            <remarks>
            Details about the interface go here.
            </remarks>
        </member>
        <member name="M:TestInterface.InterfaceMethod(System.Int32)">
            <summary>
            Documentation that describes the method goes here.
            </summary>
            <param name="n">
            Parameter n requires an integer argument.
            </param>
            <returns>
            The method returns an integer.
            </returns>
        </member>
    </members>
</doc>
```

## <a name="compiling-the-code"></a>Compilando o código

Para compilar o exemplo, digite a seguinte linha de comando:

`csc XMLsample.cs /doc:XMLsample.xml`

Esse comando cria o arquivo XML *XMLsample.xml*, que você pode exibir no navegador ou usando o comando TYPE.

## <a name="robust-programming"></a>Programação robusta

A documentação XML começa com ///. Quando você cria um novo projeto, os assistentes colocam algumas linhas iniciais /// para você. O processamento desses comentários tem algumas restrições:

- A documentação deve ser em XML bem formado. Se o XML não estiver bem formado, um aviso será gerado e o arquivo de documentação conterá um comentário que diz que foi encontrado um erro.

- Os desenvolvedores são livres para criar seu próprio conjunto de marcas. Há um conjunto de marcas recomendadas (confira [Marcas recomendadas para comentários da documentação](recommended-tags-for-documentation-comments.md)). Algumas das marcas recomendadas têm significado especial:

  - A marca \<param> é usada para descrever parâmetros. Se ela é usada, o compilador verifica se o parâmetro existe e se todos os parâmetros são descritos na documentação. Se a verificação falhar, o compilador emitirá um aviso.

  - O atributo `cref` pode ser anexado a qualquer marca para fornecer uma referência a um elemento de código. O compilador verifica se esse elemento de código existe. Se a verificação falhar, o compilador emitirá um aviso. O compilador respeita qualquer instrução `using` quando procura por um tipo descrito no atributo `cref`.

  - A marca \<summary> é usada pelo IntelliSense no Visual Studio para exibir informações adicionais sobre um tipo ou membro.

    > [!NOTE]
    > O arquivo XML não fornece informações completas sobre o tipo e os membros (por exemplo, ele não contém nenhuma informação de tipo). Para obter informações completas sobre um tipo ou membro, o arquivo de documentação deve ser usado com a reflexão no membro ou tipo real.

## <a name="see-also"></a>Consulte também

- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
- [-doc (opções do compilador do C#)](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)  
- [Comentários da documentação XML](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)  
