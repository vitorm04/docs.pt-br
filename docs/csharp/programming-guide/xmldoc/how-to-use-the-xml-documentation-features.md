---
title: "Como usar as Funcionalidades da Documentação XML (Guia de Programação em C#)"
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: eeee77db523bc0ad97f425d4ba8076ae5740dfe8
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-use-the-xml-documentation-features-c-programming-guide"></a><span data-ttu-id="f5577-102">Como usar as Funcionalidades da Documentação XML (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="f5577-102">How to: Use the XML Documentation Features (C# Programming Guide)</span></span>
<span data-ttu-id="f5577-103">O exemplo a seguir fornece uma visão geral básica de um tipo que foi documentado.</span><span class="sxs-lookup"><span data-stu-id="f5577-103">The following sample provides a basic overview of a type that has been documented.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f5577-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f5577-104">Example</span></span>  
 <span data-ttu-id="f5577-105">[!code-cs[csProgGuideDocComments#15](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/how-to-use-the-xml-documentation-features_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="f5577-105">[!code-cs[csProgGuideDocComments#15](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/how-to-use-the-xml-documentation-features_1.cs)]</span></span>  
  
 <span data-ttu-id="f5577-106">**// Este arquivo .xml foi gerado com o exemplo de código anterior.**</span><span class="sxs-lookup"><span data-stu-id="f5577-106">**// This .xml file was generated with the previous code sample.**</span></span>  
<span data-ttu-id="f5577-107">**\<?xml version="1.0"?>**</span><span class="sxs-lookup"><span data-stu-id="f5577-107">**\<?xml version="1.0"?>**</span></span>  
<span data-ttu-id="f5577-108">**\<doc>**</span><span class="sxs-lookup"><span data-stu-id="f5577-108">**\<doc>**</span></span>  
 <span data-ttu-id="f5577-109">**\<assembly>**</span><span class="sxs-lookup"><span data-stu-id="f5577-109">**\<assembly>**</span></span>  
 <span data-ttu-id="f5577-110">**\<name>xmlsample\</name>**</span><span class="sxs-lookup"><span data-stu-id="f5577-110">**\<name>xmlsample\</name>**</span></span>  
 <span data-ttu-id="f5577-111">**\</assembly>**</span><span class="sxs-lookup"><span data-stu-id="f5577-111">**\</assembly>**</span></span>  
 <span data-ttu-id="f5577-112">**\<members>**</span><span class="sxs-lookup"><span data-stu-id="f5577-112">**\<members>**</span></span>  
 <span data-ttu-id="f5577-113">**\<nome do membro="T:SomeClass">**</span><span class="sxs-lookup"><span data-stu-id="f5577-113">**\<member name="T:SomeClass">**</span></span>  
 <span data-ttu-id="f5577-114">**\<summary>**</span><span class="sxs-lookup"><span data-stu-id="f5577-114">**\<summary>**</span></span>  
 <span data-ttu-id="f5577-115">**A documentação de resumo de nível fica aqui. \</summary>**</span><span class="sxs-lookup"><span data-stu-id="f5577-115">**Class level summary documentation goes here.\</summary>**</span></span>  
 <span data-ttu-id="f5577-116">**\<remarks>**</span><span class="sxs-lookup"><span data-stu-id="f5577-116">**\<remarks>**</span></span>  
 <span data-ttu-id="f5577-117">**Comentários mais longos podem ser associados a um tipo ou membro** </span><span class="sxs-lookup"><span data-stu-id="f5577-117">**Longer comments can be associated with a type or member** </span></span>  
 <span data-ttu-id="f5577-118">**por meio da marca de comentário\</remarks>**</span><span class="sxs-lookup"><span data-stu-id="f5577-118">**through the remarks tag\</remarks>**</span></span>  
 <span data-ttu-id="f5577-119">**\</member>**</span><span class="sxs-lookup"><span data-stu-id="f5577-119">**\</member>**</span></span>  
 <span data-ttu-id="f5577-120">**\<nome do membro="F:SomeClass.m_Name">**</span><span class="sxs-lookup"><span data-stu-id="f5577-120">**\<member name="F:SomeClass.m_Name">**</span></span>  
 <span data-ttu-id="f5577-121">**\<summary>**</span><span class="sxs-lookup"><span data-stu-id="f5577-121">**\<summary>**</span></span>  
 <span data-ttu-id="f5577-122">**Repositório para a propriedade de nome\</summary>**</span><span class="sxs-lookup"><span data-stu-id="f5577-122">**Store for the name property\</summary>**</span></span>  
 <span data-ttu-id="f5577-123">**\</member>**</span><span class="sxs-lookup"><span data-stu-id="f5577-123">**\</member>**</span></span>  
 <span data-ttu-id="f5577-124">**\<nome do membro="M:SomeClass.#ctor">**</span><span class="sxs-lookup"><span data-stu-id="f5577-124">**\<member name="M:SomeClass.#ctor">**</span></span>  
 <span data-ttu-id="f5577-125">**\<summary>O construtor de classe.\</summary>** </span><span class="sxs-lookup"><span data-stu-id="f5577-125">**\<summary>The class constructor.\</summary>** </span></span>  
 <span data-ttu-id="f5577-126">**\</member>**</span><span class="sxs-lookup"><span data-stu-id="f5577-126">**\</member>**</span></span>  
 <span data-ttu-id="f5577-127">**\<nome do membro="M:SomeClass.SomeMethod(System.String)">**</span><span class="sxs-lookup"><span data-stu-id="f5577-127">**\<member name="M:SomeClass.SomeMethod(System.String)">**</span></span>  
 <span data-ttu-id="f5577-128">**\<summary>**</span><span class="sxs-lookup"><span data-stu-id="f5577-128">**\<summary>**</span></span>  
 <span data-ttu-id="f5577-129">**Descrição de SomeMethod.\</summary>**</span><span class="sxs-lookup"><span data-stu-id="f5577-129">**Description for SomeMethod.\</summary>**</span></span>  
 <span data-ttu-id="f5577-130">**\<nome do parâmetro="s"> A descrição do parâmetro para s fica aqui\</param>**</span><span class="sxs-lookup"><span data-stu-id="f5577-130">**\<param name="s"> Parameter description for s goes here\</param>**</span></span>  
 <span data-ttu-id="f5577-131">**\<seealso cref="T:System.String">**</span><span class="sxs-lookup"><span data-stu-id="f5577-131">**\<seealso cref="T:System.String">**</span></span>  
 <span data-ttu-id="f5577-132">**Você pode usar o atributo cref em qualquer marca para fazer referência a um tipo ou membro** </span><span class="sxs-lookup"><span data-stu-id="f5577-132">**You can use the cref attribute on any tag to reference a type or member** </span></span>  
 <span data-ttu-id="f5577-133">**e o compilador verificará se a referência existe. \</seealso>**</span><span class="sxs-lookup"><span data-stu-id="f5577-133">**and the compiler will check that the reference exists. \</seealso>**</span></span>  
 <span data-ttu-id="f5577-134">**\</member>**</span><span class="sxs-lookup"><span data-stu-id="f5577-134">**\</member>**</span></span>  
 <span data-ttu-id="f5577-135">**\<nome do membro="M:SomeClass.SomeOtherMethod">**</span><span class="sxs-lookup"><span data-stu-id="f5577-135">**\<member name="M:SomeClass.SomeOtherMethod">**</span></span>  
 <span data-ttu-id="f5577-136">**\<summary>**</span><span class="sxs-lookup"><span data-stu-id="f5577-136">**\<summary>**</span></span>  
 <span data-ttu-id="f5577-137">**Algum outro método. \</summary>**</span><span class="sxs-lookup"><span data-stu-id="f5577-137">**Some other method. \</summary>**</span></span>  
 <span data-ttu-id="f5577-138">**\<returns>**</span><span class="sxs-lookup"><span data-stu-id="f5577-138">**\<returns>**</span></span>  
 <span data-ttu-id="f5577-139">**Resultados retornados são descritos por meio da marca returns. \</returns>**</span><span class="sxs-lookup"><span data-stu-id="f5577-139">**Return results are described through the returns tag.\</returns>**</span></span>  
 <span data-ttu-id="f5577-140">**\<seealso cref="M:SomeClass.SomeMethod(System.String)">**</span><span class="sxs-lookup"><span data-stu-id="f5577-140">**\<seealso cref="M:SomeClass.SomeMethod(System.String)">**</span></span>  
 <span data-ttu-id="f5577-141">**Observe o uso do atributo cref para fazer referência a um método específico \</seealso>**</span><span class="sxs-lookup"><span data-stu-id="f5577-141">**Notice the use of the cref attribute to reference a specific method \</seealso>**</span></span>  
 <span data-ttu-id="f5577-142">**\</member>**</span><span class="sxs-lookup"><span data-stu-id="f5577-142">**\</member>**</span></span>  
 <span data-ttu-id="f5577-143">**\<nome do membro="M:SomeClass.Main(System.String[])">**</span><span class="sxs-lookup"><span data-stu-id="f5577-143">**\<member name="M:SomeClass.Main(System.String[])">**</span></span>  
 <span data-ttu-id="f5577-144">**\<summary>**</span><span class="sxs-lookup"><span data-stu-id="f5577-144">**\<summary>**</span></span>  
 <span data-ttu-id="f5577-145">**O ponto de entrada do aplicativo.**</span><span class="sxs-lookup"><span data-stu-id="f5577-145">**The entry point for the application.**</span></span>  
 <span data-ttu-id="f5577-146">**\</summary>**</span><span class="sxs-lookup"><span data-stu-id="f5577-146">**\</summary>**</span></span>  
 <span data-ttu-id="f5577-147">**\<nome do parâmetro ="args"> Uma lista de argumentos de linha de comando\</param>**</span><span class="sxs-lookup"><span data-stu-id="f5577-147">**\<param name="args"> A list of command line arguments\</param>**</span></span>  
 <span data-ttu-id="f5577-148">**\</member>**</span><span class="sxs-lookup"><span data-stu-id="f5577-148">**\</member>**</span></span>  
 <span data-ttu-id="f5577-149">**\<nome do membro="P:SomeClass.Name">**</span><span class="sxs-lookup"><span data-stu-id="f5577-149">**\<member name="P:SomeClass.Name">**</span></span>  
 <span data-ttu-id="f5577-150">**\<summary>**</span><span class="sxs-lookup"><span data-stu-id="f5577-150">**\<summary>**</span></span>  
 <span data-ttu-id="f5577-151">**Propriedade de nome \</summary>**</span><span class="sxs-lookup"><span data-stu-id="f5577-151">**Name property \</summary>**</span></span>  
 <span data-ttu-id="f5577-152">**\<value>**</span><span class="sxs-lookup"><span data-stu-id="f5577-152">**\<value>**</span></span>  
 <span data-ttu-id="f5577-153">**Uma marca value é usada para descrever o valor da propriedade \</value>**</span><span class="sxs-lookup"><span data-stu-id="f5577-153">**A value tag is used to describe the property value\</value>**</span></span>  
 <span data-ttu-id="f5577-154">**\</member>**</span><span class="sxs-lookup"><span data-stu-id="f5577-154">**\</member>**</span></span>  
 <span data-ttu-id="f5577-155">**\</members>**</span><span class="sxs-lookup"><span data-stu-id="f5577-155">**\</members>**</span></span>  
<span data-ttu-id="f5577-156">**\</doc>**</span><span class="sxs-lookup"><span data-stu-id="f5577-156">**\</doc>**</span></span>   
## <a name="compiling-the-code"></a><span data-ttu-id="f5577-157">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="f5577-157">Compiling the Code</span></span>  
 <span data-ttu-id="f5577-158">Para compilar o exemplo, digite a seguinte linha de comando:</span><span class="sxs-lookup"><span data-stu-id="f5577-158">To compile the example, type the following command line:</span></span>  
  
 `csc XMLsample.cs /doc:XMLsample.xml`  
  
 <span data-ttu-id="f5577-159">Isso criará o arquivo XML XMLsample.xml, que você pode exibir em seu navegador ou usando o comando TYPE.</span><span class="sxs-lookup"><span data-stu-id="f5577-159">This will create the XML file XMLsample.xml, which you can view in your browser or by using the TYPE command.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="f5577-160">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="f5577-160">Robust Programming</span></span>  
 <span data-ttu-id="f5577-161">A documentação XML começa com ///.</span><span class="sxs-lookup"><span data-stu-id="f5577-161">XML documentation starts with ///.</span></span> <span data-ttu-id="f5577-162">Quando você cria um novo projeto, os assistentes colocam algumas linhas iniciais /// para você.</span><span class="sxs-lookup"><span data-stu-id="f5577-162">When you create a new project, the wizards put some starter /// lines in for you.</span></span> <span data-ttu-id="f5577-163">O processamento desses comentários tem algumas restrições:</span><span class="sxs-lookup"><span data-stu-id="f5577-163">The processing of these comments has some restrictions:</span></span>  
  
-   <span data-ttu-id="f5577-164">A documentação deve ser em XML bem formado.</span><span class="sxs-lookup"><span data-stu-id="f5577-164">The documentation must be well-formed XML.</span></span> <span data-ttu-id="f5577-165">Se o XML não estiver bem formado, um aviso será gerado e o arquivo de documentação conterá um comentário que diz que foi encontrado um erro.</span><span class="sxs-lookup"><span data-stu-id="f5577-165">If the XML is not well-formed, a warning is generated and the documentation file will contain a comment that says that an error was encountered.</span></span>  
  
-   <span data-ttu-id="f5577-166">Os desenvolvedores são livres para criar seu próprio conjunto de marcas.</span><span class="sxs-lookup"><span data-stu-id="f5577-166">Developers are free to create their own set of tags.</span></span> <span data-ttu-id="f5577-167">Há um conjunto de marcas recomendado (consulte a seção de Leituras complementares).</span><span class="sxs-lookup"><span data-stu-id="f5577-167">There is a recommended set of tags (see the Further Reading section).</span></span> <span data-ttu-id="f5577-168">Algumas das marcas recomendadas têm significado especial:</span><span class="sxs-lookup"><span data-stu-id="f5577-168">Some of the recommended tags have special meanings:</span></span>  
  
    -   <span data-ttu-id="f5577-169">A marca \<param> é usada para descrever parâmetros.</span><span class="sxs-lookup"><span data-stu-id="f5577-169">The \<param> tag is used to describe parameters.</span></span> <span data-ttu-id="f5577-170">Se ela for usada, o compilador verificará se o parâmetro existe e se todos os parâmetros são descritos na documentação.</span><span class="sxs-lookup"><span data-stu-id="f5577-170">If used, the compiler will verify that the parameter exists and that all parameters are described in the documentation.</span></span> <span data-ttu-id="f5577-171">Se a verificação falhar, o compilador emitirá um aviso.</span><span class="sxs-lookup"><span data-stu-id="f5577-171">If the verification failed, the compiler issues a warning.</span></span>  
  
    -   <span data-ttu-id="f5577-172">O atributo `cref` pode ser anexado a qualquer marca para fornecer uma referência a um elemento de código.</span><span class="sxs-lookup"><span data-stu-id="f5577-172">The `cref` attribute can be attached to any tag to provide a reference to a code element.</span></span> <span data-ttu-id="f5577-173">O compilador verificará se este elemento de código existe.</span><span class="sxs-lookup"><span data-stu-id="f5577-173">The compiler will verify that this code element exists.</span></span> <span data-ttu-id="f5577-174">Se a verificação falhar, o compilador emitirá um aviso.</span><span class="sxs-lookup"><span data-stu-id="f5577-174">If the verification failed, the compiler issues a warning.</span></span> <span data-ttu-id="f5577-175">O compilador respeita qualquer instrução `using` quando procura por um tipo descrito no atributo `cref`.</span><span class="sxs-lookup"><span data-stu-id="f5577-175">The compiler respects any `using` statements when it looks for a type described in the `cref` attribute.</span></span>  
  
    -   <span data-ttu-id="f5577-176">A marca \<summary> é usada pelo IntelliSense no Visual Studio para exibir informações adicionais sobre um tipo ou membro.</span><span class="sxs-lookup"><span data-stu-id="f5577-176">The \<summary> tag is used by IntelliSense inside Visual Studio to display additional information about a type or member.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="f5577-177">O arquivo XML não fornece informações completas sobre o tipo e os membros (por exemplo, ele não contém nenhuma informação de tipo).</span><span class="sxs-lookup"><span data-stu-id="f5577-177">The XML file does not provide full information about the type and members (for example, it does not contain any type information).</span></span> <span data-ttu-id="f5577-178">Para obter informações completas sobre um tipo ou membro, o arquivo de documentação deve ser usado com a reflexão no membro ou tipo real.</span><span class="sxs-lookup"><span data-stu-id="f5577-178">To get full information about a type or member, the documentation file must be used together with reflection on the actual type or member.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5577-179">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f5577-179">See Also</span></span>  
 <span data-ttu-id="f5577-180">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="f5577-180">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="f5577-181">[/doc (Opções do compilador C#)](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) </span><span class="sxs-lookup"><span data-stu-id="f5577-181">[/doc (C# Compiler Options)](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) </span></span>  
 [<span data-ttu-id="f5577-182">Comentários da documentação XML</span><span class="sxs-lookup"><span data-stu-id="f5577-182">XML Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)

