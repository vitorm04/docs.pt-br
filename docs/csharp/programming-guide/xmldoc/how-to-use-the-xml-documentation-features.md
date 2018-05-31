---
title: Como usar as Funcionalidades da Documentação XML (Guia de Programação em C#)
ms.date: 07/20/2015
helpviewer_keywords:
- XML documentation [C#]
- C# language, XML documentation features
ms.assetid: 8f33917b-9577-4c9a-818a-640dbbb0b399
ms.openlocfilehash: d7f1f51040033cf25f7f1aefb04d249e6e028ca3
ms.sourcegitcommit: 77d9a94dac4c05827ed0663d95e0f9ad35d6682e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2018
ms.locfileid: "34472770"
---
# <a name="how-to-use-the-xml-documentation-features-c-programming-guide"></a><span data-ttu-id="c6754-102">Como usar as Funcionalidades da Documentação XML (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="c6754-102">How to: Use the XML Documentation Features (C# Programming Guide)</span></span>
<span data-ttu-id="c6754-103">O exemplo a seguir fornece uma visão geral básica de um tipo que foi documentado.</span><span class="sxs-lookup"><span data-stu-id="c6754-103">The following sample provides a basic overview of a type that has been documented.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c6754-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c6754-104">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#15](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/how-to-use-the-xml-documentation-features_1.cs)]  

<span data-ttu-id="c6754-105">O exemplo gera um arquivo .xml com o seguinte conteúdo:</span><span class="sxs-lookup"><span data-stu-id="c6754-105">The example generates an .xml file with the following contents:</span></span>

```xml  
<?xml version="1.0"?>  
<doc>  
 <assembly>  
 <name>xmlsample</name>  
 </assembly>  
 <members>  
 <member name="T:SomeClass">  
 <summary>  
 Class level summary documentation goes here.</summary>  
 <remarks>  
 Longer comments can be associated with a type or member  
 through the remarks tag</remarks>  
 </member>  
 <member name="F:SomeClass.m_Name">  
 <summary>  
 Store for the name property</summary>  
 </member>  
 <member name="M:SomeClass.#ctor">  
 <summary>The class constructor.</summary>  
 </member>  
 <member name="M:SomeClass.SomeMethod(System.String)">  
 <summary>  
 Description for SomeMethod.</summary>  
 <param name="s"> Parameter description for s goes here</param>  
 <seealso cref="T:System.String">  
 You can use the cref attribute on any tag to reference a type or member  
 and the compiler will check that the reference exists. </seealso>  
 </member>  
 <member name="M:SomeClass.SomeOtherMethod">  
 <summary>  
 Some other method. </summary>  
 <returns>  
 Return results are described through the returns tag.</returns>  
 <seealso cref="M:SomeClass.SomeMethod(System.String)">  
 Notice the use of the cref attribute to reference a specific method </seealso>  
 </member>  
 <member name="M:SomeClass.Main(System.String[])">  
 <summary>  
 The entry point for the application.  
 </summary>  
 <param name="args"> A list of command line arguments</param>  
 </member>  
 <member name="P:SomeClass.Name">  
 <summary>  
 Name property </summary>  
 <value>A value tag is used to describe the property value</value>  
 </member>  
 </members>  
</doc>   
```

## <a name="compiling-the-code"></a><span data-ttu-id="c6754-106">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="c6754-106">Compiling the Code</span></span>  
 <span data-ttu-id="c6754-107">Para compilar o exemplo, digite a seguinte linha de comando:</span><span class="sxs-lookup"><span data-stu-id="c6754-107">To compile the example, type the following command line:</span></span>  
  
 `csc XMLsample.cs /doc:XMLsample.xml`  
  
 <span data-ttu-id="c6754-108">Isso criará o arquivo XML XMLsample.xml, que você pode exibir em seu navegador ou usando o comando TYPE.</span><span class="sxs-lookup"><span data-stu-id="c6754-108">This will create the XML file XMLsample.xml, which you can view in your browser or by using the TYPE command.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="c6754-109">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="c6754-109">Robust Programming</span></span>  
 <span data-ttu-id="c6754-110">A documentação XML começa com ///.</span><span class="sxs-lookup"><span data-stu-id="c6754-110">XML documentation starts with ///.</span></span> <span data-ttu-id="c6754-111">Quando você cria um novo projeto, os assistentes colocam algumas linhas iniciais /// para você.</span><span class="sxs-lookup"><span data-stu-id="c6754-111">When you create a new project, the wizards put some starter /// lines in for you.</span></span> <span data-ttu-id="c6754-112">O processamento desses comentários tem algumas restrições:</span><span class="sxs-lookup"><span data-stu-id="c6754-112">The processing of these comments has some restrictions:</span></span>  
  
-   <span data-ttu-id="c6754-113">A documentação deve ser em XML bem formado.</span><span class="sxs-lookup"><span data-stu-id="c6754-113">The documentation must be well-formed XML.</span></span> <span data-ttu-id="c6754-114">Se o XML não estiver bem formado, um aviso será gerado e o arquivo de documentação conterá um comentário que diz que foi encontrado um erro.</span><span class="sxs-lookup"><span data-stu-id="c6754-114">If the XML is not well-formed, a warning is generated and the documentation file will contain a comment that says that an error was encountered.</span></span>  
  
-   <span data-ttu-id="c6754-115">Os desenvolvedores são livres para criar seu próprio conjunto de marcas.</span><span class="sxs-lookup"><span data-stu-id="c6754-115">Developers are free to create their own set of tags.</span></span> <span data-ttu-id="c6754-116">Há um conjunto de marcas recomendadas (confira [Marcas recomendadas para comentários da documentação](recommended-tags-for-documentation-comments.md)).</span><span class="sxs-lookup"><span data-stu-id="c6754-116">There is a recommended set of tags (see [Recommended tags for documentation comments](recommended-tags-for-documentation-comments.md)).</span></span> <span data-ttu-id="c6754-117">Algumas das marcas recomendadas têm significado especial:</span><span class="sxs-lookup"><span data-stu-id="c6754-117">Some of the recommended tags have special meanings:</span></span>  
  
    -   <span data-ttu-id="c6754-118">A marca \<param> é usada para descrever parâmetros.</span><span class="sxs-lookup"><span data-stu-id="c6754-118">The \<param> tag is used to describe parameters.</span></span> <span data-ttu-id="c6754-119">Se ela for usada, o compilador verificará se o parâmetro existe e se todos os parâmetros são descritos na documentação.</span><span class="sxs-lookup"><span data-stu-id="c6754-119">If used, the compiler will verify that the parameter exists and that all parameters are described in the documentation.</span></span> <span data-ttu-id="c6754-120">Se a verificação falhar, o compilador emitirá um aviso.</span><span class="sxs-lookup"><span data-stu-id="c6754-120">If the verification failed, the compiler issues a warning.</span></span>  
  
    -   <span data-ttu-id="c6754-121">O atributo `cref` pode ser anexado a qualquer marca para fornecer uma referência a um elemento de código.</span><span class="sxs-lookup"><span data-stu-id="c6754-121">The `cref` attribute can be attached to any tag to provide a reference to a code element.</span></span> <span data-ttu-id="c6754-122">O compilador verificará se este elemento de código existe.</span><span class="sxs-lookup"><span data-stu-id="c6754-122">The compiler will verify that this code element exists.</span></span> <span data-ttu-id="c6754-123">Se a verificação falhar, o compilador emitirá um aviso.</span><span class="sxs-lookup"><span data-stu-id="c6754-123">If the verification failed, the compiler issues a warning.</span></span> <span data-ttu-id="c6754-124">O compilador respeita qualquer instrução `using` quando procura por um tipo descrito no atributo `cref`.</span><span class="sxs-lookup"><span data-stu-id="c6754-124">The compiler respects any `using` statements when it looks for a type described in the `cref` attribute.</span></span>  
  
    -   <span data-ttu-id="c6754-125">A marca \<summary> é usada pelo IntelliSense no Visual Studio para exibir informações adicionais sobre um tipo ou membro.</span><span class="sxs-lookup"><span data-stu-id="c6754-125">The \<summary> tag is used by IntelliSense inside Visual Studio to display additional information about a type or member.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="c6754-126">O arquivo XML não fornece informações completas sobre o tipo e os membros (por exemplo, ele não contém nenhuma informação de tipo).</span><span class="sxs-lookup"><span data-stu-id="c6754-126">The XML file does not provide full information about the type and members (for example, it does not contain any type information).</span></span> <span data-ttu-id="c6754-127">Para obter informações completas sobre um tipo ou membro, o arquivo de documentação deve ser usado com a reflexão no membro ou tipo real.</span><span class="sxs-lookup"><span data-stu-id="c6754-127">To get full information about a type or member, the documentation file must be used together with reflection on the actual type or member.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6754-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c6754-128">See Also</span></span>  
 [<span data-ttu-id="c6754-129">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="c6754-129">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="c6754-130">-doc (opções do compilador do C#)</span><span class="sxs-lookup"><span data-stu-id="c6754-130">/doc (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)  
 [<span data-ttu-id="c6754-131">Comentários da documentação XML</span><span class="sxs-lookup"><span data-stu-id="c6754-131">XML Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)
