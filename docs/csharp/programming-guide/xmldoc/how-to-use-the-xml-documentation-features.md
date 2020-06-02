---
title: Como usar os recursos de documentação XML-guia de programação C#
ms.date: 06/01/2018
helpviewer_keywords:
- XML documentation [C#]
- C# language, XML documentation features
ms.assetid: 8f33917b-9577-4c9a-818a-640dbbb0b399
ms.openlocfilehash: b7c5a8a895271f067505496c0d13f98b66a393d9
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287357"
---
# <a name="how-to-use-the-xml-documentation-features"></a><span data-ttu-id="4c2bf-102">Como usar as funcionalidades da documentação XML</span><span class="sxs-lookup"><span data-stu-id="4c2bf-102">How to use the XML documentation features</span></span>

<span data-ttu-id="4c2bf-103">O exemplo a seguir fornece uma visão geral básica de um tipo que foi documentado.</span><span class="sxs-lookup"><span data-stu-id="4c2bf-103">The following sample provides a basic overview of a type that has been documented.</span></span>

## <a name="example"></a><span data-ttu-id="4c2bf-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4c2bf-104">Example</span></span>

[!code-csharp[csProgGuideDocComments#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#15)]

<span data-ttu-id="4c2bf-105">O exemplo gera um arquivo *. xml* com o conteúdo a seguir.</span><span class="sxs-lookup"><span data-stu-id="4c2bf-105">The example generates an *.xml* file with the following contents.</span></span>

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

## <a name="compiling-the-code"></a><span data-ttu-id="4c2bf-106">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="4c2bf-106">Compiling the code</span></span>

<span data-ttu-id="4c2bf-107">Para compilar o exemplo, digite o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="4c2bf-107">To compile the example, enter the following command:</span></span>

`csc XMLsample.cs /doc:XMLsample.xml`

<span data-ttu-id="4c2bf-108">Esse comando cria o arquivo XML *XMLsample. xml*, que pode ser exibido em seu navegador ou usando o `TYPE` comando.</span><span class="sxs-lookup"><span data-stu-id="4c2bf-108">This command creates the XML file *XMLsample.xml*, which you can view in your browser or by using the `TYPE` command.</span></span>

## <a name="robust-programming"></a><span data-ttu-id="4c2bf-109">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="4c2bf-109">Robust programming</span></span>

<span data-ttu-id="4c2bf-110">A documentação XML começa com `///` .</span><span class="sxs-lookup"><span data-stu-id="4c2bf-110">XML documentation starts with `///`.</span></span> <span data-ttu-id="4c2bf-111">Quando você cria um novo projeto, os assistentes colocam algumas linhas iniciais `///` no para você.</span><span class="sxs-lookup"><span data-stu-id="4c2bf-111">When you create a new project, the wizards put some starter `///` lines in for you.</span></span> <span data-ttu-id="4c2bf-112">O processamento desses comentários tem algumas restrições:</span><span class="sxs-lookup"><span data-stu-id="4c2bf-112">The processing of these comments has some restrictions:</span></span>

- <span data-ttu-id="4c2bf-113">A documentação deve ser em XML bem formado.</span><span class="sxs-lookup"><span data-stu-id="4c2bf-113">The documentation must be well-formed XML.</span></span> <span data-ttu-id="4c2bf-114">Se o XML não estiver bem formado, um aviso será gerado e o arquivo de documentação conterá um comentário que diz que foi encontrado um erro.</span><span class="sxs-lookup"><span data-stu-id="4c2bf-114">If the XML is not well-formed, a warning is generated and the documentation file will contain a comment that says that an error was encountered.</span></span>

- <span data-ttu-id="4c2bf-115">Os desenvolvedores são livres para criar seu próprio conjunto de marcas.</span><span class="sxs-lookup"><span data-stu-id="4c2bf-115">Developers are free to create their own set of tags.</span></span> <span data-ttu-id="4c2bf-116">Há um [conjunto recomendado de marcas](recommended-tags-for-documentation-comments.md).</span><span class="sxs-lookup"><span data-stu-id="4c2bf-116">There is a [recommended set of tags](recommended-tags-for-documentation-comments.md).</span></span> <span data-ttu-id="4c2bf-117">Algumas das marcas recomendadas têm significado especial:</span><span class="sxs-lookup"><span data-stu-id="4c2bf-117">Some of the recommended tags have special meanings:</span></span>

  - <span data-ttu-id="4c2bf-118">A `<param>` marca é usada para descrever os parâmetros.</span><span class="sxs-lookup"><span data-stu-id="4c2bf-118">The `<param>` tag is used to describe parameters.</span></span> <span data-ttu-id="4c2bf-119">Se ela é usada, o compilador verifica se o parâmetro existe e se todos os parâmetros são descritos na documentação.</span><span class="sxs-lookup"><span data-stu-id="4c2bf-119">If used, the compiler verifies that the parameter exists and that all parameters are described in the documentation.</span></span> <span data-ttu-id="4c2bf-120">Se a verificação falhar, o compilador emitirá um aviso.</span><span class="sxs-lookup"><span data-stu-id="4c2bf-120">If the verification fails, the compiler issues a warning.</span></span>

  - <span data-ttu-id="4c2bf-121">O `cref` atributo pode ser anexado a qualquer marca para fazer referência a um elemento de código.</span><span class="sxs-lookup"><span data-stu-id="4c2bf-121">The `cref` attribute can be attached to any tag to reference a code element.</span></span> <span data-ttu-id="4c2bf-122">O compilador verifica se esse elemento de código existe.</span><span class="sxs-lookup"><span data-stu-id="4c2bf-122">The compiler verifies that this code element exists.</span></span> <span data-ttu-id="4c2bf-123">Se a verificação falhar, o compilador emitirá um aviso.</span><span class="sxs-lookup"><span data-stu-id="4c2bf-123">If the verification fails, the compiler issues a warning.</span></span> <span data-ttu-id="4c2bf-124">O compilador respeita qualquer instrução `using` quando procura por um tipo descrito no atributo `cref`.</span><span class="sxs-lookup"><span data-stu-id="4c2bf-124">The compiler respects any `using` statements when it looks for a type described in the `cref` attribute.</span></span>

  - <span data-ttu-id="4c2bf-125">A `<summary>` marca é usada pelo IntelliSense dentro do Visual Studio para exibir informações adicionais sobre um tipo ou membro.</span><span class="sxs-lookup"><span data-stu-id="4c2bf-125">The `<summary>` tag is used by IntelliSense inside Visual Studio to display additional information about a type or member.</span></span>

    > [!NOTE]
    > <span data-ttu-id="4c2bf-126">O arquivo XML não fornece informações completas sobre o tipo e os membros (por exemplo, ele não contém nenhuma informação de tipo).</span><span class="sxs-lookup"><span data-stu-id="4c2bf-126">The XML file does not provide full information about the type and members (for example, it does not contain any type information).</span></span> <span data-ttu-id="4c2bf-127">Para obter informações completas sobre um tipo ou membro, use o arquivo de documentação junto com a reflexão no tipo ou membro real.</span><span class="sxs-lookup"><span data-stu-id="4c2bf-127">To get full information about a type or member, use the documentation file together with reflection on the actual type or member.</span></span>

## <a name="see-also"></a><span data-ttu-id="4c2bf-128">Veja também</span><span class="sxs-lookup"><span data-stu-id="4c2bf-128">See also</span></span>

- [<span data-ttu-id="4c2bf-129">Guia de programação em C#</span><span class="sxs-lookup"><span data-stu-id="4c2bf-129">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="4c2bf-130">-Doc (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="4c2bf-130">-doc (C# compiler options)</span></span>](../../language-reference/compiler-options/doc-compiler-option.md)
- [<span data-ttu-id="4c2bf-131">Comentários da documentação XML</span><span class="sxs-lookup"><span data-stu-id="4c2bf-131">XML documentation comments</span></span>](./index.md)
- [<span data-ttu-id="4c2bf-132">Processador de documentação do DocFX</span><span class="sxs-lookup"><span data-stu-id="4c2bf-132">DocFX documentation processor</span></span>](https://dotnet.github.io/docfx/)
- [<span data-ttu-id="4c2bf-133">Processador de documentação do Sandcastle</span><span class="sxs-lookup"><span data-stu-id="4c2bf-133">Sandcastle documentation processor</span></span>](https://github.com/EWSoftware/SHFB)
