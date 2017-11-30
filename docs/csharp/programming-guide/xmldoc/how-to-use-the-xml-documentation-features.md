---
title: "Como usar as Funcionalidades da Documentação XML (Guia de Programação em C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- XML documentation [C#]
- C# language, XML documentation features
ms.assetid: 8f33917b-9577-4c9a-818a-640dbbb0b399
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: eb647a275a5cd5fac2316706591440d9792861b3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-the-xml-documentation-features-c-programming-guide"></a><span data-ttu-id="09680-102">Como usar as Funcionalidades da Documentação XML (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="09680-102">How to: Use the XML Documentation Features (C# Programming Guide)</span></span>
<span data-ttu-id="09680-103">O exemplo a seguir fornece uma visão geral básica de um tipo que foi documentado.</span><span class="sxs-lookup"><span data-stu-id="09680-103">The following sample provides a basic overview of a type that has been documented.</span></span>  
  
## <a name="example"></a><span data-ttu-id="09680-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="09680-104">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#15](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/how-to-use-the-xml-documentation-features_1.cs)]  
  
 <span data-ttu-id="09680-105">**// Este arquivo .xml foi gerado com o exemplo de código anterior.**</span><span class="sxs-lookup"><span data-stu-id="09680-105">**// This .xml file was generated with the previous code sample.**</span></span>  
<span data-ttu-id="09680-106">**\<?xml version="1.0"?>**</span><span class="sxs-lookup"><span data-stu-id="09680-106">**\<?xml version="1.0"?>**</span></span>  
<span data-ttu-id="09680-107">**\<doc>**</span><span class="sxs-lookup"><span data-stu-id="09680-107">**\<doc>**</span></span>  
 <span data-ttu-id="09680-108">**\<assembly>**</span><span class="sxs-lookup"><span data-stu-id="09680-108">**\<assembly>**</span></span>  
 <span data-ttu-id="09680-109">**\<name>xmlsample\</name>**</span><span class="sxs-lookup"><span data-stu-id="09680-109">**\<name>xmlsample\</name>**</span></span>  
 <span data-ttu-id="09680-110">**\</assembly>**</span><span class="sxs-lookup"><span data-stu-id="09680-110">**\</assembly>**</span></span>  
 <span data-ttu-id="09680-111">**\<members>**</span><span class="sxs-lookup"><span data-stu-id="09680-111">**\<members>**</span></span>  
 <span data-ttu-id="09680-112">**\<nome do membro="T:SomeClass">**</span><span class="sxs-lookup"><span data-stu-id="09680-112">**\<member name="T:SomeClass">**</span></span>  
 <span data-ttu-id="09680-113">**\<summary>**</span><span class="sxs-lookup"><span data-stu-id="09680-113">**\<summary>**</span></span>  
 <span data-ttu-id="09680-114">**A documentação de resumo de nível fica aqui. \</summary>**</span><span class="sxs-lookup"><span data-stu-id="09680-114">**Class level summary documentation goes here.\</summary>**</span></span>  
 <span data-ttu-id="09680-115">**\<remarks>**</span><span class="sxs-lookup"><span data-stu-id="09680-115">**\<remarks>**</span></span>  
 <span data-ttu-id="09680-116">**Mais comentários podem ser associados um tipo ou membro**</span><span class="sxs-lookup"><span data-stu-id="09680-116">**Longer comments can be associated with a type or member**</span></span>  
 <span data-ttu-id="09680-117">**por meio da marca de comentário\</remarks>**</span><span class="sxs-lookup"><span data-stu-id="09680-117">**through the remarks tag\</remarks>**</span></span>  
 <span data-ttu-id="09680-118">**\</member>**</span><span class="sxs-lookup"><span data-stu-id="09680-118">**\</member>**</span></span>  
 <span data-ttu-id="09680-119">**\<nome do membro="F:SomeClass.m_Name">**</span><span class="sxs-lookup"><span data-stu-id="09680-119">**\<member name="F:SomeClass.m_Name">**</span></span>  
 <span data-ttu-id="09680-120">**\<summary>**</span><span class="sxs-lookup"><span data-stu-id="09680-120">**\<summary>**</span></span>  
 <span data-ttu-id="09680-121">**Repositório para a propriedade de nome\</summary>**</span><span class="sxs-lookup"><span data-stu-id="09680-121">**Store for the name property\</summary>**</span></span>  
 <span data-ttu-id="09680-122">**\</member>**</span><span class="sxs-lookup"><span data-stu-id="09680-122">**\</member>**</span></span>  
 <span data-ttu-id="09680-123">**\<nome do membro="M:SomeClass.#ctor">**</span><span class="sxs-lookup"><span data-stu-id="09680-123">**\<member name="M:SomeClass.#ctor">**</span></span>  
 <span data-ttu-id="09680-124">**\<Resumo > o construtor da classe.  \< /summary >**</span><span class="sxs-lookup"><span data-stu-id="09680-124">**\<summary>The class constructor.\</summary>**</span></span>  
 <span data-ttu-id="09680-125">**\</member>**</span><span class="sxs-lookup"><span data-stu-id="09680-125">**\</member>**</span></span>  
 <span data-ttu-id="09680-126">**\<nome do membro="M:SomeClass.SomeMethod(System.String)">**</span><span class="sxs-lookup"><span data-stu-id="09680-126">**\<member name="M:SomeClass.SomeMethod(System.String)">**</span></span>  
 <span data-ttu-id="09680-127">**\<summary>**</span><span class="sxs-lookup"><span data-stu-id="09680-127">**\<summary>**</span></span>  
 <span data-ttu-id="09680-128">**Descrição de SomeMethod.\</summary>**</span><span class="sxs-lookup"><span data-stu-id="09680-128">**Description for SomeMethod.\</summary>**</span></span>  
 <span data-ttu-id="09680-129">**\<nome do parâmetro="s"> A descrição do parâmetro para s fica aqui\</param>**</span><span class="sxs-lookup"><span data-stu-id="09680-129">**\<param name="s"> Parameter description for s goes here\</param>**</span></span>  
 <span data-ttu-id="09680-130">**\<seealso cref="T:System.String">**</span><span class="sxs-lookup"><span data-stu-id="09680-130">**\<seealso cref="T:System.String">**</span></span>  
 <span data-ttu-id="09680-131">**Você pode usar o atributo cref em qualquer marca para fazer referência a um tipo ou membro**</span><span class="sxs-lookup"><span data-stu-id="09680-131">**You can use the cref attribute on any tag to reference a type or member**</span></span>  
 <span data-ttu-id="09680-132">**e o compilador verificará se a referência existe. \</seealso>**</span><span class="sxs-lookup"><span data-stu-id="09680-132">**and the compiler will check that the reference exists. \</seealso>**</span></span>  
 <span data-ttu-id="09680-133">**\</member>**</span><span class="sxs-lookup"><span data-stu-id="09680-133">**\</member>**</span></span>  
 <span data-ttu-id="09680-134">**\<nome do membro="M:SomeClass.SomeOtherMethod">**</span><span class="sxs-lookup"><span data-stu-id="09680-134">**\<member name="M:SomeClass.SomeOtherMethod">**</span></span>  
 <span data-ttu-id="09680-135">**\<summary>**</span><span class="sxs-lookup"><span data-stu-id="09680-135">**\<summary>**</span></span>  
 <span data-ttu-id="09680-136">**Algum outro método. \</summary>**</span><span class="sxs-lookup"><span data-stu-id="09680-136">**Some other method. \</summary>**</span></span>  
 <span data-ttu-id="09680-137">**\<returns>**</span><span class="sxs-lookup"><span data-stu-id="09680-137">**\<returns>**</span></span>  
 <span data-ttu-id="09680-138">**Resultados retornados são descritos por meio da marca returns. \</returns>**</span><span class="sxs-lookup"><span data-stu-id="09680-138">**Return results are described through the returns tag.\</returns>**</span></span>  
 <span data-ttu-id="09680-139">**\<seealso cref="M:SomeClass.SomeMethod(System.String)">**</span><span class="sxs-lookup"><span data-stu-id="09680-139">**\<seealso cref="M:SomeClass.SomeMethod(System.String)">**</span></span>  
 <span data-ttu-id="09680-140">**Observe o uso do atributo cref para fazer referência a um método específico \</seealso>**</span><span class="sxs-lookup"><span data-stu-id="09680-140">**Notice the use of the cref attribute to reference a specific method \</seealso>**</span></span>  
 <span data-ttu-id="09680-141">**\</member>**</span><span class="sxs-lookup"><span data-stu-id="09680-141">**\</member>**</span></span>  
 <span data-ttu-id="09680-142">**\<nome do membro="M:SomeClass.Main(System.String[])">**</span><span class="sxs-lookup"><span data-stu-id="09680-142">**\<member name="M:SomeClass.Main(System.String[])">**</span></span>  
 <span data-ttu-id="09680-143">**\<summary>**</span><span class="sxs-lookup"><span data-stu-id="09680-143">**\<summary>**</span></span>  
 <span data-ttu-id="09680-144">**O ponto de entrada do aplicativo.**</span><span class="sxs-lookup"><span data-stu-id="09680-144">**The entry point for the application.**</span></span>  
 <span data-ttu-id="09680-145">**\</summary>**</span><span class="sxs-lookup"><span data-stu-id="09680-145">**\</summary>**</span></span>  
 <span data-ttu-id="09680-146">**\<nome do parâmetro ="args"> Uma lista de argumentos de linha de comando\</param>**</span><span class="sxs-lookup"><span data-stu-id="09680-146">**\<param name="args"> A list of command line arguments\</param>**</span></span>  
 <span data-ttu-id="09680-147">**\</member>**</span><span class="sxs-lookup"><span data-stu-id="09680-147">**\</member>**</span></span>  
 <span data-ttu-id="09680-148">**\<nome do membro="P:SomeClass.Name">**</span><span class="sxs-lookup"><span data-stu-id="09680-148">**\<member name="P:SomeClass.Name">**</span></span>  
 <span data-ttu-id="09680-149">**\<summary>**</span><span class="sxs-lookup"><span data-stu-id="09680-149">**\<summary>**</span></span>  
 <span data-ttu-id="09680-150">**Propriedade de nome \</summary>**</span><span class="sxs-lookup"><span data-stu-id="09680-150">**Name property \</summary>**</span></span>  
 <span data-ttu-id="09680-151">**\<value>**</span><span class="sxs-lookup"><span data-stu-id="09680-151">**\<value>**</span></span>  
 <span data-ttu-id="09680-152">**Uma marca value é usada para descrever o valor da propriedade \</value>**</span><span class="sxs-lookup"><span data-stu-id="09680-152">**A value tag is used to describe the property value\</value>**</span></span>  
 <span data-ttu-id="09680-153">**\</member>**</span><span class="sxs-lookup"><span data-stu-id="09680-153">**\</member>**</span></span>  
 <span data-ttu-id="09680-154">**\</members>**</span><span class="sxs-lookup"><span data-stu-id="09680-154">**\</members>**</span></span>  
<span data-ttu-id="09680-155">**\</doc>**</span><span class="sxs-lookup"><span data-stu-id="09680-155">**\</doc>**</span></span>   
## <a name="compiling-the-code"></a><span data-ttu-id="09680-156">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="09680-156">Compiling the Code</span></span>  
 <span data-ttu-id="09680-157">Para compilar o exemplo, digite a seguinte linha de comando:</span><span class="sxs-lookup"><span data-stu-id="09680-157">To compile the example, type the following command line:</span></span>  
  
 `csc XMLsample.cs /doc:XMLsample.xml`  
  
 <span data-ttu-id="09680-158">Isso criará o arquivo XML XMLsample.xml, que você pode exibir em seu navegador ou usando o comando TYPE.</span><span class="sxs-lookup"><span data-stu-id="09680-158">This will create the XML file XMLsample.xml, which you can view in your browser or by using the TYPE command.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="09680-159">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="09680-159">Robust Programming</span></span>  
 <span data-ttu-id="09680-160">A documentação XML começa com ///.</span><span class="sxs-lookup"><span data-stu-id="09680-160">XML documentation starts with ///.</span></span> <span data-ttu-id="09680-161">Quando você cria um novo projeto, os assistentes colocam algumas linhas iniciais /// para você.</span><span class="sxs-lookup"><span data-stu-id="09680-161">When you create a new project, the wizards put some starter /// lines in for you.</span></span> <span data-ttu-id="09680-162">O processamento desses comentários tem algumas restrições:</span><span class="sxs-lookup"><span data-stu-id="09680-162">The processing of these comments has some restrictions:</span></span>  
  
-   <span data-ttu-id="09680-163">A documentação deve ser em XML bem formado.</span><span class="sxs-lookup"><span data-stu-id="09680-163">The documentation must be well-formed XML.</span></span> <span data-ttu-id="09680-164">Se o XML não estiver bem formado, um aviso será gerado e o arquivo de documentação conterá um comentário que diz que foi encontrado um erro.</span><span class="sxs-lookup"><span data-stu-id="09680-164">If the XML is not well-formed, a warning is generated and the documentation file will contain a comment that says that an error was encountered.</span></span>  
  
-   <span data-ttu-id="09680-165">Os desenvolvedores são livres para criar seu próprio conjunto de marcas.</span><span class="sxs-lookup"><span data-stu-id="09680-165">Developers are free to create their own set of tags.</span></span> <span data-ttu-id="09680-166">Há um conjunto de marcas recomendado (consulte a seção de Leituras complementares).</span><span class="sxs-lookup"><span data-stu-id="09680-166">There is a recommended set of tags (see the Further Reading section).</span></span> <span data-ttu-id="09680-167">Algumas das marcas recomendadas têm significado especial:</span><span class="sxs-lookup"><span data-stu-id="09680-167">Some of the recommended tags have special meanings:</span></span>  
  
    -   <span data-ttu-id="09680-168">A marca \<param> é usada para descrever parâmetros.</span><span class="sxs-lookup"><span data-stu-id="09680-168">The \<param> tag is used to describe parameters.</span></span> <span data-ttu-id="09680-169">Se ela for usada, o compilador verificará se o parâmetro existe e se todos os parâmetros são descritos na documentação.</span><span class="sxs-lookup"><span data-stu-id="09680-169">If used, the compiler will verify that the parameter exists and that all parameters are described in the documentation.</span></span> <span data-ttu-id="09680-170">Se a verificação falhar, o compilador emitirá um aviso.</span><span class="sxs-lookup"><span data-stu-id="09680-170">If the verification failed, the compiler issues a warning.</span></span>  
  
    -   <span data-ttu-id="09680-171">O atributo `cref` pode ser anexado a qualquer marca para fornecer uma referência a um elemento de código.</span><span class="sxs-lookup"><span data-stu-id="09680-171">The `cref` attribute can be attached to any tag to provide a reference to a code element.</span></span> <span data-ttu-id="09680-172">O compilador verificará se este elemento de código existe.</span><span class="sxs-lookup"><span data-stu-id="09680-172">The compiler will verify that this code element exists.</span></span> <span data-ttu-id="09680-173">Se a verificação falhar, o compilador emitirá um aviso.</span><span class="sxs-lookup"><span data-stu-id="09680-173">If the verification failed, the compiler issues a warning.</span></span> <span data-ttu-id="09680-174">O compilador respeita qualquer instrução `using` quando procura por um tipo descrito no atributo `cref`.</span><span class="sxs-lookup"><span data-stu-id="09680-174">The compiler respects any `using` statements when it looks for a type described in the `cref` attribute.</span></span>  
  
    -   <span data-ttu-id="09680-175">A marca \<summary> é usada pelo IntelliSense no Visual Studio para exibir informações adicionais sobre um tipo ou membro.</span><span class="sxs-lookup"><span data-stu-id="09680-175">The \<summary> tag is used by IntelliSense inside Visual Studio to display additional information about a type or member.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="09680-176">O arquivo XML não fornece informações completas sobre o tipo e os membros (por exemplo, ele não contém nenhuma informação de tipo).</span><span class="sxs-lookup"><span data-stu-id="09680-176">The XML file does not provide full information about the type and members (for example, it does not contain any type information).</span></span> <span data-ttu-id="09680-177">Para obter informações completas sobre um tipo ou membro, o arquivo de documentação deve ser usado com a reflexão no membro ou tipo real.</span><span class="sxs-lookup"><span data-stu-id="09680-177">To get full information about a type or member, the documentation file must be used together with reflection on the actual type or member.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09680-178">Consulte também</span><span class="sxs-lookup"><span data-stu-id="09680-178">See Also</span></span>  
 [<span data-ttu-id="09680-179">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="09680-179">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="09680-180">/doc (opções do compilador c#)</span><span class="sxs-lookup"><span data-stu-id="09680-180">/doc (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)  
 [<span data-ttu-id="09680-181">Comentários da documentação XML</span><span class="sxs-lookup"><span data-stu-id="09680-181">XML Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)
